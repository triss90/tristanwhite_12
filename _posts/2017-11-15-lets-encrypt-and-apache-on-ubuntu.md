---
layout: post
title: "Let's Encrypt and Apache on Ubuntu"
date: 2017-11-15 13:11:57 +0100
author: "Tristan White"
tags: Server
---



## Step 1 — Install the Let's Encrypt Client

To use Let's Encrypt we need to install some software on our server. The official client is calle Certbot.

**First, add the repository:**

{% highlight console %}
sudo add-apt-repository ppa:certbot/certbot
{% endhighlight %}

Press ``Enter`` and then update the package list to get the new repository's package information:

{% highlight console %}
sudo apt-get update
{% endhighlight %}

Install Certbot from the new repository with apt-get:

{% highlight console %}
sudo apt-get install python-certbot-apache
{% endhighlight %}

Done! The certbot Let's Encrypt client is now ready to use.

<br>
## Step 2 — Set Up the SSL Certificate

Generating an SSL certificate using Certbot is very straightforward. Simply run the certbot command like so:

{% highlight console %}
sudo certbot --apache -d example.com
{% endhighlight %}

You can install a single certificate that is valid for multiple domains and subdomains like so:

{% highlight console %}
sudo certbot --apache -d example.com -d www.example.com
{% endhighlight %}

If you have multiple virtual hosts, you should run certbot once for each to generate a new certificate for each.

After the dependencies are installed you will be presented with a guide to customize your certificate options, such as recoveryemail, forcing HTTPS and so on.

Once the installtion has completed you can find you certificate files in ``/etc/letsencrypt/live.``

<br>
## Step 3 — Verifying Certbot Auto-Renewal
The certificate only lasts 90 days. However the certbot package runs twice a day to make sure to make sure the certificates stay renewed.

To test the renewal process, you can do a dry run with certbot:

{% highlight console %}
sudo certbot renew --dry-run
{% endhighlight %}
