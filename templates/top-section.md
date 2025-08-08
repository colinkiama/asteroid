{% extends "base.html" %}
{% block head %}
<title>{{ section.title }}</title>
{% endblock %}

{% block header %}
<header>
    <h1>{{ section.title }}</h1>
</header>
{% endblock %}

{% block main_body_content %}
<aside class="sidebar-drawer">
    <div class="container">
        {# Fill sidebar with navigation tree info #}
    </div>
</aside>

<main id="main-content">
    {{ section.content|safe }}
    {{ body_macros::table_of_contents_top_tree(page_context=section) }}

</main>

{% endblock %}

{% block table_of_contents %}
    {{ body_macros::table_of_contents(page_context=section) }}
{% endblock %}