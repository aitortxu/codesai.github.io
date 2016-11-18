# Codesai website

Jekyll based website for Codesai


## Setup

### Docker

1. Clone the repository
2. Navigate to the repository folder in a terminal
3. Run `docker-compose up`
4. You may access the local website at `localhost:4000`
5. Start coding and jekyll will automatically build after you save changes

If you experience problems with jekyll automatic builds you can start another terminal and run `docker exec -it {name} bash`. You may now use `jekyll build` on demand.
To check the name of your docker container you can run `docker ps`, it may be something like {name_of_jekyll_folder}_web_1.

### Your own environment

1. Clone the repository
2. Install ruby
3. Navigate to the repository folder in a terminal.
4. Run `bundle install`
5. Run `jekyll build`
6. Run `jekyll serve`, if on windows run `jekyll serve --force_polling` instead
7. You may access the local website at `localhost:4000`
8. Start coding and jekyll will automatically build after you save changes

If you experience problems with jekyll automatic builds you can start another terminal, navigate to the repository folder and run `jekyll build` on demand.


## Jekyll Concepts

### Workflow

When running `jekyll build`, the content is autogenerated in the `_site` folder. This is the folder that is deployed and accessed by the browser.
We use `jekyll serve` to automatically execute the build after we save changes and allow access to the site at `localhost:4000`. If on windows, use `jekyll serve --force_polling`. This is to compensate for the `--watch` option not working on windows, and it is applied by default.

Having the `jekyll serve` running, we can save changes and refresh the page to see the changes. However, there is an issue:

- When saving changes to .yml files, llike `_config.yml`, we should restart the `jekyll serge` to see changes. Or stop the docker container with `Ctrl+C` and execute `docker-compose up` again.

### Plugins

We are using the `jekyll-multiple-languages-plugin` to generate the english version of the site at `_site/en/`. The content is duplicated inside the folder but with the language set to english.

- To allow for translations, we have a `_i18n` folder with an .yml file for each language, following the two-letter convention. In this case: `es.yml` and `en.yml`.
- The spansih is the default language build at the root of `_site`.
- To translate content, we use the liquid tag provided by the plugin: `{% translate my.content %}`. This would check the language .yml files and look for the value for `my.content`.

### Layouts and includes

The layouts in the `_layouts` and the includes in the `_includes` folder may save use time and remove html duplication. It is usually used for the head, header and footer for convenience.

- We must have specified a layout in an .html file for liquid to evaluate it.


## Website

- The styles are in the `airspace.css` file and it will be renamed and refactored once we have everything in place and the theme has become obsolete.
- The styles for the `@media` queries are in the `responsive.css` file. It should also be cleaned up like the previous one.
- We use the bootstrap breakpoints:
    1. Extra small devices (xs): `768px` This is the **default** (mobile first)
    2. Small devices (sm): `768px ... 991px`
    3. Medium devices (md): `992px ... 1199px`
    4. Large devices (lg): `1200px`