---
ID: 1694
post_title: How to Run Apps in Any Language
author: GreatSites
post_excerpt: ""
layout: post
permalink: >
  https://greatsites.io/posts/web-development/how-to-run-apps-in-any-language/
published: true
post_date: 2020-10-01 17:40:32
---
<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>How to Run Apps in Any Language</p><cite><a href="https://serverpilot.io/docs/how-to-run-apps-in-any-language/">https://serverpilot.io/docs/how-to-run-apps-in-any-language/</a></cite></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph {"style":{"color":{"background":"#f7eda4"}}} -->
<p class="has-background" style="background-color:#f7eda4"><strong>Careful! We can only provide support for PHP apps.</strong><br><br>Unless you're absolutely sure about what you're doing, you should stop now!</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Though not supported by ServerPilot, it is possible to run apps written in languages other than PHP on your server. These include</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>Node.js apps such as Ghost,</li><li>Python apps such as Django,</li><li>Ruby apps built with Rails, and</li><li>Go apps built with Revel.</li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2>Step One: Connect a New Server to ServerPilot</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>You should start with a new server rather than one you're using for PHP apps. This way, if you break your server while installing your non-PHP app, it won't affect your PHP apps.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Step Two: Create an App in ServerPilot</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Log in to ServerPilot and create a new app. You can select any PHP version for your app. It won't matter which PHP version you've selected as your app won't use PHP.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>If your app needs a MySQL database, create a database for your app through ServerPilot.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Step Three: Install Your Non-PHP App</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Follow the instructions for your app to install only the app without any additional web server.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>If the instructions you're following are telling you to install or in any way configure Nginx or Apache, do not follow them!</strong>&nbsp;Instead, look for instructions that show you only how to install the app itself.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>It is safe to install packages that aren't web servers, such as&nbsp;nodejs,&nbsp;npm,&nbsp;ruby,&nbsp;python,&nbsp;pip,&nbsp;java, or&nbsp;perl.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Step Four: Run Your App On Its Own Port</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Start your app so that it runs on any high-numbered port. Some apps use a specific port by default. For example, Ghost uses port 2368.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Step Five: Proxy Requests to Your App's Port</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p><a href="https://serverpilot.io/docs/getting-started-with-ssh-and-sftp/">SSH or SFTP</a>&nbsp;in to your server as the user the app belongs to and create the file&nbsp;apps/APPNAME/public/.htaccess&nbsp;with the following contents (replace 2368 with the port your app is running on):</p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">RewriteRule index.html http://localhost:2368/ [P]
RewriteRule (.*) http://localhost:2368/$1 [P]</pre>
<!-- /wp:preformatted -->

<!-- wp:heading -->
<h2>Adding Domains</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>You can now add a domain to your app through ServerPilot, point DNS for that domain to your server's IP address, and request your app using just the URL:</p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">http://YOUR_DOMAIN/</pre>
<!-- /wp:preformatted -->

<!-- wp:heading -->
<h2>Things to Remember</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Unlike PHP apps, most other apps do not start by default when your server is rebooted. You should follow the instructions provided by your non-PHP app to ensure that it starts by default when you reboot your server.</p>
<!-- /wp:paragraph -->