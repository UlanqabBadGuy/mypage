---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: 首页
---

# 欢迎来到我的笔记本

这里是我的个人笔记网站，用于记录和分享学习笔记、技术文档和个人思考。

## 最新笔记

<div class="notes-preview">
  {% for note in site.notes limit:5 %}
    <article class="note-preview">
      <h2>
        <a href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
      </h2>
      <div class="note-meta">
        <time datetime="{{ note.date | date_to_xmlschema }}">
          {{ note.date | date: "%Y-%m-%d" }}
        </time>
      </div>
      {% if note.excerpt %}
      <div class="note-excerpt">
        {{ note.excerpt }}
      </div>
      {% endif %}
    </article>
  {% endfor %}
</div>

<div class="view-all">
  <a href="{{ site.baseurl }}/notes" class="button">查看所有笔记</a>
</div>

<style>
.notes-preview {
  margin: 2rem 0;
}

.note-preview {
  margin-bottom: 2rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #eee;
}

.note-preview h2 {
  margin-bottom: 0.5rem;
}

.note-preview h2 a {
  color: #333;
  text-decoration: none;
}

.note-preview h2 a:hover {
  color: #0366d6;
}

.note-meta {
  color: #666;
  font-size: 0.9rem;
  margin-bottom: 1rem;
}

.note-excerpt {
  color: #666;
  font-size: 1rem;
  line-height: 1.6;
}

.view-all {
  text-align: center;
  margin: 2rem 0;
}

.button {
  display: inline-block;
  padding: 0.8rem 1.6rem;
  background-color: #0366d6;
  color: white;
  text-decoration: none;
  border-radius: 4px;
  transition: background-color 0.2s;
}

.button:hover {
  background-color: #0256b9;
}
</style>
