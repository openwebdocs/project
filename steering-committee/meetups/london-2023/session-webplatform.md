# Deep dive session: Web Platform feature grouping

## Minutes

* Simplified features status discussion
  * How do we give developers a clear signal at the top of the page about the implementation status of a feature, so they don’t have to decipher the BCD tables?
* Feature hierarchy for the Web Platform
  * As part of the simplified feature status, we’ll be developing a feature hierarchy that looks at features across technologies, that might also be used to drive discoverability (eg side bars on MDN)
* **Dom**: MDN describes a subset of the web platform. Because the WP is evolving, MDN needs to reflect that reality:
  * Keeping track of the changes, documenting things that are coming, integrating our processes with the specs, compare what’s in the specs with what’s in MDN (e.g. diffing webref and MDN or BCD.
  * [https://dontcallmedom.github.io/mdn-gaps/](https://dontcallmedom.github.io/mdn-gaps/)
  * How do we present the platform, split it into pieces that users can make sense of (not just all 13,000 pieces that are in BCD). Right now MDN takes a very granular approach. But Web DX tries to organize things into higher-level things called “features”. MDN can organize its content to reflect this. It is a 2-way communication as well, since in some ways MDN has a better grasp than the standards authors of how web devs understand the platform.
* **Kadir**:
  * In every survey, keeping up with changes to WP is a top pain point. Devs have to update when the platform changes but also have FOMO.
  * WP is multi-vendor, moves forward in fits & starts.
  * Important to give clarity about what is and isn’t available, and for that we need to refer to things. e.g. “CSS Grid” - what is actually included in this?
  * Currently caniuse (500 high level features) and BCD (13,000 low-level features) are the methods for this. We need both high and low level views!
  * So can we have a feature hierarchy to represent WP features. Make an ontology for the WP, that we can use in different contexts. e.g. chromestatus wants to refer to features.
  * Daniel and François have been working on this. [https://github.com/web-platform-dx/feature-set/blob/main/towards-features.md](https://github.com/web-platform-dx/feature-set/blob/main/towards-features.md)
  * Simplify BCD tables to provide a summary high level compat statement.
  * Two pieces:
    * Feature hierarchy
    * How to present this to users (currently BCD tables)  
* **Daniel**:
  * [https://github.com/web-platform-dx/feature-set/](https://github.com/web-platform-dx/)
  * Some features are really collections of things, but some cross over or are deeply nested structures.
  * e.g. we can talk about “CSS Cascade Layers”: [https://github.com/web-platform-dx/feature-set/pull/40/files#diff-1b4c86b9736d7ea20093289b00b4b9cd2f4ed04257e080ee10633e8186950349](https://github.com/web-platform-dx/feature-set/pull/40/files#diff-1b4c86b9736d7ea20093289b00b4b9cd2f4ed04257e080ee10633e8186950349) 
  * [https://github.com/ddbeck/common-web-feature-mockup](https://github.com/ddbeck/common-web-feature-mockup)
  * Can generate support summaries from the definition of a feature: [https://github.com/ddbeck/common-web-feature-mockup/blob/main/query-results/array-relative-indexing.json](https://github.com/ddbeck/common-web-feature-mockup/blob/main/query-results/array-relative-indexing.json)
  * Get high level views of what a feature is composed of and when it is shipping in all/any browsers.
  * Want to work with people to present this to web developers.
* **Robert**: what are people’s impressions of this?
  * Dipika: It’s calling an overarching guide a “feature”. The way we present it to developers should be clear and not confuse them more.
  * Vinyl: we could have a switch on the website which lets people see the detailed compat.
  * Florian D: Not sure how it fits right now into the existing content. It seems that there’s something between guides and reference.
  * Ruth: at the moment MDN keeps guides alongside reference and breaks down when features cross over.
  * Dom: this ontology can be used to provide structure and consistency among the IA. MDN can also give feedback when the structure does not make sense.
  * Daniel: when this is presented to people they find new uses for it, outside the narrow compat usage.
  * Patrick: worked in 2 APIs on MDN recently, and realized that the API page is not an API, it is a feature including (e.g.) CSS. We need to call it an API because there is nowhere else to put it on MDN. So in some ways API overview pages are feature pages.
  * Jean-Yves:
    * we have caniuse (high) and BCD (low), maybe there are more levels.
    * The ontology may change over time (e.g. now we talk about Grid and Subgrid, but maybe eventually we will only talk about Grid). So how will this evolve over time?
  * Kadir: yes, it needs to evolve. For example, array methods: when new ones are added, does this mean we can’t use array any more? So there is an ontology piece but also an availability piece. When do people think of something as available (part of the web platform)? Most people have to support browsers going some number of versions back. This is the baseline, and changes as browsers release new features. Post-IE, it is not static, and this makes life harder for developers. So we need to define and represent this baseline, in which most people can use it most of the time. e.g. major browsers going 2 versions back.
  * Estelle:
    * not sure how we will define the baseline. Maybe multiple baselines for large corps, and for governments, and for average web devs.
    * Module pages could be a place to represent readiness.
    * A lot of people don’t know features exist. Technical summary is possibly a place to put it
  * Kadir: re multiple baselines: some users (like frameworks) don’t know who their users are, so can’t choose a baseline.
  * Robert:
    * How much do devs care about compat? For many orgs it is more cost-effective to ship and fix breakages.
    * Baseline and grouping is on tech features, but also consider use cases (e.g. I want 3-column layout, I don’t care about the tech.
  * Florian S:
    * Would be important for MDN to scrap e.g. groupdata, and it needs to be in some day-to-day workflow, so they are maintained properly.
    * Sidebars and see also could be generated (related content).
    * Maybe have static analysis to see where your site is at wrt the baseline.
  * Will: for sidebars, if a subfeature can live in >1 feature, which feature do you show in the sidebar?
  * Dom: all of them.
  * Ruth: timeline/resources?
  * Robert: good to understand cost for MDN at the start.
  * Kadir: place for prototyping to figure out if this can be useful and if so where. Then if we think it is useful: scale up, and then resourcing becomes an issue.  So perhaps we can spend time workshopping these questions. Two areas to prototype:
    * Prototyping of ontology development is essential to get feedback about how it can be useful or it calcifies.
    * Also for displaying summary info to developers (the old traffic light system).

## Action items

1. Prototype of ontology development
2. Prototype replacing groupdata with feature-sets
