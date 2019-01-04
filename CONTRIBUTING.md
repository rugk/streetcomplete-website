# Contributing

Nice you want to contribute. If you submit more than a few typo-fixes you can also add yourself to the humans.txt.

## Content

If you find a typo, a grammatical or spelling mistake feel free to fix it. Also all other useful text changes are very appreciated. To find the text snippet you are looking for, here is a small overview over the structure of this repo:

* `_data/`
  * `locales`   - the translations/languages for the website
* `_includes/`  - HTML parts of the website. Here you can also find the `index.html`.
* `_layouts`    - Layouts for different parts of the website.
* `assets/`
  * `_sass`     - CSS snippets
  * `css`       - CSS files, which include things in `_sass`.
  * `fonts`     - Well... fonts.
  * `img`       - You guess it...
  * `js`        - JavaScripts for the site, including libraries.
* `pages/`      - The different pages of my site, localized in the given languages.

Of course you can also edit this Markdown files.
Write keys (in YAML for example) in camelCase for consistency.
When adding PNG or JPG images, please compress them with services such as https://tinypng.com/ before.

# Translating

Translations are saved in [`_data/locales`](_data/locales). You can use the English version [`en.yml`](_data/locales/en.xml) as a template. The used syntax is [Yaml](http://www.yaml.org/). Theoretically you could use a different syntax thanks to the fact that Jekyll parses many different ones, but for consistency I recommend to use only one.

The variable `t` contains the current translated strings.
When including a translation, always include the English fallback:
```liquid
{{ t.siteDescr | default: tfb.siteDescr }}
```

If you want to translate a complete page go to `pages`, copy the existing file, adjust the front matter and translate it.

## Development

### Necessary software

In my [humans.txt](./humans.txt) you can find all software I use. If you're familiar with the used software (mostly only [Jekyll](https://jekyllrb.com/)) there is not much I have to explain.

The generation has been tested with the following Jekyll versions:
* 3.8.5

<!-- ### How to switch to development version
1. Set `JEKYLL_ENV` to "development".
2. This will disable HTML compression. Alternatively set `compress_html.blanklines` to `true` in `.config.yml` to get a nicely formatted output. If you do so either unset the environment variable or remove the variable from `compress_html.ignore.envs`
3. Uncomment `sass.style: compressed` in `.config.yml` to disable nice CSS minification. -->

### Recommend software

All in all many requirements can be automatically fulfilled by using some libraries. Use an editor (or plugin), which supports [editorconfig](http://editorconfig.org/#download) and [sass-lint](https://atom.io/packages/linter-sass-lint). You can also use [remark-lint](https://github.com/wooorm/remark-lint) to check Markdown files. For checking JavaScript please use for code-style checking it use [ESLint](http://eslint.org/). All config files for these tools are included in the repo.

I also recommend you to use a YAML linter. :smile:
