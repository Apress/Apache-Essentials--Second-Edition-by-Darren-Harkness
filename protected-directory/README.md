If you are setting up your dev environments using a publicly-accessible subdomain, you are going to want to add in some protection. There’s a couple of reasons for this:

You don’t want search engines to index the content on your dev site, which would harm the rankings of your production site.

You don’t want any random person to be able to access the developer site, which might have issues or be vulnerable to attacks.

The best way to prevent against this is to protect the development subdomain behind a password. We covered this in Chapter 2, in the Using .htaccess files section. Of course, that gets annoying very quickly when you’re trying to build a site and need to access it frequently, on multiple devices.

The configuration below gives you the best of both worlds. The development subdomain will be accessible without a password to all devices on your local network. You’ll be able to access it from your laptop, desktop, or tablet, and never be bothered by an authentication prompt. People outside your local network — say a colleague or a client needing to do review — will be prompted for a password before being able to access the site. And if they don’t have that password, they’ll get an HTTP error.

Let’s assume that addresses in your network follow the 192.168.x.x address format.  That is, the IP address on the network for your laptop might be something like 192.168.0.131, whereas your iPad’s IP Address might be 192.168.0.132. You want to allow any device on your local network to access the website without anything getting in the way.

This configuration makes use of three core directives:
* Allow,
* Require (and its associated directives AuthType, AuthName and AuthUserFile), and
* Satisfy

Allow is used to specify a hostname, IP Address, or range or IP Addresses in a whitelist for access.

Require is used in tandem with authentication. This directive says that Apache needs a user to be valid before they can access the website.

The Satisfy directive, when set to ‘any’, sets an either/or scenario in Apache; if the user requesting the page is outside of the 192.168.0.x IP address range, they will be presented with a login prompt.  Otherwise, an error page will be shown informing the user they will have to authenticate on the Apache server.