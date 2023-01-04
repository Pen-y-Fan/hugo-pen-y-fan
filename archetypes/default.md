---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
tags: [PHP, Resource]
url: {{ now.Format "2006"}}/{{ now.Format "01"}}/{{ now.Format "02"}}/{{ .Name }}
summary: "This is the summary"
---

![display name](images/image-unsplash.jpg "Title")
Photo
by [Image author](https://unsplash.com/@<Image-author>?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
on [Unsplash](https://unsplash.com/s/photos/security?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

{{< lead >}}
This is the lead paragraph, often the same as the summary.
{{< /lead >}}

## First heading
