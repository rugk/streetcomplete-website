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


### Coding style

#### General

* Pay attention to accessibility.
* Test every regular expression you create on <https://regex101.com/> and paste a link to the test into the source code.  
  *Exception:* Easy regular expressions used in CSS selectors.

#### Liquid

* As for indentation of the Liquid syntax I recommend to either use 4 spaces or use the default indentation of the current file you are editing for practicability reasons.
* Do translations in the following way: `{{ t.TransEntry | default: tfb.TransEntry }}`. This provides a fallback if to the English translation if the translation cannot be found.
For translations of data read from another YAML file, please use another fallback: `{{ t.[mydata.entry] | default: tfb.[mydata.entry] | default: mydata.entry }}`. This ensures that the latest fallback uses the RAW data, so that one may also do not use translations in YAML files.

#### HTML

* Do not use [target="blank"](https://css-tricks.com/use-target_blank/) unless you have good reason to do so.
* Use 4 spaces indentation.

#### CSS

* Use 2 spaces indentation.
* Do not use inline CSS for CSP-compatibility.
* Use SCSS extend instead of mixins (via include) when possible. See [this explanation](https://css-tricks.com/the-extend-concept/) (I know that's sometimes difficult...)
* Do not use `!important`. (The print stylesheet is an exception.)
* As it can be seen in the config files of the css linters, my sort order is SMACSS. You can find [the source here](https://github.com/sasstools/sass-lint/blob/ccce21aff8daa13e0078bbc1ffcd34489f25b896/lib/config/property-sort-orders/smacss.yml).

#### JavaScript/jQuery

* Do not expect visitors to have JavaScript enabled, provide fallbacks if possible. *Note:* I know this is possible in almost all cases. However users without JavaScript should only experience a slightly different website with less effects, but all core features still have to be accessible for them.  
  An example can be seen at the title (header) on the font page. You can even trigger the fallback by double-clicking on it, which will reload the site.
* It is not necessary to use "this" when you want to refer to the parent object of the functions as the Revealing Module Pattern is used. Only use this if you actually want to do something with a DOM element when the method handles an event.
* Use 4 spaces indentation.
* Do not use inline JavaScript for CSP-compatibility.
* Use [jsdoc](https://en.wikipedia.org/wiki/JSDoc) to document functions and modules.
* Do follow all basics [code organization concepts](https://learn.jquery.com/code-organization/concepts/).
* [Do not use `return false;` for ignoring the default browser behaviour.](http://fuelyourcoding.com/jquery-events-stop-misusing-return-false/)
* Avoid anonymous functions. Only use them if they are very short and describing/wrapping their behaviour would make no sense. And especially [do avoid binding them](https://learn.jquery.com/code-organization/beware-anonymous-functions/) to any event as unbinding is tricky.
* Use feature-tests where possible instead of adjusting the behavior to devices or browsers.
