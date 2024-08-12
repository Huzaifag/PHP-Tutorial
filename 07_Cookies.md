## Setting Cookies & $_COOKIE super global in PHP

**Introduction**

In our previous tutorials, we have learned to write and append to files in PHP. Now, in this tutorial, we will learn about cookies in PHP. So, let's fire up our favorite code editor and start coding.

**Cookies:**
A cookie is a small file that the server embeds on the user's computer to identify him next time whenever we visit the website.
Cookies are used to store the information of a web page in a remote browser, So that when the same user comes back to that page , that information can be retrive from browser itself.

**Usage of Cookies:**

> Session Management:Cookies are widely used to manage sessions, For example, 
when you use online shopping cart, you keep adding items into your cart and finally when checkout, all those items are added to the list of items you have purchased. 
This can be achieved using cookies.

>

 The syntax for creating a cookie is:
```php
setcookie ( name , value ,expiration time , path = "");
```
Now name and value arguments are self-explanatory, the expiration time is when the cookie will expire [e.g., for 1 day, we will use 86400 seconds], and for path, we can use "/" to use it everywhere on the site. Now, let's create a cookie:

```php
<?php
echo "Welcome to the world of cookies<br>";
// Syntax to set a cookie
// echo time();
setcookie("category", "Books", time() + 86400, "/"); 
echo "The cookie is set<br>";
?>
```
Now, We need to check if the cookie is working or not. To check the cookie open the site in a browser, then open developer tools by pressing f12, then go to network, You will see the cookie in the response header.

![Alt text](fig/cookies%20.png);
