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

In Tangler, you create `channels`. For example, you can create your own `Email to Dropbox` channel.

Each `channel` contains:

1. A `trigger` (i.e. new email in specified IMAP account)
2. One or more `actions` (i.e. create file in Dropbox)

Tangler will watch for triggers, and as soon as they happen, pass on the information to the selected actions.

This allows you to use the information from the Trigger (like the email subject, sender, body, attachments) in the Action (like the Dropbox filename, content, etc).

Check out our simple [Getting started](manual-getting-started) guide to get Tangling in 5 minutes!

## Extendable through modules

Tangler is super extendable through a simple PHP module system. Read all about the [available modules](modules.html), or create your own!

## Source code and contributions:

Ready to hack with us? Check out the project and it's modules on GitHub:

* [github](http://github.com/Tangler)

Developed a new Module yourself? Please let us know so we can share it on our module index page!


