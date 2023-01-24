# Deep dive session: Information Architecture

## Minutes

### Page types status update

* Going area by area of the site
* Done
  * Web/API - done
  * JS
  * CSS
  * HTML: hasn’t been documented yet
  * SVG
* Almost done
  * HTTP
    * Little bit of cleanup then that’s done
  * WebExtensions
    * Matters because it uses tags for sidebars, and we want to use pagetypes instead

### What is a page type?

* There’s a frontmatter (the stuff at the top of the page in the md file)  item saying what kind of page it is
* We go through each of these areas and describe what kind of things we document in here
  * Interface pages
  * Instance properties
  * Etc.
  * Figure out what kind of taxonomy we have in each area
  * Then each page has a frontmatter item saying what kind of page this is
* This means from taxonomy POV that when we’re creating new page we know what kind of page it is
* In the future this will come with rules, e.g css property you have to provide the syntax box and everything else which comes with it
* This is formalizing things we already do
* Are we differentiating between different types of page like Guide and Reference?
* Yes: cross domain things, guide, landing page, glossary, can appear in any one of these sections. We might invent more.
* “Landing page” pretty vaguely defined, no structure associated, a page which looks like its a big list of links to other pages - but there’s scope to define this more, and be a bit more organized, ensuring our landing pages are consistent
  * at the moment we’re not doing this, but this will allow us to do it
  * Landing pages aren’t accessible through the sidebar, but this will allow us to do this

### Page types and authoring tooling

* On the authoring side, this could also be used for some cli tool for a given page type could give you a little template, or even more fancy stuff using webref to automatically put in some information automatically
  * That would be super great: at the moment you have to go “I know that that page I did previously is structurally correct, so I’ll go and copy that”
  * Sometimes you copy from a place where you haven’t used the latest guidelines, will be nice to always have the latest conventions when making a new page
* Is there any CI around page types?
  * No, but we want this (there’s an open issue) and this will allow us to do this
  * Currently “pages that exist under css must have one of these page types” but we don’t enforce this currently, a manual process

### Catchall page type?

* The sidebar currently uses page type to classify? For “Done” yes, page types is used to organise into sections like “property” “method” etc.
  * Previously used tags for this
  * Will we have pages without a page type? No.
    * Guides is sort of a catchall
    * With web/api there are quite specific rules about where you can put guides, and they’ll only appear in the sidebar if we do
    * Is landing page also a catchall?
    * Difference between guide and landing page (to Will):
      * Landing page doesn’t really tell you anything substantive, just takes you off to other pages
      * Guides do tell you stuff
    * Perhaps guides should explicitly not be the catchall, risks diluting what it means
    * Perhaps we need an explicit catchall type

### New page types and temples

* Going back to yesterday’s discussion about content groups, spanning HTML and CSS, what page type does that take?
  * Current page type structure is a reflection of our current taxonomy, doesn’t mean it can’t change into the future
  * If somebody comes along and invents a new content structure, that’ll come along with new page types
    * E.g. curriculum module, pages within have new page types
    * As we invent new content, we create new page types, and ideally define the structure of them
  * In the past will different authors/contributors, there were not strict rules around “this is a new type of page and this is how it is structured” and page types should help with this
* Every page types should link to a template, but that isn’t the case currently
  * None of the JS stuff has templates, there’s a whole bunch of stuff missing
  * At some point it would be great to not have those templates missing

### Taxonomy and hierarchies

* We on MDN side need to get better about mapping content to spec urls, currently one page may map to multiple specs, which will allow us to use webref better
* IA mostly on the page, or mostly on the site? Is focus on one or the other?
  * Page types is directly about page organization, as templates directly specify how a page should look
  * But does also work on a higher level, as doing this work shows us where things are inconsistent, and does affect hierarchy
  * Also tells us how much content we have of what sort, can clearly say in API lots of reference docs, not so many guides - can put numbers behind it, “how many http headers there are” - this tells us what kind/how much of content there is, and how we might organize it better
  * Could help with search, allowing to search within page type
* A lot of questions about when we should have a new page type are really judgment calls
  * Comes down to whether we have an intentional structure or intent, “what does it mean to have an MDN tutorial”
  * “Have intent and be explicit about it”
* In terms of the taxonomy and issues in HTML: W3C have exactly the same questions in specifications, part of point of webref is having a consistent view over this
  * Should we try and map MDN taxonomy with this, or at least have a common understanding
  * “Element states” to describe the various types of input elements
    * We could totally learn from this
* Whatever reorg/reclassification we do will help content and help readers, great exercise in itself
* Are metadocs going to be part of this, and their own page types? Like templates doc
  * They don’t have a page type
  * We care most about the things in the list above, but there’s a long tail outside it
  * In terms of discoverability, hard to find page types
  * Need to be careful with page types, to capture large distinctions, but not have like 4000 different page type
* In the metadocs should have one page which explains what each page type is, and a link to its template
* Doing page type work for CSS, became much more obvious that its hierarchy is very weird
  * Lots of it is very flat, but some of it isn’t
  * Page types really help breaking this up, and ensuring there’s no miscellaneous bits
* BCD: should we bring (page) types into BCD, page types work helps us to think what kinds of types we’re thinking about
  * Implicit link anyway, pages with a page type may already have a BCD entry, and there should be a link back
  * Guide/landing page don’t, others are a bit random
  * But CI could help: “if you have a page type which is an interface, it must have a BCD entry/spec link too”
  * That’s where we want to get to eventually

### Next steps?

* Question: we have a few more to do, but what would be the next step after?
  * Link from page types to template
  * Having CI
  * Making tool to generate templated page?
    * Yes, work planned
    * Nuxt have a [command line tool](https://nuxt.com/docs/api/commands/add) which does something like this already, something to look at for inspiration
  * From a UX perspective, this information could show up in different places in yari, distinguishing between different page types visually
* When you create a ref for a web api, it’s easy to forget to create the other pages for each method/property
  * If we’re talking about tools, would be nice to generate these from the tool as well
  * Other connections are interesting and easy to forget, such as permissions policy
* This is a project with multiple expansions, is this being tracked?
  * Not yet, in our “brains” currently, but not anywhere concrete
  * We should do it!
  * Right now we’ve done the low level stuff, now we can start to think about doing things as a result

### Rollout and throw CI errors?

* What kind of rollout is anticipated?
  * In the future trying to commit something without a template will add a warning, use this to incrementally start fixing things that don’t adhere?
    * Yeah
  * CI can a bit contributor hostile
    * But we could separate checking on existing and new content
  * Does CI means locally, or on github actions?
    * It’s nice to be able to run it locally, and be 99% sure that what you commit will “make it” on github
  * CI doesn’t have to be contributor hostile, language could be more welcoming, has to be considered as part of the contributor experience
    * Flaws don’t seem to put off contributors that often
    * But, warnings should be errors, things should be enforced in general, but need to get to a certain state to enable this

### Structuring content

* To Florian D, IA means I can safely navigate through MDN
  * E.g. Webassembly, this doesn’t seems like it exists properly on MDN, looks like there’s not much, but if you know where to go you do actually find all the content
  * Can we move away from our very flat hierarchy, adding another layer to make this a better UX
  * Kadir: yes! Discussion from yesterday about web platform, presumably nobody disagrees about another layer, but how do we get started on this?
    * Will: but there’s still a need for the “Javascript” section, and here’s the “CSS” section, we don’t want to lose this just for sections about features
    * Key problem to solve: content is a hierarchy, but feature groups are not, but how do we map the latter to the former
      * If we have content in “two places” how do we display this, need to solve this to solve that
    * Original point of Learning area because it was too complicated to understand how to move from each area to another for a single feature
  * [https://developer.mozilla.org/en-US/docs/Web](https://developer.mozilla.org/en-US/docs/Web)
    * Hierarchy feels very odd here
    * Over the years people came up with random groups and groups based on what feels important
      * E.g. fullscreen api within game group
  * Ruth: regardless of how we end up structuring things, we’ll still encounter the problem where when we look from a users perspective, a 2d structure will never work
    * Thinking back historically, the weird sections exist because we had this structure of separating by technologies, but this thing exists across technologies, so where do we put this?
    * These things are broken, not because people did stupid things, but they did the best they could at the time

## Action Items

1. Finish adding page types to all pages
2. Investigate if we need a "catch-all" page type
3. Link from page types to templates
4. CI tooling
5. Tool to generate templated pages
6. Investigate if an how to show page types visually to readers