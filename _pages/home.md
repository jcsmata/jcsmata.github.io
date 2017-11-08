---
title: "Segmentation Fault"
layout: splash
permalink: /
author_profile: true
header: 
    overlay_color: "#000"
    overlay_filter: "0.5"
    overlay_image: /assets/images/header-image.jpg
excerpt: 'A website dedicated to software engineering and to the interesting things I find noteworthy to share.<br /> <br /> {::nomarkdown}<a class="twitter-follow-button" href="https://twitter.com/joaomata" data-size="large" data-show-screen-name="false" data-show-count="true"></a> 
<a class="github-button" href="https://github.com/jcsmata" data-style="mega" data-count-href="/jcsmata/followers" data-count-api="/users/jcsmata#followers" data-count-aria-label="# followers on GitHub" aria-label="Follow @jcsmata on GitHub">Follow @jcsmata</a>{:/nomarkdown}'
feature_row:
  - image_path: /assets/images/default.png
    url: /blog/extension-methods
    title: "Extension Methods in .NET"
    excerpt: "A post about extension methods and how to create them."
    btn_label: "Learn more"
  - image_path: /assets/images/default.png
    url: /blog/mysql-azure-ubuntu
    title: "Create Azure Ubuntu VM, install MySQL and remote access to it."
    excerpt: "Tutorial on how to create a Ubuntu VM on Azure, install MySQL and accessing it from your local computer."
    btn_label: "Learn more"
---

<script async defer src="https://buttons.github.io/buttons.js"></script>

<script>window.twttr = (function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0],
    t = window.twttr || {};
  if (d.getElementById(id)) return t;
  js = d.createElement(s);
  js.id = id;
  js.src = "https://platform.twitter.com/widgets.js";
  fjs.parentNode.insertBefore(js, fjs);

  t._e = [];
  t.ready = function(f) {
    t._e.push(f);
  };

  return t;
}(document, "script", "twitter-wjs"));</script>

{% include feature_row id="intro" type="center" %}

{% include feature_row %}

