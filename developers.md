# Developer installation notes

These notes cover the website changes needed for a managed Magnus installation.
They do not require access to Magnus's infrastructure or a customer's private
account. Start with the [owner setup guide](setup.md).

## The installation contract

You receive two separate pieces of public markup:

1. A website-control meta tag, unique to the customer's saved setup.
2. A module-script snippet, unique to the prepared installation.

The first proves publishing control. The second loads the visitor interface.
Neither is a provider key, reporting credential or permission to read private
workspace data. Do not invent data attributes or replace an assigned hostname
with another installation's hostname.

## Verification and delivered HTML

The public home page must return the verification tag as a real child of its
`<head>` element. For example, with the generated value substituted:

```html
<head>
  <!-- Keep the site's existing metadata. -->
  <meta name="magnus-site-verification" content="YOUR_GENERATED_VERIFICATION_VALUE">
</head>
```

The current verifier reads the exact saved HTTPS origin's `/` response. It does
not follow redirects, sign in, execute JavaScript or inspect an iframe's document.
It rejects private network addresses, invalid TLS and unsupported responses.
A name/value inside a JavaScript string, HTML comment or template does not count.

Check the **Network response** or **View page source**, not just the browser's
post-JavaScript Elements panel. The home-page response must be readable publicly
without a consent click, bot challenge or account login. It must honor an
uncompressed response request; the current check is bounded to 256 KiB and six
seconds. An oversized or incompatible response needs investigation, not removal
of the ownership check.

If the customer entered an address that redirects, correct the saved origin to
the final address before provisioning. `www` and apex hostnames are distinct.
Keep the current tag available after setup; do not rotate it independently of
the saved Magnus setup.

## Install the exact module once

Use the generated snippet. The example shape is:

```html
<script
  type="module"
  src="https://YOUR_ASSIGNED_ASSISTANT_HOST/widget.js"
  crossorigin="anonymous"
></script>
```

It can sit in the delivered head or body, subject to the host's code mechanism.
For the current installation checker, the module source must be present in the
home page's delivered HTML. A launcher injected only after load is not enough.
Preserve `type="module"`, the exact `src` and anonymous cross-origin loading.

| Website structure | Where to put it |
| --- | --- |
| Static HTML or a client-side SPA | Verification in the delivered `index.html` head; script in that same delivered document or shared template. |
| Server-rendered React or Next.js | A server-rendered root layout/head for verification and a server-delivered script element. Confirm the emitted HTML. A client-only effect or after-interaction script loader alone does not satisfy the current checker. |
| CMS or theme | An authorized head/template hook or custom-code setting that emits the actual tags into the public response. Check for sanitization and caches. |
| Hosted site builder | Confirm the account/plan can emit both tags in the delivered document. An iframe embed or a dashboard field that injects tags only in the browser may not work. |

These are integration requirements, not a list of certified Magnus plugins.
Use your platform's current documentation for its publishing mechanism. Do not
change a customer's theme, purchase a plugin or promise compatibility without
checking the actual response.

## Content Security Policy

Add the assigned origins to the site's existing policy. Do not replace the whole
policy with an example or broaden it to `*` to get a green result.

| Directive | Origins required by the standard embed |
| --- | --- |
| `script-src` | The exact assistant origin and `https://challenges.cloudflare.com`. |
| `style-src` or the applicable stylesheet directive | The exact assistant origin for its external stylesheets. |
| `connect-src` | The exact assistant origin. Keep other approved API destinations. |
| `frame-src` | `https://challenges.cloudflare.com` for the security widget. |

If an additional intake API is configured at another origin, add that exact
origin to `connect-src` as well. Loading chat assets does not prove its definition,
chat or intake API connections are permitted. This mismatch can leave a visible
interface that cannot answer or prepare a request.

Sites using nonces or `strict-dynamic` need an adaptation consistent with their
existing policy. Do not add `unsafe-eval` or weaken inline-script restrictions as
a workaround. Check the actual production response headers, not only a local
Vite development server, which may send no production CSP.

Cloudflare documents Turnstile's [script/frame requirements and nonce support](https://developers.cloudflare.com/turnstile/reference/content-security-policy/).
The pre-clearance feature has additional same-origin requirements; it is not
required by the current standard Magnus setup.

## Origins, browser requests and security checks

- Serve the website and assigned assistant over HTTPS with valid certificates.
- Use the exact approved website origin. A second staging, preview or `www` origin needs its own reviewed configuration.
- Preserve anonymous module loading and the service's CORS behavior. Do not add cookies or a reverse proxy as a quick origin workaround.
- Ensure the security widget can load and display an interactive challenge when needed.
- Never fake a successful security token or turn off server verification to pass a production check.

Your normal form and contact route should remain available when chat or request
preparation is temporarily unavailable.

## Route placement and single-page applications

Publish the approved embed once through a stable shared template. Avoid placing
a second copy inside every client-side page component. Verify navigation by both
fresh page loads and internal links.

The configured placement policy determines display. It can select public routes
or route prefixes and exclude routes. Do not assume that inserting the script
site-wide automatically permits every page. Agree exclusions for administration,
accounts, portals, checkout and results/status pages. Placement controls display;
they do not grant authorization or make private page contents approved sources.

## Optional request preparation

Request preparation is an application integration, not a DOM autofill script.
The receiving business registers the fields, allowed values, purpose and action.
The application keeps an editable draft separate from a confirmed submission.
Consent and security verification cannot come from model-generated field changes.

Before adding it to a customer website, confirm with the setup team:

- Which request/form is supported and which fields may be collected.
- Where the visitor can review, correct and explicitly send the values.
- Which receiving endpoint accepts that exact version and returns a durable acknowledgement.
- How retries and an unknown acknowledgement are reconciled without duplicate sends.
- Which disclosure, processors, retention and fallback form apply.

Do not assume the normal embed enables this integration. Do not forward form
values to analytics, browser storage or error reports. Any real submission or
notification test needs an agreed destination and explicit authorization.

## Acceptance before handover

1. Check the exact tag and module in the public HTML response.
2. Complete **Check my website** and **Check installation** in the customer's setup.
3. Inspect production CSP, module/CSS requests and service requests for errors.
4. Verify the intended public pages and exclusions, including SPA navigation.
5. Try approved public questions, source links, follow-ups and unknown facts.
6. Check keyboard operation, narrow phones, long replies, option buttons and the input position.
7. Where configured, verify preparation consent, draft corrections, final review and the ordinary-form fallback.
8. Confirm the customer's reporting access without exposing report credentials to the website.

Separate a synthetic UI test from a real model answer, and both from a real
receiving-system test. A successful test of one does not establish the others.

## Updating or removing an installation

Keep the existing installation identity during runtime/content updates. Use the
new snippet only if the team supplies one as part of a reviewed update. Do not
recreate an installation, change its origin or reset its allowance to work around
an error.

For removal, have the service disabled through its management process and remove
the site embed as instructed. Deleting markup alone does not revoke server
credentials or erase accepted requests. Domain moves and ownership transfers need
a reviewed transition, not a copied tag.

[Owner guide](setup.md) · [Troubleshooting](troubleshooting.md)
