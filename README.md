# My Little Templater v1.0.5

![NPM Build Status](https://travis-ci.org/nmarus/my-little-templater.svg?branch=master)

My-Little-Templater is a simple templating utility that can be used for constructing text documents for various purposes. It is built using [mustache.js](https://www.npmjs.com/package/mustache) and supports all syntax found there.

This can be used to generate anything from shell scripts, to html pages, to Cisco IOS configurations. Anything that can be applied to a template can easily be generated using simple [{{ mustache }}](https://mustache.github.io/) syntax.

### Requirements:

 - nodejs 0.10 or newer

### Install:

```bash
npm install my-little-templater -g
```

### Usage:

```bash
Usage: mlt [options] [<output filename> | - ]

Options:

-h, --help              output usage information
-V, --version           output the version number
-t, --template [value]  Template filename
-y, --yaml     [value]  YAML filename
-p, --parts    [value]  Directory containing template parts (Optional)
```

### Example(s):

#### Sample Folder Structure:

```bash
├── partials
│   ├── foot.part
│   └── head.part
├── templates
│   └── test.template
└── test.yml
```

***File: "partials/head.part"***

```html
 <html>
     <head><title>Hello {{name}}!</title></head>
     <body>
```

***File: "partials/foot.part"***

```html
    </body>
</html>
```

***File: "templates/test.template"***

```html
{{> head}}

    <h1>Hello {{name}}!</h1>

    <p>
    I see you like {{favorite_food}} and
    {{favorite_drink}}! I do too! What are
    the odds?
    </p>

{{> foot}}
```

***File: "test.yml"***

```yml
name: "Joe Smith"
favorite_food: "Pizza"
favorite_drink: "Diet Coke"
```

#### Render:

```bash
mlt -t templates/test.template -p partials -y test.yml out.html
```

***File: "out.html"***

```html
<html>
    <head><title>Hello Joe Smith!</title></head>
    <body>

    <h1>Hello Joe Smith!</h1>

    <p>I see you like Pizza and Diet Coke! I do too! What are the odds?</p>

    </body>
</html>
```
