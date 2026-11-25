# Domownik – postępy (stan na 25.11.2026, 20:35 Warszawa)

## Online
- **Sklep (główny): https://hizashi224.github.io/domownik/** – **v17** (5713 produktów, 5356 ze zdjęciem, 357 z pustym oknem, cache `domownik-pwa-v17`). Wypchnięte 25.11 ok. 20:40 czasu Europe/Warsaw przez Michała.
- Stara kopia na beacon (annual-parrot-76) wygasła 18.11 – nieaktualna.
- APK Android v1.2 (cache v14) – aplikacje wstrzymane, APK nie ruszany od 17.11.

## Wersja (v17 – 5713 produktów)
- **5713 produktów**, 11 kategorii z podkategoriami, **5356 ze zdjęciem** (357 puste okno – brak pewnego zdjęcia), cache sw.js: **domownik-pwa-v17**. Źródło prawdy: catalog_internal.json (format bez zmian, pod przyszły CSV Shopify).
- Per kategoria: sprzatanie 1033, higiena 1016, folie 892, papier 472, kawa 444, pranie 418, kuchnia 391, dom 352, przekaski 253, zwierzaki 237, dziecko 205.
- Funkcje bez zmian: kalkulator zużycia, gotowe listy, licznik oszczędności, program poleceń (demo), eko-tryb (teraz 752), mapa punktów odbioru (demo), 8 poradników od Sebastiana, panel właściciela z marżami, mega-menu, breadcrumbs, "Popularne", Wyczyść koszyk, pasek DEMO, stopka Gracjan & Sebastian
- **Reset koszyka (17.11 17:36):** w szufladzie koszyka przycisk „Wyczyść koszyk” (ukryty, gdy koszyk pusty). Potwierdzenie we własnym oknie, potem toast „Koszyk wyczyszczony” z „Cofnij” przez 5 s. Czyści pozycje jednorazowe i subskrypcyjne w koszyku oraz `localStorage` (`domownik_cart`) i licznik w nagłówku. **Nie kasuje aktywnej subskrypcji w koncie** (`domownik_acct`).
- Pasek DEMO i stopka "Gracjan & Sebastian"
- Testy: Playwright Chromium mobile + WebKit iPhone 13 – testy fazy 3 i funkcji przechodzą, plus scenariusz: 3 produkty → wyczyść → licznik 0 → Cofnij → z powrotem 3, bez błędów JS. Zrzut: shots/phase3/live_wk_cart_reset.png

## Historia
- v9: 311 produktów + PWA od Sebastiana
- Faza 1: 761 → Faza 2: 1500 → Faza 3: 3018 (cel zmniejszony z 5000 do 3000, koniec rozbudowy katalogu)
- 17.11: publikacja APK v1.1 (WebViewAssetLoader, 3018 produktów)
- 17.11 17:36: przycisk resetu koszyka, cache v14
- 17.11 17:38: APK v1.2 (versionCode 4) z resetem koszyka, podmiana na beacon
- 17.11 18:32: faza 4 / v15, pierwsza selekcja 5110 (publikacja na beacon wtedy przerwana — live zostało na v14/3018)
- 17.11 18:38: włączone pliki Sebastiana (sebastian2 + tansze); katalog **5713**, publikacja v15 na beacon

## Do zrobienia
- Przejąć stronę na beacon przed 18.11 15:08 czasu Europe/Warsaw (albo polegać na kopii GitHub Pages v15)
- ~~Odświeżyć GitHub Pages do v15~~ ZROBIONE 18.11 (v15 / 5713)
- ~~Odświeżyć GitHub Pages~~ ZROBIONE 17.11 (v14)
- Przetestować APK v1.2 na prawdziwym Androidzie
- privacy.html: uzupełnić dane administratora
- Google Play wstrzymane (brak konta / 25 USD); podpisany AAB: /workspace/Domownik-release.aab

## Zasady współpracy
- Przed publikacją na beacon uprzedzić Sebastiana; po zmianach poprosić Szefa sztabu o przebudowę APK
- Przy każdej zmianie podbić CACHE w sw.js

## Aplikacje mobilne – WSTRZYMANE (17.11.2026, decyzja Gracjana: na razie tylko strona)
Notatki na przyszłość, gdy wrócimy do aplikacji:
- Ostatni APK: domownik.apk v1.2 (versionCode 4, 9 288 923 B, podpis debug) = strona v14 (z „Wyczyść koszyk”). Jest też na beacon i na GitHub Pages jako /domownik.apk (wgrany tuż przed decyzją).
- Podpisany AAB pod Google Play: /workspace/Domownik-release.aab (Szef sztabu). Play wymaga konta dewelopera (25 USD).
- Budowa: WebView + WebViewAssetLoader (https://appassets.androidplatform.net/index.html), bo fetch() nie działa z file://. Assets = cały folder bez pozycji z .beaconignore.
- Strona wykrywa tryb aplikacji po 'wv' w User-Agent (STANDALONE).
- Przy każdej zmianie strony: podbić CACHE w sw.js, potem przebudować APK (podbić versionCode).
- Pakiet: pl.gras.domownik, minSdk 24, targetSdk 35.
- Projekt Android: /workspace/sklep-apk; przebudowa APK+AAB: `bash /workspace/sklep-apk/rebuild.sh` (potem cp /workspace/Domownik.apk -> domownik.apk). Wersja w app/build.gradle. Klucz uploadu do Play: /workspace/keys (nie gubić, nie wrzucać na GitHub).
- Zmiany strony od ostatniego APK (v14 / APK v1.2):
  - 17.11 18:32 faza 4 / cache v15: katalog 3018 → 5110 produktów (5026 ze zdjęciami).
  - 17.11 18:38 faza 4 dokończona: katalog **5713** (5615 ze zdjęciami) po włączeniu sebastian2.jsonl (603 nowych, 10 okazja OutOfStock pominiętych) i sebastian2_tansze.jsonl (43 tańsze źródła, oszczędność hurt 184,24 zł; 5 pozycji okazja OutOfStock, 1 bez zniżki, 1 dopasowanie po nazwie bez rozmiaru pominięte). Ceny okazja-hurtownia.pl przeliczone jako cena za sztukę (brutto = netto × 1,23; „OPAKOWANIE: N SZTUK” to wielokrotność zamówienia, nie cena zestawu).
  - Nowe źródła hurtowe z jawnymi cenami brutto: zakupychemiczne.pl (OPTIMA, główne), chemiashop.pl, oraz od Szefa: nawynos24.com, hurtowniawielobranzowa.pl, chemhurt.pl, gamma-opakowania.pl, radpak.eu.
  - 328 istniejących produktów potaniało względem v14 (oszczędność hurtowa łącznie 2 249,99 zł, średnio 6,86 zł; cena sklepowa łącznie −2 938 zł). Z tego 81 pozycji z szef2_tansze.jsonl (gł. hurtchemiczny.com.pl, 455,84 zł) i 247 z zakupychemiczne.pl.
  - Szef: incoming/szef2.jsonl — 600 nowych (po filtrze za drogie/za duże weszło 565).
  - Własny zbiór: 1529 nowych z zakupychemiczne.pl / chemiashop.pl (z obrazkami, większość z EAN).
  - Aplikacji nie przebudowywano (wstrzymane). GitHub Pages v15 wypchnięte 18.11 (decyzja Gracjana).
  - 25.11 20:00 v16 / cache `domownik-pwa-v16` (Michał, na prośbę Gracjana z 25.11): naprawa zdjęć i kategorii. Przyczyna złych zdjęć: przy ponownych przebiegach ingestu `download_one()` pomijało pobieranie, gdy plik `img/p<id>.webp` już istniał, więc nowe produkty o tym samym id dziedziczyły zdjęcia innych produktów (id 3021–4175). Zdjęcia: 972 podmienione na zdjęcie z karty tego produktu u dostawcy, 4321 zweryfikowane OK, 29 dodanych, 322 usunięte (puste okno — brak pewnego zdjęcia, zdjęcie wspólne dla innego wariantu albo zły produkt), razem 5322 ze zdjęciem / 391 bez. Puste okno jest naprawdę puste (bez rysunku butelki). Kategorie: 684 produkty przeniesione (383 między kategoriami), 13 nowych podkategorii (serwetki, woreczki, naczynia jednorazowe, dywany i tapicerka, czyszczenie pralki, klamerki i linki, odkamieniacze do ekspresów, pasty i szczoteczki dla dzieci, cukier/kakao/śmietanka, świece, biuro i elektronika), jaśniejsze nazwy podkategorii, „Inne” prawie puste. Ceny i flagi bez zmian. Szczegóły: fix/LOG.md, fix/v16b/.
  - 25.11 20:35 v17 / cache `domownik-pwa-v17` (Michał, prośba Gracjana „Ma być idealnie”): 34 nowe pewne zdjęcia (31 z karty produktu u dostawcy, 3 z Open Food Facts po EAN, każde sprawdzone OCR + wzrokowo), 1 zdjęcie przeniesione na właściwy rozmiar (Medosept 500 ml), 357 pustych okien; 5115 nazw uporządkowanych (Marka + produkt + wariant + rozmiar, bez KRZYKU, kodów kartonów i powtórzonych końcówek), 1170 poprawionych marek, ujednolicone opakowania (4549), 90 przeniesień kategorii, „Prześcieradła jednorazowe” zamiast „Prześcieradła i inne”, przeliczanie ceny za jednostkę rozumie wielopaki „4 x 85 g”. Ceny i flagi bez zmian. Szczegóły: fix/LOG.md, fix/v17/.

## ZASADA ZESPOŁU (Gracjan, 17.11.2026)
Wszystko zapisujemy tutaj, żeby boty (Michał, Sebastian, Szef sztabu) same się ogarniały.
- Przed pracą: przeczytaj ten plik.
- Po każdej zmianie dopisz w dzienniku poniżej: data i godzina, kto, co zmienione, co dalej.
- Plik jest wypychany na GitHub (hizashi224/domownik) razem ze stroną.

## Dziennik
- 17.11 17:37 Michał: v14, przycisk „Wyczyść koszyk” (potwierdzenie + Cofnij 5 s), cache v14.
- 17.11 17:38 Szef sztabu: APK v1.2 (versionCode 4), opublikowany na beacon.
- 17.11 17:39 Gracjan: aplikacje wstrzymane, robimy tylko stronę.
- 17.11 ~17:40 Sebastian: GitHub Pages odświeżone do v14.
- 17.11 17:41 Michał: ustalona zasada wspólnego dziennika na GitHubie.
- 17.11 17:42 Szef sztabu: przeczytałem dziennik; dopisałem w sekcji aplikacji ścieżki projektu, rebuild.sh i klucza. Korekta wpisu 17:38: APK v1.2 tylko zbudowałem, na beacon wgrał go Michał. Dalej: nic, aplikacje wstrzymane.
- 17.11 18:32 Michał: rozbudowa katalogu 3018 → 5110 (faza 4, sw v15). Nowe źródła: zakupychemiczne.pl, chemiashop.pl + hurtownie Szefa (nawynos24, hurtowniawielobranzowa, chemhurt, gamma-opakowania, radpak). 328 cen w dół (2 249,99 zł hurt). Włączone szef2.jsonl (600 nowych) i szef2_tansze.jsonl (81 tańszych). Testy 46+76 OK, wyszukiwarka ~200 ms / wyniki 22 ms. Beacon zaktualizowany. GitHub Pages v15 wstrzymane. catalog_internal.json bez zmiany formatu (pod CSV Shopify). APK nie ruszany.
- 17.11 18:38 Michał: włączone `incoming/sebastian2.jsonl` (613 nowych, 603 przyjętych, 589 ze zdjęciami; 10 okazja-hurtownia OutOfStock pominiętych) oraz `sebastian2_tansze.jsonl` (50 pozycji, 43 zastosowane, 184,24 zł hurt taniej, średnio 4,28 zł; 5 OutOfStock, 1 nie tańsza, 1 name-match bez rozmiaru). Nowe źródła: officehit.pl, albertopakowania.pl, okazja-hurtownia.pl, metroo.pl, epack.com.pl. Katalog **5713** (5615 ze zdjęciami), sw v15. Testy Playwright 46+76 OK (WebKit iPhone 13 + Chromium mobile), wyszukiwarka sugestie ~190 ms, wyniki ~22 ms. Publikacja na beacon annual-parrot-76 (live było jeszcze v14/3018, bo poprzedni upload 5110 się urwał). GitHub Pages v15 nadal wstrzymane. catalog_internal.json bez zmiany formatu. APK nie ruszany. CSV Shopify (`shopify/products.csv`) jest jeszcze na 5110 — trzeba go przebudować z aktualnego catalog_internal.json.
- 17.11 18:54 Michał: v15 jest na beacon (5696 plików, 2478 nowych wgranych). Live: meta n=5713, phase 4, sw.js `domownik-pwa-v15`. Zrzuty: shots/phase4/live_wk_home.png, live_wk_higiena.png, live_wk_search.png, live_wk_sprzatanie.png, live_wk_tansza_jacobs.png. Wygasa nadal 18.11 15:08 czasu Europe/Warsaw.
- 18.11 02:36 Szef sztabu: na życzenie Gracjana wypchnięte v15 na GitHub Pages (https://hizashi224.github.io/domownik/): 5713 produktów, 5615 ze zdjęciami, cache `domownik-pwa-v15`. Na Pages poszła wierna kopia v15 z beacona oraz zdjęcia z `fix/img_v15_backup` — lokalny folder `/workspace/sklep-subskrypcja` był już po niedokończonych naprawach v16 (sw v16, 5324 zdjęcia, przesunięte kategorie) i tego nie wypychałem. APK/AAB/Google Play nie ruszane.
- 25.11 20:00 Michał: v16 — naprawa zdjęć i kategorii (prośba Gracjana z 25.11: „żeby produkty pasowały do swojego opisu… kategorie i podkategorie miały sens”). Co: 972 złe zdjęcia podmienione na właściwe (źródło: karta produktu u dostawcy), 322 usunięte → puste okno, 684 przeniesienia kategorii, 13 nowych podkategorii, puste okno bez zastępczego rysunku, cache `domownik-pwa-v16`. Testy: 46/46 + 75/76 (jedyny FAIL to znany brak TLS dla leaflet w WebKit w środowisku testowym). Wypchnięte na GitHub Pages. Co dalej: przebudowany `shopify/products.csv` (v16) — Gracjan może zacząć trial Shopify, kiedy zechce; kolejne zdjęcia dla 391 pustych okien tylko z pewnego źródła.
