# Deep dive session: Content

## Description

* Guides: focus on what guides we have and where they should fit
* Upcoming content: what do we want to do?
* Out of date content

## Minutes

### Browsers and versions

* Should try not to keep compat data in content, but if we have to, keep it in the BCD section. When we want to make {{Compat}} redundant, we will only have “Browser compatibility” H2 in this situation).
* How far back should we note compat issues? Browser versions, or time. We use time for dropping docs (not supported in 2 years).

### External links

* Estelle: should add dates to external resources so we know when they are out of date. At what point do we remove notes about old browsers versions (e.g. supported since Fx 4).
* Ruth: we already have guidelines for this, compat should be in BCD only. But sometimes compat is too nuanced to keep in BCD - maybe prose is OK but only in Browser compat section
* Patrick: MS has tools to help look for this kind of content (like mentions of Firefox versions). Also has a date in front matter that’s manually maintained for “last substantive change".
* Dom: can say: in front matter of page: this page will need revision when some condition happens, and tooling can alert us when this happens.
* Ruth: external links audit. Some domains are always OK. Once we have audited links we can check new external links. Check links that now redirect somewhere else.
* Could annotate links as “last checked at”, or when it was written, or when it was added.

### Sunsetting strategy

* Games
* Server-side tools and testing (including Express, Django, React etc)
* If analytics shows that people use it we should probably not delete it.
* Could say we are considering sunsetting, and maybe people will offer to maintain them. But need to understand cost of maintaining them. Dipika: but we still need to approve changes.
* Games: we don’t like it because it is out of date. Dom: tutorials that haven’t been updated in 5 years are certainly out of date.
* Makes sense to have some content about games that points people to resources, but Games docs is too much.
* Look at how old it is, ask our users, but we might not reach the right people.
* Community engagement strategy must depend on what we want and what we think the community is likely to do.
* When we remove content we need to redirect somewhere. Not just 404. Like with firefox-source-docs. Estelle: could have custom Games page for this.
* Dipika: 2 things:
  * Things we don’t want
  * Things we want but don’t/can’t maintain

### Updating content

* SVG updates are blocking on attributes
* Ruth: the way we do attributes is OK. Will: it is confusing that we have attributes in three places. 
* JYP: attributes should be in the attribute pages (or below them). Estelle: but it gets repetitive. Ruth: even global attribute might have different meanings for different elements.
* JYP in SVG many attributes are the same on 5 or 6 elements, which is less the case in HTML. Want to avoid one page per attribute name systematically, or that page gets very confusing. Estelle: some attributes need their own page (e.g. step)
* SVG definitely on the table for updates. Could hire someone. Could break it up into pieces (e.g. summary of all SVG elements in a page).
* Have we thought of cheatsheets? We haven’t done it although we have talked about it. Tricky in the context of our pages. Good for social media. Could try this with Josh’s regex work.
* PWA proposal: [https://github.com/orgs/mdn/projects/26/views/8?pane=issue&itemId=15979055](https://github.com/orgs/mdn/projects/26/views/8?pane=issue&itemId=15979055)
  * Could benefit from SMEs from several different orgs, including Patrick 
  * Two ways to work with SMEs
    * Writer writes, having talked to SME
    * SME writes, writer reviews and cleans
* Dom’s script to identify content gaps: how can we integrate this into roadmapping?
  * [https://dontcallmedom.github.io/mdn-gaps/](https://dontcallmedom.github.io/mdn-gaps/) 
  * Yes, if there’s a whole section, it’s a larger project, or there are just issues for individual gaps.
  * Could automate it. (AI)
  * Could annotate it with projects that are already in the backlog. (AI)
  * Could then just take a few hours to generate projects (AI)
  * Do we also need a diff, to see which we have already triaged?
* Patrick: how do we work with browser vendors: Ruth: so far only Firefox. Also Chris is writing up Chrome Web APIs. Patrick: for Edge, he is flagged when new features land, and will document them on MDN.

### Sidebars

* (Will) 2 problems: how are they authored
* How are they generated
* What do they look like / What is in them (UX)
* LIKE:
  * Different sections
* DON'T LIKE
  * Expanded by default
  * Long
  * Redundant (Array.prototype)
  * Too many macros
  * INCONSTISTANCY
  * (Related topics at the top)
* IDEAS
  * Short title
  * Icon after link
* Leo: WHY, WHY?, WHYYYYY?
* (WIll) How big should they be?
* How many different sidebars should we have? Do we expect them to be all the same
* Nesting
* Examples of good sidebars
* (Dominic) What is used for:
  * To give you sense where you re
  * Helps you finding other topics
  * They should be driven by user needs and not by what we like
* (Patrick) When you are on MDN you are on a journey, but none of breadcrumbs and sidebars provide this. Should we have small sidebars, but we should make sidebar be redundant, and maybe stay.
* (Bryan) More levels, a tree?
* (Leo) I like the .Net sidebar search feature (less powerful than the site sidebar), but allows you to find info in the sidebar without losing the context
* (Florian D): do we want to have one sidebar for all, but that's all a yari's nightmare (downloading the same content again and again)
* (Will) I like sidebars that doesn't change too much on me, but that may be difficult
* (Ruth) Do we want sidebars to reflect the folder hierarchy, or do we want to author them.
* (Florian) But the web platform is a collection of interface and entities independently from where they are. I don't want to bother to know where they are.
* (Florian) Performance API is cut into 5-6 groups which doesn't make sense. (Will) but that's curation (All) Yes.
* (Jean-Yves) Can we measure how our users are using CURRENT sidebars? (Ruth) Would be a good idea. (Florian D) We need a precise question to add telemetry (possible and happy to do it). It should be intentional measurement.
* (Leo) Having one single sidebar seems to be leading to a lot of problem. And small sidebars (API/JS) seems better because they are smallish and have context.
* (Dipika) Should we interview users? (Florian D.) Not enough constrained, will depend a lot from the context and it will be very hard to have something out of it.
* (Ruth) what about feature at different places
* (Patrick) What about having sidebars that are different on the same page depending on where you come from.
* (Florian D.) if you lose context, make it explicit in the link (Florian): if you go to the LA, indicate it in the sidebar
* (Dipika) Maybe we ask too much from sidebars? Maybe make sidebar simpler for navigation and not for other things (like discoverability)

## Action items

1. Remove "related topics" menu
2. Move icon to right
3. Remove the columns in sidebar (inheritance, but also under HTML)
4. Remove inheritance from JS
5. Define metrics for instrumentation
6. Short titles
