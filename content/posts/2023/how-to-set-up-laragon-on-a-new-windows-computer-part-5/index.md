---
title: "How to set up Laragon on a new Windows computer (part 5) - MailHog"
date: 2023-01-04T15:10:19Z
draft: false
tags: [PHP, Resource, MailHog]
url: 2023/01/04/how-to-set-up-laragon-on-a-new-windows-computer-part-5
summary: "Laragon ships with Mail Catcher, which intercepts mail sent using the PHP mail() function. MailHog goes one
step further and acts as a local mailbox. No mail will ever leave the local PC!"
---

![Royal mail postbox](images/kutan-ural-yCxBGq7nuA8-unsplash.jpg "Royal mail postbox")
Photo
by [Kutan Ural](https://unsplash.com/@kutanural?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
on [Unsplash](https://unsplash.com/photos/yCxBGq7nuA8?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

{{< lead >}}
Laragon ships with Mail Catcher, which intercepts mail sent using the PHP mail() function. MailHog goes one step further
and acts as a local mailbox. No mail will ever leave the local PC!
{{< /lead >}}

## Download MailHog

Download MailHog from [releases](https://github.com/mailhog/MailHog/releases), the file for Windows
is **MailHog_windows_amd64.exe**

![MailHog_windows_amd64.exe](images/2023-01-04_17_12_23-Releases_mailhog_MailHog.jpg "MailHog_windows_amd64.exe")

## Copy to Laragon

Create a directory in the laragon bin folder called **mailhog**

Copy the downloaded file and rename it **MailHog.exe**

![MailHog.exe](images/2023-01-04_17_21_28-mailhog.jpg "MailHog.exe")

## Hosts file

Click the red **h** in the top right corner of Laragon, you will need to allow elevated privileges. By default,
the C:\WINDOWS\system32\drivers\etc\\**hosts** file will open in **notepad++**

Add the following lines above any Laragon magic:

```ini
# Manual
127.0.0.1      mailhog	    # Manual for laragon\bin\MailHog.exe

# Laragon magic
```

Save the file, you may need to allow elevated privileges again.

## Autostart

Open Laragon's procfile (**Laragon menu > Laragon > Procfile**) and add these lines:

```ini
MailHog.exe : autorun MailHog.exe PWD=C:\laragon\bin\mailhog
MailHog Admin : autorun http://mailhog:8025 
```

Every time Laragon starts the **MailHog.exe** will automatically run, in the background, and the MailHog admin website
will launch.

## App settings

Any apps you create will need to be configured to use the following settings:

- mail protocol: smtp
- hostname: mailhog
- port: 1025

Example Laravel app:

```ini
MAIL_MAILER = smtp
MAIL_HOST = mailhog
MAIL_PORT = 1025
MAIL_USERNAME = null
MAIL_PASSWORD = null
```

The above settings are the **default** for a Laravel app! No further changes are required 🎉

## Testing

Start Laragon (or stop and start), the MailHog admin page should open in your default bowser.

To test it's working, in any Laravel project, open a **tinker** console `php artisan tinker`. Send the welcome view by
email:

```php
Mail::send('welcome', [], fn($message) => 
$message->to('admin@example.com')->subject('Testing MailHog'));
```

You should see `= Illuminate\Mail\SentMessage {#4721}`, the number will be different.

View the MailHog admin page in your bowser, click the inbox and the message to open it:

![MailHog inbox](images/2023-01-04_18_07_12-MailHog.jpg "MailHog inbox")

## mail() settings

Apps which use the PHP mail() function can be configured by editing the **php.ini**:

**Laragon menu > PHP > php.ini**, by detail it will open in **Notepad++**

Search (**CTRL** **F**) for **mail function**

Amend as follows:

```ini
[mail function]
; For Win32 only.
; https://php.net/smtp
SMTP = mailhog
; https://php.net/smtp-port
smtp_port = 1025

; For Win32 only.
; https://php.net/sendmail-from
sendmail_from = laragon@example.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
; https://php.net/sendmail-path
;sendmail_path =

; Force the addition of the specified parameters to be passed as extra parameters
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail().
;mail.force_extra_parameters =

; Add X-PHP-Originating-Script: that will include uid of the script followed by the filename
mail.add_x_header = Off

sendmail_path="C:/laragon/bin/mailhog/MailHog.exe sendmail"
```

### Test mail()

Open terminal (cmdr) and enter the PHP interactive shell.

```shell
php -a 
```

In the PHP interactive shell type (or paste) the following:

```php
mail('my_mail@example.com','Test', 'Test message', 'From: Laragon');
```

Open MailHog to view the message:

![MailHog via mail()](images/2023-01-15_15_49_55-MailHog.jpg "MailHog via mail()")

## Stop MailHog.exe

Laragon will start MailHog using the Procfile, however, it will not close the running service when Laragon is exited.

### Command line

One of the easiest ways is from the command line:

From the command line, MailHog can be verified if it's still running:

```shell
tasklist | findstr /i /c:"MailHog.exe"
```

The output will be similar to:

```text
MailHog.exe        9360 Console         1     11,188 K
```

To kill the process:

```shell
taskkill /im MailHog.exe /f
```

Which will output similar to:

```text
SUCCESS: The process "MailHog.exe" with PID 9360 has been terminated.
```

This is dependent on the process being started as an administrator, or your account, you may need elevated privileges to
stop it.

### Task manager

To end the MailHog.exe process using **Task Manager**:

1. open Task Manager (<kbd>Win</kbd> start typing **Task** and press <kbd>Enter</kbd> when Task Manager displays as the
   first item)
2. sort by process **name** by clicking the **name** heading, the cravat **^** should display 
3. **expand all** (under **view** dropdown)
4. look down the list for Laragon (even if Laragon is closed, it will be shown under background processes)
5. right-click **MailHog.exe**
6. select **End task**

![Task manager](images/2023-01-08_12_48_03-Task-Manager.jpg "Task manager")

Personally, MailHog takes up 0.1% of memory and very little process, so I just leave it running, even after I close
Laragon.

## Further information

Mailhog has a **Chaos Monkey**, inspired by Netflix. Which can randomly add faults. This can be used to test how your
app responds to mail failures: [Introduction to Jim](https://github.com/mailhog/MailHog/blob/master/docs/JIM.md)

[Authentication](https://github.com/mailhog/MailHog/blob/master/docs/Auth.md) can be set up, as required.
