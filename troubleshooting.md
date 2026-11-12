# Troubleshoot website setup

Start with the step shown in your saved setup. Keep using that setup rather than
creating a second website or business to try again.

[Owner guide](setup.md) · [Developer notes](developers.md)

## Account and website verification

| Problem | What to check |
| --- | --- |
| I cannot open setup | Confirm you are using the account and access link provided during the assisted rollout. Verify your account email when prompted. |
| Magnus cannot find the tag | Publish the exact current tag inside the delivered home page's `<head>`, publish the site and clear its page cache. Check View page source. |
| The tag appears in Elements but verification fails | A client-side script may have inserted it after load. The current verifier needs the tag in the server's HTML response. |
| The website redirects | Save the final HTTPS origin. The verifier does not follow an apex-to-`www`, HTTP-to-HTTPS or other redirect. |
| Verification is temporarily unavailable | Wait at least 30 seconds between checks. Confirm public HTTPS, valid TLS and that the home page is not protected by a login or challenge. |
| The tag expired before setup finished | Request fresh verification in the existing setup. Review any refreshed offer; do not reuse an old value. |
| I entered the wrong address | Before installation is issued, use **Edit website address**. A live or issued installation needs a reviewed move. |
| I control DNS but cannot add HTML | The current flow does not offer DNS TXT/file proof. Ask your authorized website developer or setup contact for help; do not bypass proof. |

A very large home page or a server that ignores the uncompressed-response request
can also fail the bounded verifier. Share the technical symptom with the team.
Do not send hosting credentials or disable the site's security controls yourself.

## Preparation and installation

| Problem | What to check |
| --- | --- |
| Setup says preparing or waiting for a preview | Service preparation is assisted. Keep the existing setup; contact the team if it is delayed. Do not approve an empty review. |
| Installation code is not available yet | Confirm website verification and review of the exact content/service offer are complete. |
| I pasted the snippet but **Check installation** fails | Keep the verification tag and the exact supplied `type="module"` script in the home-page response. Check the assigned hostname, publishing cache and whether a tag manager injected it only after load. |
| A launcher appears but setup is not active | A visible widget does not establish current ownership, approved content or an enabled matching release. Complete the setup checks. |
| I see two launchers | Remove duplicate script insertions or overlapping integrations. Keep the approved embed in one shared location. |
| Chat appears on the wrong pages | Review the configured placement and exclusions. Check both direct loads and internal navigation. |

## The interface loads but cannot reply

Check, in this order:

1. Does the page use the exact approved origin, including `www`?
2. Does production CSP allow both the assistant assets and its connections?
3. Can the security widget load and complete its check?
4. Does the installation still have current service authority and allowance?
5. Is the published content version the approved one?

A developer can inspect the production Network and Console panels. Share status
codes, public URLs and time with the team; omit security tokens, authorization
headers and visitor messages. Do not remove server-side checks, use another site's
snippet or expose a provider key as a workaround.

## Wrong or incomplete answers

Record the public question, the expected answer and the exact published page that
supports it. The team should check whether the source was captured, approved,
retrieved and represented correctly before changing instructions.

If a price is wrong, preserve the currency, units, tax wording and conditions in
your report. If information conflicts, correct the underlying public source and
review the new offer. The fact that a service is missing from an answer is not
proof your website never published it.

Do not paste customer records, private documents or credentials into a public
issue to demonstrate a problem.

## Request preparation or sending

| Problem | What to check |
| --- | --- |
| There is no preparation option | The standard embed does not enable form preparation automatically. Ask whether your installation has that integration. |
| Start is disabled | Read the purpose notice, make the explicit preparation choice and complete the security check. Never ask the AI to set consent. |
| A field is missing or wrong | Correct the editable draft before sending. Unknown details must remain unconfirmed. |
| The notice or definition cannot load | Use the ordinary form. The team must check the approved version, connection policy and current authority. |
| Sending has an error or an unclear result | Do not repeatedly click or create a second enquiry. Use the integration's status/reconciliation path and ask the team to confirm the receiving acknowledgement. |
| I closed a draft | Closing a draft is not confirmation that server/provider records or an accepted request have been deleted. Follow the published notice. |

## Recovery, transfers and multiple sites

After account recovery, a domain change or an ownership transfer, old tags and
approvals may no longer authorize access. Follow the current setup/recovery
instructions. Do not claim an existing site as a new installation or share a
previous owner's account.

Each website keeps its own source approval, installation and reporting access.
Being a teammate in a business does not automatically grant access to another
person's website report.

## What to include in a support request

- Website address and the setup step or visible error.
- Approximate time, timezone, browser and screen size where relevant.
- Public URL/status code or a screenshot with private details removed.
- For an answer problem, the public source that should have supported it.

Use the contact provided with your setup. Do not include passwords, account codes,
private headers, API keys, report tokens or visitor transcripts in GitHub issues.
