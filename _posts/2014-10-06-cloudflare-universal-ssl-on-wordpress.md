---
author: Mathew Estrada
slug: cloudflare-universal-ssl-wordpress
title: CloudFlare Universal SSL on WordPress
categories:
- Tutorial
images:  /assets/2014-10-06-cloudflare-universal-ssl-on-wordpress/
---

| ![CloudFlare Logo]({{page.images}}cloudflare-blog.jpg) | ![CloudFlare SSL]({{page.images}}cloudflare-illustration-universal-ssl-1-.png) |
| ---------------------------------------- | ---------------------------------------- |
|                                          |                                          |

You may have heard. CloudFlare recently announced free SSL for all websites on its free plan. This is exciting and a fantastic move in the right direction to defend against crazy government mass surveillance and snopping. Basically, anybody using the CloudFlare free plan will automatically have their domain added to an SSL certificate, enabling verified https:// for the website.

It is important to note that this “Flexible SSL” method will only encrypt traffic from the visitor to the CloudFlare CDN. All data transmitted from the web server to CloudFlare (and visa versa) will be insecure. This is okay for personal or websites with no critical information being transmitted, but not for websites wishing to secure personal information (e.g. eCommerce).

If you run a WordPress blog, enable development mode in CloudFlare web panel (to disable caching) and then install the [WordPress HTTPS](https://wordpress.org/plugins/wordpress-https/) and optionally the [HTTPS Insecure Content Fixer](https://wordpress.org/plugins/ssl-insecure-content-fixer/) (it may help fix anything broken) plugins.

I still had some issues with loading of insecure content after installing these plugins. One extra thing I had to do was modify my **wp-config.php** and add this above the **require_once**. This is because we are now behind a reverse proxy.

```
if (isset($_SERVER['HTTP_X_FORWARDED_PROTO']) && $_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https')
 $_SERVER['HTTPS']='on';
```

To redirect all traffic from http:// to https://, put this in your .htaccess:

```
RewriteCond %{HTTP:CF-Visitor} '"scheme":"http"'
RewriteRule ^(.*)$ https://YOURDOMAIN.com$1 [L]
```

 

You’ll also want to install the [CloudFlare](https://wordpress.org/plugins/cloudflare/) plugin so that IP addresses resolving to your server will be the true visitor as opposed to the CloudFlare reverse proxy.
There are non-plugin alternatives for this: [https://support.cloudflare.com/hc/en-us/sections/200038166-How-do-I-restore-original-visitor-IP-to-my-server-logs-](https://support.cloudflare.com/hc/en-us/sections/200038166-How-do-I-restore-original-visitor-IP-to-my-server-logs-)

You should now be all set! I had to disable the [WP User Avatar](https://wordpress.org/plugins/wp-user-avatar/) plugin which let me use my own uploaded avatar. It was doing something funky and invalidating a callback URL and that was breaking SSL and returning an insecure non-HTTPS warning on some pages.

 

![How CF SSL Works]({{page.images}}ssl.png)