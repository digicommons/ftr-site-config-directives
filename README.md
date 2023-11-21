# ftr-site-config directives
Many of the directives used in [Full-Text RSS](https://help.fivefilters.org/full-text-rss) site config files are not documented. Therefore, I ran grep on the config files in the [fivefilters/ftr-site-config](https://github.com/fivefilters/ftr-site-config) repo to see which directives are in use.

Please feel free to add information on directives and their use.

## Available ftr-site-config directives
> [!NOTE]
> The FTR site pattern docs are available [here](https://help.fivefilters.org/full-text-rss/site-patterns.html#pattern-format).

### Metadata
| Directive | Usage             | Graby support | Description |
|-----------|-------------------|:-------------:|-------------|
| `title`   | `title: [XPath]`  | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#title-xpath)  |
| `body`    | `body: [XPath]`   | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#body-xpath)   |
| `date`    | `date: [XPath]`   | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#date-xpath)   |
| `author`  | `author: [XPath]` | &#9989;       | [body](https://help.fivefilters.org/full-text-rss/site-patterns.html#author-xpath) |

### Stripping, clearing, cleaning
| Directive           | Usage                 | Graby support | Description  |
|---------------------|-----------------------|:-------------:|--------------|
| `strip`             | `strip: [XPath]`      | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#strip-xpath) |
| `strip_attr`        | `strip_attr: [XPath]` |               | See `faz.net.txt` for usage (f.e. `strip_attr: //img/@width`)  |
| `strip_comments`    | `strip_comments: [yes\|no]` |         | See `news.ycombinator.com.txt` for usage.<br> Possibly custom per-site comments parser? |
| `strip_id_or_class` | `strip_id_or_class: [string]` | &#9989; | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#strip-id-or-class-string) |
| `strip_image_src`   | `strip_image_src: [string]` | &#9989; | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#strip-image-src-string)   |

### (Pre-) Processing
| Directive               | Usage      | Graby support | Description |
|-------------------------|------------|:-------------:|-------------|
| `tidy`                  |            | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#tidy-yes-no)  |
| `prune`                 |            | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#prune-yes-no-default-yes) |
| `autodetect_on_failure` |            | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#autodetect-on-failure-yes-no-default-yes) |
| `insert_detected_image` | `yes`/`no` |               | Prevent use of detected image (e.g. logo on article without image). Mentioned [here](https://github.com/fivefilters/ftr-site-config/pull/1251#issuecomment-1817654995) |

### Multi-page articles
| Directive                   | Usage     | Graby support | Description |
|-----------------------------|-----------|:-------------:|-------------|
| `single_page_link`          |           | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#single-page-link-xpath)  |
| `single_page_link_in_feed`  |           |               | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#single-page-link-in-feed-xpath)  |
| `next_page_link`            |           | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#next-page-link-xpath)  |
| `autodetect_next_page`      |           |               | See `jetzt.sueddeutsche.de.txt` for example |
| `if_page_contains`          |           | &#9989;       | Used with single_page_link, see `washingtonpost.com.txt` for example  |

### String replacement
| Directive             | Usage    | Graby support | Description |
|-----------------------|----------|:-------------:|-------------|
| `replace_string()`    |          | &#9989; (?)   | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#replace-string-string-to-find-replacement-string) |
| `find_string  `       |          | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#replace-string-string-to-find-replacement-string) |
| `replace_string  `    |          | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#replace-string-string-to-find-replacement-string) |

### Authentication
| Directive               | Usage    | Graby support | Description |
|-------------------------|----------|:-------------:|-------------|
| `login_extra_fields`    |          | &#9989;       |             |
| `login_password_field`  |          | &#9989;       |             |
| `login_uri`             |          | &#9989;       |             |
| `login_username_field`  |          | &#9989;       |             |
| `not_logged_in_xpath`   |          | &#9989;       |             |
| `requires_login`        |          | &#9989;       |             |

### HTTP headers
See [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#http-header-header-name-header-value), possibly any header.

> [!CAUTION]
> Is this case sensitive?

| Directive                 | Usage    | Graby support | Description |
|---------------------------|----------|:-------------:|-------------|
| `http_header(Cookie)`     |          | &#9989;       |             |
| `http_header(User-Agent)` |          | &#9989;       |             |
| `http_header(accept)`     |          | &#9989;       |             |
| `http_header(referer)`    |          | &#9989;       |             |

### Test-URLs
| Directive               | Usage    | Graby support | Description |
|-------------------------|----------|:-------------:|-------------|
| `test_contains`         |          |               |             |
| `test_url`              |          | &#9989;       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#test-url-string)  |
| `test_urls`             |          |               | Supposedly used with multi-page articles, see `theatlantic.com.txt`  |

### Not documented
| Directive                 | Example                     | Graby support | Description                       | Found in          |
|---------------------------|-----------------------------|:-------------:|-----------------------------------|-------------------|
| `convert_double_br_tags`  | `convert_double_br_tags: yes` |             |                                   | scilogs.de.txt    |
| `native_ad_clue`          |                             | &#9989;       |                                   | buzzfeed.com.txt  |
| `parser`                  | `parser: html5php`          | &#9989;       | Possibly used with `html5php`, `gumbo`, `libxml`. <br> Hint on usage provided [here](https://help.fivefilters.org/full-text-rss/site-patterns.html#tidy-yes-no).<br> Graby [uses](https://github.com/j0k3r/graby/blob/master/src/SiteConfig/SiteConfig.php#L142) either `libxml` or `html5lib`.                                  | nymag.com.txt     |
| `skip_json_ld`            | `skip_json_ld: yes`         | &#9989;       | Explicitly [skip](https://github.com/j0k3r/graby/blob/master/src/SiteConfig/SiteConfig.php#L197) getting data from [JSON-LD](https://en.wikipedia.org/wiki/JSON-LD). | spiegel.de.txt    |
| `skip_id_or_class`        | `skip_id_or_class: Layout-sidebar`  |       |                                   | github.com.txt    |
| `src_lazy_load_attr`      | `src_lazy_load_attr: data-full-src` | &#9989; |                                 | slate.fr.txt      |
| `footnotes`               | `footnotes: no`             |               |                                   | jetzt.sueddeutsche.de.txt |
| `move_into()`             | `move_into([XPath]): [XPath]` |             |                                   | smithsonianmag.com.txt  |
| `wrap_in()`               | `wrap_in([tag]): [XPath]`   | &#9989;       |                                   | smithsonianmag.com.txt  |
| `dissolve`                | `dissolve: [XPath]`         |               |                                   | bbc.com.txt       |
| `span`                    | `span: [XPath]`             |               |??, possibly mistake?              | cloud.google.com.txt  |

### Unsupported by Full-Text RSS (?)
| Directive         | Example                     | Description                       | Found in          |
|-------------------|-----------------------------|-----------------------------------|-------------------|
| `post_strip_attr` | post_strip_attr: //*/@class | "strip all class attributes after processing"  | global.txt |

### Useful XPath snippets
See ["Basics of XPath 1.0"](https://doc.wallabag.org/en/user/errors_during_fetching) in Wallabag docs
- `and`
- `concat`
- `contains()`
- `normalize-space`
- `substring-before`

## To-Do
- [ ] Add section on app support of directives (e.g. "Supported by: FTR, Wallabag etc.")

## Extracting directives
To extract directives from site config files, use:
```
grep -h -o -E --exclude='LICENSE.txt' '^[^#][^:]+:' *.txt | sed 's/:$//' | sort -u > output.txt
```

To search files for occurrence of specific directive, use `grep -rl '^directive' *.txt` in directory with site configs.
