---
title: Test Messenger With YAML Deploy
date: 2023-07-25 6:40:00 +00
categories: [Technical, Messenger]
tags: [messenger, chat, technical]   # TAG names should always be lowercase
---
{% raw %}
# Messenger Chat Plugin Code
div#fb-root

# Your Chat Plugin code
div#fb-customer-chat.fb-customerchat

script.
  var chatbox = document.getElementById('fb-customer-chat');
  chatbox.setAttribute("page_id", "105512498005912");
  chatbox.setAttribute("attribution", "biz_inbox");

# Your SDK code
script.
  window.fbAsyncInit = function() {
    FB.init({
      xfbml: true,
      version: 'v17.0'
    });
  };

  (function(d, s, id) {
    var js, fjs = d.getElementsByTagName(s)[0];
    if (d.getElementById(id)) return;
    js = d.createElement(s); js.id = id;
    js.src = 'https://connect.facebook.net/en_US/sdk/xfbml.customerchat.js';
    fjs.parentNode.insertBefore(js, fjs);
  }(document, 'script', 'facebook-jssdk'));

  {% endraw %}
