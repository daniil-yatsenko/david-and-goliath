# Project context

- This is a new, design-first business website with static pages and a CMS. The repository currently consists mostly of boilerplate with a few initial project updates; do not assume every template choice is an established project requirement.
- Webflow owns the HTML, CSS, CMS, and hosting. This repository provides the custom code that enhances the Webflow site.
- The main responsibilities here are visual animations and interactions, design-related fine-tuning of the existing HTML, and functionality such as the mobile burger menu.
- Work within that architecture: treat the Webflow-rendered DOM as the integration surface, and avoid introducing a separate site renderer, CMS, or hosting setup unless requested.

## Loading and delivery

- `src/js/utils/routerWebflow.js` is embedded inside a `<script>` tag near the bottom of the Webflow HTML.
- On custom domains, the router loads the production CDN script.
- On `webflow.io` domains, it first checks the local HTTPS Vite server on port `3011`. When available, it loads the Vite client and `/js/index.js` as modules; otherwise, it falls back to the staging CDN script.
- Production custom code is built with Vite and delivered via CDN. The production and staging CDN URLs in the router are currently placeholders awaiting project configuration.
- Keep the local development port consistent between `package.json` and the router when changing it.

## Working expectations

- Preserve the design-first nature of the site when implementing interactions and animation.
- Account for the fact that the authoritative markup and styling live in Webflow, outside this repository. If a change requires Webflow edits, describe the required elements, classes, or attributes clearly.
- Do not treat starter README instructions or placeholder configuration as evidence that deployment has already been configured.
