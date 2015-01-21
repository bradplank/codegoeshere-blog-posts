Ghost.js - Upstart Configuration
================================

Making Ghost.js production ready on a web server is extremely simple.  This post will cover the use of the three utilities below:

* [upstart](http://upstart.ubuntu.com/) - Upstart is an event-based replacement for the /sbin/init daemon which handles starting of tasks and services during boot, stopping them during shutdown and supervising them while the system is running.
* [forever](https://github.com/foreverjs/forever) - A simple CLI tool for ensuring that a given script runs continuously
* [su](http://manpages.ubuntu.com/manpages/gutsy/man1/su.1.html) - change user ID or become super-user

Here is a really simple example of creating an upstart configuration for Ghost to keep the app service (Node.js / Express) running even if the app service crashes or the server is rebooted [*/etc/init/ghost.conf*]:

```
#!upstart
description "upstart script for a production Ghost.js server"

start on startup
stop on shutdown

expect fork

script
    exec su -l ghost -c 'NODE_ENV=production forever start --uid "ghost" -a -l /home/ghost/Ghost/ghost.log --minUptime 5000 --spinSleepTime 2000 /home/ghost/Ghost/index.js'
end script

pre-stop script
    exec su -l ghost -c 'forever stop ghost'
end script
```

The above upstart configuration accomplishes the following to make the Ghost.js app service production ready:

* Ghost.js should be started after boot without user interaction
`start on startup`
* Hardening the server by starting Ghost.js as the 'ghost' user
`su -l ghost -c '<forever_command>'`
* Continuous uptime
`forever start [options] <script>`


After saving the upstart configuration [/etc/init/ghost.conf], it is time to test your hard work:

* Reboot the server, `reboot`
* List forever scripts, `su -l ghost -c 'forever list'`

If all went well, you should see the Ghost.js app service listed.  Upstart uses inotify to watch the configuration directory for changes if adjustments need to be made, however, if a job is running, all instances of the job must be stopped before the changes take effect.

Additional upstart information:

* [Frequently Asked Questions](http://upstart.ubuntu.com/faq.html)
* [The Upstart Event System: What It Is And How To Use It by Digital Ocean](https://www.digitalocean.com/community/tutorials/the-upstart-event-system-what-it-is-and-how-to-use-it)
