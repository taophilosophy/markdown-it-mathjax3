# markdown-it-mathjax3-tao 


This is a fork of [tani/markdown-it-mathjax3](https://github.com/tani/markdown-it-mathjax3) and merged form [AustenLamacraft/markdown-it-mathjax3](https://github.com/AustenLamacraft/markdown-it-mathjax3). And I updated the dependency packages to the latest version as much as possible. Part of vitepress references [brc-dd/vitepress-mathjax3](https://github.com/brc-dd/vitepress-mathjax3). If you need a full example of this plugin in the vitepress project, please refer to the [taophilosophy/taophilosophy.github.io](https://github.com/taophilosophy/taophilosophy.github.io).
 
This version is implemented by `AustenLamacraft` as `loader: {load: [“input/tex”, “output/chtml”]}` . **Note that mml3 output is still not supported. If anyone is able to implement this, please let me know, thanks a lot.** I am using the plugin under vitepress.

## Using markdown-it-mathjax3-tao in **vitepress** 
The plugin is configured under **vitepress** in the following way:

if you are using another package manager such as **yarn**, **npm** or **pnpm** then this should be the case:

`package.json` :

```
{
  "type": "module",
  "license": "BSD-3-Clause",
  "dependencies": {
   "vitepress": "1.2.2",
	"markdown-it-mathjax3-tao": "4.3.2"
  },
  "scripts": {
    "docs:dev": "vitepress dev docs",
    "docs:build": "vitepress build docs",
    "docs:preview": "vitepress preview docs"
  }
}
```

If you using **bun** :

`package.json` :

```
{
  "type": "module",
  "license": "BSD-3-Clause",
  "dependencies": {
   "vitepress": "1.2.2",
	"markdown-it-mathjax3-tao": "4.3.2"
  },
    "trustedDependencies": [
    "markdown-it-mathjax3-tao",
    "esbuild",
    "vue-demi"
  ],
  "scripts": {
    "docs:dev": "vitepress dev docs",
    "docs:build": "vitepress build docs",
    "docs:preview": "vitepress preview docs"
  }
}
```

`.vitepress/config.mjs` :

```
import mathjax3 from 'markdown-it-mathjax3-tao';

const customElements = [
  'mjx-container',
  'mjx-assistive-mml',
  'math',
  'maction',
  'maligngroup',
  'malignmark',
  'menclose',
  'merror',
  'mfenced',
  'mfrac',
  'mi',
  'mlongdiv',
  'mmultiscripts',
  'mn',
  'mo',
  'mover',
  'mpadded',
  'mphantom',
  'mroot',
  'mrow',
  'ms',
  'mscarries',
  'mscarry',
  'mscarries',
  'msgroup',
  'mstack',
  'mlongdiv',
  'msline',
  'mstack',
  'mspace',
  'msqrt',
  'msrow',
  'mstack',
  'mstack',
  'mstyle',
  'msub',
  'msup',
  'msubsup',
  'mtable',
  'mtd',
  'mtext',
  'mtr',
  'munder',
  'munderover',
  'semantics',
  'math',
  'mi',
  'mn',
  'mo',
  'ms',
  'mspace',
  'mtext',
  'menclose',
  'merror',
  'mfenced',
  'mfrac',
  'mpadded',
  'mphantom',
  'mroot',
  'mrow',
  'msqrt',
  'mstyle',
  'mmultiscripts',
  'mover',
  'mprescripts',
  'msub',
  'msubsup',
  'msup',
  'munder',
  'munderover',
  'none',
  'maligngroup',
  'malignmark',
  'mtable',
  'mtd',
  'mtr',
  'mlongdiv',
  'mscarries',
  'mscarry',
  'msgroup',
  'msline',
  'msrow',
  'mstack',
  'maction',
  'semantics',
  'annotation',
  'annotation-xml',
  'mjx-c',
  'mjx-mstyle',
  'mjx-mspace',
  'mjx-mover',
  'mjx-base',
  'mjx-over',
  'mjx-texatom',
  'mjx-mfrac',
  'mjx-frac',
  'mjx-dbox',
  'mjx-dtable',
  'mjx-row',
  'mjx-den',
  'mjx-dstrut',
  'mjx-line',
  'mjx-num',
  'mjx-mrow',
  'mjx-msqrt',
  'mjx-sqrt',
  'mjx-box',
  'mjx-surd',
  'mjx-nstrut',
  'mjx-msup',
  'mjx-script',
  'mjx-math',
  'mjx-mn',
  'mjx-mo',
  'mjx-mi',
];

export default defineConfig({
	markdown: {
		config(md) {
			md.use(mathjax3, {
               tex: {tags: 'ams'},
               loader: {load: ["input/tex", "output/chtml"]},
			});
		}

	},
   vue: {
    template: {
      compilerOptions: {
        isCustomElement: (tag) => customElements.includes(tag),
      },
    },
  },
	head: [
				[
			'script',
			{
				async: '',
				src: 'https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js',
			}
		],
	],
})
```

`.vitepress/theme/custom.css` :

```
mjx-container {
  display: inline-block;
  margin: auto 2px -2px;
}

mjx-container > svg {
  margin: auto;
  display: inline-block;
}
```

`.vitepress/theme/index.js` :

```
import DefaultTheme from 'vitepress/theme'
import './custom.css'

export default DefaultTheme
```

## Below is an archive
------------------------------------------------------------------------------------------------------------------------------------------
                          Below is an archive   以下是存档内容
-------------------------------------------------------------------------------------------------------------------------------------------

Add Math to your Markdown


This is a fork of [markdown-it-katex](http://waylonflinn.github.io/markdown-it-katex/) to support MathJax v3 and SVG rendering.

## Quick Start

1. Install markdown-it and this plugin

   ```
   npm install markdown-it markdown-it-mathjax3
   ```

2. Use it in your  code

   ```javascript
   var md = require('markdown-it')(),
       mathjax3 = require('markdown-it-mathjax3');
   
   md.use(mathjax3);
   
   // double backslash is required for javascript strings, but not html input
   var result = md.render('# Math Rulez! \n  $\\sqrt{3x-1}+(1+x)^2$');
   ```

## Customization

This plugin accepts the MathJax configuration.
Instead of `<script>window.MathJax = { tex: ..., svg: ...}</script>`,
pass it like `md.use(mathjax3, { tex: ..., svg: ... })`.

## FAQ

- How to attach equation tags?
  -- Pass the options like `md.use(mathjax3, { tex: {tags: 'ams'} })`

## Examples

### Inline

Surround your LaTeX with a single `$` on each side for inline rendering.
```
$\sqrt{3x-1}+(1+x)^2$
```

### Block

Use two (`$$`) for block rendering. This mode uses bigger symbols and centers
the result.

```
$$\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}$$
```

## Syntax

Math parsing in markdown is designed to agree with the conventions set by pandoc:

    Anything between two $ characters will be treated as TeX math. The opening $ must
    have a non-space character immediately to its right, while the closing $ must
    have a non-space character immediately to its left, and must not be followed
    immediately by a digit. Thus, $20,000 and $30,000 won’t parse as math. If for some
    reason you need to enclose text in literal $ characters, backslash-escape them and
    they won’t be treated as math delimiters.
