---
title: "Your First Post Title"
date: 2026-09-01 10:00:00
categories: [Research]                      # one or two levels, e.g. [Research, Windows]
tags: [active directory, windows]           # lowercase; these become the tag pills
description: One sentence shown in post listings, search results and the RSS feed.
published: false                            # ← delete this line to publish
Open with the point, not the preamble: what you found, why it matters, and who should care. Readers of technical essays decide in two sentences whether to stay.
Section headings appear in the floating Contents panel
Use `##` for major sections and `###` for sub-points; the table of contents on the right builds itself from them.
Inline code looks like `Get-ADUser -Filter *`, and fenced blocks get syntax highlighting and a copy button:
```powershell
Get-ADUser -Filter * -Properties ServicePrincipalName |
  Where-Object { $_.ServicePrincipalName } |
  Select-Object SamAccountName, ServicePrincipalName
```
> Callout boxes come in four flavors: `.prompt-tip`, `.prompt-info`, `.prompt-warning`, `.prompt-danger`.
{: .prompt-info }
Footnotes work exactly as on your brother's site[^1] — the number links down, the return arrow links back.
![Description for screen readers and search engines](/assets/img/posts/example.png){: width="700" }
Image captions go in italics on the very next line.
Closing
State what to do with this, or what remains unknown. Then stop — a strong last paragraph is the part people quote.
[^1]: Reference or source. Footnotes collect automatically at the bottom of the post.
