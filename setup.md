# Set up Magnus on your website

This guide is for a website owner and anyone helping them install Magnus. Setup
is currently assisted: the Magnus team prepares the service while you verify the
website, approve its information and publish the supplied code.

[Overview](README.md) · [Developer notes](developers.md) · [Troubleshooting](troubleshooting.md)

## Before you start

| Requirement | What you need |
| --- | --- |
| Website | A publicly reachable HTTPS website with a valid certificate. |
| Permission | Authority to configure this website, or an authorized developer who can help. |
| Account | Access to your own Magnus account and a verified email address. Current enrollment is assisted/invitation-based. |
| Website editing | A way to publish a verification meta tag in the home page's delivered HTML head, and a module script in the delivered site HTML. |
| Public information | Accurate services, conditions, contact details and a privacy page that you can approve for answers. |
| Security settings | Someone who can update the site's Content Security Policy if it restricts third-party connections. |
| Review | A person who can check the proposed information, service allowance and disclosures before activation. |

A social profile, marketplace listing or page whose HTML you cannot configure is
not enough for the current website-control check. Password-protected sites,
localhost and private network addresses do not pass the public check.

You do not supply an AI-provider key or give Magnus your hosting password for
normal managed setup. Your developer can publish the two supplied tags without
receiving your Magnus sign-in credentials. A custom assistant domain may need
separate DNS work; it is not a prerequisite for the standard assigned embed.

## 1. Open website setup

Use the setup link provided with your access. In a signed-in account the setup
surface is `/websites/new`; the website-specific entry is `/start?intent=website`.
If you do not yet have access, use your Magnus setup contact rather than creating
a second account or trying operator commands.

Verify your account email if asked. Email verification identifies the account;
website verification is a separate step.

Choose the website's display name and exact address. Then explicitly select an
existing business you own, create the named business, or choose the
personal/noncommercial option. A personal website does not require a business.
The same account can manage more than one business or website. Private work tools
and workspace connections remain separate choices.

## 2. Save the correct website address

Use the final HTTPS origin that visitors reach, for example:

```text
https://www.garden.example
```

An origin contains the scheme and hostname. Do not enter a service-page path,
query string, login URL, custom port or website administrator address.
`https://garden.example` and `https://www.garden.example` are different origins.
If one redirects to the other, save the final address. The current verifier does
not follow that redirect on your behalf.

Before installation has been issued, **Edit website address** can correct a saved
address in the same setup. Saving a changed address requires a new verification
and content review. Moving an already issued or active installation is a reviewed
site-move process; do not replace its identity yourself.

## 3. Verify control of the website

Magnus supplies a unique tag resembling this example:

```html
<meta name="magnus-site-verification" content="YOUR_GENERATED_VERIFICATION_VALUE">
```

1. Copy your own generated tag from setup.
2. Publish it inside the home page's real `<head>` element.
3. Publish the website changes and clear any relevant page cache.
4. In Magnus, choose **Check my website**.

Use **View page source** to confirm that the tag is in the HTML delivered by the
server. A tag added later by JavaScript, a tag manager, an iframe, a comment or a
template is not sufficient. The current check does not run the page's JavaScript.
Your developer can use the [HTML checks](developers.md#verification-and-delivered-html).

Keep the current tag published after verification. Do not reuse another site's
tag. If setup expires or asks for fresh verification, request the new tag through
that same setup. Wait at least 30 seconds between public verification attempts.

This confirms control of the website's publishing configuration. It does not
establish legal ownership of a company, approve the assistant's information or
grant access to private workspace records. DNS TXT verification and verification
files are not alternative methods in the current customer setup.

## 4. Review what Magnus will know

The team prepares a review from selected public website sources. Check the actual
information, not just whether the page list looks complete:

- Services and products, including important exclusions.
- Prices, currencies, minimum quantities, tax wording and other conditions.
- Locations, service areas, contact routes and availability wording.
- Who is responsible for arrangements, costs and delivery.
- FAQs, policies and the next steps a visitor should be offered.

Point out missing or conflicting information before approval. A missing detail
in the assistant's review does not mean your business does not offer it.

Some material needs extra preparation: image-only prices, PDFs, private pages,
third-party feeds and content available only after an interactive action are not
automatically covered. Do not assume that every linked page or document has been
ingested. Ask to see the coverage and omissions.

Review the actual service allowance, terms and privacy disclosure. Publish the
reviewed disclosure where visitors can read it. Approve the exact offer shown in
your setup. Corrected content or a changed offer requires a new review; it cannot
silently inherit your earlier approval.

## 5. Let the team prepare the service

The team configures your installation, model allocation, abuse controls, security
check and protected reporting. Seeing **preparing** or **waiting for a preview**
is not a request to create another website or approve a blank offer.

Your website control, approved information and service availability are distinct
checks. The team must confirm each one. You should receive the installation code
for this website and the agreed allowance before going live.

## 6. Publish the installation code

Copy the complete snippet supplied for your own installation. Its shape is:

```html
<script
  type="module"
  src="https://YOUR_ASSIGNED_ASSISTANT_HOST/widget.js"
  crossorigin="anonymous"
></script>
```

`YOUR_ASSIGNED_ASSISTANT_HOST` is a placeholder, not an address to publish. Use the
exact generated snippet, including its assigned hostname and `type="module"`.
Do not paste an AI key, reporting token or model credential into your website.

Publish the snippet once through your website's supported custom-code mechanism.
For the current installation check, the supplied module script must also be
present in the delivered home-page HTML. JavaScript-only or tag-manager injection
can make a launcher appear without passing installation verification.

If your website uses a security policy, have your developer add only the assigned
origins it needs. Both loading the script and connecting to the service must be
allowed. See [the CSP requirements](developers.md#content-security-policy).
A script that loads while its API connection is blocked is not a working install.

Keep the verification tag. Do not replace the website address, reuse another
installation's snippet or add the same script twice.

## 7. Check installation and page placement

Return to Magnus and choose **Check installation**. This checks the current tag,
exact module script and enabled release version. It does not call the AI model.
A successful check is a technical milestone; it is not an answer-quality test.

Then inspect the pages where the launcher should appear. Placement and knowledge
coverage are different: publishing the script site-wide does not mean every page
has been approved as an answer source, or that chat is meant to appear everywhere.

Choose the intended public pages and exclusions with the setup team or available
placement controls. Exclude private accounts, customer portals, administration,
checkout, status pages and other unsuitable routes. Confirm exclusions after
navigating within a single-page application as well as after a fresh page load.

Use the same setup and installation for updates. If a technical check fails,
correct that setup; do not generate another identity to get around it.

## 8. Try representative visitor questions

Agree any real model tests and their allowance with your setup contact. Use
ordinary public questions and fictional examples, not private customer records.
Check at least these cases:

| Try | Check |
| --- | --- |
| What do you offer? | The business is explained accurately and the relevant services are present. |
| A price question | The correct currency, units and published conditions stay together. |
| A comparison | The answer preserves the differences rather than merging packages. |
| A follow-up | The answer understands the current question and relevant earlier context. |
| A correction | A changed detail replaces the old detail without losing unrelated information. |
| An unknown fact | Magnus asks or gives an appropriate next step instead of inventing an answer. |
| An unrelated/private request | No private information or unsupported action is offered. |
| The same steps on a phone | Options, answers, input, consent and close/back controls stay usable. |

Check links and contact destinations. A normal contact link opens that page; it
does not mean Magnus has already sent an enquiry or booked anything.

Record any wrong answer together with the question, expected public source and
time. Omit private visitor details. The team needs to distinguish a missing source,
a retrieval problem and an incorrect answer before making a correction.

## 9. Add request preparation only when it has been configured

The standard embed does not automatically read or fill arbitrary website forms.
Request preparation needs a separately reviewed set of fields, data-use notice,
receiving destination and confirmation flow. Ask which of your requests are
actually supported before announcing them.

Where configured, the visitor chooses AI preparation, describes their needs,
checks an editable draft and separately confirms sending the displayed values.
Security checks and required fields still apply. Magnus cannot set consent on the
visitor's behalf. Success must come from the receiving system, not from a sentence
in the conversation.

Test the full receiving flow with the team using an agreed test destination or an
explicitly authorized real enquiry. Do not send an unannounced test to your sales
or support team. Keep an ordinary form/contact route available if preparation is
unavailable. Before collecting personal details, publish the installation's own
reviewed purposes, processors, retention and privacy contacts.

## After launch

- Keep the verification tag and approved embed published.
- Tell the team when services, prices, conditions, privacy wording or the domain change.
- Review a new content offer before its information replaces the live version.
- Check the website dashboard and source freshness. A chat question is not a confirmed lead or sale.
- Report failed replies or deliveries without pasting personal data into an issue.
- Use the website's existing Magnus identity when adding another feature or connecting work tools.

For a second website, repeat verification and source review for that website.
Do not copy the first site's identity, reporting credentials or approval. One
account can manage multiple sites without merging their information or reports.

## Pause, remove or transfer

Ask for the installation's service to be disabled through the current management
process, then remove its embed where appropriate. Removing the script stops that
page showing chat; it does not itself revoke server authority or delete an already
accepted request. Keep an ordinary contact route available.

A domain transfer, a new owner or account recovery needs current ownership review.
Do not give the new owner your account, copy another site's verification value or
try to recover authority from an old script. Existing requests and retained
records follow their reviewed receiving/privacy process.

## Get help

Use the setup contact provided with your access. Share the exact website address,
the step that failed, approximate time and a screenshot with private information
removed. Do not share account passwords, security codes, API keys or visitor
messages in a public GitHub issue.

[Find a specific problem](troubleshooting.md) · [Developer notes](developers.md)
