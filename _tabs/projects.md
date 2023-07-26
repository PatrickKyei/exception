---
layout: page
title: Projects
icon: fas fa-briefcase
order: 5
# The Archives of projects posts.
---

{% include lang.html %}

{% assign df_strftime_m = site.data.locales[lang].df.archives.strftime | default: '/ %m' %}
{% assign df_dayjs_m = site.data.locales[lang].df.archives.dayjs | default: '/ MM' %}

<div id="archives" class="pl-xl-3">

{% for post in site.posts %}
  {% if post.categories contains 'Projects' or post.tags contains 'projects' %}
    {% capture cur_year %}{{ post.date | date: "%Y" }}{% endcapture %}

    {% if cur_year != last_year %}
      {% unless forloop.first %} {% endunless %}
      <div class="year lead">{{ cur_year }}</div>
      <ul class="list-unstyled">
      {% assign last_year = cur_year %}
    {% endif %}

    <li>
    {% assign ts = post.date | date: '%s' %}
      <span class="date day" data-ts="{{ ts }}" data-df="DD">{{ post.date | date: "%d" }}</span>
      <span class="date month small text-muted ms-1" data-ts="{{ ts }}" data-df="{{ df_dayjs_m }}">
        {{ post.date | date: df_strftime_m }}
      </span>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>

    {% if forloop.last %}</ul>{% endif %}
  {% endif %}
{% endfor %}

<div id="fb-root"></div>

    <!-- Your Chat Plugin code -->
    <div id="fb-customer-chat" class="fb-customerchat">
    </div>

    <script>
      var chatbox = document.getElementById('fb-customer-chat');
      chatbox.setAttribute("page_id", "105512498005912");
      chatbox.setAttribute("attribution", "biz_inbox");
    </script>

    <!-- Your SDK code -->
    <script>
      window.fbAsyncInit = function() {
        FB.init({
          xfbml            : true,
          version          : 'v17.0'
        });
      };

      (function(d, s, id) {
        var js, fjs = d.getElementsByTagName(s)[0];
        if (d.getElementById(id)) return;
        js = d.createElement(s); js.id = id;
        js.src = 'https://connect.facebook.net/en_US/sdk/xfbml.customerchat.js';
        fjs.parentNode.insertBefore(js, fjs);
      }(document, 'script', 'facebook-jssdk'));
    </script>
