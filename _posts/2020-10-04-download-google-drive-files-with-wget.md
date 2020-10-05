---
ID: 1735
post_title: DOWNLOAD GOOGLE DRIVE FILES WITH WGET
author: GreatSites
post_excerpt: ""
layout: post
permalink: >
  https://greatsites.io/posts/web-development/download-google-drive-files-with-wget/
published: true
post_date: 2020-10-04 20:10:48
---
<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>DOWNLOAD GOOGLE DRIVE FILES WITH WGET OR CURL</p><cite>https://www.matthuisman.nz/2019/01/download-google-drive-files-wget-curl.html</cite></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph -->
<p><strong>Note: Make sure the file has been shared 'via link' as the script does not authenticate you.</strong></p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Small File&nbsp;(less than 100MB)</h2>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>cd ~

export fileid=1yXsJq7TTMgUVXbOnCalyupESFN-tm2nc
export filename=matthuisman.jpg

## WGET ##
wget -O $filename 'https://docs.google.com/uc?export=download&amp;id='$fileid

## CURL ##
curl -L -o $filename 'https://docs.google.com/uc?export=download&amp;id='$fileid</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>Large File (more than 100MB)</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>cd ~

export fileid=1sNhrr2u6n48vb5xuOe8P9pTayojQoOc_
export filename=combian.rar

## WGET ##
wget --save-cookies cookies.txt 'https://docs.google.com/uc?export=download&amp;id='$fileid -O- \
     | sed -rn 's/.*confirm=(&#91;0-9A-Za-z_]+).*/\1/p' > confirm.txt

wget --load-cookies cookies.txt -O $filename \
     'https://docs.google.com/uc?export=download&amp;id='$fileid'&amp;confirm='$(&lt;confirm.txt)

## CURL ##
curl -L -c cookies.txt 'https://docs.google.com/uc?export=download&amp;id='$fileid \
     | sed -rn 's/.*confirm=(&#91;0-9A-Za-z_]+).*/\1/p' > confirm.txt

curl -L -b cookies.txt -o $filename \
     'https://docs.google.com/uc?export=download&amp;id='$fileid'&amp;confirm='$(&lt;confirm.txt)

rm -f confirm.txt cookies.txt</code></pre>
<!-- /wp:code -->