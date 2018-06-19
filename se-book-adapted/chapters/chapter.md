{% macro add_front_matter(topic) %}
title: "Text Book Chapter : {{ topic.heading }}"
footer: footer.md
{% endmacro %}

{% macro show_priority(level) %}{% set star = "<span class='glyphicon glyphicon-star' aria-hidden='true'></span>" %}{% set empty = "<span class='glyphicon glyphicon-star-empty' aria-hidden='true'></span>" %}{% set stars = {"1": star + empty + empty + empty, "2": star + star + empty + empty, "3": star + star + star + empty, "4": star + star + star + star} %}{{stars[level] }}{% endmacro %}

{% macro show_level_three(location, topic) %}
{% set level_location =  location + "/" + topic.name %}
{% set title =  "#### " + topic.heading %}
<panel type="seamless" header="{{ title }}" expanded>
  <button type="button" class="btn btn-default btn-sm" aria-label="Left Align">
  <md>%%{{ show_priority(topic.priority) |safe }}%%</md></button>
  <button type="button" class="btn btn-default btn-sm" aria-label="Left Align"><md>%%<include src="{{ level_location }}/text.md#outcomes" inline />%%</md></button><p/>
  <include src="{{ level_location }}/text.md#body" />
  <include src="{{ level_location }}/text.md#extras" />
</panel>
{% endmacro %}


{% macro show_level_two(location, topic) %}
{% set level_location =  location + "/" + topic.name %}
{% set level_is_empty =  (topic.name == "") %}
{% if not level_is_empty %}
  <panel type="seamless" expanded>
    <span slot="header" class="panel-title"><include src="{{ level_location }}/text.md#title"/></span>
{% endif %}
  {% for sub_topic in topic.level_three_topics %}
    {{show_level_three(level_location , sub_topic) }}
  {% endfor %}
{% if not level_is_empty %}
  </panel>
{% endif %}
{% endmacro %}


{% macro show_level_one(location, topic) %}
{% set level_location =  location + "/" + topic.name %}
{% set level_is_empty =  (topic.name == "") %}
{% if not level_is_empty %}
<panel type="seamless" expanded>
  <span slot="header" class="panel-title"><include src="{{ level_location }}/text.md#title" /></span>
{% endif %}
  {% for sub_topic in topic.level_two_topics %}
    {{show_level_two(level_location , sub_topic) }}
  {% endfor %}
{% if not level_is_empty %}
  </panel>
{% endif %}
{% endmacro %}


{% macro show_chapter(chapter) %}
<frontmatter>
title: {{ chapter.heading }}
</frontmatter>

{% set level_location =  "../../book/" + chapter.name %}
<link rel="stylesheet" href="{{baseUrl}}/book/css/textbook.css">

<div class="website-content">

<include src="../../common/header.md" />

%%**<include src="{{ level_location }}/../path.md" inline />**%%

<div id="title">
  <include src="{{ level_location }}/text.md#title" />
</div>

{% for topic in chapter.level_one_topics %}
  {{show_level_one(level_location, topic) }}
{% endfor %}

</div>
{% endmacro %}