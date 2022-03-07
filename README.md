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

[An Introduction into Designing Cars!](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;training4all&#x2F;an_introduction_into_designing_cars.4054812.html)
> 

[The Video Editing Process for Interviews: Creating the Story Edit](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;training4all&#x2F;the_video_editing_process_for_interviews_creating_the_story_edit.4054777.html)
> 

[Fun and Easy Illustrations in Procreate - Creating Colorful Houses](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;training4all&#x2F;fun_and_easy_illustrations_in_procreate_creating_colorful_houses.4054761.html)
> 

[3D Letters Masterclass for Procreate](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;_d_letters_masterclass_for_procreate.4054727.html)
> 

[Mastering CSS Grid 2021](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;mastering_css_grid.4054718.html)
<!--END_SECTION:example-->

> This started as a little proof-of-concept for @brianlovin!
