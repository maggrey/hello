```html

<html>
<head>
<title>Rails Hello World</title>
</head>
<body>
<h1>Rails Hello World</h1>

<p>
You can implement this (and all other example applications) on your AWS server or on your own computer.
</p>
<p>
Your own computer would need rvm, ruby, and rails installed, but does not need Apache.  To install on your own computer, follow steps 2-4 of the "Server and Development Machine Setup" instructions in the <a href="http://www.ecst.csuchico.edu/~tyson/classes/465.f14/aws_server_setup.html">Server Setup instructions</a>.
</p>



<hr>
<h3>Step 1: Create "empty" rails application</h3>
<p>
Create directory for your rails applications.  
</p>
<blockquote>
$ cd ~/rails
</blockquote>
<p>
Use the rails "new" command to create a new application called "hello"
</p>
<blockquote>
$ rails new hello<br>
$ cd hello<br>
</blockquote>
<p>
this create lots of files in the directory ./hello (good thing you wrote rfind)
</p>
<p>
as a beginner, you will be working with a small subset of these files
</p>
<ul>
<li>db -- this is where the database will live</li>
<li>config -- this is where configuration files live</li>
<li>app -- this is where the application lives</li>
<li>app/assets -- this is where .css, javascript, and other assets (files) live</li>
</ul>
<p>
The directories where most of your work will go:
</p>

<ul>
<li>app/controllers</li>
<li>app/models</li>
<li>app/views</li>
</ul>
<br>
<hr>
<h3>Step 2: run the application in development mode </h3>
<blockquote>
$ rails server<br>
-or-<br>
$ rails s<br>
</blockquote>
<p>
The "rails" utility does a lot of different tasks.  First we used it for creating a new rails applications.  Now we are using it to run a development server.
</p>
<p>
When run in development mode, a specialized http server (WEBrick) is used.  It hosts the rails application in the current directory on port 3000 (Apache does not need to be installed).
</p>
<p>
If you are developing on a remote server (such as your AWS server)
navigate to port 3000 on the hosting machine
</p>
<blockquote>
e.g:  http://54.69.30.218:3000/
</blockquote>
<p>
If you are developing on your local computer, navigate to: 
</p>
<blockquote>
http://localhost:3000
</blockquote>
<p>
by default rails is showing us the "you have not done anything yet page"
</p>
<hr>
<h3>Step 3: Add a new default landing page</h3>
<p>
We can add a new default by creating the file hello/public/index.html
</p>
<p>
&lt;!DOCTYPE html&gt;<br/>&lt;html&gt;<br/>&lt;body&gt;<br/>&lt;h1&gt;Rails hello application public/index.html&lt;/h1&gt;<br/>&lt;/body&gt;<br/>&lt;/html&gt;
</p>
<p>
reload the page (in your browser)
</p>
<p>
This isn't very interesting. Apache will serve an html file, but at least we know rails is running.
</p>
<p>
next we will create a rails view
</p>
<p>
NOTE: from here on, "hello" will be used for ~/rails/hello
</p>
<blockquote>
$ rm hello/public/index.html   # so rails won't default there anymore
</blockquote>
<hr>
<h3>Step 4: Create a rails "home" view</h3>
<p>
make a directory for the "home" (default) view
</p>
<blockquote>
$ cd hello/app/views<br>
$ mkdir home<br>
$ cd home<br>
</blockquote>
<p>
your current directory should be hello/app/views/home
</p>
<p>
add the following to the new file index.html.erb
</p>
<blockquote>
$ vim index.html.erb
</blockquote>

<p>
&lt;h1&gt;Hello Utility -- app/views/home/index.html.erb&lt;/h1&gt;
</p>
<hr>
<h3>Step 5: Create a route</h3>
<p>
Now we need to tell rails that when the user navigates to this
application it should show this page
</p>
<p>
this requires two things: a route and a controller
</p>
<p>
add the following to hello/config/routes.rb (add it inside the .do loop)
</p>
<blockquote>
$ vim hello/app/config/routes.rb
</blockquote>
<p>
  root "home#index"
</p>
<p>

we are telling rails that when someone asks for the "root" they should be directed to the index operation of the home controller
</p>
<p>
You can see all the routes for a rail application using the "rake" utility

</p>
<blockquote>
$ rake routes
</blockquote>

<p>
NOTE: we could have called this route and controller anything we wanted.  But "home" is the conventional name, and rails is all about convention.
<p>

<hr>
<h3> Step 6: Create a home controller</h3>
add the following text to the new file home_controller.rb
</p>
<blockquote>
$ vim hello/app/controllers/home_controller.rb
</blockquote>
<p>
class HomeController < ApplicationController<br>
&nbsp;&nbsp;&nbsp;def index<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# don't need to do anything here (too simple of an application).  Usually will do work here.<br>
&nbsp;&nbsp;&nbsp;end<br>
end
</p>
<p>
reload the page
</p>
<hr> 
<h3>Step 7: Add come functionality to the simple home view created above</h3>
<p>
Add the following embedded ruby to index.html.erb
</p>
<blockquote>
$ vim hello/app/views/home/index.html.erb
</blockquote>
<blockquote>
<%= "Hello! the date is " + `date` %>
</blockquote>
<p>
reload the page
</p>
<p>
Code in &lt;%= &nbsp;&nbsp;%&gt;is executed by the ruby interpretor.  The results are placed in the .html file.
</p>
<p>
Code in &lt;% &nbsp;&nbsp;%&gt;is executed by the ruby interpretor.  The results are placed in the .html file.
</p>
<p>
Try adding some more ruby code to index.html.erb
</p>

<hr>
<h3>Review:</h3>
</p>
<ol>
<li>create new rails application:  $ rails new hello</li>
<li>create a home view (default view) index.html.erb</li>
<li>create a route from "root" to the new home view</li>
<li>create a home controller</li>
<li>gave the home controller some functionality by embedding ruby code</li>
</ol>
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

</body>
</html>
