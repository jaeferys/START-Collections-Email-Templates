# START: COLLECTIONS — Nine email templates

**Nine HTML files total: one complete template for each status, using one consistent START design.** This is the replacement package. Each file already contains its own status-specific message; no master-layout assembly is needed.

The design keeps the original START logo, banner, patterned background, footer, cyan/charcoal palette, and animated signature. Only buyer/order placeholders and optional finance notes need to be filled before sending.

| File | Sent when |
| --- | --- |
| `01-order-received.html` | Buyer submits the order; payment verification is pending |
| `02-payment-confirmed.html` | Finance verifies payment |
| `03-in-production.html` | Finance starts production |
| `04-out-for-shipping.html` | Order ships |
| `05-received-successfully.html` | Finance marks the order received |
| `06-canceled.html` | Finance cancels a confirmed order |
| `07-refund-in-process.html` | Finance starts the refund |
| `08-refund-successful.html` | Refund is sent |
| `09-payment-rejected.html` | Finance rejects the payment |

## Use

1. Open the relevant HTML source and replace its `{{variable_name}}` placeholders with buyer/order details. All nine subjects and their required fields are in `subjects.json`. Set the subject separately in your email sender; the HTML title does not set it.
2. For optional finance notes, remove the whole `{{#if finance_note}}…{{/if}}` block when there is no note. When a note exists, fill `{{finance_note}}`, keep the block's contents, and remove the two markers.
3. Use real absolute HTTPS URLs for tracking, the merch ticket form, and the store. Enter `amount` without `PHP` because the template supplies it. Include item name, size, and quantity in `items_ordered`; separate multiple items with line breaks when using the renderer, or `<br>` tags when editing HTML manually.
4. Send the completed HTML through your email tool's HTML-body feature. Do not paste source code into a normal visual composer. Test-send to Gmail, Outlook, and a phone before connecting the workflow.

The placeholders are not universal email-provider merge tags; replace them manually, map them to your sender's variables, or use the optional renderer below. HTML-escape inserted buyer text and link attributes.

## Optional automatic replacement

Python 3 is enough; no package installation is needed. Copy the fictional `sample-data.json` to a private location and replace its values. Then run:

```sh
python3 render.py 02-payment-confirmed.html /path/to/private-order.json --output rendered/email.html
```

The renderer fills one file, escapes text, preserves line breaks, hides empty finance notes, and rejects missing fields or unsafe dynamic links. It does not send emails. Keep real buyer data outside your public repository. The sample products, amount, dates, address, refund range, and example.com links are demonstrations.

## GitHub and images

Upload the nine HTML files and these supporting files to your repository. The separate preview page is optional and is not part of the nine-template ZIP. Email images use the original direct HTTPS artwork URLs supplied with the START template. If you replace them, use publicly accessible HTTPS image URLs.

The templates use email presentation tables, inline styles, responsive padding, image alt text, Outlook wrappers, and Outlook-compatible buttons. Rounded corners and animation can vary between email clients. Nothing was published to GitHub and no emails were sent.

## Verification

The package contains exactly nine HTML files. They match the previously checked Signature templates byte for byte; each passed browser layout checks at 320, 375, and 800 pixels. Required fields, payment verification wording, the two-day support window, refund notices, and receipt instructions were checked. The standalone preview supports all nine statuses.
