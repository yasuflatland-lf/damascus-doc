# Damascus User Guide
[Damascus](https://github.com/yasuflatland-lf/damascus) is a CRUD scaffolding generation tool for Liferay DXP. This repository is the user guide on the Github page.

## How to run locally
1. Install Ruby
1. Install Jekyll and bundler gems with `gem install jekyll bundler` command.
1. In the `_config.yml` file, please make sure the theme is pointing the local theme instead of the local one as below.
    ```bash
    theme: just-the-docs
    # remote_theme: pmarsceill/just-the-docs
    ```
1. Clone this repository and go to the root directory and run `bundle exec jekyll serve`
1. Now browse to `http://localhost:4000`

## How to deploy production.
1. In the `_config.yml` file, please make sure the theme is pointing the remote theme instead of the local one as below.
    ```bash
    # theme: just-the-docs
    remote_theme: pmarsceill/just-the-docs
    ```
1. Push the code to `gh-pages` repository.
For more details, please see the [Jekyll Quickstart page](https://jekyllrb.com/docs/).
## How to update search
This User Guide is using [Just the Docs](https://pmarsceill.github.io/just-the-docs/docs/search/) theme. Once you create pages, run `bundle exec just-the-docs rake search:init` to generate search index and `git push` to `gh-pages` repository.