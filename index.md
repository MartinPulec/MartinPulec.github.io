<link rel="alternate" type="application/atom+xml" title="{{ site.title }}" href="/feed.xml">

{% for post in site.posts %}
## {{ post.title }}
### {{ post.date | date_to_string }}
{{ post.content }}
{% endfor %}

<a class="btn btn-rss" href="/feed.xml" target="_blank">RSS</a>

