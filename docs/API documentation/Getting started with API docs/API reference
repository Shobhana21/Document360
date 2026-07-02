This article covers everything you need to manage your API references in Document360. Creating new references, keeping them in sync with your spec, and using the available actions to view, edit, publish, and organize your API documentation.

---

## API references list

The API references list gives you a central view of all configured API references in your workspace. To access it, navigate to **API documentation ({ })** in the left navigation bar and click **API references** in the left navigation pane.

From here you can see the name, type, and last updated date for each reference. You can also create a new API reference by clicking **New API** in the top right corner.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Managing-API-documentation-CreateNew.png" class="article_image" alt="API references list in Document360 showing configured references with options.">

---

## Create a new API reference

To create a new API reference, click the **Create** dropdown in the top navigation bar and select **New API**. This opens the New API reference window where you have four options:

- **Upload API definition** - Upload a JSON, YAML, or YML spec file directly from your device or from Document360 Drive.
- **Create from URL** - Fetch your spec automatically from a hosted URL.
- **CI/CD Flow** - Integrate with your pipeline to update documentation automatically on every spec change. Requires Node.js.
- **Try sample Pet Store API file** - Use Document360's sample spec file to explore the workspace before uploading your own.

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
Document360 supports OpenAPI 2.0, OpenAPI 3.0, OpenAPI 3.1, and Postman API specifications. Within each API workspace, you can create a maximum of 3 API references.
:::

### Upload API definition

1. Select the **Upload API definition** radio button.
2. Click **Upload from my device** to upload from your local storage, or **Choose from Drive** to select a file from Document360 Drive. You can also drag and drop your file directly into the window.
3. Document360 parses the file and generates the API reference. If warnings are detected, expand the **Alerts and Warnings** section to review them.
4. Click **New API reference** to proceed to the publish confirmation window.

### Create from URL

1. Select the **Create from URL** radio button and click **Next**.
2. Enter the URL pointing to your OpenAPI specification file.
3. Click **New API reference**. Document360 fetches and processes the spec.

### CI/CD flow

The CI/CD flow lets you keep your API documentation automatically in sync with your spec. Instead of manually uploading a new spec every time your API changes, you integrate the Document360 CLI into your pipeline so documentation updates automatically on every spec change.

For full setup instructions, see the <a href="https://docs.document360.com/docs/ci-cd-integration" target="_blank">CI/CD integration</a> article.

---

## API reference actions

Once an API reference is created, click the **More (⋯)** icon next to it in the API references list to access the following actions:

| Action | What it does |
|--------|-------------|
| Edit | Update the spec file or URL the reference was created from. |
| Resync | Regenerate the documentation from the latest version of the spec at the existing URL. |
| View API definition | Preview the raw API specification file. |
| Download original API source | Download the current version of the spec file to your local storage. |
| Publish | Publish all draft articles in the API reference to the Knowledge base site. |
| Delete | Permanently delete the API reference and all its generated content. |
| View logs | Review alerts, warnings, and errors from the most recent import or resync. |

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
To allow readers to download the API source file from the Knowledge base site, ensure the **Show download API source** toggle is turned on in the Knowledge base portal settings.
:::

---

## Keeping your documentation in sync

When your API changes - new endpoints added, parameters updated, responses modified, but you do not need to update your documentation manually. Regenerating your API reference pulls in all changes from your spec automatically.

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
Any custom content you have added to individual endpoint articles is retained when you regenerate your documentation. Only the spec-generated content is updated.
:::

### Resync from an existing URL

1. In the API references list, click the **More (⋯)** icon next to the reference you want to update.
2. Click **Resync**. The documentation regenerates from the latest version of the spec at the existing URL.

### Update to a new URL

1. Click the **More (⋯)** icon next to the reference.
2. Click **Edit**.
3. Enter the new URL in the **URL** field.
4. Click **Update**.

### Regenerate from a spec file

1. Click the **More (⋯)** icon next to the reference.
2. Click **Edit**.
3. Upload the latest spec file in JSON, YAML, or YML format.
4. Click **Update**.

### Resync via CI/CD

If your API reference was set up with the CI/CD flow, resyncing happens automatically as part of your pipeline whenever your spec changes. You can also trigger a manual resync using the `apidocs:resync` command:

```bash
d360 apidocs:resync \
  --apiKey=YOUR_API_KEY \
  --userId=YOUR_USER_ID \
  --apiReferenceId=YOUR_API_REFERENCE_ID \
  --path=PATH_TO_SPEC_FILE
```

For full details on setting up and managing the CI/CD flow, see the <a href="https://docs.document360.com/docs/ci-cd-integration" target="_blank">CI/CD integration</a> article.

---

## Automatic vs manual resync

| Creation method | Automatic resync | Manual resync |
|----------------|-----------------|--------------|
| File upload | Not available | Yes, via Edit in the portal |
| URL import | Not available | Yes, via Resync or Edit in the portal |
| CI/CD flow | Yes - runs as part of your pipeline | Yes, run the CLI command manually |

If you generated your API documentation from a URL or a file, it will not update automatically. To have documentation update automatically, integrate with the CI/CD flow.

---

## Understanding endpoint deletion during resync

When you update your API specification file, any endpoints that are no longer present in the new spec are permanently deleted along with any custom content added to those endpoint pages.

To update your spec file safely:

1. Upload the updated spec file in the **Edit API reference** window.
2. If any endpoints are deleted, a warning is displayed. Click **Show deleted endpoints** to review the list of affected endpoints.
3. Select the **Confirm to continue** checkbox to acknowledge the deletion.
4. Click **Update** to proceed.

Deleted endpoints are moved to the **Recycle bin**, where they can be previewed for up to 30 days but cannot be restored.

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
If you are using the resync API endpoint programmatically, send `ForceImport = false` to preview the list of endpoints that will be deleted without proceeding. Send `ForceImport = true` to confirm and proceed.
:::

---

## Keeping documentation in draft

After uploading or resyncing a spec, you can keep the resulting documentation in draft mode rather than publishing it immediately.

- In the publish confirmation window, click **Close** instead of **Publish**. All generated articles will remain in draft mode.
- Draft articles are visible in the Categories & Articles pane in the portal but are not accessible to readers on the Knowledge base site.
- You can review, edit, and add custom content to draft articles before publishing.

---

## Nested categories

Document360 supports up to three levels of subcategories in the API documentation workspace. Categories are created based on the tag definitions in your spec file.

To create nested categories, use the `>` symbol in your OpenAPI tags:

```yaml
tags:
  - name: "Pets > Details"
```

This creates a `Pets` category with a `Details` subcategory inside it. This structure is preserved during resync.

:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
If your spec defines more than three levels of nesting, any categories beyond the third level are placed at the third level.
:::

---

## Category ordering

The order in which categories appear in your documentation matches the tag order defined in your spec file. To change the category order, reorder the `tags` array in your spec and resync.

---

## Category options

Right-clicking a category in the Categories & Articles pane gives you the following options:

| Option | What it does |
|--------|-------------|
| Rename | Rename the category. |
| Article | Add a new article or sub-article inside the category. |
| Sub category | Add a subcategory inside the category. |
| Change type | Change the category type. |
| Set drive folder | Link the category to a Document360 Drive folder. |
| Edit API reference | Update the spec file or URL for the API reference. |
| Download original API source | Download the current spec file. |
| Publish | Publish all draft articles in the category. |
| Security | Configure who can access the category from the portal and the Knowledge base site. |
:::(Info) (<p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
You can move endpoint articles between subfolders within the same API reference folder. It is not possible to move an endpoint article from one API reference folder to a different API reference folder.
:::
---

## FAQ

<div class="faq-wrapper" data-type="details-wrapper">
<details open>
<summary><p>How often is an API reference resynced automatically?</p></summary>
<div data-type="details-content"><p>API references created from a URL or file are not resynced automatically. They must be updated manually via the portal. To enable automatic updates, integrate with the CI/CD flow.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>Can I move a specific API endpoint article from one API reference folder to another?</p></summary>
<div data-type="details-content"><p>No. You can move endpoint articles between subfolders within the same API reference folder, but not between different API reference folders.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>Can an API documentation article have the same URL as a Knowledge base article?</p></summary>
<div data-type="details-content"><p>No. API documentation articles and Knowledge base articles cannot share the same URL. However, they can exist under the same subdomain.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>Can I keep generated documentation in draft mode?</p></summary>
<div data-type="details-content"><p>Yes. After uploading a spec, click <strong>Close</strong> instead of <strong>Publish</strong> in the confirmation window. All generated articles will be saved in draft mode.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>How many levels of categories are supported?</p></summary>
<div data-type="details-content"><p>The API documentation workspace supports up to three levels of subcategories. Additional levels are collapsed to the third level.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>Can I create nested folders automatically from the spec file?</p></summary>
<div data-type="details-content"><p>Yes, using the <code>&gt;</code> symbol in OpenAPI tags (e.g. <code>Pets &gt; Details</code>). This creates a hierarchical structure that is preserved during resync.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>Can readers access the Knowledge base site during Document360 portal downtime?</p></summary>
<div data-type="details-content"><p>Yes. GET calls of the Customer API run independently of the Document360 portal, so readers can continue accessing the site during scheduled maintenance or portal downtime.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

---

## Helpful links

- <a href="https://www.npmjs.com/package/d360" target="_blank">d360 npm package</a>
- <a href="https://github.com/document360/d360" target="_blank">d360 source code</a>
