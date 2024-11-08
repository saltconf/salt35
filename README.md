# SALT34 Website

This repository houses [the website for SALT35](https://saltconf.github.io/salt34/). This website was forked directly from [the repository](https://github.com/saltconf/salt29) housing the [the SALT29 website](http://salt.linguistics.ucla.edu/29/).

Beyond the obvious content changes, the structure of this repository differs substantially from that for the SALT29 website in order to factor the site content from the site structure and aesthetics using [jekyll](https://jekyllrb.com/). This change should enable organizers of future SALTs to:

1. More easily change information site-wide–by editing the [YAML](https://yaml.org/) files in `_data`.
2. More easily edit site-wide styles in `_sass`. Style files have been fully refactored and converted to [SASS](https://sass-lang.com/) from vanilla CSS.
3. Edit page structure site-wide in `_layouts`. This page structure supports [liquid templates](https://shopify.github.io/liquid/), allowing flexible population of page contents–e.g. automatic construction of the program from YAML. 
