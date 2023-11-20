# EPFL search plugins

A collection of search plugins for [EPFL](https://www.epfl.ch) using
[OpenSearch](https://en.wikipedia.org/wiki/OpenSearch) hosted on GitHub pages.

Please read the [MDN](https://developer.mozilla.org/en-US/docs/Web/OpenSearch)
documentation.

Theses plugins were hosted on http://mycroftproject.com, but it become more
difficult to manage them, so this repository was created.

Last but not least, the auto-discovery of OpenSearch is no longer working with 
Google Chrome (see this
[stackoverflow](https://stackoverflow.com/questions/56400952/does-chrome-allow-auto-discovery-of-opensearch)).


## Add / Generate plugins

While it sould be built on push with GitHub actions (WIP), you can generate 
the plugins' XML files and the HTML that reference them by end, running 

```bash
node index.js
```

It take data from [list.json](./list.json) and output plugins XML files in the
[opensearch](./opensearch) directory.

:warning: when adding a new plugin, you have to add the corresponding icons in
the [img](./img) repository. See the [Icons](#icons) section of this document.


### Options

Please run `node index.js --help` to see available options.


## Plugins list

The plugins list stand in the [list.json](./list.json) file. When adding a new
search plugin, `name`, `shortName`, `description`, `contact`, `image`, 
`searchURL` and `searchQueryURL` have to be set.


## Icons

> When possible, search engines should offer a 16x16 image of type
> "image/x-icon" or "image/vnd.microsoft.icon" (the Microsoft ICO format) and a
> 64x64 image of type "image/jpeg" or "image/png".

Each icons of this repo has a "epfl-search-service.svg" image, in the
[img](./img) directory. Use this [svg] image to generate the 16×16 image of
type `image/x-icon` and a 64×64 image of `image/png`. It's pretty easy with
[imagemagick]: 

```bash
convert -background transparent -resize 16 epfl-search-service.svg epfl-search-service.ico

convert -background transparent -resize 64 epfl-search-service.svg epfl-search-service.png
```

You can use [epfl-search-tempalte.svg](./img/epfl-search-tempalte.svg) as
template to create new search plugins.




[imagemagick]: https://imagemagick.org
