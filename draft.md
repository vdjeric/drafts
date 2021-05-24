# Clarity on Flow’s Direction and Open Source Engagement

*Summary: Flow prioritizes the Facebook codebase’s need for more type safety and fast performance on very large codebases. Flow’s over-arching philosophy is evolving beyond just “JavaScript with types” and we will be adding new language features including new syntax that goes beyond type annotations to address internal users’ evolving needs. We are also making changes to how we engage with open source. Read on for more details.* 

## Flow’s Latest Features

Since the [last open source update](https://medium.com/flow-type/what-were-building-in-2020-bcb92f620c75) a year ago, Flow has shipped many enhancements:

* A new architecture called [Types First](https://medium.com/flow-type/types-first-the-only-supported-mode-in-flow-jan-2021-3c4cb14d7b6c), which drastically improved performance 
* [More specific errors](https://medium.com/flow-type/making-flow-error-suppressions-more-specific-280aa4e3c95c) - both by adding error codes, and making errors suppressible only at their primary location 
* [Improved handling of generics](https://medium.com/flow-type/flows-improved-handling-of-generic-types-b5909cc5e3c5)
* Enhanced IDE features, including:
    * Function signature information on hover and autocomplete
    * Go-to-definition and autocomplete improvements
    * JS doc-comment display on hover and autocomplete
    * Auto-imports and global autocomplete (behind the `autoimports` flag)

This work aligns with our three focus areas: improving performance at scale, increasing type-safety, and enhancing the IDE experience. These will continue to be our focus areas in the future.

## Changes in Flow’s Priorities

Flow is almost exclusively developed by a 10 person team within Facebook, and our primary customers are Facebook engineers who use Flow. Internally, we have tens of thousands of developers who write JavaScript, including one project with tens of millions of lines of code. The team’s priority is the needs of our internal Facebook customers.

When Flow started, Facebook’s internal JS codebase had no types. The top priority was to enable types to be added to the codebase in a gradual and easy way. To ease adoption of Flow, we made design choices that hurt scalability (e.g. relying on global inference which does not require type annotations at module boundaries) and hurt type-safety (allowing untyped code and `any` types).

Today, almost every JS file in Facebook’s codebase has Flow enabled, and over 90% are at the higher [Flow Strict](https://flow.org/en/docs/strict/) standard. With this evolution of our codebase, we have changed the trade-offs Flow makes. A high degree of internal Flow adoption means we can now focus on increasing type-safety and predictability. Doing so means limiting the kinds of programs Flow allows, including restricting otherwise valid JS patterns to increase the safety and predictability of our overall system. High internal adoption of Flow types and rapid growth of our codebase also means that we have to emphasize scalability. These choices might make Flow more intrusive (for example, asking for more type annotations) to use on external projects that don’t have the same needs, like small projects or projects that interact with untyped code. 

Large, complicated codebases not only require good performance, but increased type-safety and developer ergonomics. While so far Flow has de-facto been just “JavaScript with types”, this is not a guiding principle. In the next year, we will introduce new language features, including new syntax that goes beyond type annotations, to address our users’ evolving requirements. Stay tuned for more details.

## Flow Open Source

The fast growth of Facebook’s internal JS codebase and the great demand from our internal users mean that sadly we do not have resources to work on features requested only by external users. We also handle a very large amount of internal support requests, so we also do not have the resources to respond to all external Github issues. This lack of resources manifests as regrettably long response times to GitHub issues and PRs.

Going forward, Flow is staying open source and we will be happy to review pull requests that improve library definitions and website documentation, but we may not be able to accept PRs from external contributors for Flow itself if the PRs don’t align with our priorities. The complexity of Flow’s codebase makes it difficult for external developers to contribute to Flow itself and it is very time consuming to review such pull requests, so we may close PR’s that don’t align with our internal priorities. Similarly, we will close GitHub issues when we know we will not be able to provide timely support for external users.

We realize this change may make Flow less suitable for use in some external projects, but if you use Flow and align with our focus areas of type-safety, scalability for very large codebases, and an enhanced IDE experience, Flow may still be the right choice for your project.

Finally, we want to give a shout-out to the hardworking maintainers of [flow-typed](https://github.com/flow-typed/flow-typed) who maintain community type definitions for third-party libraries! The `flow-typed` community-led model has proven itself very effective, so we will investigate moving more of our builtin type definitions (DOM, Node, React, etc) to `flow-typed` to enable the open-source community to depend less on Flow’s release cycle and Flow team’s review & approval process.

## Next Steps

In the past year, Flow has shipped a variety of new improvements. We will continue to focus in the coming year on improving the IDE experience, increasing type-safety, and enhancing performance for large codebases. Soon, we’ll share more details of some of the exciting new projects we have been working on. 

