# EPFL search plugins

TL;DR please visit https://ponsfrilus.github.io/searchplugins/

## About

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

While it sould be built on push with GitHub actions, you can generate the
plugins' XML files and the HTML that reference them by hand, running:

```bash
node index.js
```

It takes data from [list.json](./list.json) and output plugins XML files in the
[opensearch](./opensearch) directory.

:warning: when adding a new plugin, you have to add the corresponding icons in
the [img](./img) repository. See the [Icons](#icons) section of this document.


### Options

Please run `node index.js --help` to see available options.


## Plugins list

The plugins list stands in the [list.json](./list.json) file. When adding a new
search plugin, `name`, `shortName`, `description`, `contact`, `image`, 
`searchURL` and `searchQueryURL` have to be set.


## Icons

> When possible, search engines should offer a 16x16 image of type
> "image/x-icon" or "image/vnd.microsoft.icon" (the Microsoft ICO format) and a
> 64x64 image of type "image/jpeg" or "image/png".

Each icons of this repo has a `epfl-search-service.svg` image, in the
[img](./img) directory. Use this [svg] image to generate the 16×16 image of
type `image/x-icon` and a 64×64 image of `image/png`. It's pretty easy with
[imagemagick]: 

```bash
convert -background transparent -resize 16 epfl-search-service.svg epfl-search-service.ico

convert -background transparent -resize 64 epfl-search-service.svg epfl-search-service.png
```

Alternatively, you can run this script to do them all:

```bash
for f in $(ls img/*.svg); do 
    echo "Generating ico and png for $f";
    filename=$(basename -- "$f")
    extension="${filename##*.}"
    filename="${filename%.*}"
    convert -background transparent -resize 16 $f img/$filename.ico
    convert -background transparent -resize 64 $f img/$filename.png
done
```




You can use [epfl-search-tempalte.svg](./img/epfl-search-tempalte.svg) as
template to create new search plugins.




[imagemagick]: https://imagemagick.org
