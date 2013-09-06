# Module wishlist

Tangler is a new project, and many modules remain to be implemented.
If you are interested in helping out, please do!

Here is a list of modules that we'd think will be valuable to add.
For each of them we try to maintain a list of urls to api docs, composer modules, or other useful resources.
For each module we specify ideas for triggers and actions.

## Dropbox

* [API Docs](https://www.dropbox.com/developers/core/docs)
* [Composer module](https://github.com/dropbox/dropbox-sdk-php)

### Trigger
- New file in folder
- New directory

### Action
- Create textfile
- Append textfile
- Copy file from trigger (copy existing file or attachment from the trigger)
- Create directory

## Twitter

### Trigger

- Search Mention: triggers from mention of search term
- My Tweet: when you tweet something new yourself
- Search & Geo Mention: Search mention in specific geo region
- New Follower 
- User tweet: when selected user tweets
- New favorited
- PM ?

### Action

- Create Tweet
- PM ?

## Schedule / Clock

Primarily to trigger events happening and specific intervals, times, days, etc

## Excel

Append data to an excel sheet, or generate new ones

## Facebook Private + Pages

### Trigger

- New PM
- New post by
- New post self
- New Tag
- New Comment on own post

## Mollie 

Send SMS messages through Mollie API

* [Website](http://www.mollie.nl)
* [Composer module](https://packagist.org/packages/linkorb/mollie-sms-php)

## Amazon S3

### Trigger
- New object
- New bucket

### Action
- Create bucket
- Copy file from trigger
- Create Text Object

## HipChat

* [API docs](https://www.hipchat.com/docs/api)
* [Composer module](https://github.com/hipchat/hipchat-php)

### Trigger

- New message in room
- New room

### Action

- ~~Send message~~
- Create Room Topic

## GitHub

* [API Docs](http://developer.github.com/v3/)
* [Composer module](https://github.com/KnpLabs/php-github-api)

### Trigger

- New Commit Comment
- New Pull Request
- New Organization (?)
- New Gist
- New Notification
- New Watcher
- New Repository
- New Branch

### Action

- Create Issue
- Create Pull Request

## Imap

* [PHP Module](http://nl1.php.net/manual/en/book.imap.php)
* [Composer module - zetacomponents](https://github.com/zetacomponents/Mail)


### Trigger

- New Email
- New Mailbox

### Action

None

## MailChimp

* [API Docs](http://apidocs.mailchimp.com/api/2.0/)
* [Composer module](https://bitbucket.org/mailchimp/mailchimp-api-php)

### Trigger

- New Subscriber
- New Campaign
- New Group
- New List
- New Unsubscriber

### Action

- Add subscriber
- Unsubscribe email

