---
article_html: "<h2 id=\"floatterm\">FloatTerm</h2>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;&lt;leader&gt;&lt;leader&gt;w&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;FloatermNew waylonwalker&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n<span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">g</span><span class=\"p\">[</span><span class=\"s1\">&#39;floaterm_opener&#39;</span><span
  class=\"p\">]</span> <span class=\"o\">=</span> <span class=\"s1\">&#39;vsplit&#39;</span>\n<span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;gee&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;FloatermNew lf&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<script>\ndocument.onkeyup = function
  (e) {\n    if (e.key === 'j') {\n        document.querySelectorAll('a.next')[0].click()\n
  \   }\n    if (e.key === 'k') {\n        document.querySelectorAll('a.prev')[0].click()\n
  \   }\n}\n</script>\n<div class='prevnext'>\n\n    <style type='text/css'>\n\n    :root
  {\n      --prevnext-color-text: #eefbfe;\n      --prevnext-color-angle: #e1bd00c9;\n
  \     --prevnext-subtitle-brightness: 3;\n    }\n    [data-theme=\"light\"] {\n
  \     --prevnext-color-text: #1f2022;\n      --prevnext-color-angle: #ffeb00;\n
  \     --prevnext-subtitle-brightness: 3;\n    }\n    [data-theme=\"dark\"] {\n      --prevnext-color-text:
  #eefbfe;\n      --prevnext-color-angle: #e1bd00c9;\n      --prevnext-subtitle-brightness:
  3;\n    }\n    .prevnext {\n      display: flex;\n      flex-direction: row;\n      justify-content:
  space-around;\n      align-items: flex-start;\n    }\n    .prevnext a {\n      display:
  flex;\n      align-items: center;\n      width: 100%;\n      text-decoration: none;\n
  \   }\n    a.next {\n      justify-content: flex-end;\n    }\n    .prevnext a:hover
  {\n      background: #00000006;\n    }\n    .prevnext-subtitle {\n      color: var(--prevnext-color-text);\n
  \     filter: brightness(var(--prevnext-subtitle-brightness));\n      font-size:
  .8rem;\n    }\n    .prevnext-title {\n      color: var(--prevnext-color-text);\n
  \     font-size: 1rem;\n    }\n    .prevnext-text {\n      max-width: 30vw;\n    }\n
  \   </style>\n\n    <a class='prev' href='/extending-vim/slide-16'>\n\n\n        <svg
  width=\"50px\" height=\"50px\" viewbox=\"0 0 24 24\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n
  \           <path d=\"M13.5 8.25L9.75 12L13.5 15.75\" stroke=\"var(--prevnext-color-angle)\"
  stroke-width=\"1.5\" stroke-linecap=\"round\" stroke-linejoin=\"round\"> </path>\n
  \       </svg>\n        <div class='prevnext-text'>\n            <p class='prevnext-subtitle'>prev</p>\n
  \           <p class='prevnext-title'>extending vim with shell commands | 16</p>\n
  \       </div>\n    </a>\n\n    <a class='next' href='/extending-vim/slide-0'>\n\n
  \       <div class='prevnext-text'>\n            <p class='prevnext-subtitle'>next</p>\n
  \           <p class='prevnext-title'>extending vim with shell commands | 0</p>\n
  \       </div>\n        <svg width=\"50px\" height=\"50px\" viewbox=\"0 0 24 24\"
  fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n            <path d=\"M10.5
  15.75L14.25 12L10.5 8.25\" stroke=\"var(--prevnext-color-angle)\" stroke-width=\"1.5\"
  stroke-linecap=\"round\" stroke-linejoin=\"round\"></path>\n        </svg>\n    </a>\n
  \ </div>"
cover: ''
date: 2022-11-12
datetime: 2022-11-12 00:00:00+00:00
description: ''
edit_link: https://github.com/edit/main/pages/extending-vim.md
html: "<h2 id=\"floatterm\">FloatTerm</h2>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;&lt;leader&gt;&lt;leader&gt;w&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;FloatermNew waylonwalker&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n<span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">g</span><span class=\"p\">[</span><span class=\"s1\">&#39;floaterm_opener&#39;</span><span
  class=\"p\">]</span> <span class=\"o\">=</span> <span class=\"s1\">&#39;vsplit&#39;</span>\n<span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;gee&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;FloatermNew lf&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<script>\ndocument.onkeyup = function
  (e) {\n    if (e.key === 'j') {\n        document.querySelectorAll('a.next')[0].click()\n
  \   }\n    if (e.key === 'k') {\n        document.querySelectorAll('a.prev')[0].click()\n
  \   }\n}\n</script>\n<div class='prevnext'>\n\n    <style type='text/css'>\n\n    :root
  {\n      --prevnext-color-text: #eefbfe;\n      --prevnext-color-angle: #e1bd00c9;\n
  \     --prevnext-subtitle-brightness: 3;\n    }\n    [data-theme=\"light\"] {\n
  \     --prevnext-color-text: #1f2022;\n      --prevnext-color-angle: #ffeb00;\n
  \     --prevnext-subtitle-brightness: 3;\n    }\n    [data-theme=\"dark\"] {\n      --prevnext-color-text:
  #eefbfe;\n      --prevnext-color-angle: #e1bd00c9;\n      --prevnext-subtitle-brightness:
  3;\n    }\n    .prevnext {\n      display: flex;\n      flex-direction: row;\n      justify-content:
  space-around;\n      align-items: flex-start;\n    }\n    .prevnext a {\n      display:
  flex;\n      align-items: center;\n      width: 100%;\n      text-decoration: none;\n
  \   }\n    a.next {\n      justify-content: flex-end;\n    }\n    .prevnext a:hover
  {\n      background: #00000006;\n    }\n    .prevnext-subtitle {\n      color: var(--prevnext-color-text);\n
  \     filter: brightness(var(--prevnext-subtitle-brightness));\n      font-size:
  .8rem;\n    }\n    .prevnext-title {\n      color: var(--prevnext-color-text);\n
  \     font-size: 1rem;\n    }\n    .prevnext-text {\n      max-width: 30vw;\n    }\n
  \   </style>\n\n    <a class='prev' href='/extending-vim/slide-16'>\n\n\n        <svg
  width=\"50px\" height=\"50px\" viewbox=\"0 0 24 24\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n
  \           <path d=\"M13.5 8.25L9.75 12L13.5 15.75\" stroke=\"var(--prevnext-color-angle)\"
  stroke-width=\"1.5\" stroke-linecap=\"round\" stroke-linejoin=\"round\"> </path>\n
  \       </svg>\n        <div class='prevnext-text'>\n            <p class='prevnext-subtitle'>prev</p>\n
  \           <p class='prevnext-title'>extending vim with shell commands | 16</p>\n
  \       </div>\n    </a>\n\n    <a class='next' href='/extending-vim/slide-0'>\n\n
  \       <div class='prevnext-text'>\n            <p class='prevnext-subtitle'>next</p>\n
  \           <p class='prevnext-title'>extending vim with shell commands | 0</p>\n
  \       </div>\n        <svg width=\"50px\" height=\"50px\" viewbox=\"0 0 24 24\"
  fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n            <path d=\"M10.5
  15.75L14.25 12L10.5 8.25\" stroke=\"var(--prevnext-color-angle)\" stroke-width=\"1.5\"
  stroke-linecap=\"round\" stroke-linejoin=\"round\"></path>\n        </svg>\n    </a>\n
  \ </div>"
jinja: false
long_description: ''
now: 2022-12-09 13:48:24.795918
path: pages/extending-vim.md
published: 'False'
slide: 17-extending vim with shell commands
slug: extending-vim/slide-17
status: draft
super_description: ''
tags:
- vim
templateKey: blog-post
title: extending vim with shell commands | 17
today: 2022-12-09
---

## FloatTerm

``` lua
vim.keymap.set('n', '<leader><leader>w', '<cmd>FloatermNew waylonwalker<cr>')
vim.g['floaterm_opener'] = 'vsplit'
vim.keymap.set('n', 'gee', '<cmd>FloatermNew lf<cr>')
```

<script>
document.onkeyup = function (e) {
    if (e.key === 'j') {
        document.querySelectorAll('a.next')[0].click()
    }
    if (e.key === 'k') {
        document.querySelectorAll('a.prev')[0].click()
    }
}
</script>
<div class='prevnext'>

    <style type='text/css'>

    :root {
      --prevnext-color-text: #eefbfe;
      --prevnext-color-angle: #e1bd00c9;
      --prevnext-subtitle-brightness: 3;
    }
    [data-theme="light"] {
      --prevnext-color-text: #1f2022;
      --prevnext-color-angle: #ffeb00;
      --prevnext-subtitle-brightness: 3;
    }
    [data-theme="dark"] {
      --prevnext-color-text: #eefbfe;
      --prevnext-color-angle: #e1bd00c9;
      --prevnext-subtitle-brightness: 3;
    }
    .prevnext {
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: flex-start;
    }
    .prevnext a {
      display: flex;
      align-items: center;
      width: 100%;
      text-decoration: none;
    }
    a.next {
      justify-content: flex-end;
    }
    .prevnext a:hover {
      background: #00000006;
    }
    .prevnext-subtitle {
      color: var(--prevnext-color-text);
      filter: brightness(var(--prevnext-subtitle-brightness));
      font-size: .8rem;
    }
    .prevnext-title {
      color: var(--prevnext-color-text);
      font-size: 1rem;
    }
    .prevnext-text {
      max-width: 30vw;
    }
    </style>
    
    <a class='prev' href='/extending-vim/slide-16'>
    

        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M13.5 8.25L9.75 12L13.5 15.75" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"> </path>
        </svg>
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>prev</p>
            <p class='prevnext-title'>extending vim with shell commands | 16</p>
        </div>
    </a>
    
    <a class='next' href='/extending-vim/slide-0'>
    
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>next</p>
            <p class='prevnext-title'>extending vim with shell commands | 0</p>
        </div>
        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M10.5 15.75L14.25 12L10.5 8.25" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
    </a>
  </div>