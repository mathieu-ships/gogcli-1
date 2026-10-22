# --html-from-text proof (openclaw/gogcli#1251, head 853d8639)

## CLI (branch build v0.46.0-6-g853d8639; account, recipient and IDs redacted)

```
$ gog --account SENDER gmail send --to RECIPIENT --subject "PR proof: default" --body-file body.txt  --json
Note: Using direct access token (expires in ~1 hour; no auto-refresh)
{
  "from": "Sender <sender@example.com>",
  "messageId": "<id>",
  "threadId": "<id>"
}
$ gog --account SENDER gmail send --to RECIPIENT --subject "PR proof: html-from-text" --body-file body.txt --html-from-text --json
Note: Using direct access token (expires in ~1 hour; no auto-refresh)
{
  "from": "Sender <sender@example.com>",
  "messageId": "<id>",
  "threadId": "<id>"
}
```

## MIME parts of the sent messages

```
text/plain  (quoted-printable)  third line: 'This paragraph is one logical line in the message source, long enough that Gmail web would…'

multipart/alternative
text/plain  (quoted-printable)  third line: 'This paragraph is one logical line in the message source, long enough that Gmail web would…'
text/html  (7bit)  third line: 'This paragraph is one logical line in the message source, long enough that Gmail web would…'

```

## Gmail web rendered body (div.a3s innerHTML)

### default

```html
<div>Hi,<br>
<br>
This paragraph is one logical line in the message source, long enough<br>
that Gmail web would cut it into pieces of about seventy characters if<br>
the message had only a text/plain part.<br>
<br>
1. A list item that is also long enough to wrap when the window is<br>
narrow, such as on a phone<br>
2. A short item<br>
<br>
Thanks<div class="yj6qo"></div><div class="adL"><br>
</div></div>```

### html-from-text

```html
<div>Hi,<br>
<br>
This paragraph is one logical line in the message source, long enough that Gmail web would cut it into pieces of about seventy characters if the message had only a text/plain part.<br>
<br>
1. A list item that is also long enough to wrap when the window is narrow, such as on a phone<br>
2. A short item<br>
<br>
Thanks<div class="yj6qo"></div><div class="adL"><br>
</div></div>```
