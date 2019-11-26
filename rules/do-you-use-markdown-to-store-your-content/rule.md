

---
authors:
  - id: 1
    title: Adam Cogan
  - id: 53
    title: Thiago Passos
  - id: 89
    title: Anthony Ison
  - id: 84
    title: Patricia Barros
  - id: 72
    title: Gabriel George
---




<span class='intro'> <p class="ssw15-rteElement-P">​​​You&#160;want users to easily edit content, so you put an&#160;&quot;edit&quot; button on the page. From there, you can&#160;choose between the power of HTML or the limitations of Markdown.<br></p><dl class="image"><dt> 
      <img src="/PublishingImages/edit-button.jpg" alt="edit-button.jpg" /> 
   </dt><dd>Figure&#58; &quot;Edit&quot; button to encourage users updating the&#160;​content​<br></dd></dl><p class="ssw15-rteElement-P">
   <b>HTML</b> is frightening for most users, as&#160;one wrong tag or an inline styling can break the whole page view.&#160;<br></p><p class="ssw15-rteElement-P">
   <b>Markdown</b> is simpler​​&#160;​and encourages more editing without breaking the page.​​​<br></p><p>The original spec for Markdown can be found at <a href="https&#58;//daringfireball.net/projects/markdown/syntax">https&#58;//daringfireball.net/projects/markdown/syntax</a>. Although, it does not specify the syntax unambiguously – so there are different flavours of the spec available. Some popular ones include&#58;</p><ul><li><a href="https&#58;//spec.commonmark.org/0.29/">Commonmark Spec</a></li><li><a href="https&#58;//github.github.com/gfm/">GitHub Flavored Markdown (GFM) Spec</a><br></li><li><a href="https&#58;//github.com/markdown-it/markdown-it">markdown-it</a>&#160;(really flexible, pluggable library based on CommonMark)<br></li></ul><p>The&#160;<a href="https&#58;//github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet">Markdown Cheatsheet</a>&#160;is a great page to reference when learning Markdown.<br></p><p>If you use markdown-it, there are many plugins that allow you to extend markdown. <a href="https&#58;//sugarlearning.com/">SugarLearning</a>&#160;provides a more extensive&#160;<a href="https&#58;//my.sugarlearning.com/SSW/items/13308/markdown-cheatsheet">cheatsheet</a>&#160;which includes a number of custom&#160;templates and markdown-it&#160;plugins.<br></p><dl class="image"><dt><img src="/PublishingImages/markdown.jpg" alt="markdown.jpg" /><br></dt></dl><p></p><h3 class="ssw15-rteElement-H3">​Video​s<br></h3><p class="ssw15-rteElement-P">Watch the video&#160;&quot;Markdown - &#160;How to use it, What is it and Why Use it | Ask a Dev&quot;&#58;<br></p><div class="ms-rtestate-read ms-rte-embedcode ms-rte-embedil ms-rtestate-notify"> 
   <iframe width="750" height="422" src="https&#58;//www.youtube.com/embed/p_SsHtKRj-8" frameborder="0"></iframe>&#160;</div><p class="ssw15-rteElement-P"> 
   <br> 
</p>Watch the video where Thiago explains the benefits of using Markdown&#58; 
<div class="ms-rtestate-read ms-rte-embedcode ms-rte-embedil ms-rtestate-notify s4-wpActive"> 
   <iframe width="750" height="422" src="https&#58;//www.youtube.com/embed/j3ix99MdSic" frameborder="0"></iframe>&#160;</div> </span>

<h3 class="ssw15-rteElement-H3">​Don't store content as HTML - It's a&#160;trap​&#160;​<br></h3><p>​Rich HTML&#160;Editors&#160;​make your life easier at the beginning and produce content that looks&#160;nice and clean, but behind the scenes, it generates&#160;HTML which can get out of control quickly especially&#160;if you need to&#160;edit the source code (E.g.&#160;include a special style).&#160;It becomes incredibly difficult to maintain over time.&#160;</p><p>Some examples of rich HTML editors that you can embed in your web applications&#58;</p><ul><li> 
      <a href="https&#58;//www.telerik.com/kendo-angular-ui/components/editor/">​​Kendo Editor</a>​<br></li><li> 
      <a href="https&#58;//www.tiny.cloud/">TinyMCE</a></li><li> 
      <a href="https&#58;//ckeditor.com/">CKEditor</a>​<br></li></ul><div> 
   <b>Note&#58; </b>None of these are recommended because of the HTML that is generated.<br></div><dl class="badImage"><dt>
      <img src="/PublishingImages/HTML-bad.jpg" alt="HTML-bad.jpg" /> 
   </dt><dd>Figure&#58; Bad example - HTML generated by a rich editor&#160;gets harder&#160;to&#160;maintain over time.​</dd></dl> ​This link shows many things that have to be fixed in&#160;bad HTML&#58;&#160;<a href="https&#58;//www.diffchecker.com/CIGu4K19">https&#58;//www.diffchecker.com/CIGu4K19​</a>.​​ 
<h3 class="ssw15-rteElement-H3">Store content in Markdown​<br></h3><p>​Content is typically either stored in files (eg. git) or a database. When stored in files, it is common to use a static site generator with a JAMStack approach. (eg. Gatsby, Vuepress, Hexo, etc) That is, you commit content into git and a CI/CD pipeline is executed. The resulting files (html and css) are&#160;then served from storage which is cheaper and typically&#160;more&#160;scalable than compute resources in the cloud. In this case, the workflow will be a development style workflow (commit to git, push, etc) and&#160;the editor will be the one you choose. (e.g. GitHub editor or VS Code) These editors are&#160;not likely to produce a rich editing experience, nor do they need to.​<br></p><p>For a non-technical audience, it helps to&#160;store your content as markdown in a database and convert to HTML on the fly. This removes the code repository/CI/CD pipelines and can feel more natural for a non-developer audience. In this case, you will provide an editor and it is recommended that this be a rich editor.&#160;<br></p><p><span style="color&#58;#cc4141;font-family&#58;&quot;segoe ui&quot;, &quot;trebuchet ms&quot;, tahoma, arial, verdana, sans-serif;font-size&#58;18px;">Markdown rich editors</span><br></p><p>The Markdown rich editors are not as good as the HTML ones​, but at least the content they produce is maintainable over&#160;time.<br></p><p>Some example of rich Markdown editors are&#58;<br></p><ul><li> 
      <a href="http&#58;//prosemirror.net/">​​ProseM​irror</a>​​<br></li><li> 
      <a href="https&#58;//pandao.github.io/editor.md/">Editor.Md</a><br> Note&#58; It is the #1 editor on 
      <a href="https&#58;//ourcodeworld.com/articles/read/359/top-7-best-markdown-editors-javascript-and-jquery-plugins">Top 7&#58; Best Markdown editors Javascript and jQuery plugins</a><br></li><li>
      <a href="https&#58;//ui.toast.com/tui-editor/">ToastUI Editor</a>&#160;(recommended)<br>​Note&#58; ToastUI provides more customisation options (menu and language) than Editor.md</li></ul><dl class="goodImage"><dt>
      <img src="/PublishingImages/markdown-good.jpg" alt="markdown-good.jpg" />
   </dt><dd>Figure&#58; Good example - Markdown looks clean<br></dd></dl><h3 class="ssw15-rteElement-H3">​​Markdown can have rich content too​</h3><p>Markdown is simple and limited, but you can&#160;make it richer​.</p><p>One way is to use inline HTML, this allows you to use HTML tags that you are familiar with (only if you need to) and embed things like YouTube videos or JavaScript.​<br><br></p><dl class="image"><dt> 
      <img src="/PublishingImages/use-html-in-markdown.png" alt="use-html-in-markdown.png" style="width&#58;750px;" /> 
   </dt><dd>Figure&#58; OK Example – you can use raw HTML in your Markdown, and mostly it will work pretty well. But you can’t use Markdown’s syntactic sugar in the HTML</dd></dl><p>The other way is to use templates or containers&#58;</p><dl class="badImage"><dt> 
      <img src="/PublishingImages/danger-html-and-markdown.png" alt="danger-html-and-markdown.png" style="width&#58;750px;" /> 
   </dt><dd>Figure&#58; Bad Example – The danger of using HTML in your Markdown files is that you add too much formatting e.g. use Bootstrap classes that create tight coupling between the content and the presentation</dd></dl><p>A better way is to use a plugin (if your Markdown engine supports it).<br></p><dl class="goodImage"><dt>
      <img src="/PublishingImages/vuepress-custom-container.png" alt="vuepress-custom-container.png" style="width&#58;750px;" />
   </dt><dd>Figure&#58; Good Example – VuePress has a custom container that generates nice alert boxes like Bootstrap but without tying the presentation to the CSS framework in the content</dd></dl><p class="ssw15-rteElement-P">Unfortunately, Markdown does not support YouTube videos embedding out of the box. However, there is a workaround to embed it.<br></p><p class="ssw15-rteElement-CodeArea">[![What is SSW TV](http&#58;//img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](http&#58;//www.youtube.com/watch?v=dQw4w9WgXcQ)<br><br><img src="/SiteAssets/using-markdown-to-store-your-content/YouTube%20Embed%20Workaround.png" alt="YouTube Embed Workaround.png" style="margin&#58;5px;" /><br><br></p><dd class="ssw15-rteElement-FigureGood">​​​Figure&#58; Good Example - Workaround to embed YouTube video using YouTube's generated thumbnail&#160;<br></dd><p class="ssw15-rteElement-P">​​If your site is using &quot;<a href="https&#58;//www.npmjs.com/package/markdown-it">markdown-it​</a>&quot; parser, you can also install &quot;<a href="https&#58;//www.npmjs.com/package/markdown-it-video">markdown-it-video</a>&quot; to allow YouTube video directly embedded into the page, rather than providing just an image and​ a link.<br></p><p class="ssw15-rteElement-CodeArea">​@[youtube](http&#58;//www.youtube.com/embed/dQw4w9WgXcQ)<br><br><img src="/SiteAssets/using-markdown-to-store-your-content/YouTube%20Embed%20with%20Plugin.png" alt="YouTube Embed with Plugin.png" style="margin&#58;5px;width&#58;808px;" /><br><br></p><dd class="ssw15-rteElement-FigureGood">​​Figure&#58; Better Example - YouTube video embedding using plugin​​​<br></dd><h3>Markdown to HTML rendering processes<br></h3><dl class="image"><dt>
      <img src="/PublishingImages/markdown-rendering.jpg" alt="markdown-rendering.jpg" style="width&#58;750px;" />
   </dt><dd>Figure&#58; The markdown rendered either Client-side or Server-side<br></dd></dl>

