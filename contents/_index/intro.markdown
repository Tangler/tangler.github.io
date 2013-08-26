# What is Tangler?

Tangler allows you to integrate many different types of systems and services. No code required!

## Example use-cases

* Send an email through <b>SMTP</b> when you receive a <b>HipChat</b> message
* Send a <b>HipChat</b> message when a new <b>local file</b> is detected in a selected directory
* Send a <b>Pushover</b> notification when a new message arives in your <b>IMAP</b> account
* Create a new <b>local file</b> on your machine when someone subscribes to your <b>MailChimp</b> account
* ...etc. *The options are limitless!*

It allows your script or application to work with **any** of the [available modules](modules.html), 
no matter what programming language you use.



## How does it work?

Tangler let's you define `channels`. For example, you can create your own `Email to HipChat` channel.

Each `channel` contains:

1. A `trigger` (i.e. new email in specified IMAP account)
2. One or more `actions` (i.e. send a message to HipChat)

Tangler will watch for triggers, and as soon as they happen, pass on the information to the selected actions. 
This allows you to use the information from the Trigger (like the email subject, sender, body, attachments) in the Action (like the HipChat message, or sendername).

## Example configuration

This is an example configuration file for the above `file2email.xml` example: 


```
<tangler>
    <channel>
        <key>file2email</key>
        <label>File to Email</label>
        <description>Send an email by creating a file</description>
        <trigger class="Tangler\Module\File\NewFileTrigger">
            <parameter key="dir">/tmp/demo.in/</parameter>
        </trigger>
        <action class="Tangler\Module\Smtp\SendEmailAction">
            <parameter key="smtp.host">mail.example.web</parameter>
            <parameter key="smtp.username">myusername</parameter>
            <parameter key="smtp.password">mypassword</parameter>
            <parameter key="subject">New file: {{filename}}</parameter>
            <parameter key="from">tangler@example.web</parameter>
            <parameter key="to">me@example.web</parameter>
            <parameter key="body">{{filename}}: {{contents}}</parameter>
        </action>        
    </channel>
</tangler>
```

You can run this Tangler by typing: `tangler file2email.xml`

This will start Tangler, which will monitor the directory `/tmp/demo.in` for new files.

As soon as you create a new file there, 
Tangler will e-mail that file to you.

## Extendable

Tangler is super extendable through a simple PHP module system. Check the manual about [creating your own modules](manual-creating-modules.html)

## Source code and contributions:

Ready to hack with us? Check out the project and it's modules on GitHub:

* [github](http://github.com/Tangler)

Developed a new Module yourself? Please let us know so we can share it on our module list page!
