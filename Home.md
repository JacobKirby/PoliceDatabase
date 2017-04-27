# Documentation - Still a work in progress
## Build Version 1.1.2

#### Getting Started
You need to have somewhat knowledge of web servers and their workings to operate this, I cannot go over every little step. To get started you'll need to upload the web files to a server. Then import the 'database.sql' file into a database, this can easily be done using phpMyAdmin.

If you’re using SSL on your site, then you need to go into **/php_includes/base.inc.php/** and uncomment out
>if(!isset($_SERVER['HTTPS']) && !strstr($_SERVER["HTTP_CF_VISITOR"], "https")) {
	header("Location: https://$_SERVER[HTTP_HOST]$_SERVER[REQUEST_URI]", true, 303);
	exit();
}

Once that's done go ahead and navigate to wherever you uploaded the files to and go ahead and register yourself. Once registered go into the database (I recommend using phpMyAdmin) and go to the `users` table. You should see yourself and click edit. Where it says `dept` and `rank`, this is where your department and rank status goes. If you look at the `dept` table, you'll see the ID of each department, that's what you'll put in on the `dept` column in users. For the rank column in `users`, it goes by the 'ranks' column in `dept`. Everything is in numerical order, and starts at 0.

Example: If you're a Sergeant in SWAT, then your department will be 5 and your rank will be 2.

To get you setup as the administrator, set your `dept` to 2 and your `rank` to 0. This will put you into the Staff department, and set your rank to Admin. Then click save.

From here, go ahead and login/refresh the site and you'll see all the pages. Navigate to Admin Tools -> Database Settings. Go ahead and set all the settings it's asking for. You can change these at any time, and set to whatever you wish.

Once that's done, the database is ready to be used for your members. Keep reading for further instructions on how to do things.

### Still need help?
As I try not to pay attention to this project anymore, support is limited. However, if you need me, feel free to email me: contact@coltonbrister.com

Along with that, I do offer installations for a fixed price of $35. I do not accept PayPal.

### Changing Passwords
If a user of yours happens to forget their password, you'll need to follow the steps bellow to get it changed for them.

1. Direct them to `/passhasher.php` and ask them to enter in a new password.
2. This will spit out a hash/salt, ask them to copy/paste that to you.
3. Navigate to the `users` table and find the officer in the `display` column and click edit.
4. Copy/paste the hash into the `hash` column and then do the same thing for the salt in the `salt` column.
5. Click save, make sure they can login and you're done.
**Note: Some people tend to forget their username, so give them their username as well. This can be found in the `uname` column.**