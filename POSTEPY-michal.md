# Domownik – postępy Michała (stan na 17.11.2026, 18:54 Warszawa)

## Online
- Sklep: https://annual-parrot-76.beacon.host/ (wygasa 18.11 15:08 czasu Europe/Warsaw, chyba że Gracjan przejmie link claim)
- APK Android **v1.2** (versionCode 4, 9 288 923 B, podpis debug): https://annual-parrot-76.beacon.host/domownik.apk – zawiera przycisk „Wyczyść koszyk” i cache `domownik-pwa-v14`. sha256: `2cb747e981c4ef54104285b7e97ab7f7a0ca5887b5cffb574cab171c6626aab1`
- Kopia GitHub Pages (Sebastian): https://hizashi224.github.io/domownik/ – nadal v14 (3018). Wypchnięcie v15 wstrzymane do odwołania (decyzja Gracjana, migracja na Shopify w toku). Folder źródłowy /workspace/sklep-subskrypcja/ jest gotowy do skopiowania (bez plików z .beaconignore) — teraz 5713 produktów, sw v15.

## Wersja (faza 4, v15 – ok. 5700 produktów)
- **5713 produktów**, 11 kategorii z podkategoriami, **5615 ze zdjęciami**, cache sw.js: **domownik-pwa-v15**. Źródło prawdy: catalog_internal.json (format bez zmian, pod przyszły CSV Shopify).
- Per kategoria: higiena 990, sprzątanie 952, folie 769, papier 567, kawa 499, pranie 484, kuchnia 421, dom 341, przekąski 248, zwierzaki 239, dziecko 203.
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
- Przejąć stronę na beacon przed 18.11 15:08 czasu Europe/Warsaw (GitHub Pages v15 wstrzymane; trwa przygotowanie pod Shopify)
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
  - Aplikacji nie przebudowywano (wstrzymane). GitHub Pages v15 nie wypychane (wstrzymane do odwołania).

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
- 17.11 17:42 Michał: decyzja Gracjana – każdy bot ma osobny plik postępów (ten plik: Michał).
- 17.11 18:32 Michał: rozbudowa katalogu 3018 → 5110 (faza 4, sw v15). Nowe źródła: zakupychemiczne.pl, chemiashop.pl + hurtownie Szefa (nawynos24, hurtowniawielobranzowa, chemhurt, gamma-opakowania, radpak). 328 cen w dół (2 249,99 zł hurt). Włączone szef2.jsonl (600 nowych) i szef2_tansze.jsonl (81 tańszych). Testy 46+76 OK, wyszukiwarka ~200 ms / wyniki 22 ms. Beacon zaktualizowany. GitHub Pages v15 wstrzymane. catalog_internal.json bez zmiany formatu (pod CSV Shopify). APK nie ruszany.
- 17.11 18:32 Michał: decyzja Gracjana („po prostu to zrób”) — migracja na **Shopify**, nie na Shopera. Paczka w `/workspace/sklep-subskrypcja/shopify/`: `products.csv` (**5110 wierszy, 5,8 MB**, jeden plik; przebudowane po fazie 4). GitHub Pages ma na razie tylko zdjęcia v14 (p1–p3019). Przed importem do Shopify trzeba wypchnąć img/p3020+ (2031 plików), inaczej te pozycje wejdą bez zdjęć., `build_shopify.py` (powtarzalny do ~5000), kolekcje, subskrypcje, motyw Dawn, 8 poradników, szkice regulaminu i polityki, `KROKI.md`. Zdjęcia w CSV: `https://hizashi224.github.io/domownik/img/p<id>.webp` (próbka 5 URL = HTTP 200). Shopify przyjmuje WebP przy produktach; folder `img-jpg/` to tylko fallback. Konta Shopify nie zakładałem — Gracjan otwiera trial (3 dni) według KROKI.md i daje znać. Katalog jest już na 5110 (cel 5000 osiągnięty). Skrypt jest powtarzalny. Aplikacji mobilnych nie ruszam.
- 17.11 18:38 Michał: włączone `incoming/sebastian2.jsonl` (613 nowych, 603 przyjętych, 589 ze zdjęciami; 10 okazja-hurtownia OutOfStock pominiętych) oraz `sebastian2_tansze.jsonl` (50 pozycji, 43 zastosowane, 184,24 zł hurt taniej, średnio 4,28 zł; 5 OutOfStock, 1 nie tańsza, 1 name-match bez rozmiaru). Nowe źródła: officehit.pl, albertopakowania.pl, okazja-hurtownia.pl, metroo.pl, epack.com.pl. Katalog **5713** (5615 ze zdjęciami), sw v15. Testy Playwright 46+76 OK (WebKit iPhone 13 + Chromium mobile), wyszukiwarka sugestie ~190 ms, wyniki ~22 ms. Publikacja na beacon annual-parrot-76 (live było jeszcze v14/3018, bo poprzedni upload 5110 się urwał). GitHub Pages v15 nadal wstrzymane. catalog_internal.json bez zmiany formatu. APK nie ruszany. CSV Shopify (`shopify/products.csv`) jest jeszcze na 5110 — trzeba go przebudować z aktualnego catalog_internal.json.
- 17.11 18:54 Michał: v15 jest na beacon (5696 plików, 2478 nowych wgranych). Live: meta n=5713, phase 4, sw.js `domownik-pwa-v15`. Zrzuty: shots/phase4/live_wk_home.png, live_wk_higiena.png, live_wk_search.png, live_wk_sprzatanie.png, live_wk_tansza_jacobs.png. Wygasa nadal 18.11 15:08 czasu Europe/Warsaw.
- 17.11 18:59 Michał: przebudowa `shopify/products.csv` skryptem `build_shopify.py` z aktualnego `catalog_internal.json` (v15, 5713 produktów, w tym 43 tańsze źródła Sebastiana). Wynik: **5713 wierszy, 6 486 301 B (6,2 MB)**, jeden plik — bez podziału (limit Shopify 15 MB). Ze zdjęciem w CSV: **5615**; bez zdjęcia (puste Image Src): **98**. Na GitHub Pages nadal v14 (meta n=3018, phase 3, v12): **2995** URL-i `p1.webp`–`p3019.webp` = HTTP 200, **2620** URL-i `p3020.webp`–`p5714.webp` = 404. Próbka: p1/p100/p1000/p2000/p2995/p3018/p3019 = 200; p3020/p3500/p4000/p5000/p5714 = 404. Zaktualizowane liczby w `shopify/KROKI.md`, `collections.md` (m.in. papier 567, sprzątanie 952, folie 769, kawa 499, dom 341; nowa podkolekcja `sc:dom-inne`; eko 68, duże opakowanie 704) oraz `README.md`. Konta Shopify nie zakładałem, nic nie wypychałem na GitHub.
- 25.11 20:00 Michał: v16 — naprawa zdjęć i kategorii (prośba Gracjana z 25.11: „żeby produkty pasowały do swojego opisu… kategorie i podkategorie miały sens”). Co: 972 złe zdjęcia podmienione na właściwe (źródło: karta produktu u dostawcy), 322 usunięte → puste okno, 684 przeniesienia kategorii, 13 nowych podkategorii, puste okno bez zastępczego rysunku, cache `domownik-pwa-v16`. Testy: 46/46 + 75/76 (jedyny FAIL to znany brak TLS dla leaflet w WebKit w środowisku testowym). Wypchnięte na GitHub Pages. Co dalej: przebudowany `shopify/products.csv` (v16) — Gracjan może zacząć trial Shopify, kiedy zechce; kolejne zdjęcia dla 391 pustych okien tylko z pewnego źródła.
- 25.11 20:35 Michał: v17 — „Ma być idealnie” (Gracjan, 25.11). Zdjęcia: +34 pewne (OCR + wzrok), Medosept 5 l miał etykietę 500 ml → zdjęcie przeniesione na 500 ml; 357 pustych okien zostaje (brak pewnego zdjęcia). Nazwy: 5115 uporządkowanych, 1170 marek poprawionych (np. „P G Fairy” → Fairy, worki „Stella” ze zdjęciem Service Pack → Service Pack), pole opakowania ujednolicone (4549). Kategorie: 90 przeniesień (np. proszki Bros na mrówki były w „Proszkach do prania”, chusteczki Pampers w „Pieluszkach”, sól do zmywarki w tabletkach). Kontrola zdjęć: OCR marki dla 5324 zdjęć + 132 pary prawie identycznych zdjęć obejrzane. Cache `domownik-pwa-v17`, `shopify/products.csv` przebudowany (5356 ze zdjęciem). Testy 46/46 + 75/76 (znany FAIL: brak TLS dla leaflet w WebKit w środowisku testowym). Co dalej: puste okna tylko z pewnego źródła.
