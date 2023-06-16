<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Odporúča sa najskôr nainštalovať nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) a potom po vstupe do adresára `direnv allow` ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) sa spustí automaticky po vstupe do adresára).

Význam je: čínsky preklad do japončiny, kórejčiny, angličtiny, anglický preklad do všetkých ostatných jazykov. Ak chcete podporovať iba čínštinu a angličtinu, stačí napísať `zh: en` .

Význam je: čínsky preklad do japončiny, kórejčiny, angličtiny, anglický preklad do všetkých ostatných jazykov. Ak chcete podporovať iba čínštinu a angličtinu, stačí napísať `zh: en` .

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

### Pokyny na automatizáciu prekladu dokumentov

Pozrite si úložisko kódu [xxai-art/doc](https://github.com/xxai-art/doc)

Odporúča sa najskôr nainštalovať nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) a potom po vstupe do adresára `direnv allow` ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) sa spustí automaticky po vstupe do adresára).

Aby som sa vyhol veľkej kódovej základni prekladanej do stoviek jazykov, vytvoril som samostatnú kódovú základňu pre každý jazyk a vytvoril som organizáciu na uloženie kódovej základne

Nastavením premennej prostredia `GITHUB_ACCESS_TOKEN` a následným spustením [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) sa automaticky vytvorí úložisko kódu.

Samozrejme, môžete ho vložiť aj do kódovej základne.

Odkaz na prekladový skript [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Kód skriptu sa interpretuje takto:

[bunx](https://bun.sh/docs/cli/bunx) je náhrada za npx, ktorý je rýchlejší. Samozrejme, ak nemáte nainštalovaný bun, môžete namiesto toho použiť `npx` .

`bunx mdt zh` vykreslí `.mdt` v adresári zh ako `.md` , pozrite si 2 prepojené súbory nižšie

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` je základný kód pre preklad (ak máte nainštalovaný iba `nodejs` , ale `bun` a `direnv` nie sú nainštalované, môžete na preklad spustiť aj `npx i18n` ).

Bude analyzovať [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , konfigurácia `i18n.yml` v tomto dokumente je nasledovná:

```
en:
zh: ja ko en
```

Význam je: čínsky preklad do japončiny, kórejčiny, angličtiny, anglický preklad do všetkých ostatných jazykov. Ak chcete podporovať iba čínštinu a angličtinu, stačí napísať `zh: en` .

Posledným je [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , ktorý extrahuje obsah medzi hlavným názvom a prvým titulkom `README.md` každého jazyka a vygeneruje záznam `README.md` . Kód je veľmi jednoduchý, môžete sa naň pozrieť sami.

Na bezplatný preklad sa používa Google API. Ak nemáte prístup k službe Google, nakonfigurujte a nastavte proxy server, napríklad:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Prekladový skript vygeneruje preloženú vyrovnávaciu pamäť v adresári `.i18n` , skontrolujte ju pomocou `git status` a pridajte ju do úložiska kódu, aby ste sa vyhli opakovaným prekladom.

Spustite `bunx i18n` zakaždým, keď upravíte preklad, aby ste aktualizovali vyrovnávaciu pamäť.

Ak sa pôvodný text a preklad upravia súčasne, vyrovnávacia pamäť bude zmätená, takže ak chcete upraviť, môžete upraviť iba jednu a potom spustiť `bunx i18n` na aktualizáciu vyrovnávacej pamäte.
