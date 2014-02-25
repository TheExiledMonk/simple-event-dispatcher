Simple PHP Event dispatcher library
===================================

This is a simple event dispatcher and handling library for PHP. I found I kept having
to cut and paste this about, so instead I decided to put it into its own library
with hopes of saving me some time.

One particularly useful feature of this code is that it supports Regex wildcards on handlers.

Usage
-----

```php
    require_once('Events.php');
    
    // Register an event for every time a user is created
    \simple_event_dispatcher\Events::register('user', 'create', function($namespace, $event, &$parameters) { 

        // Your code here

    });


    .
    .
    .

    class MyExampleFrameworkUser {

        ...


        public function Create($username, $passcode) {

            ...

            // User creation code

            ...


            // Ok, user is created, tell anyone who's interested
            \simple_event_dispatcher\Events::trigger('user', 'create', [
                'user' => $new_user
            ]);

        }

    }

```

Author
------

* Marcus Povey <marcus@marcus-povey.co.uk>
