ED-Image-Resizer---EE2-Add-On
=============================

Resizes images within Expression Engine templates and caches the file. This is a fork of the original plugin at http://devot-ee.com/add-ons/ed-imageresizer. It is more portable because it sets the cache path using $_SERVER['DOCUMENT_ROOT'] instead of having to hard-code the path in the plugin. It also provides an absolute path to the image using EE's config('site_url') variable. 

ED Image resizer for ExpressionEngine 2.x

Resize images on the fly

Installation

Copy pi.ed_imageresizer.php to @system/expressionengine/third_party/ed_imageresizer/
Change cache folder path variable to your config at @system/expressionengine/config/config.php:

$cache_path = "cache/"; // with a trailing slash

Usage

Parameters

* @image@ (string) _required_ : the file to resize
* @maxWidth@ (integer) : maximum width of the resized image
* @maxHeight@ (integer) : maximum height of the resized image
* @forceWidth@ (boolean "yes" or "no", default "no") : will force the width, even if the original's width is less
* @forceHeight@ (boolean "yes" or "no", default "no") : will force the height, even if the original's height is less
* @cropratio@ (string format "integer:integer") : crops the image to the defined ratio
* @cropstart@ (string format "tl" for top left) : where to start the crop using two letter codes (tl, tc, tr, cl, cc, cr, bl, bc, br) defaults to 'cc'
* @default@ (string) : a backup image to use if the @image@ is not found
* @alt@ (string) : an alt tag for the image
* @class@ (string) : a class for the image tag
* @id@ (string) : an ID for the image tag
* @title@ (string) : a title for the image tag
* @href_only@ (boolean "yes" or "no", default "no") : if yes, will return only the href, not the image tag
* @debug@ (boolean "yes" or "no", default "no") : will optionally output an error message if one is encountered, otherwise will fail silently
* @grayscale@ (boolean "yes" or "no", default "no") : grayscales the resized image

Usage example

{exp:ed_imageresizer
    image="{my_image_field}"
    default="/images/site/default_image.png"
    maxWidth="100"
    cropratio="100:120"
    class="my_class"
    alt="Image description"
    grayscale="yes"
    }

Would then output the following:

<img src="http://mysite.com/cache/resized_image.jpg" width="100" height="120" alt="Image description" />