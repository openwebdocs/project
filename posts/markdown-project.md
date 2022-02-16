
In 2021, the Open Web Docs team, with help from Mozilla, the W3C, and the wider web docs community, converted the authoring format for MDN Web Docs  - all 11,000 pages of it - from HTML to Markdown. In this post we'll talk about why we did it, how we did it, and how it turned out.

## HTML soup

Before 2020, MDN was a Wiki, and contributors edited pages using a web-based WYSIWYG HTML editor. This made it easy to make casual contributions: people could edit text and apply simple formatting, like **bold** or `code`, without having to edit the underlying HTML. But a WYSIWYG editor is not well-suited to more complex edits, and authors often had to edit the underlying HTML source directly. Also, because the underlying source was hidden by default, HTML cruft, like `<span id="486uw3y3">` crept into the source, often from authors pasting HTML from another rich editing environment into the MDN WYSIWYG editor.

In 2020, MDN replaced the old Wiki with a new platform in which the source for the docs was stored in a GitHub repository as a collection of HTML files, and this was built into web pages by the [Yari](https://github.com/mdn/yari/) code. This had several major advantages, but it meant that the old WYSIWYG editor was no more. Instead, all authors had to edit MDN pages as raw HTML documents.

For technical writers, HTML is hard to write and hard to review. It's easy to make mistakes like missing closing tags or getting the nesting wrong, and it's hard for reviewers to spot these kinds of mistakes. Also, we had to escape HTML tags in any example code we wrote, which is difficult and error-prone. For example, here's a code sample from the page on [`<dl>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dl):

```
<pre class="brush: html">&lt;dl&gt;
  &lt;dt&gt;Name&lt;/dt&gt;
  &lt;dd&gt;Godzilla&lt;/dd&gt;
  &lt;dt&gt;Born&lt;/dt&gt;
  &lt;dd&gt;1952&lt;/dd&gt;
  &lt;dt&gt;Birthplace&lt;/dt&gt;
  &lt;dd&gt;Japan&lt;/dd&gt;
  &lt;dt&gt;Color&lt;/dt&gt;
  &lt;dd&gt;Green&lt;/dd&gt;
&lt;/dl&gt;
</pre>
```

In practice, this makes writers concentrate so much on the markup that it's hard to concentrate on the writing itself.

Also, authors were faced with the result of 15 years of people pasting rich content into the WYSIWYG editor, resulting in source like this:

```
<pre class="brush: js"><span class="kd">const</span> <span class="nx">element</span> <span class="o">=</span> <span class="nx">driver</span><span class="p">.</span><span class="nx">findElement</span><span class="p">(</span><span class="nx">By</span><span class="p">.</span><span class="nx">id</span><span class="p">(</span><span class="s1">'myElementId'</span><span class="p">));</span></pre>
```

It was clear that for the long-term health of MDN, we needed a better authoring experience than this, both for volunteer contributors and for full-time staff writers.

## Choosing a format, part 1 - Markdown

Replacing HTML as the authoring format for MDN wasn't a new idea: we had discussed it many times in the last few years. We had considered both [AsciiDoc](https://www.writethedocs.org/guide/writing/asciidoc/) and [reStructuredText](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html) and in many ways these formats are superior to Markdown: they are more powerful, they support semantic markup, and they have extensibility built in.

Instead of these, we chose Markdown, because Markdown is such a widely used and supported format. This gives us two major advantages:
- almost everyone coming to MDN is going to understand Markdown well enough to contribute right away. Even though many MDN contributions need an understanding of the (sometimes extreme!) complexity of MDN, many contributions do not, and Markdown makes these contributions as easy as possible.
- there's great and often seamless tool support for Markdown. Most modern code editors have Markdown preview built in. [Prettier](https://prettier.io/) has support for Markdown (and even for code samples embedded in Markdown). GitHub can display rich diffs for Markdown.

## Choosing a format, part 2 - but which Markdown?

One difficulty with Markdown is that there isn't a single Markdown. There are multiple incompatible versions, each featuring different extensions to the basic syntax. It was observed early on that we could make a lossless and entirely automatic conversion from HTML to Markdown, by using syntax extensions for components such as `class` and `id` attributes.

This would have made the project go much quicker, because we would not have had to clean up the source content. But it would have delivered much less value, precisely because we would not have cleaned up the source content. The main purpose of this project was to have readable source files.

This pushed us towards a minimalist approach, in which we would:

1. choose a baseline flavour of Markdown
2. analyse our current files to figure out which extensions we needed
3. decide on a syntax for the extensions
4. update our sources to clean any HTML syntax that we didn't want to take into our future

## Choosing a format, part 3 - the gory details

For the baseline we chose [GitHub-Flavored Markdown](https://github.github.com/gfm/) (GFM). This is well-supported and has a good spec. It is a superset of [CommonMark](https://spec.commonmark.org/), and just adds a few extensions. We might have chosen CommonMark as a baseline, except GFM supports tables, which we knew we needed.

The next step was to figure out what to do about features in the MDN source files that weren't supported in GFM. For each feature like this, there are three options:

1. Stop using the feature: find another way to do the thing we want. For example, we had some markup that would present items in multicolumn layout, and [we decided that we could live without this](https://github.com/mdn/content/discussions/7263). Making decisions like this helps simplify the MDN authoring experience, which we think is a good thing!

2. Invent a Markdown-style syntax for the feature. [We decided to do this, for example, for `<dl>` elements](https://github.com/mdn/content/issues/4367), which are very widely used in MDN.

3. Keep using HTML for the feature. We tried to minimise the amount of HTML we would end up having in our source docs. However, where a feature was localized in use, and where a direct Markdown equivalent did not exist, we decided to keep HTML. [We opted to do this, for example, for `<sub>` and `<sup>`](https://github.com/mdn/content/issues/4578).

The process for making these decisions was to file GitHub issues presenting the feature, with a few possible options for resolving it, then solicit feedback from writers including Mozilla staff, OWD staff, W3C staff, and members of the wider community. This was the heart of the whole project, and authors care a lot about their authoring tools. So it was important to us that anyone - but especially authors - should be able to participate in the discussion, and that we would not prejudge the outcome. Often the resolution we adopted was not one of the expected options, as people really engaged with the process and helped us make good choices.

After we had a resolution for each issue we updated the documentation for writing [Markdown on MDN](https://developer.mozilla.org/en-US/docs/MDN/Contribute/Markdown_in_MDN), and pointed from this document back to the discussion, so people can understand how we reached each decision.

One principle that emerged from this process was: we wanted syntax that would work reasonably well with tools that expected plain GFM. For example, [we chose a syntax for notes and warnings that would look OK as GFM](https://github.com/mdn/content/issues/3483). Similarly, we considered using the [Kramdown syntax for `<dl>`](https://kramdown.gettalong.org/syntax.html#definition-lists), but eventually chose something based on the GFM `<ul>` syntax, mostly because it would look OK when formatted using Prettier.

## Implementing the tools

Once we had a plan for how we wanted the conversion to go, we needed a tool to convert our source files from HTML to Markdown. The conversion tool, `h2m`, uses the [Unified](https://unifiedjs.com/) framework, with additions to handle the extra syntax we've defined. It takes as input a directory containing one or more pages in HTML format, and converts any HTML pages it finds into Markdown pages.

We also needed an update to the Yari platform to perform the reverse operation, converting the Markdown back into HTML when we render the pages.

## Converting the content

Once we had the `h2m` conversion tool, we could start preparing the content for conversion. When we run the conversion tool over a set of pages, it also produces a report telling us which HTML features were unconvertible. We could then go through the content, making any changes needed to make the content Markdown-convertible.

Once we were happy with the conversion report, we'd create and review a PR to convert the pages. The conversion was made in two Git commits: one to rename the files from "index.html" to "index.md", and another to replace the file contents. This helps Git understand that we are changing an existing file, so we preserve its change history.

With over 11,000 pages on MDN, this was a big task. First we tested the water with the documentation for the JavaScript [`Map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) object. That seemed to go fine, so we followed up with all the [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) documentation (about 1000 pages) and then all the [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) documentation (also about 1000 pages). After that we converted the [Web API](https://developer.mozilla.org/en-US/docs/Web/API) documentation, which was more than 6000 pages, and was a scary PR to merge.

From there we were at about 70% converted, and gradually worked through the rest, finishing up in early October, about 6 months after we started the project.

## Building foundations for the future

Looking back from where we are now, we're really happy to be in Markdown. That code sample for `<dl>` we quoted at the start:

```
<pre class="brush: html">&lt;dl&gt;
  &lt;dt&gt;Name&lt;/dt&gt;
  &lt;dd&gt;Godzilla&lt;/dd&gt;
  &lt;dt&gt;Born&lt;/dt&gt;
  &lt;dd&gt;1952&lt;/dd&gt;
  &lt;dt&gt;Birthplace&lt;/dt&gt;
  &lt;dd&gt;Japan&lt;/dd&gt;
  &lt;dt&gt;Color&lt;/dt&gt;
  &lt;dd&gt;Green&lt;/dd&gt;
&lt;/dl&gt;
</pre>
```

now [looks like this](https://github.com/mdn/content/blob/43e6201e3ce12498ddeb4ec47b68b37c41d66430/files/en-us/web/html/element/dl/index.md?plain=1#L169-L180):


````
```html
<dl>
  <dt>Name</dt>
  <dd>Godzilla</dd>
  <dt>Born</dt>
  <dd>1952</dd>
  <dt>Birthplace</dt>
  <dd>Japan</dd>
  <dt>Color</dt>
  <dd>Green</dd>
</dl>
```
````

The code sample quoted above that used to look like this:

```
<pre class="brush: js"><span class="kd">const</span> <span class="nx">element</span> <span class="o">=</span> <span class="nx">driver</span><span class="p">.</span><span class="nx">findElement</span><span class="p">(</span><span class="nx">By</span><span class="p">.</span><span class="nx">id</span><span class="p">(</span><span class="s1">'myElementId'</span><span class="p">));</span></pre>
```

now [looks like this](https://github.com/mdn/content/blob/43e6201e3ce12498ddeb4ec47b68b37c41d66430/files/en-us/learn/tools_and_testing/cross_browser_testing/your_own_automation_environment/index.md?plain=1#L294-L296):

````
```js
const element = driver.findElement(By.id('myElementId'));
```
````

But it's not about individual blocks of content. Overall, writing and reviewing is dramatically easier than it used to be. The beauty of Markdown, as a writer, is that it lets you concentrate on expressing concepts and hardly thinking about syntax at all.

At Open Web Docs, we always have to consider which projects to take on next. In particular we have to choose between projects to write new documentation, projects to improve existing documentation, and projects to improve documentation infrastructure. They're all important, but infrastructure projects like Markdown conversion sometimes seem hard to justify because they don't provide an immediate benefit to our readers. The success of the Markdown project was that the rendered pages look (mostly) exactly the same!

But we have to think about the long term. MDN has been around for 17 years, and we hope (and have to work with the belief that) it will be around for decades more. We might have gone on for another year or two with HTML-format documentation, and it would just have been a drag on our productivity. But we knew that this wasn't a sustainable foundation in the long term.

We think we have something now that we could live with for a long time, and we think it's worth the effort it took to build.
