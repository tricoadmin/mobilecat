### MobileCat ###
Developed at the Tri-College libraries, MobileCat provides a mobile-ready interface to III WebOPACs. It is written in PHP.

An example of this web application can be viewed at http://m.tripod.brynmawr.edu

Discuss this project at our new google group: http://groups.google.com/group/mobilecat

### Prerequisites ###

  * PHP version >= 5.1.6
    * servers running PHP 5.1.x must also install PECL json extension, included in standard releases after 5.2.
  * PECL HTTP: http://pecl.php.net/package/pecl_http (This can be installed via [PEAR](http://pear.php.net/))
  * Simple HTML DOM parser: http://simplehtmldom.sourceforge.net/
  * Smarty templates: http://www.smarty.net/

### Download ###
Download [MobileCat version 1.1](http://code.google.com/p/mobilecat/downloads/detail?name=mobilecat-1.1.tar.gz).

### Installation ###
This is the first release of this software to the general public. The following steps should be all that is required to get the software working with your WebOPAC. However, there may be differences in configuration that we did not foresee. Please help us make this software and documentation better if it needs tweaking to work with your WebOPAC installation.

  * Install all prerequisites listed above
  * Edit the template file **briefcit.html** in your WebOPAC installation and insert the following code (do **not** indent the code, as the WebOPAC requires data tags to start at the beginning of a line):

```
<span style="display: none" class="mobileinfo">
<span>
<!--{fieldspec:VbT}-->
</span>
<span>
<!--{fieldspec:Vbi020}-->
</span>
<span>
<!--{media}-->
</span>
<span>
<!--{mark}-->
</span>
<span>
<!--{year}-->
</span>
<span>
<!--{bibloc}-->
</span>
</span>
```

  * Extract the MobileCat source code to a location in the Apache document tree
  * Ensure that this location has **AllowOverride all** in the Apache configuration, so that MobileCat's .htaccess file can be processed
  * Ensure the **templates\_c/** directory is writable by the Apache user
  * Edit the file **SiteParse.php** and put in values for the following variables:
    * **$catalog\_url** - The URL of your WebOPAC
    * **$base\_url** - The URL that maps to the location where you've installed MobileCat
    * **$catalog\_name** - The name of your catalog
    * **$def\_scope** - The scope value you'd like MobileCat to search using. This can be found in the URL bar of your WebOPAC under the variable **searchscope**
    * **$email\_from** - The email address you'd like messages from mobilecat to be sent from
    * **$feedback\_email** - The email address to send to for messages from the feedback form
    * **$cover\_image\_type** - Currently this is either "syndetics" or "openlibrary". Syndetics requires a subscription, whereas Open Library can be used by anyone with no further configuration.
    * **$syndetics\_client** - If you choose to use Syndetics for cover images, enter your institution's client id
    * **$email\_subject\_prefix** - Messages from MobileCat will be sent with this text in the subject line
  * Go to your MobileCat URL and try it out

### Customization ###
  * Edit **static/mobile.css** to change the basic appearance/colors
  * Add an image at **static/apple-touch-icon.png** that will be used if your site is bookmarked on an iPhone
  * Change the image at **static/nocover.jpg** that is used when a cover image isn't found
  * The HTML files under **templates/** may also be modified to a certain extent
  * For backend customization, the file **SiteParse.php** can be modified. This class is a child class of **IIIParse.php**, so you can override any functionality of the system specific to your site.


### AJAX vs. non-AJAX ###
There are two versions of the mobile interface that can be presented. Devices using a Safari browser are presented with an AJAX-style dynamic interface. Other devices/browsers are presented with a non-AJAX version. You can force the usage of the Javascript (or non-JS) version by appending **forcejs=[0|1]** to the URL when browsing to the site. For example: http://m.tripod.brynmawr.edu/?forcejs=1