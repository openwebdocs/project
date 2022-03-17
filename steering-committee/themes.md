# OWD themes / work streams

When deciding what to work on, Open Web Docs has benefits of web developers & designers worldwide in mind and works according to the mission and core values of the [OWD charter](https://github.com/openwebdocs/project/blob/main/charter.md).

Additional high-level criteria for open and sponsor/vendor-neutral prioritization that further guides OWD’s decision-making can be found in the [OWD prioritization guidelines](https://github.com/openwebdocs/project/blob/main/steering-committee/prioritization-criteria.md).

On a yearly basis, Open Web Docs formulates overarching themes (work streams) that put some of our work into broader perspective and illustrates our objectives and goals we try to achieve with our quarterly project work. In 2022 and possibly beyond, our themes are:

* [Improving the quality of MDN's most important documentation](#improving-the-quality-of-mdns-most-important-documentation)
* [Make contributing to MDN more accessible and more productive to more people](#make-contributing-to-mdn-more-accessible-and-more-productive-to-more-people)
* [Offer structured content and data for documentation to be used in multiple contexts](#offer-structured-content-and-data-for-documentation-to-be-used-in-multiple-contexts)
* [Support the Interop 2022 initiative](#support-the-interop-2022-initiative)

## Improving the quality of MDN's most important documentation

MDN is huge but very uneven: some of it is excellent and some is out of date, misleading, or inaccurate. Reference docs are often inconsistently organized, with key information (such as spec references, examples, or BCD) often missing. Code samples are inconsistently formatted and very often do not adhere to our own quality/style guidelines. As maintainers we don’t have tools to track these systemic issues.

We would like to take steps towards addressing this in 2022. In particular we would like to focus on areas of the site that are both *problematic* and *important*.

**Metrics might include:**

* 100% of (JS language only?) code samples in pages are consistently formatted and linted

* x% of pages that should have BCD tables, spec URLs, or examples, have them (prerequisite: we know which sorts of pages should have these, and can track which pages actually do)

* When a feature is identified as experimental/deprecated/nonstandard, the page agrees with status recorded in BCD

* Specific content areas known to be problematic and important (e.g. [privacy](https://github.com/openwebdocs/project/issues/60)) have been revised/rewritten

* Rate of bugs filed against particular areas (specifically bugs about wrong or misleading content) declines

**Work might include:**

* Running Prettier/ESLint on our content in CI

* Having page types describing what pages can/must contain, and tooling to check (also perhaps in CI)

* Generating experimental/deprecated banners from BCD and clean up old and bad content/data (stubs, deprecated browser versions, etc)

* Identifying specific content areas to target and reworking them. Includes measuring bugs to find clusters in particular areas of the docs.

## Make contributing to MDN more accessible and more productive to more people

Contributing to MDN has changed drastically at the end of 2020. The wiki moved into GitHub and the contribution flow is very different from what was in the 15+ years before this change. 

We would like to improve the experience of contributors and communities that contribute to MDN and invite more people to become active contributors.

**Metrics might include:**

* Number of first time contributors is increasing
* Number of unanswered issues is decreasing
* Contributor diversity is increasing

**Work might include:**

* Finish migrating the contribution docs from [https://developer.mozilla.org/en-US/docs/MDN/Contribute](https://developer.mozilla.org/en-US/docs/MDN/Contribute) to [https://mdn-contributor-docs.mozilla.org](https://mdn-contributor-docs.mozilla.org) 
* Update the BCD contribution docs and data guidelines so that contributing to BCD is no longer dependent on expert knowledge.
* Publish prominent articles about MDN contribution elsewhere ([https://www.smashingmagazine.com/2018/05/contributing-mdn-webdocs/](https://www.smashingmagazine.com/2018/05/contributing-mdn-webdocs/) as an example for this)
* Identify interruptions in the workflow of (first time) contributors (how is the github bot perceived and is it helpful?, etc)
* Identify tools to develop that help with contributing to MDN ([https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) is an example for an authoring pack that eases contributions to docs.microsoft.com)

## Offer structured content and data for documentation to be used in multiple contexts

With projects like BCD, mdn-data, and W3C’s webref, we have seen a demand from various people, projects, tools, IDEs, to consume web platform documentation and data in a structured form and outside of the context of the website. 

We would like to further explore and streamline the structured content and data offering and enable more programmatic access to web platform docs.

See also [https://github.com/openwebdocs/project/issues/34](https://github.com/openwebdocs/project/issues/34) for the original proposal of this theme.

**Metrics might include:**

* Increased number of projects that consume MDN docs, BCD data, webref data programmatically.

**Work might include:**

* Fixing page titles
* Introducing MDN page types and BCD data types
* Working with IDEs to identify needs for structured access
* Making the markdown source pure and therefore accessible (no more KumaScript).

## Support the Interop 2022 initiative

Interop 2022 is an initiative by Apple, Bocoup, Google, Igalia, Microsoft, and Mozilla. It is a benchmark to measure interoperability between the major browser implementations focusing on 15 troublesome areas identified by developers. Browser vendors are working throughout the year to improve their score, reflecting a better interoperability between browsers. This involves fixing bugs and implementing new features.

This will lead to new techniques, new good practices that have to be documented on MDN.

Open Web Docs can help this initiative by identifying and fixing relevant areas of documentation. 

**Metrics might include:**

* %-age of interop features documented
* %-age of interop features meeting modern documentation standards/templates
* %-age of interop features providing up-to-date content and compat data.

**Work might include:**

* Assessing the quality of documentation in the 15 interop areas.
* Identifying documentation work needed.
* Updating and restructuring existing documentation in order to showcase the modern way of solving the problem
* Enhancing the reference documentation where needed (adding guides, glossary entries, …)
