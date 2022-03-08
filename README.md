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

[A Practical Project management in excel spreadsheets](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;a_practical_project_management_in_excel_spreadsheets.4055682.html)
> 

[Learning Spring Security Fundamentals](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;learning_spring_security_fundamentals.4055639.html)
> 

[Amazon Web Services (AWS) with Python   Boto3](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;bonnytuts&#x2F;amazon_web_services_aws_with_python__boto.4055631.html)
> 

[Communication Skills to Attract, Impress   Convince Anyone](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;communication_skills_to_attract_impress__convince_anyone.4055482.html)
> 

[Bass Lessons For Beginners Musicians](https:&#x2F;&#x2F;sanet.st&#x2F;blogs&#x2F;tomorrowland2&#x2F;bass_lessons_for_beginners_musicians.4055480.html)
<!--END_SECTION:example-->

> This started as a little proof-of-concept for @brianlovin!
