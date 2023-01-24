# Deep dive session: Code examples

## Description

* Code playground: “all code on MDN”
  * Every piece of code which is either runnable (live sample, example, code snippets, …)
  * Or even everything lives in a code block
* Experiments with interactive examples on Web API pages
* Consolidate and take ownership of external examples such as on codepen, jsfiddle, etc.?

## Goal

* Make authorship and maintenance of examples easier

## Minutes

* We have:
  * Examples in page (static code blocks)
  * Interactive examples
    * Oddity: they’re separate from content (from authorship POV), it should feel more like one thing (Florian S)
    * Florian D: is there any reason that every example isn’t interactive?
* There’s two discussions here:
  * One: how do we maintain examples within the workflow of content
  * Two: how do we display these examples to users
* To make changes across the board is a huge undertaking, because there’s so many interactive examples everywhere)
* The cost of developing and maintaining examples is probably different from content:
  * Do we need as many of them?
  * Should we prioritize certain ones?
    * Some bring certain value, others not so, do they all have the same cost of maintenance?
* Different ways of showing examples:
  * Static code blocks
  * Live samples
    * EmbedLiveSample macro
    * Code lives in content
    * Much more likely to be maintained and correct
  * Github pages embedded
    * EmbedGHLiveSample
    * Difference from above is code lives in github instead of the content, reasoning behind these is CSPs or similar
    * As an author, this one is annoying
      * Hard to keep content in sync
  * Interactive Examples
  * Codepen, jsfiddle, glitch
  * Github pages interactive
  * Github pages not embedded
* As a user: why do we have so many?
  * From “my” POV: there’s two types, one static, one interactive
  * Should we just formalise them into these types
* Making things as simple as possible is good for making contribution easy
* Is the easy thing that live samples lives within the markdown specifically, or in the content repo?
  * Sibling index.html, css, etc.
* Proposal: every example except from static code blocks, and github non-embedded, live within the content repo as a sibling folder to index.md. One standardised way for all of this.
* Ruth: we’ll have some cases where an interactive examples isn’t what we’re looking for, but a github pages more explicit example is more what we want
* Context setup: specialized rendering context for, e.g. CSS or canvas
* How many examples do we have that have to be running on github pages for CSP, do we have to have an interactive example on the page for these if they’re not many?
  * Would be worth doing a dive into why people have chosen these other ways of doing examples
  * Security limits around APIs: adjective on iframe, https, headers, etc. we’ll surely see more of these things for new web platform features
    * Need to take this into account for examples
    * Generating subdomains for these examples is on the table, to set insecure headers
* Codepen, jsfiddle:
  * Don’t have personal accounts, use an official MDN one
  * Or just remove entirely if we can
  * Until we get rid of it, definitely not approve any which aren’t on an MDN account
* Separate the authorship concern from the rendering/infrastructure concerns for how we display these to users in a secure way
  * If we can simplify existing systems we make the future, running some sort of in-page editor, easier
  * Other than interactive examples, there’s no real standard
* Currently you can transplant examples from other pages, you can include then anywhere in multiple pages
  * This would be odd if examples live “next” to content
  * No analysis done of if this is something we often do, if this is a constraint we can live around
  * It won’t get ugly, even if we do allow it it can’t be more messy than what we have now
* Github pages interactive are nasty
  * The github page implements the interactivity, not taking on the appearance of the site at all
* Some examples are easy: here’s all the code, here’s the result
  * Some are more difficult, here’s a bit of code, here’s some description about it, here’s some more, etc.
  * If that’s the only two ways it is, that’s already quite confined, because all the code is in the content folder
* New content layout allows us to make any example interactive, if we want
  * One feature Florian always wanted to build was to be able to change something then share it with others: MDN Playground
* Is one of the reasons behind the mess of different examples because of a community aspect?
  * For contributors beyond people in this room: if the new model takes twice as long as the current one, contributions will surely drop
    * Hopefully this new model will make it easier
* Assets:
  * We’ve been working on allowing assets next to files, need to think about that as we implement this to ensure we don’t step on each other’s toes
  * Have a set of assets that are not too big in size, and conform to Mozilla’s guidelines, so we don’t have a huge repo nor lots of different versions of old Mozilla guidelines
  * Most files are small, but some are quite large, and it adds up, and binary files aren’t diffed
  * But we could have allowlists for certain websites such as archive.org for “blessed” mp3 examples etc.
* Does “new model” work better for some pages more than others, e.g. more for reference pages than guide pages, which this doesn’t seem to work quite so well for
  * When prototyping ensure we do so across multiple types of pages
* Florian D: super happy to keep live samples, but would change how we render/include them
* Would be nice if a lot of the reference pages had useful examples
  * When we did interactive examples, we came to standards for how to write examples
  * Standardising the example system should standardise how we author them
* For CSS: what is missing for some users is “give me the context here”, this depends on stuff, I want to reproduce it myself
  * I want to have full control, both the nice CSS view, but also “view source”
  * Would be good for user testing, asking them how they want to interact with code
  * Code completion
* Eloquent javascript book online does a very good job of examples
* Playground:
  * There would be nice ways to integrate with third parties (e.g. fastly) to run backend pieces: some examples are hard because we don’t have that, but there are ways out there to do that easily
  * A lot of these examples are similar to those happening for web platform tests: there may be lessons to be learned from there
    * E.g. a websocket server to rely on to run your test

## Action items

1. Remove codepen/jsfiddle/glitch examples? Document we won’t accept them
2. Finalize spec for content example folders, and prototype it for a few pages
3. User testing: ask users how they want to interact with code (context vs no context)
4. Take good look at embedded github examples and understand what we have and why