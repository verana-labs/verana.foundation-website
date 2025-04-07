---
title: Service Directory and Search Engine
date: 2024-11-05T00:00:00+02:00
subtitle: "Register your Verifiable Service in a Service Directory, and let users find you. Instantly."
comments: false
bigimg: [{src: "/img/triangle.jpg"}, {src: "/img/sphere.jpg"}, {src: "/img/hexagon.jpg"}]
---

## Service Directory

### What is the Service Directory?

The Service Directory is a public database of [DIDs](https://www.w3.org/TR/did-1.0/) maintained in a VPR, that can be used by crawlers to index the metadata of the VS provided by these DIDs.

Search engines simply need to iterate over the Service Directory and index VSs based on VS metadata (DID Document, presented credentials,…) For example, the Service directory is essential to Verifiable User Agents (VUAs), such as social browsers, cdn browsers,… but can although be used by a general classic form-based search engine that would return simple link(s) for accessing VSs.

Any participant can register a DID in the DID directory by executing a transaction in a VPR.

{{< image "/img/diddirindex.svg" "" "max-width: 800px;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 800px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

### Search the Service Directory

Indexer can be run as a container with a locally deployed VPR node. It is then easy to deploy the search engine and provide a fancy familiar prompt:

{{< image "/img/verana-search.png" "" "max-width: 800px;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 800px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

**Great to know**: results are not biased nor manipulated 😀, because they rely on verifiable data.
