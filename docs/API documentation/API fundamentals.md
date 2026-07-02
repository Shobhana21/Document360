Document360's API documentation feature gives you a complete, end-to-end solution for publishing, managing, and testing API references. Whether you're a startup shipping your first public API or an enterprise maintaining dozens of internal microservices, Document360 turns your OpenAPI specification into polished, interactive developer documentation without requiring any custom tooling or manual formatting.

---

## What is API documentation and why does it matter?

API documentation is the technical reference that tells developers exactly how to interact with your API: which endpoints exist, what parameters they accept, what responses they return, and how authentication works. Unlike general knowledge base articles, API docs follow a strict, structured format derived from a machine-readable specification file.

**Why it matters:**

- **Reduces integration time.** Clear docs cut onboarding from days to hours. Developers spend less time guessing and more time building.
- **Reduces support burden.** When docs answer the "how do I authenticate?" and "what does a 422 mean?" questions, your team fields fewer tickets.
- **Builds developer trust.** Incomplete or outdated API docs signal an unreliable product. High-quality documentation is a direct signal of product quality.
- **Enables self-service.** External partners, customers, and third-party developers can integrate without needing hand-holding from your team.

---

## API documentation vs regular documentation

| Aspect | API documentation | Regular documentation |
|--------|-------------------|----------------------|
| Primary audience | Developers and technical integrators | End users, internal teams |
| Structure | Driven by a specification file (OpenAPI, Postman) | Manually authored articles |
| Content type | Endpoints, parameters, schemas, auth methods | Guides, how-tos, conceptual articles |
| Interactivity | Live testing via Try It! | Static reading |
| Versioning | Tied to API spec versions | Managed editorially |
| Auto-generation | Yes, from spec file | No |

In Document360, API documentation lives in a dedicated API workspace that is separate from your standard knowledge base. This allows different access controls, routing, and branding for your developer-facing content.

---

## Supported specification formats

Document360 supports the following specification formats:

- **OpenAPI 2.0** (formerly Swagger)
- **OpenAPI 3.0**
- **OpenAPI 3.1** (includes webhook support)
- **Postman Collections**

Files can be uploaded as **JSON**, **YAML**, or **YML**.
:::(Info) ( <p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
If you're starting fresh, use <strong>OpenAPI 3.1</strong>. It's the current standard, supports webhooks natively, and has the richest tooling ecosystem. If you're migrating from an existing Swagger 2.0 setup, Document360 accepts it as-is while you upgrade incrementally.
:::

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/Screenshot-API_references.png" class="article_image" alt="Document360 interface showing categories, articles, and options for creating new content.">

The **Try It!** feature in Document360 allows you to test API endpoints directly on the Knowledge base site. The interactive console enables developers to input the necessary parameters and execute API calls, getting real-time responses, without leaving the documentation or writing any code.

<img src="https://cdn.document360.io/860f9f88-412e-4570-8222-d5bf2f4b7dd1/Images/Documentation/2_Screenshot-API_try_it.png" class="article_image" alt="Document360 Try It! console showing live API testing.">
:::(Info) ( <p class="fa-regular fa-circle-exclamation" data-type="icon"></p> NOTE)
The <strong>Try It!</strong> section supports multiple security schemes simultaneously, enabling users to test endpoints that require combined authentication methods more effectively.
:::

---

## Webhooks in OpenAPI 3.1

Document360 supports webhooks defined in OpenAPI 3.1. Webhooks appear with an event icon in your API reference and include a payload section based on your schema. If no example is provided, Document360 shows a default example and a sample payload. Try It! is not available for webhooks. Webhooks are supported for file uploads, URL imports, and CI/CD flows.

---

## Authorization techniques

When interacting with an API, it is important to ensure that only authorized users can access certain data or perform specific actions. Document360 supports the following authorization methods:

- **Basic authentication** - Requires a username and password passed in the request.
- **Bearer token** - Authenticates with a token generated after login.
- **API key** - Uses a unique key, passed in the request headers, for authentication.
- **OAuth2** - Secures APIs through various flows: Authorization Code, PKCE, Client Credentials, and Implicit.
- **OpenID Connect** - Extends OAuth2 by adding user identity verification.

### OAuth2 and OpenID Connect: additional configuration

When working with APIs that use OAuth2 or OpenID Connect, two settings are required for Try It! to work correctly:

- **Redirect URI** - Set this in your OAuth provider to the format `domain/oauth`. For example: `https://apidocs.document360.com/oauth`.
- **Silent renewal** - Document360 automatically refreshes the authorization token in the background during active Try It! sessions, so users do not need to re-authenticate manually.

---

## FAQ

<div class="faq-wrapper" data-type="details-wrapper">
<details open>
<summary><p>How is API documentation different from regular documentation?</p></summary>
<div data-type="details-content"><p>API documentation is specifically designed to explain endpoints, authentication, and integrations. It is separate from your standard knowledge base articles and useful for developer-facing content.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>What is an API reference?</p></summary>
<div data-type="details-content"><p>An API reference is a documentation resource that provides comprehensive information about the functions, classes, methods, parameters, return types, and other components of an API. It is a guide or manual for developers who want to integrate or use the API in their applications.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>What are the supported specification file formats?</p></summary>
<div data-type="details-content"><p>You can upload your specification file as a <strong>URL</strong>, <strong>JSON</strong>, <strong>YAML</strong>, or <strong>YML</strong> file. Document360 supports OpenAPI 2.0, OpenAPI 3.0, OpenAPI 3.1, and Postman API specifications.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>How many API references can I create?</p></summary>
<div data-type="details-content"><p>Within each API workspace, you can create a maximum of 3 API references.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>What is the default ordering of categories when uploading an OpenAPI specification file?</p></summary>
<div data-type="details-content"><p>Categories in Document360 are created based on the tag order defined in your spec file. For example, if your spec defines tags in the order Pet, Store, User — the categories will appear in that same order.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>The "Try It!" option is not available on the Knowledge base site. What could be the reason?</p></summary>
<div data-type="details-content"><p>If the <strong>Try It!</strong> feature isn't visible, ensure that both the server variable and the server URL are properly defined in your API specification file. Without these, the feature will not function.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

<div class="faq-wrapper" data-type="details-wrapper">
<details>
<summary><p>Can API reference dropdown values be modified through the UI?</p></summary>
<div data-type="details-content"><p>No. Changes to API reference elements such as dropdown values can only be made through the OpenAPI specification file. Modifying these values through the UI is not currently supported.</p></div>
</details>
<button class="details-arrow" type="button"></button>
</div>

---

## Related videos

### Experience our modern API documentation in Document360

<iframe src="https://www.youtube.com/embed/EaMrT3xmNm8" frameborder="0" allowfullscreen allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" width="560" height="315"></iframe>

### Test API endpoints directly from documentation with Try It!

<iframe src="https://www.youtube.com/embed/wAehAmm4a5E" frameborder="0" allowfullscreen allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" width="560" height="315"></iframe>

---

## Additional information

<a href="https://document360.com/blog/introducing-document360-api-documentation/" target="_blank">Read our blog on</a> - **Introducing API Documentation: Enhance your API Experience** 
