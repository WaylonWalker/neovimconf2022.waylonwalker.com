---
article_html: "<p>Vimconf 2022</p>\n<h2 id=\"the-pitch\">The pitch</h2>\n<p>Extending
  vim does not need to be complicated and can be done using cli tools\nthat you might
  already be comfortable with.  Examples, setting up\ncodeformatters with autocmds,
  using lf/ranger as a tui file manager, generating\nnew files using a template framework
  like cookiecutter/copier/yeoman, using ag\nto populate your quickfix.</p>\n<h2 id=\"me\">Me</h2>\n<ul>\n<li>Husband</li>\n<li>Father
  of two</li>\n<li>Eater of spicy shit</li>\n</ul>\n<p><div class=\"highlight\"><pre><span></span><code><span
  class=\"p\">:</span><span class=\"nb\">term</span> pipx run waylonwalker\n</code></pre></div>\n<img
  alt='one chip challenge' src='/paqui.jpg' style='width:250px; float: right;position:absolute;right:500px;'/></p>\n<p>pipx
  run waylonwalker</p>\n<h2 id=\"plugins\">Plugins</h2>\n<p>Plugins are awesome, this
  talk will not focus on plugins, but will use them when it makes sense.</p>\n<div
  class=\"admonition note\">\n<p>A lot can be done with the command line</p>\n</div>\n<h2
  id=\"vimscript-lua\">vimscript / lua</h2>\n<p>lua is an amazing feature of neovim.
  \ Both let you extend neovim in amazing\nways with little effort, but there quickly
  becomes a limit where you need to\nlearn a lot more about it to do what you need.</p>\n<div
  class=\"admonition note\">\n<p>lua can be a deep rabbit hole</p>\n</div>\n<h2 id=\"why-a-cli\">why
  a cli</h2>\n<p>A cli is going to be slower than vimscript/lua in many cases, but
  its often\nsomething that you already know.  If you write any sort of code its very
  likely\nthat you can write a cli in that language that you are familiar with and
  get\nthe benefits of all your familiar tooling.</p>\n<ul>\n<li>familiarity</li>\n<li>low
  barrier to entry</li>\n<li>works good enough</li>\n<li>works cross editor</li>\n</ul>\n<div
  class=\"admonition note\">\n<p>Start with something you are comfortable in</p>\n</div>\n<h2
  id=\"run-a-command\">run a command</h2>\n<p>Lets start with some cli's.</p>\n<div
  class=\"highlight\"><pre><span></span><code>vimconf!!&lt;esc&gt;!!figlet\n</code></pre></div>\n<p>run
  it</p>\n<div class=\"highlight\"><pre><span></span><code>       _                            __
  _ _ \n__   _(_)_ __ ___   ___ ___  _ __  / _| | |\n\\ \\ / / | &#39;_ ` _ \\ / __/
  _ \\| &#39;_ \\| |_| | |\n \\ V /| | | | | | | (_| (_) | | | |  _|_|_|\n  \\_/ |_|_|
  |_| |_|\\___\\___/|_| |_|_| (_|_)\n</code></pre></div>\n<h2 id=\"chat\">Chat</h2>\n<div
  class=\"highlight\"><pre><span></span><code>__        ___           _         _
  \                _     _                \n\\ \\      / / |__   __ _| |_   ___| |__
  \  ___  _   _| | __| | __      _____ \n \\ \\ /\\ / /| &#39;_ \\ / _` | __| / __|
  &#39;_ \\ / _ \\| | | | |/ _` | \\ \\ /\\ / / _ \\\n  \\ V  V / | | | | (_| | |_
  \ \\__ \\ | | | (_) | |_| | | (_| |  \\ V  V /  __/\n   \\_/\\_/  |_| |_|\\__,_|\\__|
  |___/_| |_|\\___/ \\__,_|_|\\__,_|   \\_/\\_/ \\___|\n\n\n _ __ _   _ _ __    \n|
  &#39;__| | | | &#39;_ \\   \n| |  | |_| | | | |_ \n|_|   \\__,_|_| |_(_)\n</code></pre></div>\n<div
  class=\"admonition danger\">\n<p>gimme a command</p>\n</div>\n<h2 id=\"so-whats-going-on-here\">So
  what's going on here</h2>\n<div class=\"admonition note\">\n<p>:.! works on standard
  unix pipes</p>\n</div>\n<p>-&gt; Your input is piped into the command as stdin.
  -&gt;</p>\n<div class=\"highlight\"><pre><span></span><code>echo &quot;vimconf&quot;
  | figlet\n</code></pre></div>\n<p>-&gt; Then replaced with what comes from stdout.
  -&gt;</p>\n<h2 id=\"a-lot-of-things-dont-work-on-stdinstdout\">A lot of things dont
  work on stdin/stdout</h2>\n<p>For instance many formatters work out of fileio, so
  I made a small, crappy,\nworks for me, shim, <code>genericformat</code>.</p>\n<div
  class=\"highlight\"><pre><span></span><code>pipx install genericformat\n</code></pre></div>\n<hr
  />\n<div class=\"admonition danger\">\n<p class=\"admonition-title\">Danger</p>\n<p>use
  it if it works for you, it works for me</p>\n</div>\n<h2 id=\"for-to-work-your-cli-must-accept-stdin\">for
  .! to work your cli must accept stdin</h2>\n<p>Many formatters don't support stdin
  so I made a little shim <code>genericformat</code> </p>\n<div class=\"highlight\"><pre><span></span><code>genericformat
  --help\n\nusage: genericformat <span class=\"o\">[</span>-h<span class=\"o\">]</span>
  --formatter FORMATTER <span class=\"o\">[</span>code<span class=\"o\">]</span>\n\nformat
  some code with a formatter\n\npositional arguments:\n  code                  the
  code to format\n\noptions:\n  -h, --help            show this <span class=\"nb\">help</span>
  message and <span class=\"nb\">exit</span>\n  --formatter FORMATTER\n                        path
  to the formatter to run\n</code></pre></div>\n<h2 id=\"format-some-code\">format
  some code</h2>\n<p>Format this one python statement.</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"nb\">print</span><span class=\"p\">(</span><span class=\"s1\">&#39;here&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<p>press !!genericformat --formatter
  black<cr></p>\n<div class=\"highlight\"><pre><span></span><code><span class=\"nb\">print</span><span
  class=\"p\">(</span><span class=\"s2\">&quot;here&quot;</span><span class=\"p\">)</span>\n</code></pre></div>\n<p>Now
  try a multiline statement.</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"k\">def</span> <span class=\"nf\">func</span><span class=\"p\">(</span><span
  class=\"n\">arg_one</span><span class=\"p\">,</span> <span class=\"n\">arg_two</span><span
  class=\"p\">,</span> <span class=\"n\">arg_three</span><span class=\"p\">,</span>
  <span class=\"n\">kwarg</span><span class=\"o\">=</span><span class=\"s1\">&#39;one&#39;</span><span
  class=\"p\">,):</span>\n   <span class=\"o\">...</span>\n</code></pre></div>\n<p>press
  Vj!genericformat --formatter black<cr></p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"k\">def</span> <span class=\"nf\">func</span><span class=\"p\">(</span>\n
  \   <span class=\"n\">arg_one</span><span class=\"p\">,</span>\n    <span class=\"n\">arg_two</span><span
  class=\"p\">,</span>\n    <span class=\"n\">arg_three</span><span class=\"p\">,</span>\n
  \   <span class=\"n\">kwarg</span><span class=\"o\">=</span><span class=\"s2\">&quot;one&quot;</span><span
  class=\"p\">,</span>\n<span class=\"p\">):</span>\n    <span class=\"o\">...</span>\n</code></pre></div>\n<p>Want
  Docstrings???</p>\n<p>press V6j!doq</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"k\">def</span> <span class=\"nf\">func</span><span class=\"p\">(</span>\n
  \   <span class=\"n\">arg_one</span><span class=\"p\">,</span>\n    <span class=\"n\">arg_two</span><span
  class=\"p\">,</span>\n    <span class=\"n\">arg_three</span><span class=\"p\">,</span>\n
  \   <span class=\"n\">kwarg</span><span class=\"o\">=</span><span class=\"s2\">&quot;one&quot;</span><span
  class=\"p\">,</span>\n<span class=\"p\">):</span>\n    <span class=\"sd\">&quot;&quot;&quot;func.</span>\n\n<span
  class=\"sd\">    :param arg_one:</span>\n<span class=\"sd\">    :param arg_two:</span>\n<span
  class=\"sd\">    :param arg_three:</span>\n<span class=\"sd\">    :param kwarg:</span>\n<span
  class=\"sd\">    &quot;&quot;&quot;</span>\n    <span class=\"o\">...</span>\n</code></pre></div>\n<h2
  id=\"using-bufwritepost-for-formatters\">using BufWritePost for formatters</h2>\n<p>My
  old config written in vimscript if you care.</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"k\">function</span><span class=\"p\">!</span> s:PyPreSave<span class=\"p\">()</span>\n
  \   Black\n<span class=\"k\">endfunction</span>\n\n<span class=\"k\">function</span><span
  class=\"p\">!</span> s:PyPostSave<span class=\"p\">()</span>\n    execute <span
  class=\"s2\">&quot;!tidy-imports --black --quiet --replace-star-imports --action
  REPLACE &quot;</span> . bufname<span class=\"p\">(</span><span class=\"s2\">&quot;%&quot;</span><span
  class=\"p\">)</span>\n    execute <span class=\"s2\">&quot;!isort &quot;</span>
  . bufname<span class=\"p\">(</span><span class=\"s2\">&quot;%&quot;</span><span
  class=\"p\">)</span>\n    execute <span class=\"s2\">&quot;!black &quot;</span>
  . bufname<span class=\"p\">(</span><span class=\"s2\">&quot;%&quot;</span><span
  class=\"p\">)</span>\n    execute <span class=\"s2\">&quot;e&quot;</span>\n<span
  class=\"k\">endfunction</span>\n\n<span class=\"p\">:</span>command<span class=\"p\">!</span>
  PyPreSave :<span class=\"k\">call</span> s:PyPreSave<span class=\"p\">()</span>\n<span
  class=\"p\">:</span>command<span class=\"p\">!</span> PyPostSave :<span class=\"k\">call</span>
  s:PyPostSave<span class=\"p\">()</span>\n\naugroup waylonwalker\n    autocmd<span
  class=\"p\">!</span>\n    autocmd bufwritepre *.<span class=\"k\">py</span> <span
  class=\"k\">silent</span><span class=\"p\">!</span> execute <span class=\"s1\">&#39;PyPreSave&#39;</span>\n
  \   autocmd bufwritepost *.<span class=\"k\">py</span> <span class=\"k\">silent</span><span
  class=\"p\">!</span> execute <span class=\"s1\">&#39;PyPostSave&#39;</span>\naugroup
  <span class=\"k\">end</span>\n</code></pre></div>\n<h2 id=\"lua-all-the-things\">Lua
  all the things</h2>\n<div class=\"admonition note\">\n<p>This is <strong>neovimconf</strong>
  after all</p>\n</div>\n<h2 id=\"using-bufwritepost-for-formatters_1\">using BufWritePost
  for formatters</h2>\n<p>My latest config written in <code>lua</code>.</p>\n<div
  class=\"highlight\"><pre><span></span><code><span class=\"kd\">local</span> <span
  class=\"n\">settings</span> <span class=\"o\">=</span> <span class=\"nb\">require</span><span
  class=\"s1\">&#39;waylonwalker.settings&#39;</span>\n\n<span class=\"n\">M</span><span
  class=\"p\">.</span><span class=\"n\">waylonwalker_augroup</span> <span class=\"o\">=</span>
  <span class=\"n\">augroup</span><span class=\"p\">(</span><span class=\"s1\">&#39;waylonwalker&#39;</span><span
  class=\"p\">,</span> <span class=\"p\">{</span> <span class=\"n\">clear</span> <span
  class=\"o\">=</span> <span class=\"kc\">true</span> <span class=\"p\">})</span>\n<span
  class=\"n\">M</span><span class=\"p\">.</span><span class=\"n\">format_python</span>
  <span class=\"o\">=</span> <span class=\"kr\">function</span><span class=\"p\">()</span>\n
  \   <span class=\"kr\">if</span> <span class=\"n\">settings</span><span class=\"p\">.</span><span
  class=\"n\">auto_format</span><span class=\"p\">.</span><span class=\"n\">python</span>
  <span class=\"kr\">then</span>\n        <span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">cmd</span><span class=\"p\">(</span><span class=\"s1\">&#39;silent execute
  &quot;%!tidy-imports --black --quiet --replace-star-imports --replace --add-missing
  --remove-unused &quot; . bufname(&quot;%&quot;)&#39;</span><span class=\"p\">)</span>\n
  \       <span class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">cmd</span><span
  class=\"p\">(</span><span class=\"s1\">&#39;silent execute &quot;%!isort &quot;
  . bufname(&quot;%&quot;)&#39;</span><span class=\"p\">)</span>\n        <span class=\"n\">vim</span><span
  class=\"p\">.</span><span class=\"n\">cmd</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;silent execute &quot;%!black &quot; . bufname(&quot;%&quot;)&#39;</span><span
  class=\"p\">)</span>\n    <span class=\"kr\">end</span>\n<span class=\"kr\">end</span>\n\n<span
  class=\"n\">autocmd</span><span class=\"p\">({</span> <span class=\"s2\">&quot;BufWritePost&quot;</span>
  <span class=\"p\">},</span> <span class=\"p\">{</span>\n    <span class=\"n\">group</span><span
  class=\"o\">=</span><span class=\"n\">M</span><span class=\"p\">.</span><span class=\"n\">waylonwalker_augroup</span><span
  class=\"p\">,</span>\n    <span class=\"n\">pattern</span> <span class=\"o\">=</span>
  <span class=\"p\">{</span> <span class=\"s2\">&quot;*.py&quot;</span> <span class=\"p\">},</span>\n
  \   <span class=\"n\">callback</span> <span class=\"o\">=</span> <span class=\"n\">M</span><span
  class=\"p\">.</span><span class=\"n\">format_python</span><span class=\"p\">,</span>\n<span
  class=\"p\">})</span>\n</code></pre></div>\n<h2 id=\"file-navigation\">File Navigation</h2>\n<p><em>rg</em></p>\n<p>List
  <strong>all</strong> your files</p>\n<div class=\"highlight\"><pre><span></span><code>rg
  --files\n</code></pre></div>\n<p>use <code>gf</code> to go to file under the cursor</p>\n<h3
  id=\"map-it\">map it</h3>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"nb\">nnoremap</span> <span class=\"p\">&lt;</span>leader<span class=\"p\">&gt;</span>
  <span class=\"k\">f</span> :<span class=\"k\">new</span><span class=\"p\">&lt;</span><span
  class=\"k\">cr</span><span class=\"p\">&gt;</span>:.<span class=\"p\">!</span>rg
  <span class=\"p\">--</span><span class=\"k\">files</span><span class=\"p\">&lt;</span><span
  class=\"k\">cr</span><span class=\"p\">&gt;</span>\n</code></pre></div>\n<div class=\"admonition
  note\">\n<p class=\"admonition-title\">Note</p>\n<p>I use and reccomend Telescope,
  but <code>gf</code> can work fantasic without any setup.</p>\n</div>\n<h2 id=\"file-navigation_1\">File
  Navigation</h2>\n<p><em>markata</em></p>\n<p>I built my own static site generator,
  one thing that it can do pretty well is\nnavigate through large sets of posts and
  list out their path.  I can pipe this right into </p>\n<div class=\"highlight\"><pre><span></span><code>markata
  list --map path --filter <span class=\"s1\">&#39;&quot;til&quot; in path&#39;</span>
  --fast --no-pager\n</code></pre></div>\n<h2 id=\"file-navigation_2\">File Navigation</h2>\n<div
  class=\"highlight\"><pre><span></span><code><span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">keymap</span><span class=\"p\">.</span><span class=\"n\">set</span><span
  class=\"p\">(</span><span class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span>
  <span class=\"s1\">&#39;geit&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;terminal
  markata list --map path --filter </span><span class=\"se\">\\&#39;</span><span class=\"s1\">&quot;til&quot;
  in path</span><span class=\"se\">\\&#39;</span><span class=\"s1\"> --fast --no-pager&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;geit&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;Telescope find_files find_command=markata,list,--map,path,--filter,date==today,--fast&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;&lt;leader&gt;ee&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;vertical terminal lf&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<h2 id=\"floatterm\">FloatTerm</h2>\n<div
  class=\"highlight\"><pre><span></span><code><span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">keymap</span><span class=\"p\">.</span><span class=\"n\">set</span><span
  class=\"p\">(</span><span class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span>
  <span class=\"s1\">&#39;&lt;leader&gt;&lt;leader&gt;w&#39;</span><span class=\"p\">,</span>
  <span class=\"s1\">&#39;&lt;cmd&gt;FloatermNew waylonwalker&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n<span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">g</span><span class=\"p\">[</span><span class=\"s1\">&#39;floaterm_opener&#39;</span><span
  class=\"p\">]</span> <span class=\"o\">=</span> <span class=\"s1\">&#39;vsplit&#39;</span>\n<span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;gee&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;FloatermNew lf&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<h2 id=\"vimgrep-over-hidden-files\">vimgrep
  over hidden files</h2>\n<p>I know all the files that I care to search for are called
  build.yml, and they\nare in a hidden directory.</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"p\">:</span>args `fd <span class=\"p\">-</span>H build.yml`\n<span class=\"p\">:</span><span
  class=\"k\">vimgrep</span> <span class=\"sr\">/upload docs/</span> ##\n</code></pre></div>\n<p>Once
  opened as a buffer by using args, and a handy fd command I can vimgrep\nover all
  the open buffers using <code>##</code></p>\n<blockquote>\n<p>Open buffers are represented
  by ##</p>\n</blockquote>\n<p>Now I can just <code>dap</code> and <code>:cnext</code>
  my way through the list of changes that I\nhave, and know that I hit every one of
  them when I am at the end of my list.\nAnd can double check this in about 10s by
  scrolling back through the quickfix\nlist.</p>\n<div class='prevnext'>\n\n    <style
  type='text/css'>\n\n    :root {\n      --prevnext-color-text: #eefbfe;\n      --prevnext-color-angle:
  #e1bd00c9;\n      --prevnext-subtitle-brightness: 3;\n    }\n    [data-theme=\"light\"]
  {\n      --prevnext-color-text: #1f2022;\n      --prevnext-color-angle: #ffeb00;\n
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
  \   </style>\n\n    <a class='prev' href='/extending-vim/slide-0'>\n\n\n        <svg
  width=\"50px\" height=\"50px\" viewbox=\"0 0 24 24\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n
  \           <path d=\"M13.5 8.25L9.75 12L13.5 15.75\" stroke=\"var(--prevnext-color-angle)\"
  stroke-width=\"1.5\" stroke-linecap=\"round\" stroke-linejoin=\"round\"> </path>\n
  \       </svg>\n        <div class='prevnext-text'>\n            <p class='prevnext-subtitle'>prev</p>\n
  \           <p class='prevnext-title'>extending vim with shell commands | 0</p>\n
  \       </div>\n    </a>\n\n    <a class='next' href='/'>\n\n        <div class='prevnext-text'>\n
  \           <p class='prevnext-subtitle'>next</p>\n            <p class='prevnext-title'>extending
  vim with shell commands</p>\n        </div>\n        <svg width=\"50px\" height=\"50px\"
  viewbox=\"0 0 24 24\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n            <path
  d=\"M10.5 15.75L14.25 12L10.5 8.25\" stroke=\"var(--prevnext-color-angle)\" stroke-width=\"1.5\"
  stroke-linecap=\"round\" stroke-linejoin=\"round\"></path>\n        </svg>\n    </a>\n
  \ </div>"
cover: ''
date: 2022-11-12
datetime: 2022-11-12 00:00:00+00:00
description: Vimconf 2022 Extending vim does not need to be complicated and can be
  done using cli tools Husband Father of two Eater of spicy shit pipx run waylonwalker
  Plugi
edit_link: https://github.com/edit/main/pages/extending-vim.md
html: "<p>Vimconf 2022</p>\n<h2 id=\"the-pitch\">The pitch</h2>\n<p>Extending vim
  does not need to be complicated and can be done using cli tools\nthat you might
  already be comfortable with.  Examples, setting up\ncodeformatters with autocmds,
  using lf/ranger as a tui file manager, generating\nnew files using a template framework
  like cookiecutter/copier/yeoman, using ag\nto populate your quickfix.</p>\n<h2 id=\"me\">Me</h2>\n<ul>\n<li>Husband</li>\n<li>Father
  of two</li>\n<li>Eater of spicy shit</li>\n</ul>\n<p><div class=\"highlight\"><pre><span></span><code><span
  class=\"p\">:</span><span class=\"nb\">term</span> pipx run waylonwalker\n</code></pre></div>\n<img
  alt='one chip challenge' src='/paqui.jpg' style='width:250px; float: right;position:absolute;right:500px;'/></p>\n<p>pipx
  run waylonwalker</p>\n<h2 id=\"plugins\">Plugins</h2>\n<p>Plugins are awesome, this
  talk will not focus on plugins, but will use them when it makes sense.</p>\n<div
  class=\"admonition note\">\n<p>A lot can be done with the command line</p>\n</div>\n<h2
  id=\"vimscript-lua\">vimscript / lua</h2>\n<p>lua is an amazing feature of neovim.
  \ Both let you extend neovim in amazing\nways with little effort, but there quickly
  becomes a limit where you need to\nlearn a lot more about it to do what you need.</p>\n<div
  class=\"admonition note\">\n<p>lua can be a deep rabbit hole</p>\n</div>\n<h2 id=\"why-a-cli\">why
  a cli</h2>\n<p>A cli is going to be slower than vimscript/lua in many cases, but
  its often\nsomething that you already know.  If you write any sort of code its very
  likely\nthat you can write a cli in that language that you are familiar with and
  get\nthe benefits of all your familiar tooling.</p>\n<ul>\n<li>familiarity</li>\n<li>low
  barrier to entry</li>\n<li>works good enough</li>\n<li>works cross editor</li>\n</ul>\n<div
  class=\"admonition note\">\n<p>Start with something you are comfortable in</p>\n</div>\n<h2
  id=\"run-a-command\">run a command</h2>\n<p>Lets start with some cli's.</p>\n<div
  class=\"highlight\"><pre><span></span><code>vimconf!!&lt;esc&gt;!!figlet\n</code></pre></div>\n<p>run
  it</p>\n<div class=\"highlight\"><pre><span></span><code>       _                            __
  _ _ \n__   _(_)_ __ ___   ___ ___  _ __  / _| | |\n\\ \\ / / | &#39;_ ` _ \\ / __/
  _ \\| &#39;_ \\| |_| | |\n \\ V /| | | | | | | (_| (_) | | | |  _|_|_|\n  \\_/ |_|_|
  |_| |_|\\___\\___/|_| |_|_| (_|_)\n</code></pre></div>\n<h2 id=\"chat\">Chat</h2>\n<div
  class=\"highlight\"><pre><span></span><code>__        ___           _         _
  \                _     _                \n\\ \\      / / |__   __ _| |_   ___| |__
  \  ___  _   _| | __| | __      _____ \n \\ \\ /\\ / /| &#39;_ \\ / _` | __| / __|
  &#39;_ \\ / _ \\| | | | |/ _` | \\ \\ /\\ / / _ \\\n  \\ V  V / | | | | (_| | |_
  \ \\__ \\ | | | (_) | |_| | | (_| |  \\ V  V /  __/\n   \\_/\\_/  |_| |_|\\__,_|\\__|
  |___/_| |_|\\___/ \\__,_|_|\\__,_|   \\_/\\_/ \\___|\n\n\n _ __ _   _ _ __    \n|
  &#39;__| | | | &#39;_ \\   \n| |  | |_| | | | |_ \n|_|   \\__,_|_| |_(_)\n</code></pre></div>\n<div
  class=\"admonition danger\">\n<p>gimme a command</p>\n</div>\n<h2 id=\"so-whats-going-on-here\">So
  what's going on here</h2>\n<div class=\"admonition note\">\n<p>:.! works on standard
  unix pipes</p>\n</div>\n<p>-&gt; Your input is piped into the command as stdin.
  -&gt;</p>\n<div class=\"highlight\"><pre><span></span><code>echo &quot;vimconf&quot;
  | figlet\n</code></pre></div>\n<p>-&gt; Then replaced with what comes from stdout.
  -&gt;</p>\n<h2 id=\"a-lot-of-things-dont-work-on-stdinstdout\">A lot of things dont
  work on stdin/stdout</h2>\n<p>For instance many formatters work out of fileio, so
  I made a small, crappy,\nworks for me, shim, <code>genericformat</code>.</p>\n<div
  class=\"highlight\"><pre><span></span><code>pipx install genericformat\n</code></pre></div>\n<hr
  />\n<div class=\"admonition danger\">\n<p class=\"admonition-title\">Danger</p>\n<p>use
  it if it works for you, it works for me</p>\n</div>\n<h2 id=\"for-to-work-your-cli-must-accept-stdin\">for
  .! to work your cli must accept stdin</h2>\n<p>Many formatters don't support stdin
  so I made a little shim <code>genericformat</code> </p>\n<div class=\"highlight\"><pre><span></span><code>genericformat
  --help\n\nusage: genericformat <span class=\"o\">[</span>-h<span class=\"o\">]</span>
  --formatter FORMATTER <span class=\"o\">[</span>code<span class=\"o\">]</span>\n\nformat
  some code with a formatter\n\npositional arguments:\n  code                  the
  code to format\n\noptions:\n  -h, --help            show this <span class=\"nb\">help</span>
  message and <span class=\"nb\">exit</span>\n  --formatter FORMATTER\n                        path
  to the formatter to run\n</code></pre></div>\n<h2 id=\"format-some-code\">format
  some code</h2>\n<p>Format this one python statement.</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"nb\">print</span><span class=\"p\">(</span><span class=\"s1\">&#39;here&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<p>press !!genericformat --formatter
  black<cr></p>\n<div class=\"highlight\"><pre><span></span><code><span class=\"nb\">print</span><span
  class=\"p\">(</span><span class=\"s2\">&quot;here&quot;</span><span class=\"p\">)</span>\n</code></pre></div>\n<p>Now
  try a multiline statement.</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"k\">def</span> <span class=\"nf\">func</span><span class=\"p\">(</span><span
  class=\"n\">arg_one</span><span class=\"p\">,</span> <span class=\"n\">arg_two</span><span
  class=\"p\">,</span> <span class=\"n\">arg_three</span><span class=\"p\">,</span>
  <span class=\"n\">kwarg</span><span class=\"o\">=</span><span class=\"s1\">&#39;one&#39;</span><span
  class=\"p\">,):</span>\n   <span class=\"o\">...</span>\n</code></pre></div>\n<p>press
  Vj!genericformat --formatter black<cr></p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"k\">def</span> <span class=\"nf\">func</span><span class=\"p\">(</span>\n
  \   <span class=\"n\">arg_one</span><span class=\"p\">,</span>\n    <span class=\"n\">arg_two</span><span
  class=\"p\">,</span>\n    <span class=\"n\">arg_three</span><span class=\"p\">,</span>\n
  \   <span class=\"n\">kwarg</span><span class=\"o\">=</span><span class=\"s2\">&quot;one&quot;</span><span
  class=\"p\">,</span>\n<span class=\"p\">):</span>\n    <span class=\"o\">...</span>\n</code></pre></div>\n<p>Want
  Docstrings???</p>\n<p>press V6j!doq</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"k\">def</span> <span class=\"nf\">func</span><span class=\"p\">(</span>\n
  \   <span class=\"n\">arg_one</span><span class=\"p\">,</span>\n    <span class=\"n\">arg_two</span><span
  class=\"p\">,</span>\n    <span class=\"n\">arg_three</span><span class=\"p\">,</span>\n
  \   <span class=\"n\">kwarg</span><span class=\"o\">=</span><span class=\"s2\">&quot;one&quot;</span><span
  class=\"p\">,</span>\n<span class=\"p\">):</span>\n    <span class=\"sd\">&quot;&quot;&quot;func.</span>\n\n<span
  class=\"sd\">    :param arg_one:</span>\n<span class=\"sd\">    :param arg_two:</span>\n<span
  class=\"sd\">    :param arg_three:</span>\n<span class=\"sd\">    :param kwarg:</span>\n<span
  class=\"sd\">    &quot;&quot;&quot;</span>\n    <span class=\"o\">...</span>\n</code></pre></div>\n<h2
  id=\"using-bufwritepost-for-formatters\">using BufWritePost for formatters</h2>\n<p>My
  old config written in vimscript if you care.</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"k\">function</span><span class=\"p\">!</span> s:PyPreSave<span class=\"p\">()</span>\n
  \   Black\n<span class=\"k\">endfunction</span>\n\n<span class=\"k\">function</span><span
  class=\"p\">!</span> s:PyPostSave<span class=\"p\">()</span>\n    execute <span
  class=\"s2\">&quot;!tidy-imports --black --quiet --replace-star-imports --action
  REPLACE &quot;</span> . bufname<span class=\"p\">(</span><span class=\"s2\">&quot;%&quot;</span><span
  class=\"p\">)</span>\n    execute <span class=\"s2\">&quot;!isort &quot;</span>
  . bufname<span class=\"p\">(</span><span class=\"s2\">&quot;%&quot;</span><span
  class=\"p\">)</span>\n    execute <span class=\"s2\">&quot;!black &quot;</span>
  . bufname<span class=\"p\">(</span><span class=\"s2\">&quot;%&quot;</span><span
  class=\"p\">)</span>\n    execute <span class=\"s2\">&quot;e&quot;</span>\n<span
  class=\"k\">endfunction</span>\n\n<span class=\"p\">:</span>command<span class=\"p\">!</span>
  PyPreSave :<span class=\"k\">call</span> s:PyPreSave<span class=\"p\">()</span>\n<span
  class=\"p\">:</span>command<span class=\"p\">!</span> PyPostSave :<span class=\"k\">call</span>
  s:PyPostSave<span class=\"p\">()</span>\n\naugroup waylonwalker\n    autocmd<span
  class=\"p\">!</span>\n    autocmd bufwritepre *.<span class=\"k\">py</span> <span
  class=\"k\">silent</span><span class=\"p\">!</span> execute <span class=\"s1\">&#39;PyPreSave&#39;</span>\n
  \   autocmd bufwritepost *.<span class=\"k\">py</span> <span class=\"k\">silent</span><span
  class=\"p\">!</span> execute <span class=\"s1\">&#39;PyPostSave&#39;</span>\naugroup
  <span class=\"k\">end</span>\n</code></pre></div>\n<h2 id=\"lua-all-the-things\">Lua
  all the things</h2>\n<div class=\"admonition note\">\n<p>This is <strong>neovimconf</strong>
  after all</p>\n</div>\n<h2 id=\"using-bufwritepost-for-formatters_1\">using BufWritePost
  for formatters</h2>\n<p>My latest config written in <code>lua</code>.</p>\n<div
  class=\"highlight\"><pre><span></span><code><span class=\"kd\">local</span> <span
  class=\"n\">settings</span> <span class=\"o\">=</span> <span class=\"nb\">require</span><span
  class=\"s1\">&#39;waylonwalker.settings&#39;</span>\n\n<span class=\"n\">M</span><span
  class=\"p\">.</span><span class=\"n\">waylonwalker_augroup</span> <span class=\"o\">=</span>
  <span class=\"n\">augroup</span><span class=\"p\">(</span><span class=\"s1\">&#39;waylonwalker&#39;</span><span
  class=\"p\">,</span> <span class=\"p\">{</span> <span class=\"n\">clear</span> <span
  class=\"o\">=</span> <span class=\"kc\">true</span> <span class=\"p\">})</span>\n<span
  class=\"n\">M</span><span class=\"p\">.</span><span class=\"n\">format_python</span>
  <span class=\"o\">=</span> <span class=\"kr\">function</span><span class=\"p\">()</span>\n
  \   <span class=\"kr\">if</span> <span class=\"n\">settings</span><span class=\"p\">.</span><span
  class=\"n\">auto_format</span><span class=\"p\">.</span><span class=\"n\">python</span>
  <span class=\"kr\">then</span>\n        <span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">cmd</span><span class=\"p\">(</span><span class=\"s1\">&#39;silent execute
  &quot;%!tidy-imports --black --quiet --replace-star-imports --replace --add-missing
  --remove-unused &quot; . bufname(&quot;%&quot;)&#39;</span><span class=\"p\">)</span>\n
  \       <span class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">cmd</span><span
  class=\"p\">(</span><span class=\"s1\">&#39;silent execute &quot;%!isort &quot;
  . bufname(&quot;%&quot;)&#39;</span><span class=\"p\">)</span>\n        <span class=\"n\">vim</span><span
  class=\"p\">.</span><span class=\"n\">cmd</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;silent execute &quot;%!black &quot; . bufname(&quot;%&quot;)&#39;</span><span
  class=\"p\">)</span>\n    <span class=\"kr\">end</span>\n<span class=\"kr\">end</span>\n\n<span
  class=\"n\">autocmd</span><span class=\"p\">({</span> <span class=\"s2\">&quot;BufWritePost&quot;</span>
  <span class=\"p\">},</span> <span class=\"p\">{</span>\n    <span class=\"n\">group</span><span
  class=\"o\">=</span><span class=\"n\">M</span><span class=\"p\">.</span><span class=\"n\">waylonwalker_augroup</span><span
  class=\"p\">,</span>\n    <span class=\"n\">pattern</span> <span class=\"o\">=</span>
  <span class=\"p\">{</span> <span class=\"s2\">&quot;*.py&quot;</span> <span class=\"p\">},</span>\n
  \   <span class=\"n\">callback</span> <span class=\"o\">=</span> <span class=\"n\">M</span><span
  class=\"p\">.</span><span class=\"n\">format_python</span><span class=\"p\">,</span>\n<span
  class=\"p\">})</span>\n</code></pre></div>\n<h2 id=\"file-navigation\">File Navigation</h2>\n<p><em>rg</em></p>\n<p>List
  <strong>all</strong> your files</p>\n<div class=\"highlight\"><pre><span></span><code>rg
  --files\n</code></pre></div>\n<p>use <code>gf</code> to go to file under the cursor</p>\n<h3
  id=\"map-it\">map it</h3>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"nb\">nnoremap</span> <span class=\"p\">&lt;</span>leader<span class=\"p\">&gt;</span>
  <span class=\"k\">f</span> :<span class=\"k\">new</span><span class=\"p\">&lt;</span><span
  class=\"k\">cr</span><span class=\"p\">&gt;</span>:.<span class=\"p\">!</span>rg
  <span class=\"p\">--</span><span class=\"k\">files</span><span class=\"p\">&lt;</span><span
  class=\"k\">cr</span><span class=\"p\">&gt;</span>\n</code></pre></div>\n<div class=\"admonition
  note\">\n<p class=\"admonition-title\">Note</p>\n<p>I use and reccomend Telescope,
  but <code>gf</code> can work fantasic without any setup.</p>\n</div>\n<h2 id=\"file-navigation_1\">File
  Navigation</h2>\n<p><em>markata</em></p>\n<p>I built my own static site generator,
  one thing that it can do pretty well is\nnavigate through large sets of posts and
  list out their path.  I can pipe this right into </p>\n<div class=\"highlight\"><pre><span></span><code>markata
  list --map path --filter <span class=\"s1\">&#39;&quot;til&quot; in path&#39;</span>
  --fast --no-pager\n</code></pre></div>\n<h2 id=\"file-navigation_2\">File Navigation</h2>\n<div
  class=\"highlight\"><pre><span></span><code><span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">keymap</span><span class=\"p\">.</span><span class=\"n\">set</span><span
  class=\"p\">(</span><span class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span>
  <span class=\"s1\">&#39;geit&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;terminal
  markata list --map path --filter </span><span class=\"se\">\\&#39;</span><span class=\"s1\">&quot;til&quot;
  in path</span><span class=\"se\">\\&#39;</span><span class=\"s1\"> --fast --no-pager&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;geit&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;Telescope find_files find_command=markata,list,--map,path,--filter,date==today,--fast&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;&lt;leader&gt;ee&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;vertical terminal lf&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<h2 id=\"floatterm\">FloatTerm</h2>\n<div
  class=\"highlight\"><pre><span></span><code><span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">keymap</span><span class=\"p\">.</span><span class=\"n\">set</span><span
  class=\"p\">(</span><span class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span>
  <span class=\"s1\">&#39;&lt;leader&gt;&lt;leader&gt;w&#39;</span><span class=\"p\">,</span>
  <span class=\"s1\">&#39;&lt;cmd&gt;FloatermNew waylonwalker&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n<span class=\"n\">vim</span><span class=\"p\">.</span><span
  class=\"n\">g</span><span class=\"p\">[</span><span class=\"s1\">&#39;floaterm_opener&#39;</span><span
  class=\"p\">]</span> <span class=\"o\">=</span> <span class=\"s1\">&#39;vsplit&#39;</span>\n<span
  class=\"n\">vim</span><span class=\"p\">.</span><span class=\"n\">keymap</span><span
  class=\"p\">.</span><span class=\"n\">set</span><span class=\"p\">(</span><span
  class=\"s1\">&#39;n&#39;</span><span class=\"p\">,</span> <span class=\"s1\">&#39;gee&#39;</span><span
  class=\"p\">,</span> <span class=\"s1\">&#39;&lt;cmd&gt;FloatermNew lf&lt;cr&gt;&#39;</span><span
  class=\"p\">)</span>\n</code></pre></div>\n<h2 id=\"vimgrep-over-hidden-files\">vimgrep
  over hidden files</h2>\n<p>I know all the files that I care to search for are called
  build.yml, and they\nare in a hidden directory.</p>\n<div class=\"highlight\"><pre><span></span><code><span
  class=\"p\">:</span>args `fd <span class=\"p\">-</span>H build.yml`\n<span class=\"p\">:</span><span
  class=\"k\">vimgrep</span> <span class=\"sr\">/upload docs/</span> ##\n</code></pre></div>\n<p>Once
  opened as a buffer by using args, and a handy fd command I can vimgrep\nover all
  the open buffers using <code>##</code></p>\n<blockquote>\n<p>Open buffers are represented
  by ##</p>\n</blockquote>\n<p>Now I can just <code>dap</code> and <code>:cnext</code>
  my way through the list of changes that I\nhave, and know that I hit every one of
  them when I am at the end of my list.\nAnd can double check this in about 10s by
  scrolling back through the quickfix\nlist.</p>\n<div class='prevnext'>\n\n    <style
  type='text/css'>\n\n    :root {\n      --prevnext-color-text: #eefbfe;\n      --prevnext-color-angle:
  #e1bd00c9;\n      --prevnext-subtitle-brightness: 3;\n    }\n    [data-theme=\"light\"]
  {\n      --prevnext-color-text: #1f2022;\n      --prevnext-color-angle: #ffeb00;\n
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
  \   </style>\n\n    <a class='prev' href='/extending-vim/slide-0'>\n\n\n        <svg
  width=\"50px\" height=\"50px\" viewbox=\"0 0 24 24\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n
  \           <path d=\"M13.5 8.25L9.75 12L13.5 15.75\" stroke=\"var(--prevnext-color-angle)\"
  stroke-width=\"1.5\" stroke-linecap=\"round\" stroke-linejoin=\"round\"> </path>\n
  \       </svg>\n        <div class='prevnext-text'>\n            <p class='prevnext-subtitle'>prev</p>\n
  \           <p class='prevnext-title'>extending vim with shell commands | 0</p>\n
  \       </div>\n    </a>\n\n    <a class='next' href='/'>\n\n        <div class='prevnext-text'>\n
  \           <p class='prevnext-subtitle'>next</p>\n            <p class='prevnext-title'>extending
  vim with shell commands</p>\n        </div>\n        <svg width=\"50px\" height=\"50px\"
  viewbox=\"0 0 24 24\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n            <path
  d=\"M10.5 15.75L14.25 12L10.5 8.25\" stroke=\"var(--prevnext-color-angle)\" stroke-width=\"1.5\"
  stroke-linecap=\"round\" stroke-linejoin=\"round\"></path>\n        </svg>\n    </a>\n
  \ </div>"
jinja: false
long_description: Vimconf 2022 Extending vim does not need to be complicated and can
  be done using cli tools Husband Father of two Eater of spicy shit pipx run waylonwalker
  Plugins are awesome, this talk will not focus on plugins, but will use them when
  it makes sense
now: 2022-12-09 13:48:24.795918
path: pages/extending-vim.md
published: 'False'
slug: extending-vim
status: draft
super_description: Vimconf 2022 Extending vim does not need to be complicated and
  can be done using cli tools Husband Father of two Eater of spicy shit pipx run waylonwalker
  Plugins are awesome, this talk will not focus on plugins, but will use them when
  it makes sense. ! lua is an amazing feature of neovim.  Both let you extend neovim
  in amazing ! A cli is going to be slower than vimscript/lua in many cases, but its
  often familiarity low barrier to entry works good enough works cross editor ! Lets
  start with some
tags:
- vim
templateKey: blog-post
title: extending vim with shell commands
today: 2022-12-09
---

Vimconf 2022

## The pitch

Extending vim does not need to be complicated and can be done using cli tools
that you might already be comfortable with.  Examples, setting up
codeformatters with autocmds, using lf/ranger as a tui file manager, generating
new files using a template framework like cookiecutter/copier/yeoman, using ag
to populate your quickfix.

## Me


* Husband
* Father of two
* Eater of spicy shit

``` vim
:term pipx run waylonwalker
```
<img alt='one chip challenge' src='/paqui.jpg' style='width:250px; float: right;position:absolute;right:500px;'/>


pipx run waylonwalker

## Plugins

Plugins are awesome, this talk will not focus on plugins, but will use them when it makes sense.

!!! Note ""
    A lot can be done with the command line

## vimscript / lua

lua is an amazing feature of neovim.  Both let you extend neovim in amazing
ways with little effort, but there quickly becomes a limit where you need to
learn a lot more about it to do what you need.

!!! Note ""
    lua can be a deep rabbit hole

## why a cli

A cli is going to be slower than vimscript/lua in many cases, but its often
something that you already know.  If you write any sort of code its very likely
that you can write a cli in that language that you are familiar with and get
the benefits of all your familiar tooling.

* familiarity
* low barrier to entry
* works good enough
* works cross editor

!!! Note ""
    Start with something you are comfortable in

## run a command

Lets start with some cli's.

``` bash
vimconf!!<esc>!!figlet
```

run it

``` txt
       _                            __ _ _ 
__   _(_)_ __ ___   ___ ___  _ __  / _| | |
\ \ / / | '_ ` _ \ / __/ _ \| '_ \| |_| | |
 \ V /| | | | | | | (_| (_) | | | |  _|_|_|
  \_/ |_|_| |_| |_|\___\___/|_| |_|_| (_|_)
                                           
```

## Chat


```
__        ___           _         _                 _     _                
\ \      / / |__   __ _| |_   ___| |__   ___  _   _| | __| | __      _____ 
 \ \ /\ / /| '_ \ / _` | __| / __| '_ \ / _ \| | | | |/ _` | \ \ /\ / / _ \
  \ V  V / | | | | (_| | |_  \__ \ | | | (_) | |_| | | (_| |  \ V  V /  __/
   \_/\_/  |_| |_|\__,_|\__| |___/_| |_|\___/ \__,_|_|\__,_|   \_/\_/ \___|
                                                                           
                    
 _ __ _   _ _ __    
| '__| | | | '_ \   
| |  | |_| | | | |_ 
|_|   \__,_|_| |_(_)
                    
```

!!! danger ""
    gimme a command



## So what's going on here

!!! note ""
    :.! works on standard unix pipes

-> Your input is piped into the command as stdin. ->

```
echo "vimconf" | figlet
```

-> Then replaced with what comes from stdout. ->

## A lot of things dont work on stdin/stdout

For instance many formatters work out of fileio, so I made a small, crappy,
works for me, shim, `genericformat`.

``` bash
pipx install genericformat
```

---

!!! danger
    use it if it works for you, it works for me

## for .! to work your cli must accept stdin

Many formatters don't support stdin so I made a little shim `genericformat` 

``` bash
genericformat --help

usage: genericformat [-h] --formatter FORMATTER [code]

format some code with a formatter

positional arguments:
  code                  the code to format

options:
  -h, --help            show this help message and exit
  --formatter FORMATTER
                        path to the formatter to run
```

## format some code

Format this one python statement.

```python
print('here')
```

press !!genericformat --formatter black<cr>

```python
print("here")
```

Now try a multiline statement.

``` python
def func(arg_one, arg_two, arg_three, kwarg='one',):
   ...
```

press Vj!genericformat --formatter black<cr>

``` python
def func(
    arg_one,
    arg_two,
    arg_three,
    kwarg="one",
):
    ...
```

Want Docstrings???

press V6j!doq

``` python
def func(
    arg_one,
    arg_two,
    arg_three,
    kwarg="one",
):
    """func.

    :param arg_one:
    :param arg_two:
    :param arg_three:
    :param kwarg:
    """
    ...
```

## using BufWritePost for formatters

My old config written in vimscript if you care.

``` vim
function! s:PyPreSave()
    Black
endfunction

function! s:PyPostSave()
    execute "!tidy-imports --black --quiet --replace-star-imports --action REPLACE " . bufname("%")
    execute "!isort " . bufname("%")
    execute "!black " . bufname("%")
    execute "e"
endfunction

:command! PyPreSave :call s:PyPreSave()
:command! PyPostSave :call s:PyPostSave()

augroup waylonwalker
    autocmd!
    autocmd bufwritepre *.py silent! execute 'PyPreSave'
    autocmd bufwritepost *.py silent! execute 'PyPostSave'
augroup end
```

## Lua all the things

!!! Note ""
    This is **neovimconf** after all


## using BufWritePost for formatters

My latest config written in `lua`.

``` lua
local settings = require'waylonwalker.settings'

M.waylonwalker_augroup = augroup('waylonwalker', { clear = true })
M.format_python = function()
    if settings.auto_format.python then
        vim.cmd('silent execute "%!tidy-imports --black --quiet --replace-star-imports --replace --add-missing --remove-unused " . bufname("%")')
        vim.cmd('silent execute "%!isort " . bufname("%")')
        vim.cmd('silent execute "%!black " . bufname("%")')
    end
end

autocmd({ "BufWritePost" }, {
    group=M.waylonwalker_augroup,
    pattern = { "*.py" },
    callback = M.format_python,
})
```

## File Navigation
_rg_

List **all** your files

``` bash
rg --files
```

use `gf` to go to file under the cursor

### map it

``` vim
nnoremap <leader> f :new<cr>:.!rg --files<cr>
```


!!! Note
    I use and reccomend Telescope, but `gf` can work fantasic without any setup.

## File Navigation
_markata_

I built my own static site generator, one thing that it can do pretty well is
navigate through large sets of posts and list out their path.  I can pipe this right into 

``` bash
markata list --map path --filter '"til" in path' --fast --no-pager
```

## File Navigation

``` lua
vim.keymap.set('n', 'geit', '<cmd>terminal markata list --map path --filter \'"til" in path\' --fast --no-pager<cr>')
```

``` lua
vim.keymap.set('n', 'geit', '<cmd>Telescope find_files find_command=markata,list,--map,path,--filter,date==today,--fast<cr>')
```

``` lua
vim.keymap.set('n', '<leader>ee', '<cmd>vertical terminal lf<cr>')
```

## FloatTerm

``` lua
vim.keymap.set('n', '<leader><leader>w', '<cmd>FloatermNew waylonwalker<cr>')
vim.g['floaterm_opener'] = 'vsplit'
vim.keymap.set('n', 'gee', '<cmd>FloatermNew lf<cr>')
```

## vimgrep over hidden files ##

I know all the files that I care to search for are called build.yml, and they
are in a hidden directory.

``` vim
:args `fd -H build.yml`
:vimgrep /upload docs/ ##
```

Once opened as a buffer by using args, and a handy fd command I can vimgrep
over all the open buffers using `##`

> Open buffers are represented by ##

Now I can just `dap` and `:cnext` my way through the list of changes that I
have, and know that I hit every one of them when I am at the end of my list.
And can double check this in about 10s by scrolling back through the quickfix
list.
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
    
    <a class='prev' href='/extending-vim/slide-0'>
    

        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M13.5 8.25L9.75 12L13.5 15.75" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"> </path>
        </svg>
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>prev</p>
            <p class='prevnext-title'>extending vim with shell commands | 0</p>
        </div>
    </a>
    
    <a class='next' href='/'>
    
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>next</p>
            <p class='prevnext-title'>extending vim with shell commands</p>
        </div>
        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M10.5 15.75L14.25 12L10.5 8.25" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
    </a>
  </div>