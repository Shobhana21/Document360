The CI/CD flow lets you keep your API documentation automatically in sync with your spec file. Instead of manually uploading a new spec every time your API changes, you integrate the Document360 CLI (`d360`) into your existing pipeline. When your spec changes, the pipeline runs and your documentation updates automatically.

---

## Requirements

Before setting up the CI/CD flow, ensure the following:

- The latest version of **Node.js** is installed on the system running the pipeline.
- You have your **Document360 API key**, **user ID**, and **API reference ID** available.
- Your spec file is accessible either as a local file path or a hosted URL from within the pipeline environment.

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
If you are unfamiliar with Node.js installation, refer to the <a href="https://nodejs.org/en/learn/getting-started/how-to-install-nodejs" target="_blank">official Node.js documentation</a> for setup instructions.
:::

### Finding your API key, user ID, and API reference ID

Document360 does not provide separate standalone lookup screens for these values. Instead, all three are pre-populated for you inside a ready-to-run CLI command, available in two places:

- **When creating a new reference:** In the New API reference window, select the **CI/CD Flow** radio button.
- **For an existing reference:** Open the reference, click **Edit API reference**, then select **Show details** on the *"You can also update and resync the API Reference using our D360 npm package"* banner.

Either option displays the full `apidocs:resync` command with `--userId`, `--apiReferenceId`, and `--apiKey` already filled in.

:::(Warning) (IMPORTANT!)
The API token found under **Settings** > **Knowledge base portal** > **API tokens** is for the Document360 Customer (public) API and cannot be used with the d360 CI/CD flow. Always use the `--apiKey` value from the prefilled CLI command above.
:::

---

## Installing the Document360 CLI

The Document360 CLI tool is distributed as an npm package named `d360`. Install it globally:

```bash
npm install d360 -g
```

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
You only need to run this installation command once. If the CLI is already installed on the system, skip this step.
:::

---

## Initial setup: creating a new API reference via CLI

If you are setting up CI/CD for a new API reference, you can generate the initial import directly from the CLI.

1. In the Knowledge base portal, navigate to **API documentation** `{ }` in the left navigation bar.
2. Click the **Create** dropdown and select **New API**.
3. In the New API reference window, select the **CI/CD Flow** radio button.
4. Copy the full CLI command displayed in the window.
5. Replace the `--path` value in the copied command with the path to your spec file.

**Local file:**

```bash
--path=/Users/yourname/projects/api/openapi.yaml
```

**Hosted URL:**

```bash
--path=https://example.com/api/openapi.yaml
```

6. Paste the updated command into your terminal and press Enter.

Document360 uploads the spec file and generates the API reference.

---

## Resyncing an existing API reference

Once an API reference has been created, use the `apidocs:resync` command to update it when your spec changes. This is the command you will run in your CI/CD pipeline.

```bash
d360 apidocs:resync \
  --apiKey=YOUR_API_KEY \
  --userId=YOUR_USER_ID \
  --apiReferenceId=YOUR_API_REFERENCE_ID \
  --path=PATH_TO_SPEC_FILE
```

Replace the placeholder values:

| Parameter | What to put here |
|-----------|-----------------|
| `--apiKey` | Your Document360 API key |
| `--userId` | Your Document360 user ID |
| `--apiReferenceId` | The ID of the API reference to update |
| `--path` | Full path to your spec file, or a URL pointing to it |

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
Any custom content you have added to individual endpoint articles will be retained when a resync runs. Only the spec-generated content is updated.
:::

### Handling multiple spec files (monorepo)

The CLI does not provide a batch option — `--path` accepts a single spec file or URL.

To keep multiple services in sync from one repository, run a separate `apidocs:resync` command for each service, giving each its own `--apiReferenceId` and `--path`.

:::(Warning) (IMPORTANT)
Always pass `--path` explicitly in a monorepo. If it is omitted, the CLI auto-selects the first spec file it finds, which may not be the one you intend.
:::

### Detecting failures in your pipeline

The CLI does not currently use its exit code to signal whether an import or resync succeeded. A failed resync — for example, "Resync failed! We found N alert(s)" or an API error — is printed to the console, but the process still exits with code `0`. As a result, the pipeline step will appear to pass even when the spec was not updated.

To reliably detect failures, inspect the command's console output for failure messages and fail the step yourself if one is found, rather than relying on the exit code.

### Validating without publishing

There is no `--dry-run` flag. To validate a spec file without making any changes to your API reference, use the `apidocs:validate` command:

```bash
d360 apidocs:validate --apiKey=YOUR_API_KEY --path=PATH_TO_SPEC_FILE
```

This reports any errors or warnings in the spec without publishing or updating the reference. Note that `apidocs:validate` takes only `--apiKey` and `--path` — it does not require `--userId` or `--apiReferenceId`. Running it as a step before `apidocs:resync` is a good way to catch spec issues early in a pipeline.

---

## Managing your API key in CI

Your API key is a secret credential. Do not hardcode it in your pipeline configuration files or commit it to source control.

Store it as an environment variable or secret in your CI platform and reference it in the command:

```bash
d360 apidocs:resync \
  --apiKey=$DOCUMENT360_API_KEY \
  --userId=$DOCUMENT360_USER_ID \
  --apiReferenceId=$API_REFERENCE_ID \
  --path=./openapi.yaml
```

:::(Warning) (IMPORTANT!)
If you regenerate your API key in the Document360 portal, the old key immediately becomes invalid. Update the secret in your CI platform before the next pipeline run, or your resync will fail.
:::

---

## Pipeline examples

### GitHub Actions

Create `.github/workflows/api-docs.yml`:

```yaml
name: Sync API docs to Document360
on:
  push:
    branches: [main]
    paths: ['openapi.yaml']
jobs:
  resync:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 'lts/*'
      - run: npm install d360 -g
      - name: Resync to Document360
        shell: bash
        run: |
          set +e
          d360 apidocs:resync \
            --apiKey="${{ secrets.DOCUMENT360_API_KEY }}" \
            --userId="${{ secrets.DOCUMENT360_USER_ID }}" \
            --apiReferenceId="${{ secrets.API_REFERENCE_ID }}" \
            --path=./openapi.yaml \
            --force 2>&1 | tee resync.out
          grep -qi "Resync Successful" resync.out \
            || { echo "::error::Document360 resync failed"; exit 1; }
```

Store `DOCUMENT360_API_KEY`, `DOCUMENT360_USER_ID`, and `API_REFERENCE_ID` as repository secrets, using the values from the prefilled CLI command.

### GitLab CI

Add the following to `.gitlab-ci.yml`:

```yaml
stages:
  - sync

sync-api-docs:
  stage: sync
  image: node:lts
  rules:
    - if: '$CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH'
      changes: [openapi.yaml]
  script:
    - npm install d360 -g
    - |
      set +e
      d360 apidocs:resync \
        --apiKey="$DOCUMENT360_API_KEY" \
        --userId="$DOCUMENT360_USER_ID" \
        --apiReferenceId="$API_REFERENCE_ID" \
        --path=./openapi.yaml \
        --force 2>&1 | tee resync.out
      grep -qi "Resync Successful" resync.out || { echo "Document360 resync failed"; exit 1; }
```

Store `DOCUMENT360_API_KEY`, `DOCUMENT360_USER_ID`, and `API_REFERENCE_ID` as masked CI/CD variables under **Settings** > **CI/CD** > **Variables**.

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
GitLab cannot mask values containing hyphens, so the user ID and API reference ID will be stored unmasked.
:::

---

## Webhook support in CI/CD

Webhooks defined in your OpenAPI 3.1 spec are fully supported in CI/CD resync operations. When a resync runs, webhook definitions are updated along with the rest of the spec content.

---

## Helpful links

- <a href="https://www.npmjs.com/package/d360" target="_blank">d360 npm package</a>
- <a href="https://github.com/document360/d360" target="_blank">d360 source code</a>
