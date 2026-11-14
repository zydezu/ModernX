## Locales

ModernX is currently available in English, but you can easily switch it to your preferred language! Here's how:

1. **Download the locale pack**

Grab the [modernx-locale.json](/extras/locale/modernx-locale.json) file from this repository. This file holds translations for various languages.

2. **Add the locales to mpv**

Copy the downloaded `modernx-locale.json` file to your mpv `/script-opts` folder.

3. **Choose your language**

Adjust or add the `language` option in your `modernx.conf` to your preferred language.

```EditorConfig
# Example configuration in modernx.conf
# Set language to Simplified Chinese
language=zh
```

**Need More Info?**

For a complete list of available languages, contribution guidelines, head over to the [TRANSLATIONS.md](/docs/TRANSLATIONS.md).

**Folder Structure** [[mpv manual](https://mpv.io/manual/master/#files)]
```
📁 mpv/
└── 📁 script-opts/
    ├── 📄 modernx.conf
    └── 📄 modernx-locale.json
```
