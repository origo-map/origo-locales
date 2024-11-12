

[![License](https://img.shields.io/badge/license-BSD2-blue.svg?style=flat-square)](https://github.com/origo-map/origo/blob/master/LICENSE.txt)
# origo-locales

Language (localization) files for Origo.

## What is Origo locales?

This repo holds language files for user submitted languages. These can be used in Origo deployments to extend language support beyond the current two Origo built-in languages (Swedish and English). They are all meant to follow the same schema (which is currently under development. For further information see [Want to contribute?](#want-to-contribute))

A language file does not necessarily need to be complete. If Origo's localization control cannot find a key in the given locale it will try to look it up from a backup locale (which can be configured).

## How to get started

A language file can be used in an Origo deployment in two ways. Either it is added as a built-in language or it is added during runtime (while Origo is running). 

### As a built-in language

1. In the Origo source, add the .json file to src/loc/
2. Edit [src/controls/localization.js](https://github.com/origo-map/origo/blob/master/src/controls/localization.js). 
At the top of the file, add an import statement for the file:
```js
import enLocale from '../loc/en_US.json';
import svLocale from '../loc/sv_SE.json';
import nbLocale from '../loc/nb_NO.json';
```
3. Slightly further down create an entry for the new language in the locales object:
```js
  const locales = {
    'en-US': enLocale,
    'sv-SE': svLocale,
    'nb-NO': newLocale
  };
```
4. Build Origo and deploy

### During runtime

Via the Origo api the localization control's `addLocales()` function can be employed. It takes an array of language definitions (one or many language definitions).
```js
origo.api().getControlByName('localization').addLocales([{
    "id": "nb-NO",
    "title": "Norsk (bokmål)",
    "menuTitle": "Språk",
    "controls": {
        "measure": {
            "mainButtonTooltip": "Måle",
            "startMeasureTooltip": "Klikk for å starte målingen"
        }
    }
}])

```
This can also be performed by a plugin, at startup for instance.


## Documentation

Learn more about configuring the localization control at [documentation](https://origo-map.github.io/origo-documentation/latest/#localization-control).

## Want to contribute?
New language files or changes to existing are welcome. New files must follow the existing json structure - have a look at one of the built-in languages for the valid hierarchy and keys, [en-US for instance](https://github.com/origo-map/origo/blob/master/src/loc/en_US.json).

For as long as the language json structure is not complete (while not all of Origo is localized) new keys can be proposed via a language file in this repo.

The language id is meaningful for numbers formatting.


Please create an issue with what you intend to add or change to go with a PR. The repository will be checked for issues and PRs at regular intervals and please note that the Origo organization will not be able to validate new languages but merely that the json syntax is correct.




## Copyright
The contents of this repo are licensed under the BSD 2-clause license. It is specified in the license file (link).

## Contact
If you want to get in contact with us and other users of Origo then please join our chat on discord using this invitation: [origo.map](https://discord.gg/NWRAkWAXQ3).

On [https://origo-map.github.io/archive/](https://origo-map.github.io/archive/) you can take part of our newsletter and read about our meetups.
