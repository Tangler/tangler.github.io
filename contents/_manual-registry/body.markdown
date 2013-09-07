# The Registry

In order to prevent triggers from being processed multiple times, Tangler uses a 'Registry'.

A 'Registry' simply keeps track of all the triggers it already processed, and allows you to check if a 'new' trigger was already processed before, based on a unique key.

## How does it work?

Every processed trigger in the registry contains 2 parts:

* The `base`: usually the classname of the trigger (i.e. `Tangler\Module\File\newFileTrigger`)
* The `key`: Anything that uniquely identifies the trigger (i.e. `filename.txt_1378564674`)

### Example of a 'key' in the NewFileTrigger:

When monitorring a directory for new files, the key can be the filename + the file modification stamp.

This way, no matter how often the trigger detects the file, it will only process it once.

When you create a new file with another filename, the key will be unique, and the trigger will process.
When you update the file, and the file modification stamp changes, the key will be unique, and the trigger will process.

### Example of a 'key' in the NewEmailTrigger:

When monitorring an IMAP account for new messages, you can use the hostname + username + mailbox + IMAP Message UID as a unique key.

## Configuring the registry

If you don't configure anything, Tangler will store the registry information in a new SQLite file called `tangler.sqlite3`.
The file will be created in the directory where you start tangler.

Using an SQLite database as a registry works great for most installations.

If you intend to create enormous registry databases, or scale tangler horizontally across multiple nodes, you have another option:
You can configure the registry to store it's information in a database of your choosing.

The default Tangler distribution comes with a PdoRegistry driver, which you can use to store registry information in any PDO supported database.

To store your registry data in a MySQL database for example, you can add the following snippet to your tangler .xml file:

    <tangler>
        <registry class="Tangler\Core\PdoRegistry">
            <parameter key="dsn">mysql:dbname=tangler;host=127.0.0.1</parameter>
            <parameter key="username">username</parameter>
            <parameter key="password">password</parameter>
        </registry>
    </tangler>

NOTE: When you change the configuration of your registry, it will most often start out empty. 
This means that any trigger will be executed, even if it has been triggered before.

## How do I use the registry in my own Triggers?

When developing new Triggers, you can easily use the registry to prevent triggers from being processed multiple times.

A great example can be found in the 'newFileTrigger' class. In short, your code will look something like the following:


    namespace Tangler\Module\MyModule;

    use Tangler\Core\Interfaces\TriggerInterface;
    use Tangler\Core\AbstractTrigger;

    class NewExampleTrigger extends AbstractTrigger implements TriggerInterface
    {
        public function init()
        {
            // perform your usual init code
            // possibly registering existing triggers in the registry already
        }

        public function poll()
        {
            // Create a unique identifier for the current trigger
            // Something involving unique id's, names, or timestamps usually works great
            // The exact value of the key is not important, 
            // as long as it's unique for your trigger
            $key = 'some_unique_key';

            if (!$this->isProcessed($key)) {
                // Add your normal trigger processing code here..
                $this->setProcessed($key);
            }
        }
    }