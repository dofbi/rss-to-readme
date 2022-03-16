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

[Critical skills for New Managers](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;critical_skills_for_new_managers.4063374.html)
> 

[Advertising Photography Tutorial: Shampoo and Soap Bubbles](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;advertising_photography_tutorial_shampoo_and_soap_bubbles.4063257.html)
> 

[Pet Portraits: Capture Studio-Quality Photos of Your Pet](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;pet_portraits_capture_studio_quality_photos_of_your_pet.4063252.html)
> 

[Figma Prototyping   Animations: Design Interactive Prototypes](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;figma_prototyping__animations_design_interactive_prototypes.4063250.html)
> 

[Watercolour Illustrations: Based on Client Requirements](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;watercolour_illustrations_based_on_client_requirements.4063247.html)
<!--END_SECTION:example-->

> This started as a little proof-of-concept for @brianlovin!
