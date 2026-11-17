# Domownik – postępy Michała (stan na 17.11.2026, 18:32 Warszawa)

## Online
- Sklep: https://annual-parrot-76.beacon.host/ (wygasa 18.11 15:08 czasu Europe/Warsaw, chyba że Gracjan przejmie link claim)
- APK Android **v1.2** (versionCode 4, 9 288 923 B, podpis debug): https://annual-parrot-76.beacon.host/domownik.apk – zawiera przycisk „Wyczyść koszyk” i cache `domownik-pwa-v14`. sha256: `2cb747e981c4ef54104285b7e97ab7f7a0ca5887b5cffb574cab171c6626aab1`
- Kopia GitHub Pages (Sebastian): https://hizashi224.github.io/domownik/ – nadal v14 (3018). Wypchnięcie v15 wstrzymane do odwołania (decyzja Gracjana, migracja na Shopify w toku). Folder źródłowy /workspace/sklep-subskrypcja/ jest gotowy do skopiowania (bez plików z .beaconignore).

## Wersja (faza 4, v15 – ok. 5000 produktów)
- **5110 produktów**, 11 kategorii z podkategoriami, **5026 ze zdjęciami**, cache sw.js: **domownik-pwa-v15**. Źródło prawdy: catalog_internal.json (format bez zmian, pod przyszły CSV Shopify).
- Per kategoria: higiena 990, sprzątanie 764, folie 643, pranie 484, papier 467, kuchnia 421, kawa 390, dom 261, przekąski 248, zwierzaki 239, dziecko 203.
- Funkcje bez zmian: kalkulator zużycia, gotowe listy, licznik oszczędności, program poleceń (demo), eko-tryb (teraz 691), mapa punktów odbioru (demo), 8 poradników od Sebastiana, panel właściciela z marżami, mega-menu, breadcrumbs, "Popularne", Wyczyść koszyk, pasek DEMO, stopka Gracjan & Sebastian
- **Reset koszyka (17.11 17:36):** w szufladzie koszyka przycisk „Wyczyść koszyk” (ukryty, gdy koszyk pusty). Potwierdzenie we własnym oknie, potem toast „Koszyk wyczyszczony” z „Cofnij” przez 5 s. Czyści pozycje jednorazowe i subskrypcyjne w koszyku oraz `localStorage` (`domownik_cart`) i licznik w nagłówku. **Nie kasuje aktywnej subskrypcji w koncie** (`domownik_acct`).
- Pasek DEMO i stopka "Gracjan & Sebastian"
- Testy: Playwright Chromium mobile + WebKit iPhone 13 – testy fazy 3 i funkcji przechodzą, plus scenariusz: 3 produkty → wyczyść → licznik 0 → Cofnij → z powrotem 3, bez błędów JS. Zrzut: shots/phase3/live_wk_cart_reset.png

## Historia
- v9: 311 produktów + PWA od Sebastiana
- Faza 1: 761 → Faza 2: 1500 → Faza 3: 3018 (cel zmniejszony z 5000 do 3000, koniec rozbudowy katalogu)
- 17.11: publikacja APK v1.1 (WebViewAssetLoader, 3018 produktów)
- 17.11 17:36: przycisk resetu koszyka, cache v14
- 17.11 17:38: APK v1.2 (versionCode 4) z resetem koszyka, podmiana na beacon
- 17.11 18:32: faza 4 / v15, 5110 produktów na beacon; GitHub Pages wstrzymane

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
  - 17.11 18:32 faza 4 / cache v15: katalog 3018 → **5110** produktów (5026 ze zdjęciami).
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
