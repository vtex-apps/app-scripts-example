📢 Use this project, [contribute](https://github.com/vtex-apps/CHANGEME) to it or open issues to help evolve it using [Store Discussion](https://github.com/vtex-apps/store-discussion).

# Scripts App

A script app is an application that provides scripts to be used in external pages, such as portal stores. The scripts have to be contained in the `scripts` folder. All the script files declared at `loader.json` are parsed by the `scripts builder` and are available by using [scripts-server](https://github.com/vtex-apps/scripts-server)'s `/load.js` route. By importing the scripts-server route using a `script` HTML tag on an external page, the appropriate scripts for that page are loaded and executed instantly. 

## loader.json structure

The `loader.json` file act as a declarer of which scripts should be executed on which page. Each entry in the object must have a `RegExp` key. The values of each entry must contain an array of strings, each string pointing to a script file that will be loaded if the `RegExp` key matches the `pathname` of the current page URL.

Note in the example below that, by default, the scripts are located in the `scripts` folder, so there is no need to declare it.

Note also that there are no file extensions, as the `scripts builder` only looks for `.ts` files.

### Example

```json
{
  ".*": ["script1"],
  ".*\/p$": ["script2", "script3"],
  ".*\/b$": ["script2"]
}
```

By using the example above, the `script1` script will be loaded and executed in **all** pages of the application (`.*` matches all `pathnames`). `script1`, `script2`, and `script3` will be loaded in product pages (or pages that end in `/p`). `script1` and `script2` will be also loaded if the pages end in `/b`.

Note that you can declare multiple scripts for a single `RegExp` and multiple `RegExp` can match a single URL `pathname`. Each script is loaded and executed only one time per page, independently of how many occurrences it has in matched `RegExps`.

## Importing scripts

To import scripts, put a single script HTML tag inside the `body` element of your HTML file. This script is the same for all pages in which you want to load your app's scripts, and it will load and execute only the appropriate scripts for that page: the ones that match the `RegExps` from the `loader.json` file against the page `pathname`.

### Example

**Development**
```html
<script src="https://{{devWorkspace}}--{{account}}.myvtex.com/_v/public/vtex.scripts-server/v1/load.js" type="text/javascript"></script>
```

**Production**
```html
<script src="/api/io/_v/public/vtex.scripts-server/v1/load.js?workspace={{productionWorkspace}}" type="text/javascript"></script>
```
# APP NAME

<!-- DOCS-IGNORE:start -->
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-0-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->
<!-- DOCS-IGNORE:end -->

Under the app's name, you should explain the topic, giving a **brief description** of the **app's functionality** (what is it for?) in a store.

Next, you can **add media** (either an image of a GIF) if possible, so that users can better understand how the app works in practice. 

![Media Placeholder](https://user-images.githubusercontent.com/52087100/71204177-42ca4f80-227e-11ea-89e6-e92e65370c69.png)

## Configuration

It is possible to install in your store either by using App Store or the VTEX IO Toolbelt.

### Using VTEX App Store

1. Access the **Apps** section in your account's admin page and look for the Icommkt box;
2. Then, click on the **Install** button;
3. You'll see a warning message about needing to enter the necessary configurations. Scroll down and type in your **NAME OF A SETTINGS FIELD** in the `NAME OF THE APP` field.
4. Click on **Save**.

### Using VTEX IO Toolbelt

1. [Install](https://vtex.io/docs/recipes/development/installing-an-app/) the `vtex.icommkt@0.x` app. You can confirm that the app has now been installed by running `vtex ls` again. 
2. Access the **Apps** section in your account's admin page and look for the NAME OF THE APP box. Once you find it, click on the box.
3. Fill in the `NAME OF THE APP` field with your **NAME OF THE SETTINGS FIELD**.
4. Click on **Save**.

<!-- Remember to also **showcase any necessary disclaimer** related to the app in this section, such as the different behavior it may display during its configuration. -->

## Modus Operandi *(not mandatory)*

There are scenarios in which an app can behave differently in a store, according to its configuration. It's crucial then to go through these **behavioral changes** in this section, allowing users to fully understand the **practical application** of the app in their store.

If you feel compelled to give further details, such as the app's **relationship with others**, don't hesitate to use this section. 

<!-- DOCS-IGNORE:start -->
## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind are welcome!
<!-- DOCS-IGNORE:end -->
