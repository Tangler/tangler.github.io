# Getting started with Tangler

This short guide will take you through your first steps in Tangler.
Once you've seen how it works, you are ready to create your own Tangler files.
This is where the fun starts, as the possibilities are endless!

## Installing Tangler

    # Get the main sourcecode.
    git clone git@github.com:Tangler/Tangler.git

    # Install dependencies in ./vendor/
    composer.phar install --prefer-dist
    
p.s.: don't have composer? [get it here](http://getcomposer.org/download/), it's awesome!

## Running examples

Let's go through some simple examples to get you started:

### file2smtp

Edit `example/file2smtp.xml` 

    <tangler>
        <channel>
            <key>file2smtp</key>
            <label>Send all new files in a given directory by email</label>
            <description>
                Monitors the source directory for new files. 
                When new files are detected, they are sent through smtp
                to the provided email address.
            </description>

            <!-- 
                Configure the trigger and it's parameters 
            -->
            <trigger class="Tangler\Module\File\NewFileTrigger">
                <parameter key="dir">/tmp/tangler.in/</parameter>
            </trigger>

            <!-- 
                Configure the action and it's parameters, 
                using variables provided by the trigger 
            -->
            <action class="Tangler\Module\Smtp\SendEmailAction">
                <parameter key="smtp.host">mail.example.web</parameter>
                <parameter key="smtp.username">myusername</parameter>
                <parameter key="smtp.password">mypassword</parameter>
                <parameter key="subject">New file: {{filename}}</parameter>
                <parameter key="from">tangler@example.web</parameter>
                <parameter key="to">me@example.web</parameter>
                <parameter key="body">Hey, this is Tangler,
                    I spotted a new file: '{{filename}}':
                    {{content}}
                    Kind regards,
                    Tangler
                </parameter>
            </action>
        </channel>
    </tangler>


First up, enter or edit the trigger parameter key `dir` and enter a valid source directory (for example: `/tmp/tangler.in/`), 
Then edit the action parameters, especially the SMTP variables like `smtp.hostname`, `smtp.username` and `smtp.password`.

Now you can start your tangler file like this:

    vendor/bin/tangler run:file example/file2smtp.xml

Copy a textfile into `/tmp/tangler.io/` and see how Tangler picks it up, and emails it to you!

### imap2hipchat

Edit `example/imap2hipchat.xml` and enter a the imap credentials in the trigger section.

Obtain an `apikey` here: [https://www.hipchat.com/admin/api](https://www.hipchat.com/admin/api).
View the available rooms here: [https://www.hipchat.com/admin/rooms](https://www.hipchat.com/admin/rooms) and find the `api roomid` of the room you want to publish your messages to.

Now you can start your tangler file like this:

    vendor/bin/tangler run:file example/imap2hipchat.xml

Now send an email to the provided imap account and watch Tangler notify you in HipChat with subject, sender, etc!

## You are reading to start Tangling!

Now that you've seen the basics, it's time to create your own Tangler files! 
Check out the [available modules](modules), and see what Triggers and Actions they provide.

We are looking forward to hearing about the amazing things you'll create...
Be sure to share your creations with us, and we'll share them on our 
[Twitter](https://twitter.com/tangler_io) and [Facebook](https://www.facebook.com/tangler.io) accounts to inspire others!

Happy Tangling!  
*Team Tangler*

