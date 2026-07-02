Creating an Eddy AI Chatbot lets you set up an AI-powered assistant trained on your content, ready to answer user questions on your website or knowledge base. The creation process involves selecting content sources (the material the chatbot uses to generate answers) and then configuring how the chatbot looks and behaves. You can create a chatbot from the **AI Chatbot**(<img data-block-id="mhkg3rrw-ge5yp1-047" src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Frame%201707479697.png" class="inline-icon" mediatype="img" alt="Frame image" width="auto" height="auto" dataalign="center" datadisplay="inline" data-type="media-content" fixaspectratio="false" autoaspectratio="false" shadow="no" border="no" round="no" link="" newtab="" style="width:auto;height:auto;">) section in the Knowledge Base portal, or during the Document360 onboarding flow when setting up a new project.

---

## When to create an Eddy AI Chatbot

- Use this when you are deploying a chatbot for the first time on your website or knowledge base.
- Use this when you need a separate chatbot for a different brand, product, or website.
- Use this during Document360 onboarding if you select **Eddy AI Chatbot** as your use case.

---

## Before you begin

- Identify which content sources you want to use (knowledge base, website, files, FAQs, text, Zendesk, or Freshdesk).
- If you plan to connect Zendesk or Freshdesk, have your API token and subdomain URL ready.
- Review the [Eddy AI Chatbot overview](01-ai-chatbot-overview.md) to understand storage limits and supported sources.

---

## How to create an Eddy AI Chatbot

### Create a chatbot from the portal

1. Navigate to **AI Chatbot** (<img data-block-id="mhkg3rrw-ge5yp1-047" src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Frame%201707479697.png" class="inline-icon" mediatype="img" alt="Frame image" width="auto" height="auto" dataalign="center" datadisplay="inline" data-type="media-content" fixaspectratio="false" autoaspectratio="false" shadow="no" border="no" round="no" link="" newtab="" style="width:auto;height:auto;">) in the left navigation bar of the Knowledge Base portal.
2. Click **Create Eddy AI Chatbot**.
   The portal prompts you to add sources for your chatbot.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Eddy%20AI%20Chatbot.png" class="article_image" alt="Eddy AI Chatbot interface with highlighted options for creating a chatbot easily.">

3. Select one or more source types and follow the steps for each source. See [Adding sources to your chatbot](#adding-sources-to-your-chatbot) below.
4. Click **Create chatbot** to complete setup.

The chatbot is created and you are taken to the chatbot configuration area.

---

## Adding sources to your chatbot

### Knowledge base

1. Click **Knowledge base** (<img data-block-id="mhkg3rrw-ge5yp1-047" src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Icon.png" class="inline-icon" mediatype="img" alt="Icon" width="auto" height="auto" dataalign="center" datadisplay="inline" data-type="media-content" fixaspectratio="false" autoaspectratio="false" shadow="no" border="no" round="no" link="" newtab="" style="width:auto;height:auto;">) from the list of available sources.
2. Choose a content access option:
   - **Allow all content** — includes all articles from all workspaces and categories. The chatbot learns from your entire documentation, including any new content added later.
   - **Allow selected content** — restricts the chatbot to specific parts of your knowledge base. Choose from:
     - **Selected workspaces and languages** — includes content from the workspaces and languages you select. New languages added to those workspaces later are included automatically.
     - **Selected categories** — includes only the specific categories you select. New categories added later are **not** included automatically and must be selected manually.

:::(Info) (<span class="fa-regular fa-circle-exclamation" data-type="icon"></span> NOTE)
When you select an entire workspace, any new languages added to that workspace later are included automatically. When you select specific categories, new articles added to those categories later are not included by default.
:::

3. Click **Create chatbot** to add the Knowledge Base source.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/image-1769524973245.png" class="article_image" alt="Knowledge base source configuration screen showing allow all content and allow selected content options.">

---

### Website

You can add website content in three ways: Crawl Links, Sitemap, or individual Webpages.

#### Crawl Links

Crawl Links let you provide a starting URL. The system automatically crawls linked pages within the same domain up to 3 levels deep.

1. Click **Website** (<span class="fa-regular fa-globe"></span>) from the list of sources.
2. Select the **Crawl Links** tab.
3. Click **+ Add new**.
4. Enter the following details:
   - **Source name** — a descriptive name for this crawl link source.
   - **URL** — the URL to start crawling from.
   - **Include only paths** (optional) — path patterns to limit crawling to specific sections. Example: `blog/`, `docs/`.
   - **Exclude paths** (optional) — path patterns to skip. Example: `admin/`, `privacy/`.
5. Click **Add crawl link**.

The system begins crawling the URL and shows a progress indicator. Once added, you can edit or delete the crawl link.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/image-1769525051016.png" class="article_image" alt="Crawl link progress indicator showing number of links being crawled.">

:::(Info) (<span class="fa-regular fa-circle-exclamation" data-type="icon"></span> NOTE)
A maximum of 200 links can be crawled per site. Individual crawl links can be recrawled up to 2 times per day.
:::

**Additional considerations for Crawl Links:**

- Crawling is limited to the same domain as the starting URL. External domains are ignored.
- The crawler follows links up to a maximum depth of 3 levels from the starting page.
- Up to 1,000 URLs can be crawled per crawl session.
- From any single page, a maximum of 200 discovered links are considered.
- The crawler respects `robots.txt` rules and skips disallowed paths automatically.
- Certain non-informational pages (such as social media, privacy policies, admin pages, and job listings) are excluded by default.

---

#### Sitemap

Sitemap lets you provide a sitemap URL. The system extracts content from all pages listed in the sitemap.

1. Click **Website** (<span class="fa-regular fa-globe"></span>) from the list of sources.
2. Select the **Sitemap** tab.
3. Click **+ Add new**.
4. Enter the following details:
   - **Source name** — a descriptive name for this sitemap source.
   - **URL** — the sitemap URL.
   - **Include only paths** (optional) — path patterns to include from the sitemap. Example: `blog/`, `help/`.
   - **Exclude paths** (optional) — path patterns to exclude. Example: `archive/`, `test/`.
5. Click **Add sitemap**.

The system fetches all URLs from the sitemap and begins extracting content. Once added, you can edit or delete the sitemap.

**Additional considerations for Sitemaps:**

- Only single-level sitemaps are supported. Nested or index sitemaps referencing other sitemap files are not processed.
- Sitemap file size must be under 1 MB.
- Up to 1,000 URLs can be extracted from a sitemap.
- Include and exclude path rules are applied before ingestion.

---

#### Webpage

Webpage lets you add individual page URLs manually for precise control over which pages to include.

1. Click **Website** (<span class="fa-regular fa-globe"></span>) from the list of sources.
2. Select the **Webpage** tab.
3. Click **+ Add new**.
4. Enter the following details:
   - **Source name** — a descriptive name for this webpage.
   - **URL** — the exact page URL.
5. Click **Add webpage**.
   Repeat for each additional page you want to include.

:::(Info) (<span class="fa-regular fa-circle-exclamation" data-type="icon"></span> NOTE)
Website content is ingested only if it matches the languages enabled for the project. Pages in unsupported languages are skipped automatically across all website sources.
:::

---

### Text

1. Click **Text** (<span class="fa-light fa-text"></span>) from the list of sources.
2. Click **+ Add new**.
3. Enter the following details:
   - **Source name** — a descriptive title for this text entry.
   - **Content** — enter or paste your text content.
4. Format your text using the available toolbar options: **Bold**, **Italic**, **Underline**, **Font color**, **Highlight**, **Hyperlink**.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Modal.png" class="article_image" alt="Text source entry modal with formatting toolbar options.">

5. Click **Add text**.
   Repeat for each additional text entry you want to include.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/image-1769525191809.png" class="article_image" alt="Text source list view showing added text entries and their last updated dates.">

---

### FAQ

1. Click **FAQ** (<span class="fa-light fa-comments-question"></span>) from the list of sources.
2. Click **+ Add new**.
3. Enter the following details:
   - **Question** — the question users might ask.
   - **Answer** — the complete answer to the question.
4. Format your answer using the available toolbar options: **Bold**, **Italic**, **Underline**, **Font color**, **Highlight**, **Hyperlink**.
5. Click **Add FAQ**.
   Repeat for each additional FAQ entry you want to include.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/image-1769525269366.png" class="article_image" alt="FAQ source list view with various chatbot entries and their last updated dates.">

---

### File

1. Click **File** (<span class="fa-light fa-file"></span>) from the list of sources.
2. Click **+ Add new**.
3. Choose one of the following upload methods:
   - **Upload from my device** — browse and select files from your computer.
   - **Choose from Drive** — select files from your Document360 Drive.
   - **Drag and drop** — drag files directly into the upload area.
4. Select one or multiple files to upload. Supported formats: **DOC**, **DOCX**, **PDF**, **MD (Markdown)**, **TXT**.
5. Click **Add files** to complete the upload.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/image-1769525357705.png" class="article_image" alt="File management interface displaying uploaded documents and their last updated dates.">

:::(Info) (<span class="fa-regular fa-circle-exclamation" data-type="icon"></span> NOTE)
There is no individual file size limit, but the total size of all sources must not exceed your chatbot's storage limit (40 MB by default). Only text content is extracted from files — images and other media are not stored. If a file upload fails, an error message appears. Fix the issue and try uploading again.
:::

---

### Zendesk

1. Click **Zendesk** (<span class="fa-light fa-book-sparkles"></span>) from the list of sources.
2. Click **Connect**.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/image-1769525440421.png" class="article_image" alt="Zendesk integration options for chatbot support tickets and source details overview.">

3. Enter your Zendesk connection details:
   - **API Token** — your Zendesk API token for authentication.
   - **Administrator Email ID** — the email address associated with your Zendesk account.
   - **Subdomain URL** — your Zendesk subdomain.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Connect%20Zendesk%20Support%20-%20AI%20Chatbot.png" class="article_image" alt="Zendesk connection form showing fields for API token, administrator email, and subdomain URL.">

4. Once validated, configure your ticket filters:
   - **Tickets updated since** — select a date to fetch only tickets modified after this date.
   - **Ticket tags** — filter tickets by specific tags.
   - **Agent groups** — filter tickets assigned to specific agent groups.
   - **Include private notes** — choose whether to include internal notes from agents.
   - **Status** — filter by ticket status: Open, Pending, Solved, or Closed.
   - **Types** — filter by ticket type: Question, Problem, Incident, or Task.
   - **Priority** — filter by priority level: Low, Normal, High, or Urgent.
5. Click **Save details** to connect Zendesk and begin syncing ticket data.

Once connected, you can view the last synced date and the number of tickets fetched.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Zendesk%20-%20Connection%20Successful.png" class="article_image" alt="Zendesk connection successful screen showing last synced date and ticket count.">

:::(Info) (<span class="fa-regular fa-circle-exclamation" data-type="icon"></span> NOTE)
Ticket data is fetched from newest to oldest based on your date filter.
:::

---

### Freshdesk

1. Click **Freshdesk** (<span class="fa-light fa-book-sparkles"></span>) from the list of sources.
2. Click **Connect**.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/image-1769525510227.png" class="article_image" alt="Freshdesk integration settings for chatbot support ticket management and source details overview.">

3. Enter your Freshdesk connection details:
   - **API Token** — your Freshdesk API token for authentication.
   - **Subdomain URL** — your Freshdesk subdomain.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Connect%20Freshdesk%20-%20AI%20Chatbot.png" class="article_image" alt="Freshdesk connection form showing fields for API token and subdomain URL.">

4. Once validated, configure your ticket filters:
   - **Tickets updated since** — select a date to fetch only tickets modified after this date.
   - **Ticket tags** — filter tickets by specific tags.
   - **Agent groups** — filter tickets assigned to specific agent groups.
   - **Include private notes** — choose whether to include internal notes from agents.
   - **Status** — filter by ticket status: Open, Pending, Resolved, or Closed.
   - **Types** — filter by ticket type: Question, Problem, Incident, Feature Request, or Refund.
   - **Priority** — filter by priority level: Low, Medium, High, or Urgent.
5. Click **Save details** to connect Freshdesk and begin syncing ticket data.

Once connected, you can view the last synced date and the number of tickets fetched.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Freshdesk-%20Connection%20Successful%281%29.png" class="article_image" alt="Freshdesk connection successful screen showing last synced date and ticket count.">

:::(Info) (<span class="fa-regular fa-circle-exclamation" data-type="icon"></span> NOTE)
Ticket data is fetched from newest to oldest based on your date filter.
:::

---

### Set up Eddy AI Chatbot during onboarding

New users can set up a chatbot directly during the Document360 onboarding process.

1. When creating a new project, select **Eddy AI Chatbot** as your use case.
2. Follow the simplified onboarding flow:
   - **Step 1:** Add up to 2 sources. You can add more sources later from the portal.
   - **Step 2:** Configure appearance settings.
3. Once complete, you land in your project with the chatbot ready to use.

---

## AI Chatbot specifications
| Limit | Value | Notes |
|---|---|---|
| Default storage per chatbot | 40 MB | Applies across all connected sources combined |
| Crawl depth (Crawl Links) | 3 levels | From the starting page |
| Max URLs per crawl session | 1,000 | Per crawl link source |
| Max discovered links per page | 200 | During a crawl session |
| Max URLs per sitemap | 1,000 | Per sitemap source |
| Max sitemap file size | 1 MB | — |
| Sitemap type supported | Single-level only | Nested or index sitemaps are not processed |
| File formats supported | DOC, DOCX, PDF, MD, TXT | Images and media inside files are not ingested |
| Crawl link recrawl limit | 2 times per day | Per individual crawl link |
| Sources added during onboarding | Up to 2 | Additional sources can be added after onboarding |

---

## Best practices

- **Add the knowledge base source first** — if you already have documentation, it gives the chatbot the strongest, most verified starting content.
- **Use "Allow selected content" for large knowledge bases** — targeting specific workspaces or categories avoids training the chatbot on content that is irrelevant to your users.
- **Apply ticket filters when connecting Zendesk or Freshdesk** — filter by status, date, or tag to ensure only high-quality, resolved tickets are ingested. Be mindful of PII in ticket content.
- **Use path filters for website sources** — use **Include only paths** and **Exclude paths** to prevent the chatbot from ingesting admin pages, legal pages, or other non-informational content.
- **Test with the Playground after adding sources** — before publishing, use the Playground to verify the chatbot answers questions correctly based on the sources you have added.


<!-- PRIVATE NOTE (not for publication):
- Default storage is 40 MB per chatbot; increases are available at additional charge via Customer Success Manager.
- Additional chatbots per project are available at additional charge; pricing varies based on storage and usage.
-->
