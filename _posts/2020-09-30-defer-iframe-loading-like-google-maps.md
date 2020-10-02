---
ID: 1674
post_title: 'Defer iframe loading &#8211; like Google Maps'
author: GreatSites
post_excerpt: ""
layout: post
permalink: >
  https://greatsites.io/posts/web-development/defer-iframe-loading-like-google-maps/
published: true
post_date: 2020-09-30 13:18:26
---
<!-- wp:core-embed/wordpress {"url":"https://www.annacantrell.com/how-to/how-to-defer-loading-iframe-content/","type":"wp-embed","providerNameSlug":"anna-cantrell","className":""} -->
<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-anna-cantrell"><div class="wp-block-embed__wrapper">
https://www.annacantrell.com/how-to/how-to-defer-loading-iframe-content/
</div><figcaption>Because you know your boss is going to be mad about that Google Page Speed Insights score.</figcaption></figure>
<!-- /wp:core-embed/wordpress -->

<!-- wp:heading -->
<h2>Here’s how to do it!</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>1. Move your iframe src from&nbsp;<code>src</code>&nbsp;to&nbsp;<code>data-src</code></p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>&lt;iframe src="" data-src="https://www.youtube.com/embed/JdyDz6quE18">&lt;/iframe></code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>HTMLCOPY</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>2. Add this script in your javascript file or in a &lt;script&gt; tag at the bottom of your page.</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>function deferIframe() {
  var iframeElem = document.getElementsByTagName('iframe');
  for ( var i = 0; i &lt; iframeElem.length; i++ ) {
    if(iframeElem&#91;i].getAttribute('data-src')) {
      iframeElem&#91;i].setAttribute('src',iframeElem&#91;i].getAttribute('data-src'));
    } 
  } 
}
window.onload = deferIframe;</code></pre>
<!-- /wp:code -->