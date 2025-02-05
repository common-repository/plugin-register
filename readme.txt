=== Plugin Register ===
Contributors: mrwiblog
Donate link: http://www.stillbreathing.co.uk/donate/
Tags: plugin, register, activation, count, statistics, developer
Requires at least: 2.8
Requires PHP: 5.6
Tested up to: 4.7.2
Stable tag: 0.6.5

For Wordpress plugin developers: keep a register of when and where your plugins are activated.

== Description ==

If you are a Wordpress plugin developer the chances are your plugins are available for download from the Wordpress plugin repository. As part of that service the nice guys at Wordpress show you how many downloads of your plugin you get per day. Very useful, and if you're like me you check your downloads numbers very often.

However what these stats don't show you is where your plugin is in use - which sites it is actually being activated on. Seeing that information would allow you to see exactly which sites are using your plugin, when they installed it, and what version the site is running. That is exactly what Plugin Register does.

By including the Plugin_Register class and calling it with some simple code in your plugin, your plugin will prompt the user to register your plugin when they activate it. When they register the plugin, the Plugin Register database on your site will be updated with the name and version of your plugin, and the site name and URL where that plugin has just been activated. A simple call is made to your website to save these details in the Plugin Register table, and you get some great statistics on which site is installing what versions of your plugins.

So, what do you need to put in your plugin? This example code hows you everything you need:

`// include the Plugin_Register class
require_once( "plugin-register.class.php" );

// create a new instance of the Plugin_Register class
$register = new Plugin_Register(); // leave this as it is
$register->file = __FILE__; // leave this as it is
$register->slug = "pluginregister"; // create a unique slug for your plugin (normally the plugin name in lowercase, with no spaces or special characters works fine)
$register->name = "Plugin Register"; // the full name of your plugin (this will be displayed in your statistics)
$register->version = "1.0"; // the version of your plugin (this will be displayed in your statistics)
$register->developer = "Chris Taylor"; // your name
$register->homepage = "http://www.stillbreathing.co.uk"; // your Wordpress website where Plugin Register is installed (no trailing slash)
$register->Plugin_Register(); // set Plugin Register to be called when the plugin is activated

The reports you get include:

* Graphs showing how many registrations have been made for the last 24 hours, 14 days, 12 weeks and 12 months
* A list of all plugins registered, with how many unique versions and unique sites
* A list of all versions of a particular plugin, with the number of unique sites
* A list of all sites which have registered any of your plugins
* Details of what plugins were registered on a particular day
* A search, so you can see what sites have got version X of plugin Foo_Bar installed

== Privacy ==

Registering a plugin is completely up to the user who has just activated it. Plugin Register does NOT automatically send any data back to your website without the user manually clicking a link. Some text is displayed which invites the user to register the plugin, by default it says:

"Please consider registering your use of [your plugin name] to tell [your name] (the plugin maker) you are using it. This sends only your site name and URL to [your name] so they know where their plugin is being used. No other data is sent."

It is possible to override this default text on a per-plugin basis.

== Installation ==

1. Install from the Wordpress plugin repository
2. Activate the plugin through the 'Plugins' menu in WordPress
3. Include the plugin-register.class.php file in your plugins, instructions for how to make it work are in that file

== Screenshots ==

1. Display graphs of numbers of plugins registered over the last 24 hours, 14 days, 12 weeks or 12 months
2. Display how many registrations of each plugin you have, plus the count of unique versions and unique sites
3. Display sites which have registered their first plugin in the last 30 days
4. Display all the versions of a plugin which have been registered
5. Search registrations by site name or URL, plugin name and plugin version 

== Frequently Asked Questions ==

= Why did you write this plugin? =

Although the download stats for the Wordpress repository are great, they don't actually tell you where your plugins are installed. Having a way of seeing which sites are activating your plugins - and therefore where they are actually used, not just whether they are download - is fantastic to see your Open Source work actually in use.

= Is any personally-identifiable information saved? =

No. The only information saved by Plugin Register is the name and version of the plugin, and the name and URL of the Wordpress site it is installed on. I do not intend to ever get any persons personal information using this plugin. Registration is also manually-triggered, so no details are stored without the permission of the person who activated the plugin.

== Changelog ==

= 0.6.5 =

Moved screenshots to the right place (sorry).

= 0.6.4 =

Updated readme to make it clearer that the plugin only sends data when authorised by the user. Added screenshots.

= 0.6.3 =

Fixed deprecation error messages. Tested up to 4.7.2.

= 0.6.2 =

* Added SQL to create indexes which speed up queries

= 0.6.1 =

* Commented out call to cron notifications as it caused out of memory exceptions

= 0.6 =

* Added additional information to some reports
* Made reports quicker to navigate
* Rewrote a lot of SQL statements
* Added report to show list of registered sites

= 0.5.2 =

* Fixed error caused by latest WordPress version when activating plugins

= 0.5.1 =

* Added admin dahboard mini report
* Added list of plugins to new domain registrations report
* Added 12 month registrations view

= 0.5 =
* Added functions to delete registrations for an entire site, or an individual registration, fixed small bugs

= 0.4.2 =
* Changed register calls to use wp_remote_* functions

= 0.4.1 =
* Updated plugin URI

= 0.3 =
* Made registration manual
* Added date range graphs

= 0.2 =
* Changed main report to show just new sites registered in the last week, and show the total number of registrations and unique sites

= 0.1 =
* Initial Wordpress plugin repository commit

== Upgrade Notice ==

= 0.3 =
This version makes the registration process manual, rather than automatic. Several people were unhappy that this plugin automatically gathered information about their sites, so I changed it to be an explicit user action to register a plugin.