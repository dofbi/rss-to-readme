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

[Create Cake E-commerce Website Using Laravel](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;exclusivetutorials&#x2F;create_cake_e_commerce_website_using_laravel.4049902.html)
> 

[Back pain management](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;back_pain_management.4049901.html)
> 

[Pandas The ultimate guide on python pandas for data science](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;exclusivetutorials&#x2F;pandas_the_ultimate_guide_on_python_pandas_for_data_science.4049890.html)
> 

[Successful Software Development in Big Corporations](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;successful_software_development_in_big_corporations.4049878.html)
> 

[MIT Scratch Master Class: Beginner to Advanced level](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;mit_scratch_master_class_beginner_to_advanced_level.4049854.html)
<!--END_SECTION:example-->

> This started as a little proof-of-concept for @brianlovin!
