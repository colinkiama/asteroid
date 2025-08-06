{% extends "base.html" %}
{% block head %}
<title>{{ section.title }}</title>
{% endblock %}

{% block header %}
<header>
    <h1>{{ section.title }}</h1>
    <p>{{ section.description }}</p>
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

    <ul>
        {% for sub in section.subsections %}
            <li>
                <a href="{{ sub.permalink }}">{{ sub.title }}</a>
                <ul>
                    {% for sub_page in sub.pages %}
                        <li>
                            <a href="{{ sub_page.permalink }}">{{ sub_page.title }}</a>
                        </li>
                    {% endfor %}
                </ul>
            </li>
        {% endfor %}
    </ul>

</main>

{% endblock %}

{% block table_of_contents %}
    {% if section.toc %}
        <ul>
        {% for h1 in section.toc %}
            <li>
                <a href="{{ h1.permalink | safe }}">{{ h1.title }}</a>
                {% if h1.children %}
                    <ul>
                        {% for h2 in h1.children %}
                            <li>
                                <a href="{{ h2.permalink | safe }}">{{ h2.title }}</a>
                            </li>
                        {% endfor %}
                    </ul>
                {% endif %}
            </li>
        {% endfor %}
        </ul>
    {% endif %}
{% endblock %}