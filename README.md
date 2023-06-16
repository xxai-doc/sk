<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Časť kódu webovej stránky je open source, vítaná pomoc pri optimalizácii prekladu.

## front-end kód

* [front-end kód](https://github.com/xxai-art/web)
* [Jazykové balíčky pre stránku ako celok](https://github.com/xxai-art/web/tree/main/i18n)
* [Jazykové balíčky pre prihlasovacie moduly](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Viacjazyčná dokumentácia webovej stránky](https://github.com/xxai-doc)

Front-end programovací jazyk je [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , ktorý pridáva niektoré funkcie založené na syntaxi coffeescriptu, pozri [./coffee_plus.md](./coffee_plus.md) .

## Internacionalizácia webových stránok a dokumentov

Stavte na nasledujúcich 3 projektoch

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Prípona je `.mdt` , môžete použiť syntax podobnú `<+ ./coffee_plus/import.js>` na odkazovanie na externé súbory a generovať markdown s príponou `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Preklad Markdown nepreloží kódy a odkazy a uloží preložené vety do vyrovnávacej pamäte. Ak je preklad upravený, ale pôvodný text nie je upravený, jeho opätovným vykonaním sa úprava prekladu neprepíše.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Jazykové súbory na preklad webových stránok generovaných v `yaml` .
