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

[Skillshare - Microsoft Excel - Data Analysis with Excel Pivot Tables](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;training4all&#x2F;skillshare_microsoft_excel_data_analysis_with_excel_pivot_tables.4068590.html)
> 

[Graphic design with canva: beginner to pro](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;exclusivetutorials&#x2F;graphic_design_with_canva_beginner_to_pro.4068587.html)
> 

[Microsoft Excel | An Aspirant&#39;s Guide](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;exclusivetutorials&#x2F;microsoft_excel__an_aspirants_guide.4068582.html)
> 

[Sketchbook 101: Start a Sketchbook](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;training4all&#x2F;sketchbook_start_a_sketchbook.4068580.html)
> 

[Watercolor a Seamless Pattern: Surface Design in Adobe Photoshop for Print-On-Demand](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;training4all&#x2F;watercolor_a_seamless_pattern_surface_design_in_adobe_photoshop_for_print_on_demand.4068570.html)
<!--END_SECTION:example-->

> This started as a little proof-of-concept for @brianlovin!
