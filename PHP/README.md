
## Sessions

### Creating a session
Creating a session essentially creates a temporary storage area for each unique user. It allows you to assign each user a special token. When the user interacts with the website, this token is sent along with it. This allows your website to recognize the user and retrieve information about the user.

This code is typically included at the top of the page.

```PHP
session_start();
```

Typically upon login, a session variable is set. You can check if the session variable has been set, and therefore check if a user is logged in. Here is an example of setting a session variable after login:

```PHP
$_SESSION["username"] = $username;
```
This variable holds the user's username. Then, you can check if that user is signed in. Note that this only works if `session_start()` has been activated first, and a session exists:

```PHP
if (isset($_SESSION["username"])) {
  // do something if the user is logged in
} else {
  // do something else if the user is not logged in
}
```

### Destroying a session
When a user logs out, it's typical to destroy their session so it no longer exists. If you're doing this on a new page where a session hasn't been started yet, you must start the session first and then destroy it.

```PHP
session_start();
session_destroy(); 
```

## Configuration file
Typically with any PHP project, there is a configuration file which holds the project's sensitive database credentials. 

To do this, you usually want to use *constants* that cannot be changed. For example:

```PHP
define("host", "localhost");
define("user", "root");
define("password", "" );
define("dbname", "database_name");
```

Constants are like variables but they cannot be overwritten. Instead of referring to the host as `$host` you could just use `host` and, as long as you've defined that term as a constant, the code will know what you are referring to.

### Check if the configuration is correct

You can include some extra code to check if the connection is working or not, which can save some time when experiencing credentials-related errors:

```PHP
$con = mysqli_connect(host, user, password, dbname);
if (!$con) {
  die("Connection failed: " . mysqli_connect_error());
}
```

## Date and time
Working with date and time in PHP requires a little bit of extra work.

Typically if you want to create a date object, you can use `date()` and then inside of the parenthesis you can clarify how you want the date to be formatted.

```PHP
date("Y-m-d");
```
The above will display the date as: **2023-01-01**

You can also include the time if desired:

```PHP
date("Y-m-d H:i:s");
```
The above will display the date as: **2023-01-01 15:30:45**

For reference you can view: [formatting dates and times in PHP](https://www.php.net/manual/en/datetime.format.php).
