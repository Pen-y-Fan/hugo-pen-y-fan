---
title: "How to set up Laragon on a new Windows computer (part 2) - permissions"
date: 2022-11-08T14:04:35Z
draft: false
tags: [Laragon, Resource, WAMP, permission]
url: 2022/11/08/how-to-set-up-laragon-on-a-new-windows-computer-part-2
summary: "Laragon needs permission to run and access through the Windows firewall"
---

![SpaceX Falcon Heavy Launch](images/spacex-OHOU-5UVIYQ-unsplash.jpg "SpaceX Falcon Heavy Launch")
Photo
by [SpaceX](https://unsplash.com/@spacex?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
on [Unsplash](https://unsplash.com/s/photos/Rocket%20launch?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

{{< lead >}}
This is part 2 on how to set up and install Laragon.

Now Laragon is installed it needs permission to run and access through the Windows firewall
{{< /lead >}}

## First launch

After the restart, Laragon will automatically open, if you selected that option, otherwise press the Windows key, start
typing **laragon**, and press Enter as soon as Laragon is the top option.

![Laragon](images/2022-09-16-22-38-22-laragon-full-6-0-220916-php-8-1-10-win-32-vs-16-x-64-ts.jpg "Laragon")

### File permissions

Laragon needs to create files, and run executable programs, such as Apache and MySQL, I recommend you run Laragon using
your standard user account, rather than using "run as admin", or being prompted for elevated privileges every time you
open Laragon. Your standard user account should have permission to run Laragon.

Open Windows file explorer (tip: hold the Windows key and press e), navigate to the drive you installed Laragon,
e.g. **(C:)**, right-click the **laragon** folder and click **properties**.

1. Select the **Security** tab.
2. Under **Group or user names** check either Authenticated Users or Users have at least Modify permission
3. If they don't have at least **Modify** permission: click the **Edit** button (allow elevated privileges/enter your
   admin password)
4. Select **Users**
5. Click **Allow** next to Full control
6. **Apply**, **OK**
7. **Apply**, **OK**

![Laragon permissions](images/2022-11-07-00-15-04-laragon-permissions.jpg "Laragon permissions")

This will give your standard user account permission to run Laragon without needing to "run as admin" all the time.

### Allow firewall access

Switch back to **Laragon**.

Press the **Start All** button

The first time you start Laragon, the Windows defender firewall will prompt you to Allow access.

#### Allow MySQL

Select both checkboxes and click **Allow Access**, you will need to allow elevated privileges or need to enter an
administrator account.

![MySQL Windows Defender Firewall](images/2022-09-16-22-38-53-windows-security-alert.jpg "MySQL Windows Defender Firewall")

#### Allow Apache

Also, allow Apache. Select both checkboxes and click **Allow Access**, you will need to allow elevated privileges or
enter an administrator account.

![Apache Windows Defender Firewall](images/2022-09-16-22-39-26-windows-security-alert.jpg "Apache Windows Defender Firewall")

In the future you may enable NGINX or Redis, they will also need permission.

No data is being sent out from your computer, they need access to your network, this is the localhost or 127.0.0.1 
loopback address.

## Web

Switch back to **Laragon**, which should have Apache and MySQL started, and press the **Web** button.

![Laragon's main screen (started)](images/2022-11-08-14-31-55-laragon-full-6-0-220916-php-8-1-10-win-32-vs-16-x-64-ts.jpg "Laragon's main screen (started)")

Your default web browser will launch and the Laragon welcome page will display.

![Laragon's welcome screen](images/2022-11-08-14-42-52-laragon.jpg "Laragon's welcome screen")

That's the basics done! New projects can be created, and you are good to go! 🎉
