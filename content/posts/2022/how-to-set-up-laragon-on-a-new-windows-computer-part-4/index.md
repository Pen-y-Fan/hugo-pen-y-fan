---
title: "How to set up Laragon on a new Windows computer (part 4) - Enable security"
date: 2022-11-10T10:19:31Z
draft: false
tags: [PHP, Resource, SSL, Apache, Firefox]
url: 2022/11/10/how-to-set-up-laragon-on-a-new-windows-computer-part-4
summary: "When developing projects the development environment should be as close as possible to the production one. We
can and should enable security"
---

![Padlock and chain](images/john-salvino-bqGBbLq_yfc-unsplash.jpg "Padlock and chain")
Photo
by [John Salvino](https://unsplash.com/@jsalvino?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
on [Unsplash](https://unsplash.com/s/photos/security?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

{{< lead >}}
This is part 4 on how to set up and install Laragon.

When developing projects, the development environment should be as close as possible to the production one. We are
already at a disadvantage developing on Windows when normally, our production environment is Linux. We can not do
anything about this, we have a Windows computer! We can and should enable security.
{{< /lead >}}

## Certificates

Laragon makes security certificates for local development a doddle, this is a two-step process.

### Enable SSL

Select the Laragon **Preferences cog** in the top right

![Preferences cog](images/2022-11-10_10_37_23-Laragon_Full.jpg "Preferences cog")

Enable SSL by clicking the **Enabled** checkbox in line with Apache SSL.

![Apache SSL Enable](images/2022-11-10_10_42_18-Preferences.jpg "Apache SSL Enable")

Close the Preferences by clicking the **X**

## Add the certificate to the trusted store

From the Laragon menu, click the **Menu**, choose **Apache**, choose **SSL**,
select **Add laragon.crt to Trusted Store**

![Add laragon.crt to Trusted Store](images/2022-11-10_10_46_16-Trust-Store.jpg "Add laragon.crt to Trusted Store")

Elevated user access control is required.

## Launch Web

Next click the **Web** button, which will launch the Laragon <https://localhost> site. If all has gone well it will have
a padlock 🔒.

![Laragon with padlock](images/2022-11-10_11_43_56-Laragon.jpg "Laragon with padlock")

## Troubleshooting

### Accept the Risk

Some browsers have extra security for self-signed certificates. There is normally a way to accept, for example with
Firefox, choose **Advanced...** and then **Accept the Risk and Continue**

![Warning - Accept the Risk and Continue](images/2022-11-10_11_32_16-Accept-the-risk.png "Warning - Accept the Risk and Continue")

For other browsers Google "\<browser name\> how do I allow self-signed certificates on localhost", there are many
fixes.
