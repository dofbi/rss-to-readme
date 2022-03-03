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

[AWS Glue Studio - A Server less ETL Framework](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;exclusivetutorials&#x2F;aws_glue_studio_a_server_less_etl_framework.4050901.html)
> 

[HTML, CSS, JavaScript and BootStrap for Web designers](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;html_css_javascript_and_bootstrap_for_web_designers.4050866.html)
> 

[Pneumatic System Using Automation Studio 6.4   TIA   OPC](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;pneumatic_system_using_automation_studio__tia__opc.4050856.html)
> 

[Vue 3, Nuxt.js and Laravel: A Rapid Guide - Advanced](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;vue_nuxt_js_and_laravel_a_rapid_guide_advanced.4050790.html)
> 

[ESP8266: IoT Electronics, Programing   Eagle PCB Design](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;esp_iot_electronics_programing__eagle_pcb_design.4050730.html)
<!--END_SECTION:example-->

> This started as a little proof-of-concept for @brianlovin!
