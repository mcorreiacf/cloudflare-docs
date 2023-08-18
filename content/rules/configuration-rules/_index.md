---
pcx_content_type: concept
title: Configuration Rules
weight: 7
layout: single
meta:
  title: Configuration Rules (beta)
---

{{<beta>}} Configuration Rules {{</beta>}}

Configuration Rules allow you to customize certain Cloudflare [configuration settings](/rules/configuration-rules/settings/) for matching incoming requests.

The configuration rule expression will determine to which requests the rule settings will apply. For more information on expressions, refer to [Expressions](/ruleset-engine/rules-language/expressions/) and [Edit expressions in the dashboard](/ruleset-engine/rules-language/expressions/edit-expressions/).

{{<render file="_rules-requirements.md" withParameters="Configuration Rules require">}}

---

## Availability

The number of available configuration rules varies according to your Cloudflare plan:

{{<feature-table id="rules.config_rules">}}

## Order and priority

Configuration Rules are unique, unlike Page Rules. This is how they are applied:

1. Configuration Rules are stackable. This means that multiple matching rules will be combined and applied. So if multiple configuration rules match the same URL, then the features set in those configuration rules will all be applied. If several matching rules set a value for the same setting, the value in the last matching rule wins. For an example of a similar scenario where multiple rules match, refer to the [Origin Rules FAQ](/rules/origin-rules/faq/#what-happens-if-more-than-one-origin-rule-matches-the-current-request).

2. For conflicting settings (for example, SSL/TLS encryption mode set to Off versus set to Full), the last matching rule wins. For example, if Configuration Rule #1 is set to SSL/TLS encryption mode Off on `example.com/ssl` and Configuration Rule #2 is set to SSL/TLS encryption mode Full on `example.com/ssl`, then SSL will be set to Full for all URLs that match `example.com/ssl`, since rule #2 is the last matching rule.

3. If you have Page Rules implemented for configuration on the same path, Configuration Rules will take precedence by design.

## Execution order

{{<render file="_product_execution_order.md">}}
