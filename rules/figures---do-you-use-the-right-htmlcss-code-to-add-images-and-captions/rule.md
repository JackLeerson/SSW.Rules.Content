

---
authors:
  - id: 16
    title: Tiago Araujo
  - id: 1
    title: Adam Cogan
---




<span class='intro'> <p>​​Most developers put the image and the caption in a DIV tag. The figure is just a paragraph.​<br></p> </span>

<font class="ms-rteCustom-CodeArea"> <pre>&lt;div&gt;
&lt;img alt=&quot;&quot;/&gt;
&lt;p&gt;Figure&#58; Caption&lt;/p&gt;
&lt;/div&gt;
</pre> </font> <span class="ms-rteCustom-FigureBad">Figure&#58; Bad Example</span> 
<p>Instead, you should use &lt;DL&gt;,&#160;&lt;DT&gt; (which is the item in the list – in our case an image) and &lt;DD&gt;for a caption. This structure gives semantic<span style="line-height&#58;20.8px;"> meaning</span> to&#160;the image and&#160;figure. <br></p>
<font class="ms-rteCustom-CodeArea"> <pre>&lt;dl class=&quot;image&quot;&gt; OR &lt;dl class=&quot;badImage&quot;&gt; OR &lt;dl class=&quot;goodImage&quot;&gt;
&lt;dt&gt;&lt;img alt=&quot;&quot;/&gt;&lt;/dt&gt;
&lt;dd&gt;Figure&#58; Caption&lt;/dd&gt;
&lt;/dl&gt;
</pre> </font> <span class="ms-rteCustom-FigureGood">Figure&#58; Good Example </span> 
<p><b>Note&#58;</b>&#160;&lt;dl&gt; stands for &quot;<b>definition list</b>&quot;; &lt;dt&gt; for &quot;<b>definition term</b>&quot;; and &lt;dd&gt; for &quot;<b>definition description</b>&quot;.</p>​<br>

