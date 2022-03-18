<h3 align="center">📡📝</h3>
<h3 align="center">RSS to README Action</h3>
<p align="center">A GitHub Action that updates a section of a README from an RSS feed.</p>

---

## Usage

You can use this action in a workflow file like any other:

```yml
name: Update this repo's README

on:
  schedule:
    # Once a day at 8 AM
    - cron: 0 8 * * *

jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: JasonEtco/rss-to-readme@v1
        with:
          feed-url: https://jasonet.co/rss.xml
          readme-section: feed
```

### Options

#### `feed-url`:

The URL to an RSS feed. It's assumed that the RSS feed follow the standard format!

#### `readme-section`:

The name of the section of your README to update. This uses [`JasonEtco/readme-box`](https://github.com/JasonEtco/readme-box) to replace a section of the README and update the file. Your README should contain HTML comments like this, where `feed` is the the value of `readme-section`:

```html
### Example RSS feed:

<!--START_SECTION:feed-->
...
<!--END_SECTION:feed-->
```

You can inspect this repo's README to see it in use!

#### `max` (default: 5)

The maximum number of items to show from the RSS feed. Defaults to `5`!

#### `template` (default: `"* [{{ title }}]({{ link }}))"`)

You can provide a [Mustache](https://github.com/janl/mustache.js) template to use when rendering each item in the feed. These will be joined by a newline (`\n`). For example:

```yaml
- uses: JasonEtco/rss-to-readme@v1
  with:
    feed-url: https://jasonet.co/rss.xml
    template: "> {{ excerpt }}\n\n[Read more!]({{ url }})"
```

#### `branch` (default: github.repository.default_branch)

You can provide the target branch to update instead of the default.

#### `path` (default: 'README.md')

Path to the README file to update.

### Example RSS feed:

<!--START_SECTION:example-->
> 

[Weatherby Photography - Shooting Panoramas](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;weatherby_photography_shooting_panoramas.4065123.html)
> 

[The Right Trade - Day Trading Futures](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;the_right_trade_day_trading_futures.4065120.html)
> 

[Certified Blockchain Solutions Architect (CBSA)](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;certified_blockchain_solutions_architect_cbsa.4064957.html)
> 

[Software Testing Life Cycle](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;software_testing_life_cycle.4064952.html)
> 

[Salesforce Flows - Learn Salesforce Lightning Flows Fast](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;salesforce_flows_learn_salesforce_lightning_flows_fast.4064941.html)
<!--END_SECTION:example-->

> This started as a little proof-of-concept for @brianlovin!
