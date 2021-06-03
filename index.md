<link rel="alternate" type="application/atom+xml" title="{{ site.title }}" href="/feed.xml">
<link rel="shortcut icon" href="/favicon.ico" />

{% for post in site.posts %}
## [{{ post.title }}]({{ post.url }})
### {{ post.date | date_to_string }}
{{ post.excerpt }}
{% endfor %}

<a class="btn btn-rss" href="/feed.xml" target="_blank">RSS</a>

