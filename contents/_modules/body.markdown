# Tangler Modules

Tangler is super extendable through a simple PHP module system. 

Each module can provide:

* One or more **Triggers** (monitors stuff for events or changes)

And/or

* One or more **Actions** (does stuff)

Using a tangler config file, you can glue these triggers and actions together into an unlimited set of combinations!

## Available modules

* [File](module-file): Allows you to work with local files and directories
* [Smtp](module-smtp): Allows you to send e-mail messages through SMTP servers
* [HipChat](module-hipchat): Allows you integrate with the HipChat API

## Future modules

We maintain a list of modules on the [wishlist](/wishlist) page for future ideas.