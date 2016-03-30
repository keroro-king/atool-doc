# atool-doc

[![NPM version](https://img.shields.io/npm/v/atool-doc.svg?style=flat)](https://npmjs.org/package/atool-doc)
[![Build Status](https://img.shields.io/travis/ant-tool/atool-doc.svg?style=flat)](https://travis-ci.org/ant-tool/atool-doc)
[![Coverage Status](https://img.shields.io/coveralls/ant-tool/atool-doc.svg?style=flat)](https://coveralls.io/r/ant-tool/atool-doc)
[![NPM downloads](http://img.shields.io/npm/dm/atool-doc.svg?style=flat)](https://npmjs.org/package/atool-doc)
[![Dependency Status](https://david-dm.org/ant-tool/atool-doc.svg)](https://david-dm.org/ant-tool/atool-doc)

Static demo generator based on [atool-build](https://github.com/ant-tool/atool-build) and [dora](https://github.com/dora-js/dora)

**before**
```
./
├── README.md
└── examples
    ├── a.js
    ├── a.html
    └── b.md
```

**after**
```
./
├── README.md
├── __site
│   ├── common.js
│   ├── examples
│   │   ├── a.html
│   │   ├── a.js
│   │   ├── b.html
│   │   ├── b.js
│   └── index.html
└── examples
    ├── a.js
    ├── a.html
    └── b.md
```

## Demos

### Online Demos

Visit https://ant-tool.github.io/atool-doc/

### Local Demos

```bash
$ git clone git@github.com:ant-tool/atool-doc.git
$ cd atool-doc && npm i
$ npm run demo
```
Then, visit http://127.0.0.1:8002/

## Usage

### Setup

```bash
$ npm i atool-doc -g
```

### command

```bash
  atool-doc          start server at http://127.0.0.1:8002 for demo

  atool-doc [options]

    -h, --help       output usage information
    -v, --version    output the version number
    --dest <dir>     config path of output dir, default __site
    --source <dir>   config path of demo files dir, default examples
    --tpl <path>     config path of tpl file
    --config <path>  config path of webpack.config, default webpack.config.js
    --build          only build
    -w, --watch      using with --build, watch mode
```

## How to write demo file

Use `.js` or `.md` files to write demo under the directory specified in `source`

### `.md`

`.md` is more powerful

Write the code of demo with a section of `## code`, using language of `js/jsx/javascript`, `css` and `html` to customize css and dom

And then write other things you want at other sections, eg:

![image](https://cloud.githubusercontent.com/assets/5318333/14135283/309ee330-f68f-11e5-8d5f-fdd5a09f7fa9.png)

### `.js`

Without customizing dom, you can also work with the hook dom `div#__exampleDom`, placeholder in default [template file](https://github.com/ant-tool/atool-doc/blob/master/tpl/element.ejs), eg:

![image](https://cloud.githubusercontent.com/assets/5318333/14135388/c00356fa-f68f-11e5-9766-00133479ec6a.png)


## Customize template

If the [default template](https://github.com/ant-tool/atool-doc/blob/master/tpl/element.ejs) can not meet your needs, just try writing a new one!

- use `atool-doc --tpl somewhere` to specify your template file

- write your template file with following variables available **on the context of `file`**

  - `title`: string of file-path, `examples/basic`

  - `script`: array of script-path need to insert into the html file, `['../common.js', './basic.js']`

  - `html`: string of html element, `<div></div>`

  - `style`: string of style by css, `body { color: red; }`

  - `desc`: code of demo and other things written by markdown, `<h2>code</h2><div class="highlight"></div>`

*The template file only support syntax of `ejs` currently*
