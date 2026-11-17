# Domownik – postępy (stan na 17.11.2026, 17:38 Warszawa)

## Online
- Sklep: https://annual-parrot-76.beacon.host/ (wygasa 18.11 15:08 czasu Europe/Warsaw, chyba że Gracjan przejmie link claim)
- APK Android **v1.2** (versionCode 4, 9 288 923 B, podpis debug): https://annual-parrot-76.beacon.host/domownik.apk – zawiera przycisk „Wyczyść koszyk” i cache `domownik-pwa-v14`. sha256: `2cb747e981c4ef54104285b7e97ab7f7a0ca5887b5cffb574cab171c6626aab1`
- Kopia GitHub Pages (Sebastian): https://hizashi224.github.io/domownik/ – czeka na odświeżenie (Sebastian potwierdza z Gracjanem)

## Wersja (faza 3 + reset koszyka)
- 3018 produktów, 11 kategorii z podkategoriami, 2995 ze zdjęciami, cache sw.js: **domownik-pwa-v14**
- Funkcje: kalkulator zużycia, gotowe listy, licznik oszczędności, program poleceń (demo), eko-tryb (366), mapa punktów odbioru (demo), 8 poradników od Sebastiana, panel właściciela z marżami, mega-menu, breadcrumbs, "Popularne"
- **Reset koszyka (17.11 17:36):** w szufladzie koszyka przycisk „Wyczyść koszyk” (ukryty, gdy koszyk pusty). Potwierdzenie we własnym oknie, potem toast „Koszyk wyczyszczony” z „Cofnij” przez 5 s. Czyści pozycje jednorazowe i subskrypcyjne w koszyku oraz `localStorage` (`domownik_cart`) i licznik w nagłówku. **Nie kasuje aktywnej subskrypcji w koncie** (`domownik_acct`).
- Pasek DEMO i stopka "Gracjan & Sebastian"
- Testy: Playwright Chromium mobile + WebKit iPhone 13 – testy fazy 3 i funkcji przechodzą, plus scenariusz: 3 produkty → wyczyść → licznik 0 → Cofnij → z powrotem 3, bez błędów JS. Zrzut: shots/phase3/live_wk_cart_reset.png

## Historia
- v9: 311 produktów + PWA od Sebastiana
- Faza 1: 761 → Faza 2: 1500 → Faza 3: 3018 (cel zmniejszony z 5000 do 3000, koniec rozbudowy katalogu)
- 17.11: publikacja APK v1.1 (WebViewAssetLoader, 3018 produktów)
- 17.11 17:36: przycisk resetu koszyka, cache v14
- 17.11 17:38: APK v1.2 (versionCode 4) z resetem koszyka, podmiana na beacon

## Do zrobienia
- Przejąć stronę na beacon przed 18.11 15:08 czasu Europe/Warsaw albo przejść na GitHub Pages
- Odświeżyć GitHub Pages (Sebastian, po zgodzie Gracjana) – już z resetem koszyka i APK v1.2
- Przetestować APK v1.2 na prawdziwym Androidzie
- privacy.html: uzupełnić dane administratora
- Google Play wstrzymane (brak konta / 25 USD); podpisany AAB: /workspace/Domownik-release.aab

## Zasady współpracy
- Przed publikacją na beacon uprzedzić Sebastiana; po zmianach poprosić Szefa sztabu o przebudowę APK
- Przy każdej zmianie podbić CACHE w sw.js
