<p align="center">
  <img alt="style-it-themes-logo" src="https://raw.githack.com/style-it-themes/style-it-themes-logos/master/style-it-themes-logo-full.svg" width="580">
</p>
<br>
<h1 align="center"><strong>DD-WRT Inspired Themes</strong></h1>
<p align="center">
  <a href="./LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg?longCache=true&style=for-the-badge" alt="LICENCE">
  </a>
</p>
<p align="center">
  <a href="https://discord.gg/EpdGSfH">
    <img src="https://img.shields.io/badge/style--it--themes-discord%20channel-blue.svg?style=for-the-badge" alt="Style-It Themes (sit) Discord Channel">
  </a>
  <a href="https://github.com/style-it-themes/dd-wrt-inspired-themes/releases">
    <img src="https://img.shields.io/github/tag/style-it-themes/dd-wrt-inspired-themes.svg?label=Current%20Version&style=for-the-badge" alt="Current version">
  </a>
  <a href="https://david-dm.org/Style-it-Themes/dd-wrt-inspired-themes?type=dev">
    <img src="https://img.shields.io/david/dev/style-it-themes/dd-wrt-inspired-themes.svg?label=devDependencies&style=for-the-badge" alt="devDependencies">
  </a>
</p>

# TOC
  * [About](#about)
  * [Router Model Compatibility](#router-model-compatibility)
  * [Features](#features)
  * [Installing](#installing)
    * [Requirements](#requirements)
    * [Install This Style](#install-this-style)
    * [Router IP Setting](#router-ip-setting)
    * [Additional Userstyles](#additional-userstyles)
  * [I Found a Bug](#i-found-a-bug)
  * [Engaging with the Project](#engaging-with-the-project)
    * [Contribution Guidelines](#contribution-guidelines)
    * [Development Scripts](#development-scripts)
  * [Screens](#screens)
  * [Thanks](#thanks)

## About

The *DD-WRT Inspired Themes* style is designed for routers flashed with DD-WRT type firmware.

This style leverages the _awesome_ v2 [stylus lang color generator](https://github.com/vednoc/stylus-color-generator) by @vednoc

The default built in themes are great, but even the best dark built in theme doesn't darken all areas and many aspects could be further polished. Instead of waiting...

It's made for my personal use only, and shared because... Why not.

## Can you include these themes in DD-WRT?

From DD-WRT builds 09-07-2021-r47377 and newer, static CSS, non user customizable versions of this project are included by default.

If your router has enough memory these will be included.

>Note that some sections of external DD_WRT sites cannot be targeted via CSS at this time. BrainSlayer may add support for these at some later stage.

In any case you can not customize the built in styles and you may notice styling inconsistencies. If that bothers you DO use this project instead.

## Router Model Compatibility

At this time, its developed and tested on the *ASUS RT-AC68U*

## Features

The *DD-WRT Inspired Themes* style has optional and built in redesigns that fix,
modernize or allow consistence styling through all accessible areas.
if you wish to view complete list click below.

<details>
  <summary>Click to Expand</summary>
 
 ### Preset styles

 * Custom colors (within reason and sane choices users can make up own color schemes)
 * Dracula
 * Material
 * Material Darker
 * Solarized Dark
 * Twilight
 * The Matrix
 * Ubuntu

 ### Color Adjustments

 * Optionally darken/lighten to some extent the background, foreground and accent colors. 

 ### Navigation

 * Optionally invert navigation colors
 
 Default is inverted.

 ### Redesigned Inputs

 * Redesigned input styling for checkboxes, radio, dropdown and other interactable elements.
 
 You can optionally choose the checkbox size, however not all sizes will look or align well.
 There seems to be some issue with sizes less than `1rem` using DD-WRT web interface, this has unknown cause, works on other website I use same custom checkboxes/radios code.

 ### Image updates

 * Hotspot logos are updated and working with all dark styles.
 * DD-WRT logos use CSS filters to make them compatible with different backgrounds colors.
 * New bin icon

 ## The Kitchen Sink

 The following will match seamlessly your chosen color scheme.

 * Help, About, Wiviz pages
 * Popups e.g. Access restrictions edit list etc.
 * Progress bars/Signal quality bars etc.
 * Speedchecker dialog
 * Speedchecker logo image replacement
 * OID search
 * Optional transition effects
 * Experimental font replacements
 
</details> 

## Installing

### Requirements

* Stylus - install the addon for [Firefox](https://addons.mozilla.org/en-US/firefox/addon/styl-us/), [Chrome](https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne) or [Opera](https://addons.opera.com/en-gb/extensions/details/stylus/).

### Install This Style

[![CLICK TO INSTALL WITH - STYLUS](https://img.shields.io/badge/Install_directly_with-Stylus-21d1d0.svg?longCache=true&style=for-the-badge)](https://github.com/style-it-themes/dd-wrt-inspired-themes/raw/main/dd-wrt-inspired-themes.user.styl)  
*Click to install directly from this repository*.

### Limitations of This project

Some classic gui-style themes + DD-WRT Inspired Themes via Stylus at same time will not work together well with all cases.

For best results at this time, if you use a DD-WRT FW version that includes built in *DD-WRT Inspired Themes* please select and enable one of them.

*Works together with* blue/yellow/red/orange/cyan/elegant light styles, or the included *DD-WRT Inspired Themes*, do not enable dark styles.
*Does not work well together with* Brainslayer/kromo/vikar/xirian and possibly others will show many styling inconsistencies and breakages.

Internal DD-WRT older themes will be reworked some day when Santa has time.

#### Router IP Setting

:warning: Be aware that manual editing the style, blocks auto-updates from being pushed,
 and if you force update style any edits you made are lost and will need to be re-added.

From version 4.0, a regex matching valid IPV4 blocks is used.
This is a better setup with 0 user edits required and also auto-updates of style are served automatically.

This method introduces some quirks in some setups. Please expand relevant solution.

1) You run a server accessible via an IP and this theme is installed, all IP's will be matched even if it's not DD-WRT web interface.

If you encounter such issues and your page is styled by this theme manually reverting to previous method is the only way.
as follows:

<details>
  <summary>Click to Expand</summary>

**Section 1**

```diff
-   @-moz-document regexp('^https?://(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)(\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)){3}(\/.*)?$'),
+   @-moz-document domain('your.actual.router.ip'), domain('your.other.router.ip'),
    /*           */regexp('https?://oidsearch.s.dd-wrt?.com(/.*)?'),
    /*           */regexp('https?://speedchecker.dd-wrt?.com(/.*)?') {
```
**Section 2**

```diff
-   @-moz-document regexp('^https?://(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)(\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)){3}(\/.*)?$'),
+   @-moz-document domain('your.actual.router.ip'), domain('your.other.router.ip'),
/*           */regexp('https?://speedchecker.dd-wrt?.com(/.*)?') {
```

</details> 

2) If you access your router via a LAN domain like router.local this design choice won't work and to make it work via regex all sites on the web will be matched.

If you encounter such issues please edit style like this.

<details>
  <summary>Click to Expand</summary>

**Section 1**

```diff
-   @-moz-document regexp('^https?://(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)(\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)){3}(\/.*)?$'),
+   @-moz-document domain('your.actual.router.ip'), domain('your.other.router.ip'),
    /*           */regexp('https?://oidsearch.s.dd-wrt?.com(/.*)?'),
    /*           */regexp('https?://speedchecker.dd-wrt?.com(/.*)?') {
```
**Section 2**

```diff
-   @-moz-document regexp('^https?://(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)(\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)){3}(\/.*)?$'),
+   @-moz-document domain('your.actual.router.domain'), domain('your.other.router.domain'),
/*           */regexp('https?://speedchecker.dd-wrt?.com(/.*)?') {
```

</details> 


### Additional Userstyles
  Style-It Themes recommends Stylus Wardrobe and the Global Overlay Scrollbars can be used all together without issues.
  These add unapparelled consistent experience and extend customizations options for other areas of your browsing live.
  
  Save your retinas from the burn!

* [Overlay Scrollbars](https://github.com/StylishThemes/Overlay-Scrollbars)
* [Stylus Wardrobe](https://github.com/style-it-themes/stylus-wardrobe)

## I Found a Bug

At the first instance of finding a bug, have a look if there is already an open issue, if so add the required information as described in the [issue template](.github/ISSUE_TEMPLATE.md).

If your issue is new, please [open an issue](https://github.com/style-it-themes/dd-wrt-inspired-themes/issues/new/choose) and report your problem.

You will need to be familiar with browser development tools.

[Firefox development tools](https://developer.mozilla.org/en-US/docs/Tools)
[Chrome development tools](https://developers.google.com/web/tools/chrome-devtools)

## Engaging with the Project

There are many ways to engage with the project, all contributions types are most welcome and encouraged, e.g. ask for your fav color schemes, fix some typo(s), add documentation, prettify any included portions, provide feedback or ask a question, even help out with support/questions from other users, to name just a few ways you can engage with this project.

Open a pull request or [ticket](https://github.com/style-it-themes/dd-wrt-inspired-themes/issues/new/choose) to start the ball rolling.

For Git related contributions you will need:

1. [Fork](https://github.com/style-it-themes/dd-wrt-inspired-themes/fork) the project.
2. Install dev-dependencies `npm i --only-dev`
3. Edit the desired files according to current requirement below, commit changes, run fix script `npm run fix` and push changes.
4. Open a pull request

## Contribution Guidelines

After any changes and before opening a PR please run both development scripts below.
Then push your changes and open a PR.

If your contribution includes dependencies updates, ensure this is done as a separate commit.

Thank you in advance for any contributions.

### Development Scripts

* `npm run authors`: Regenerate the AUTHORS file based on Git history
* `npm run fix`: Runs editorconfig via ECLint with `--fix` on the styl file.

For dependencies updates;

* `npm run update`: Update development dependencies.

### For internal use Only

Releases are for internal use only, so remember to not include version bumps with your contributions 

* `npm run major`: Creates a semantic major release.
* `npm run minor`: Creates a semantic minor release.
* `npm run patch`: Creates a semantic patch release.

> Note: Dependencies updates can be submitted as part of any contribution that is a separate commit
>       from main contribution, or as a standalone contribution.

## Screens

# COMING SOON

More screenshots available in [screens directory](/screens) for your perusal.

## Thanks

@vednoc kudos and thanks, for showing me another way to save retinas from the burn.

[Openstyles](https://github.com/openstyles/stylus) for developing Stylus. The best userstyle extension on all the web.

[:arrow_up: UP :arrow_up:](#readme)
