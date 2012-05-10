Settings &mdash; Transmogrify v0.1beta2 documentation
# Settings #
## TRANSMOGRIFY_SECRET ##
<p>This is any string that is shared between the various servers involved. It is used to create the SHA1 hash. The SHA1 hash is simply used to prevent external sites from requesting arbitrary image alterations.</p>
<p>Default: &quot;&quot;</p>

## TRANSMOGRIFY_DEBUG ##
<p>This turns on debug mode, which returns more descriptive error messages and stack traces.</p>
<p>Default: False</p>

## TRANSMOGRIFY_BASE_PATH ##
<p>This is the root from where the images are located. If TRANSMOGRIFY_BASE_PATH is /home/media/, a request for file /images/spanish_inquisition.png is looked for at /home/media/images/spanish_inquisition.png. The request&#8217;s path can be altered with TRANSMOGRIFY_PATH_ALIASES.</p>
<p>Default: /home/media/</p>

## TRANSMOGRIFY_PATH_ALIASES ##
<p>Typically the location of the original file to modify is derived from:</p>
TRANSMOGRIFY_BASE_PATH + requested_url
<p>Sometimes this isn&#8217;t very useful, as the actual paths of the files don&#8217;t make for good URLs. TRANSMOGRIFY_PATH_ALIASES allows you to set regular expressions to alter incoming URLs.</p>
<p>TRANSMOGRIFY_PATH_ALIASES is a dictionary of 
	{'&lt;url_regex&gt;':</span> <span class="pre">'&lt;sub_regex&gt;'}
Each request is matched against the keys. The first match is substituted using that key&#8217;s value. For example if your images were stored in /home/www/assets/images/, but the URL was /media/images/, you would set:</p>
TRANSMOGRIFY_BASE_PATH = &quot;/home/www&quot;
TRANSMOGRIFY_PATH_ALIASES = {&#39;/media/&#39;:&#39;/assets/&#39;}
<p>so requests for /media/images/sample.jpg converts into /assets/images/sample.jpg and when added to /home/www you get the file.</p>
<p>Default: {}</p>

## TRANSMOGRIFY_USE_VHOSTS ##
<p>Allows for the use of simple lighttpd vhosts. This hasn&#8217;t been fully tested yet.</p>
<p>Default: False</p>

## TRANSMOGRIFY_VHOST_DOC_BASE ##
<p>Used with TRANSMOGRIFY_USE_VHOSTS to locate the original document.</p>
<p>Default: &quot;&quot;</p>

## TRANSMOGRIFY_NO_IMG_URL ##
<p>Allows for a generic image to return if the original file isn&#8217;t found.</p>
<p>Default: &quot;&quot;</p>