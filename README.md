# Polish 2248

Gra logiczna w przeglądarce: łącz sąsiednie kafelki o tej samej wartości w długie łańcuchy, zbieraj monety, odblokowuj narzędzia i motywy, rywalizuj w rankingu. Działa jako aplikacja na telefon (PWA) i offline.

## Uruchomienie na GitHub Pages

1. Utwórz repozytorium na GitHubie i wgraj wszystkie pliki z tego folderu (z zachowaniem `icons/` i `.github/`).
2. W repozytorium wejdź w **Settings → Pages** i w polu **Source** wybierz **GitHub Actions**.
3. Wypchnij zmiany na gałąź `main`. Workflow `Deploy to GitHub Pages` opublikuje grę pod adresem `https://TWOJ-LOGIN.github.io/NAZWA-REPO/`.

## Instalacja na telefonie

- **Android (Chrome):** otwórz adres gry, a następnie w grze wybierz **Menu → Więcej → Zainstaluj aplikację** (lub menu przeglądarki ⋮ → *Zainstaluj aplikację*).
- **iPhone/iPad (Safari):** dotknij **Udostępnij → Do ekranu początkowego**.

Po instalacji gra ma własną ikonę, działa na pełnym ekranie i po pierwszym uruchomieniu także bez internetu.

### Prawdziwy plik APK (opcjonalnie)

Jeśli chcesz plik `.apk`/`.aab` (np. do Google Play), wygeneruj go z opublikowanego adresu w [PWABuilder](https://www.pwabuilder.com) lub narzędziem [Bubblewrap](https://github.com/GoogleChromeLabs/bubblewrap). Manifest i ikony (w tym maskable) są już gotowe.

## Logowanie Google i ranking (Firebase)

Konfiguracja Firebase jest na końcu `index.html` (`firebaseConfig`). Po wdrożeniu na GitHub Pages:

1. W konsoli Firebase wejdź w **Authentication → Settings → Authorized domains** i dodaj `TWOJ-LOGIN.github.io`. Bez tego logowanie Google nie zadziała na nowej domenie.
2. Ranking zapisuje w kolekcji `leaderboard` pola: `name`, `best`, `av` (awatar), `ac` (kolor awatara), `ts`. Jeśli masz reguły Firestore ograniczające pola dokumentu, dodaj `av` i `ac`.

Bez logowania gra działa w pełni lokalnie (zapis w przeglądarce).

## Pliki

| Plik | Rola |
| --- | --- |
| `index.html` | cała gra (HTML, CSS, JS) |
| `manifest.webmanifest` | dane aplikacji: nazwa, ikony, kolory |
| `sw.js` | service worker (praca offline) |
| `icons/` | ikony aplikacji |
| `.github/workflows/pages.yml` | automatyczne wdrożenie na GitHub Pages |

Po zmianie plików zwiększ `VERSION` w `sw.js`, aby użytkownicy dostali świeżą wersję z pamięci podręcznej.
