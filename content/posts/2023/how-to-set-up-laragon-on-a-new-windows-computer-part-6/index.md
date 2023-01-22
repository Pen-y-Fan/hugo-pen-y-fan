---
title: "How to set up Laragon on a new Windows computer (part 6) - Add to path"
date: 2023-01-05T13:26:44Z
draft: false
tags: [PHP, Resource, PATH, Terminals]
url: 2023/01/05/how-to-set-up-laragon-on-a-new-windows-computer-part-6
summary: "Laragon's terminal is cmder, which will automatically give command line access to all the tools in Laragon's
development environment. If other terminals are required then Laragon can add the development tools to the Windows user
environment path."
---

![Principality Stadium in Cardiff overlooking River Taff](images/grooveland-designs-apekIDd6sT0-unsplash.jpg "Principality Stadium in Cardiff overlooking River Taff")
Photo
by [Grooveland Designs](https://unsplash.com/@groovelanddesigns?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
on [Unsplash](https://unsplash.com/photos/apekIDd6sT0?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

{{< lead >}}
Laragon's terminal is **cmder**, which will automatically give command line access to all tools in Laragon's development
environment. If other terminals are required then Laragon can add the development tools to the Windows User environment
PATH.
{{< /lead >}}

## Cmder

Laragon's terminal **cmder** can be opened from **Laragon menu > Laragon > Terminal** or click the **Terminal** button.

![!Cmder](images/2023-01-05_16_55_53-Cmder.jpg "Cmder")

Out-of-the-box **Cmder** automatically has access to many of the development environment tools. However, if you try
accessing them using **CMD**, **Powershell** or the terminal building into your favourite IDE they will not be
available.

## Add to PATH

The solution provided by Laragon is to add Laragon to PATH. Rather than do this directly from the menu I prefer to check
the current status using **Manage path**.

### Manage path

To view the current Laragon path and your user path select **Laragon Menu > Tools > Path > Manage Path**

![!Empty path](images/2023-01-05_17_17_01-Path.jpg "Empty user Path")

You can see Laragon's paths in the red rectangle. The yellow rectangle highlights the current user paths, which don't
include any of Laragon's development tools. The blue rectangle is what we need next.

### Add Laragon to the user path

To add Laragon's paths to your user path, and make them available in all terminals: Click **Menu** (in the top right
corner), then select **Add Laragon to Path**.

Scroll down, you will see the Laragon path has been copied to the user section.

![!Full user path](images/2023-01-05_17_23_28-Path.jpg "Full User path")

Open a terminal and type `php -v` you should now see PHP has been added.

Example PowerShell:

![!PowerShell](images/2023-01-05_17_40_13-PowerShell.jpg "PowerShell")

{{% alert %}}
If you have a message like 'php: The term 'php' is not recognized ...', you will need to **Sign out** and **Log in**
for the user path to take effect.
{{% /alert %}}

