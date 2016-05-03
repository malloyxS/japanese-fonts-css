japanese-fonts.css
==================

The CSS configurations for Japanese device/web fonts.

Installation
------------

### NPM

```shell
$ npm i -S seamile4kairi/japanese-fonts-css
# Recommend you to use along with PostCSS and postcss-import
$ npm i -D postcss postcss-import
```

Then, import on your CSS file.

```css
@import 'japanese-fonts-css';
```

### Download

1. Just click \[[Download ZIP](https://github.com/seamile4kairi/japanese-fonts-css/archive/master.zip)\] button or ``git clone https://github.com/seamile4kairi/japanese-fonts-css.git``.
2. Import or load the minimized CSS file:
```css
/* from CSS */
@import 'dist/japanese-fonts.min.css';
```
```html
<!-- from HTML -->
<link rel="stylesheet" href="dist/japanese-fonts.min.css" charset="utf-8">
```

### cf. Structure

```
japanese-fonts-css
|- dist
|   |- assets
|   |   `- ...                  # Copied assets
|   |- index.html               # Test file for CSS rendering
|   |- japanese-fonts.css       # Generated CSS file (non-minimized)
|   `- japanese-fonts.min.css   # Generated CSS file (minimized)
|- src                          # Directory of source files
|   |- assets
|   |   `- noto-sans-cjk-jp-min # Subset of the Noto Sans CJK JP for the size down.
|   |                           # (Git submodule / Only using Noto Sans Mono Japanse)
|   |- components
|   `- japanese-fonts.css
|- postcss.config.js            # Configurations to generate dist/japanese-fonts.css
`- other meta files...
```

Usage
-----

### Use with CSS Custom Properties

```css
.sans-serif {
  font-family: var(--jp-sans-serif);
  ...
}

.serif {
  font-family: var(--jp-serif);
  ...
}

.monospace {
  font-family: var(--jp-monospace);
}
```

Or you can also redifne custom properties as you like:

```css
:root {
  --custom-sans-serif: var(--font-apple-sans),
                       'メイリオ', Meiryo, 'ＭＳ Ｐゴシック',
                       sans-serif;
}

.hoge {
  font-family: var(--custom-sans-serif);
}
```

#### Reserved Custom Properties

- ``var(--jp-sans-serif)``: sans-serif / ゴシック体
  - ``var(--font-system)``:       San Francisco
  - ``var(--font-yu-gothic)``:    游ゴシック
  - ``var(--font-apple-sans)``:   Helvetica Neue, ヒラギノ角ゴ
  - ``var(--font-google-sans)``:  Noto Sans Japanese
- ``var(--jp-serif)``: serif / 明朝体
  - ``var(--font-yu-mincho)``:    游明朝
  - ``var(--font-apple-serif)``:  Garamond, ヒラギノ明朝
  - ``var(--font-google-serif)``: Noto Serif
- ``var(--jp-monospace)``: monospace / 等幅
  - ``var(--font-apple-mono)``:   Monaco, Osaka-Mono
  - ``var(--font-google-mono)``:  Noto Sans Mono Japanese

#### cf. About Custom Properties

- [SPEC](https://www.w3.org/TR/css-variables/)
- [PostCSS Plugins](https://github.com/postcss/postcss-custom-properties)

### Use with class or [data-jp-fonts] attribute

```html
<!-- Define with CSS class -->
<p class="jp-font--sans-serif">ゴシック体を指定</p>
<p class="jp-font--serif">明朝体を指定</p>
<p class="jp-font--monospace">等幅フォントを指定</p>
<!-- Define with [data-jp-fonts] attribute -->
<p data-jp-fonts="sans-serif">ゴシック体を指定</p>
<p data-jp-fonts="serif">明朝体を指定</p>
<p data-jp-fonts="monospace">等幅フォントを指定</p>
```
