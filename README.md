# ftr-site-config directives
Many of the directives used in [Full-Text RSS](https://help.fivefilters.org/full-text-rss) site config files are not documented. Therefore, I ran grep on the config files in the [fivefilters/ftr-site-config](https://github.com/fivefilters/ftr-site-config) repo to see which directives are in use.

Please feel free to add information on directives and their use.

## Available ftr-site-config directives
> [!NOTE]
> The FTR site pattern docs are available [here](https://help.fivefilters.org/full-text-rss/site-patterns.html#pattern-format).

### Metadata
| Directive | Usage    | Description |
|-----------|----------|-------------|
| `title`   |          | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#title-xpath)  |
| `body`    |          | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#body-xpath)   |
| `date`    |          | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#date-xpath)   |
| `author`  |          | [body](https://help.fivefilters.org/full-text-rss/site-patterns.html#author-xpath) |

### Stripping, clearing, cleaning
| Directive           | Usage                 | Description  |
|---------------------|-----------------------|--------------|
| `strip`             |                       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#strip-xpath) |
| `strip_attr`        |                       | See `faz.net.txt` for usage  |
| `strip_comments`    | `strip_comments: no`  | ?            |
| `strip_id_or_class` |                       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#strip-id-or-class-string) |
| `strip_image_src`   |                       | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#strip-image-src-string)   |

### (Pre-) Processing
| Directive               | Usage      | Description |
|-------------------------|------------|-------------|
| `tidy`                  |            | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#tidy-yes-no)  |
| `prune`                 |            | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#prune-yes-no-default-yes) |
| `autodetect_on_failure` |            | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#autodetect-on-failure-yes-no-default-yes) |
| `insert_detected_image` | `yes`/`no` | Prevent use of detected image (e.g. logo on article without image). Mentioned [here](https://github.com/fivefilters/ftr-site-config/pull/1251#issuecomment-1817654995) |

### Multi-page articles
| Directive                   | Usage     | Description |
|-----------------------------|-----------|-------------|
| `single_page_link`          |           | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#single-page-link-xpath)  |
| `single_page_link_in_feed`  |           | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#single-page-link-in-feed-xpath)  |
| `next_page_link`            |           | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#next-page-link-xpath)  |
| `autodetect_next_page`      |           | See `jetzt.sueddeutsche.de.txt` for example |
| `if_page_contains`          |           | Used with single_page_link, see `washingtonpost.com.txt` for example  |

### String replacement
| Directive             | Usage    | Description |
|-----------------------|----------|-------------|
| `replace_string()`    |          | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#replace-string-string-to-find-replacement-string) |
| `find_string  `       |          | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#replace-string-string-to-find-replacement-string) |
| `replace_string  `    |          | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#replace-string-string-to-find-replacement-string) |

### Authentication
| Directive               | Usage    | Description |
|-------------------------|----------|-------------|
| `login_extra_fields`    |          |             |
| `login_password_field`  |          |             |
| `login_uri`             |          |             |
| `login_username_field`  |          |             |
| `not_logged_in_xpath`   |          |             |
| `requires_login`        |          |             |

### HTTP headers
See [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#http-header-header-name-header-value), possibly any header.

> [!CAUTION]
> Is this case sensitive?

| Directive                 | Usage    | Description |
|---------------------------|----------|-------------|
| `http_header(Cookie)`     |          |             |
| `http_header(User-Agent)` |          |             |
| `http_header(accept)`     |          |             |
| `http_header(referer)`    |          |             |

### Test-URLs
| Directive               | Usage    | Description |
|-------------------------|----------|-------------|
| `test_contains`         |          |             |
| `test_url`              |          | [docs](https://help.fivefilters.org/full-text-rss/site-patterns.html#test-url-string)  |
| `test_urls`             |          | Supposedly used with multi-page articles, see `theatlantic.com.txt`  |

### Not documented
| Directive                 | Example                     | Description                       | Found in          |
|---------------------------|-----------------------------|-----------------------------------|-------------------|
| `convert_double_br_tags`  | `convert_double_br_tags: yes` |                                 | scilogs.de.txt    |
| `native_ad_clue`          |                             |                                   | buzzfeed.com.txt  |
| `parser`                  | `parser: html5php`          | Possibly used with `html5php`, `gumbo`, `libxml`. <br> Hint on usage provided [here](https://help.fivefilters.org/full-text-rss/site-patterns.html#tidy-yes-no)                                  | nymag.com.txt     |
| `skip_json_ld`            | `skip_json_ld: yes`         |                                   | spiegel.de.txt    |
| `skip_id_or_class`        | `skip_id_or_class: Layout-sidebar`  |                           | github.com.txt    |
| `src_lazy_load_attr`      | `src_lazy_load_attr: data-full-src` |                           | slate.fr.txt      |
| `footnotes`               | `footnotes: no`             |                                   | jetzt.sueddeutsche.de.txt |
| `move_into()`             | `move_into([XPath]): [XPath]` |                                 | smithsonianmag.com.txt  |
| `wrap_in()`               | `wrap_in([tag]): [XPath]`   |                                   | smithsonianmag.com.txt  |
| `dissolve`                | `dissolve: [XPath]`         |                                   | bbc.com.txt       |
| `span`                    | `span: [XPath]`             | ??, possibly mistake?             | cloud.google.com.txt  |

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