=== Dummy Plugin ===
Contributors: frogerme
Donate link: https://froger.me
Tags: dummy, other dummy
Requires at least: 4.9.8
Tested up to: 4.9.8
Requires PHP: 7.0
License: GPLv3
License URI: https://www.gnu.org/licenses/gpl-3.0.html

Empty plugin to demonstrate the WP Package Updater.

== Description ==

Plugin description. <strong>Basic HTML</strong> can be used in all sections.

== Dummy Section ==

An extra, dummy section.

== Installation ==

Installation instructions.

== Changelog ==

<p>This section will be displayed by default when the user clicks 'View version x.y.z details'.</p>

== Frequently Asked Questions ==

= How does it work? =
WP Remote Users Sync "listens" to changes related to WordPress users, and fires outgoing "actions" to registered remote sites. The registered remote sites with WP Remote Users Sync installed then catch incoming actions and react accordingly.
There is no "Master Website": each site is working independently, firing and receiving actions depending on each site's configuration.

= It's not working! =
Before opening a new issue on <a href="https://github.com/froger-me/wp-remote-users-sync">Github</a> or contacting the author, please check the following:

* The URLs used in settings of WP Remote Users Sync **exactly** match the URL in your WordPress settings: the protocol (`https` vs. `https`) and the subdomain (www vs. non-www) must be the same across the board. It is also worth checking the `home` option in the `wp_options` table of the WordPress databases, because in some cases the content of Settings > General > WordPress Address (URL) gets abusively overwritten by plugins or themes.
* Visit the permalinks page of each connected site (Settings > Permalinks)
* Activate and check the logs on both local and remote sites when testing (WP Remote Users Sync > Activity Logs > Enable Logs) ; try to find any discrepancies and adjust the settings
* Make sure the feature you have issue with is NOT triggered by a third-party package (plugin or theme). If it is (for instance, data is not synced when updating a user from the front end, but works fine in the admin area), please contact the developer of the third-party package and ask them to follow best practices by triggering the appropriate actions like WordPress core does in the admin area when a user is updated.
* Read the Resolved threads of the support forum - your issue might have already been addressed there

Only then should you open a support thread, with as much information as possible, including logs (with critical information obfuscated if necessary).
Also please note this plugin is provided for free to the community and being maintained during the author's free time: unless there is a prior arrangement with deadlines and financial compensation, the author will work on it at their own discretion. Insisting to contact the author multiple times via multiple channels in a short amount of time will simply result in the response being delayed further or even completely ignored.

= In Safari and iOS browsers, why do I see a "Processing..." message on Login, and why are users logged out everywhere on Logout? =

Because these browsers prevent cross-domain third-party cookie manipulation by default, explicit redirections to log in users and destroying all the user sessions when logging out are necessary. With this method, only first-party cookies are manipulated. This is akin to logging in Youtube with a Google account.

Please note that the Login User Action takes a significantly longer time to process when using explicit redirections, particularly if many remote sites are connected.

= Login & Logout are not working =
Login and Logout User Actions need to output some code in the browser to have an effect on the remote website because of the cookies used for authentication.

= What happens to existing users after activating WP Remote Users Sync? =
Existing users remain untouched, until an enabled incoming action is received from a remote site.
Users existing on one site and not the other will not be synchronised unless the user is actually updated AND both Create and Update actions are enabled on the site where the user does not exist.
For existing user databases in need of immediate synchronisation, WP Remote Users Sync provides its own user import/export tool.
