---
title: Rails 4 Asset Pipeline
author: sivan1525
layout: post
permalink: /2015/01/rails-4-asset-pipeline/
dsq_thread_id:
  - 3499533300
categories:
  - Asset Pipeline
  - Rails4
  - Ruby
---
## Basic of Rails 4 Asset Pipeline

In Rails version 3.0 and earlier, all the assets were kept in public as:

  * **public/stylesheets**
  * **public/javascripts**
  * **public/images**

Whereas in latest rails there are 3 directories for static assets:

  * **app/assets &#8211; **used to server assets for current application
  * **lib/assets -** used to serve assets for the plugins written by developers working on the application
  * **vendor/assets -** used to serve assets for third party plugins

Each of these directories has 3 subdirectories for each asset class &#8211; **<span class="go">images/ javascripts/ stylesheets/</span>**

#### Manifest files:

Manifest file is used to combine the asset to form a single file.

The key lines in manifest files are actually CSS comments, but they are used by **Sprockets** to include the proper files:

<div class="code">
  <div class="highlight">
    <pre><span class="cm">/*</span>
<span class="cm"> .</span>
<span class="cm"> .</span>
<span class="cm"> .</span>
<span class="cm"> *= require_tree .</span>
<span class="cm"> *= require_self</span>
<span class="cm">*/</span>
</pre>
    
    <div class="code">
      <div class="highlight">
        <pre><span class="go">*= require_tree .</span>
</pre>
      </div>
    </div>
    
    <p>
      ensures that all CSS files in the <code>app/assets/stylesheets</code> directory (including the tree subdirectories) are included into the application CSS. The line
    </p>
    
    <div class="code">
      <div class="highlight">
        <pre><span class="go">*= require_self</span>
</pre>
      </div>
    </div>
    
    <p>
      specifies where in the loading sequence the CSS in <code>application.css</code> itself gets included.
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p>
      <span style="color: #ff0000;"><strong>Solution to images not showing in production:</strong></span>
    </p>
    
    <p>
      The problem here is because the CSS defined in stylesheets refer to the static path, whereas name is fingerprinted with a digest hash based on the contents of the file on production.
    </p>
    
    <p>
      The way to fix that is to <a href="http://sass-lang.com/">use SCSS</a> to create dynamic links to the assets; allowing your app to put the correct path to the images, etc.
    </p>
    
    <p>
      Like changing extension of css file to .scss and setting image path as:
    </p>
    
    <pre class="lang:css decode:true" title="stylesheet code">body {    

background: asset_url('background-image.png')

}</pre>
    
    <p>
      or
    </p>
    
    <p>
      extending css file to .erb and use:
    </p>
    
    <pre class=""><span class="class">.logo</span> {
  <span class="key">background-image</span>:<span class="function"><span class="delimiter">url(</span><span class="content">'&lt;%= asset_path("logo.png"</span><span class="delimiter">)</span></span> <span class="error">%</span>&gt; <span class="string"><span class="delimiter">'</span><span class="content">)</span><span class="delimiter">;</span></span>
}</pre>
    
    <p>
      and
    </p>
    
    <p>
      for js file extend file name to .erb and use :
    </p>
    
    <pre class="">&lt;%= asset_path('logo.png') %&gt;</pre>
  </div>
  
  <div class="highlight">
  </div>
</div>

<div class="pvc_clear">
</div>

<p id="pvc_stats_80" class="pvc_stats " element-id="80">
  <img src="https://railsnuggets.com/wp-content/plugins/page-views-count/ajax-loader.gif" border=0 />
</p>

<div class="pvc_clear">
</div>