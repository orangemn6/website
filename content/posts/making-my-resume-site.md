---
title: "Making My Resume Site"
author: Jacob Goldstein
date: 2021-01-19T13:06:15-05:00
draft: false
type: post
categories:
 - webdev
tags:
 - webdev
---

So as some of you may know, I made a new resume site for myself. The url is [beta.jacobgoldstein.tk](https://beta.jacobgoldstein.tk], and it looks SICK. In this post I am going to walk you through some of the things I did.

#### [Contact Page](https://beta.jacobgoldstein.tk/contact.html)

So for the contact page, the form is controlled by a JS snippet that gets data from a PHP file. The PHP file has info like who to send it to, and all the email variables. Here is what it looks like:

```php
<?php
    $to = "linuxjacob@mail.com"; // replace this mail with yours
    $from = $_SERVER['PHP_SELF']." ".$_POST["email"];
    $fname = $_POST["name"];
    $email = $_POST["email"];
    $lname = $_POST["subject"];
    $headers = "From: $from";
    $message = $_POST["message"];

    $body = "User Message \n";
    $body .= " \n\n\t Name: ".$name;
    $body .= " \n\n\t Email: ".$email;
    $body .= " \n\n\t Subject: ".$subject;
    $body .= " \n\n\t Message: ".$message;

    if(mail($to, $subject, $body, $headers)){
        echo '<label class="success">Sent your <b>e-mail.</b></label>';
    }else{
        echo '<label class="error">Something went wrong! please try again.</label>';
    }
```


#### [About Page](https://beta.jacobgoldstein.tk/about.html)

On my about page, you can see the animated skills bar. That is done with some html and css. Here is an example.

HTML:
```html
 <p>HTML</p>
<div class="container">
  <div class="skills html">90%</div>
</div>

<p>CSS</p>
<div class="container">
  <div class="skills css">80%</div>
</div>

<p>JavaScript</p>
<div class="container">
  <div class="skills js">65%</div>
</div>

<p>PHP</p>
<div class="container">
  <div class="skills php">60%</div>
</div>
```

CSS
```css
/* Make sure that padding behaves as expected */
* {box-sizing:border-box}

/* Container for skill bars */
.container {
  width: 100%; /* Full width */
  background-color: #ddd; /* Grey background */
}

.skills {
  text-align: right; /* Right-align text */
  padding-top: 10px; /* Add top padding */
  padding-bottom: 10px; /* Add bottom padding */
  color: white; /* White text color */
}

.html {width: 90%; background-color: #4CAF50;} /* Green */
.css {width: 80%; background-color: #2196F3;} /* Blue */
.js {width: 65%; background-color: #f44336;} /* Red */
.php {width: 60%; background-color: #808080;} /* Dark Grey */
```

#### Conclusion

A magician never reveals their secrets, which is why I didn't include everything. You *can* view the source code [here](https://github.com/orangemn6/portfolio-site]. See ya next time!
