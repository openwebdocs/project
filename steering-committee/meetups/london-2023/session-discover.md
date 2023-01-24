# Deep dive session: Discoverability

## Goal

* Find ways how users can better discover content like
  * in-page navigation, sidebars and IA, search
  * the content part of it: page visual cues: what the content is about, and what it relates to.
* Better convey to use what to expect from a page
* Better lead user to related topic, through See also/Related content section (like text_underline, …)
* How to present requirement needed for a specific feature to be used (like cross-origin constraints, …) or prerequisite (what knowledge is needed

## Discussion questions

* Is there a way to better link content without author intervention (automatically)

## Minutes

* (Florian S) Not sure I like the ‘See also’ terminology. "Related content" is better.
* (Dominic): See also seems like an anti-pattern as you delegate to the user to follow it: it pushes work to the user when extra work on the page would have made the page directly useful
* (Florian S) Position of the See also: at the end? (Estelle): I include the link in the page and in the see also to prevent people leaving the page too early. But not everybody write them the same way: two ways:
  * Just links
  * Full sentences
* (Patrick) We want them to bring them to the information from 0 to the item without interruption
* (Will) a link? I click on it and finally get lost (Florian D) we can technically now have hovers (Ruth) there was some accessibility issues (mobile, …)
* (Ruth) Information architecture
  * Sidebars
  * Breadcrumbs
  * An exposed journey (Know where they are and dead ends)
  * Linking content (See also)
  * Visually represent page type
* In-page
  * H3 in TOC
  * Scroll to top
  * Traffic light System (BCD)
* Search
  * Improve search
  * Improve 404 page
* (Dipika) Please H3. But we have to improve our headings
  * H1 is lost. It means we have only one level to express information
* Having we talk to users; do we have any feedback
* (Chris) web.dev/developer.chrome.com has a long list to navigate into a page
* (Leo) Is there a problem? We are always in MDN so we want context, but a regular user comes from time to time and we need to keep the table of content.
* (Will) there are very few (20-40) pages where the table of contents would be really long.
* (Guy) Do you want to have something nested that can expend
* (Florian) We will not solve it today, we need to ask users.
* (Ruth) Other things around?
  * (Chris) Interactive examples on APIs? The more we can do, the better. (Ruth) we are almost there
  * (Chris) Traffic lights: that has been a lot of discussion about it! (Vinyl) They have to scroll down and read complex date. A traffic light system would be useful
* (Florian) Do we mean that discoverability is to discover things faster, or to discover more things?
  * Do you want your users to spend more time on the site or to find the information quicker.
  * (Chris) it depends on the type of content (guide vs reference)
  * (Florian) We have the action-driven reader (come and leave) and the analytic-driven readers (come, learn all, leave)
  * (Dipika) But they don't need to read the page (Kadir) They do. They start to read, then discover they can use it and this is frustrating (Florian M) One click for an immediate info is already to much.
* Retention (Florian) It is ambiguous: is it because it is interesting, or is it because they don't find the info. Thanks to page-type we can have better granularity to better understand such metric.
* (Brian) Can we measure "task completion" with thumb up/down. And having this very open so not to lead them into a specific direction.
* (Leo) what is the KR for retention (Ruth): Retention.
* (Janine) we can divide retention between type of users (new user, returning users) as they may not have the same goal (if they come back, they want to dive deeper)
* (Chris) For the TLS, can we add also secure context only. Could this fix the 5-6 banners at the top. (Florian) Permission, CORS, Secure context. Are all security-related. We have a discussion about how to represent them in front-matter. They are a bit separate. (Dominic) but they are prerequisites (Florian) We first need to collect the data for security, before displaying them!
* Sidebars (will) do we have time to discuss them now or not
  * (Will) KS is  not the way of doing.
  * (Florian) Sidebars are awful (difficult to find information.
  * (Leo) Sidebars are more of a product question rather than an IA question. Shouldn't we first start on IA before coming to sidebars and co question.
  * (Ruth) you cannot sandbox between content /product so we need ot talk together.
  * (Leo) Product needs are fundamentals (via user research) that should helps content. But should we work on discoverability this year, or do we have time this year to do the ground work about user research
  * (Florian M.) Sidebars could be just the folder structure. It works for a lot of large sites. ´
  * (Ruth) But this is what we discussed in the last session and is how we can map the structure into a tree structure. Is it possible or not.
  * (Florian S) At first this doesn't look possible, but we have to see what the work from Kadir and Daniel Beck could help this.

## Action items

1. H3 in TOC: user research and collecting our opinions.
2. Enabling / Experimenting with a feedback mechanism (task completion) on MDN
3. Data about dead-ends (orphaned content)
4. Define prototypes
