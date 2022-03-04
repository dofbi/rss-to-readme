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

[Domestika - Creative Web Design: Planning and Coding from Scratch](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;imfamous&#x2F;domestika_creative_web_design_planning_and_coding_from_scratch.4051909.html)
> 

[How to build and host a WordPress site from zero that loads in less than 1. 5 seconds](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;coursetraining&#x2F;how_to_build_and_host_a_wordpress_site_from_zero_that_loads_in_less_than_seconds.4051887.html)
> 

[Fashion Illustration with Adobe Photoshop](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;fashion_illustration_with_adobe_photoshop.4051658.html)
> 

[Smart Tips: Project Management   Agile](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;smart_tips_project_management__agile.4051649.html)
> 

[Blockchain: Build a Dapp using Solidity, Hardhat and React](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;blockchain_build_a_dapp_using_solidity_hardhat_and_react.4051642.html)
<!--END_SECTION:example-->

> This started as a little proof-of-concept for @brianlovin!
