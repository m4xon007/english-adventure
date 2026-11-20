# English Adventure – Misja 25 🦄 — v1.4.0

Gra edukacyjna PWA dla dzieci uczących się angielskiego (klasy 1–3), zoptymalizowana dla dzieci z co najmniej rokiem nauki.

## Funkcje
- 12 bohaterów do wyboru, osobne profile, poziom klasy 1/2/3.
- 10 odblokowywanych krain tematycznych, 379 słówek w pliku `vocabulary.json`.
- Misje po 25 zadań; 2 próby na pytanie; 3 podpowiedzi na misję.
- Typy: EN→PL, PL→EN, brakująca litera, układanie liter, rozpoznawanie obrazka, wybór obrazka, słuchanie (gdy urządzenie obsługuje), uzupełnianie zdania.
- Punkty 10/5/3/0, naklejki, ranking lokalny, nagroda rodzicielska +5 minut grania na tablecie (raz na dzień i profil).
- Wybór słówek z priorytetem powtórek, przypominanie 1/3/7/14/30 dni, zapis przerwanej misji.
- Kopie zapasowe i odtwarzanie postępów w JSON.
- Brak reklam, backendu, analityki, logowania i zewnętrznych skryptów.

## GitHub Pages – publikacja BEZ Node.js
1. Utwórz nowe repozytorium GitHub, np. `english-adventure` (Public).
2. **Rozpakuj ZIP**. Wgraj **zawartość folderu** `english-adventure` do **głównego katalogu repozytorium** (nie sam plik ZIP i nie dodatkowy folder).
3. W GitHub otwórz **Settings → Pages → Build and deployment → Source: Deploy from a branch**.
4. Wybierz gałąź `main` i katalog `/(root)`; zapisz.
5. Po opublikowaniu otwórz `https://TWOJ-LOGIN.github.io/english-adventure/`.
6. Na Androidzie otwórz stronę w Chrome i wybierz **Zainstaluj aplikację** / **Dodaj do ekranu głównego**.

Możesz także użyć innej nazwy repozytorium: dzięki względnym ścieżkom aplikacja działa pod dowolną ścieżką GitHub Pages.

## Lokalne testy
Aplikacja nie potrzebuje procesu budowania ani instalowania zależności. Aby testować ją lokalnie, uruchom prosty serwer HTTP w tym folderze:

```bash
python -m http.server 8000
```

Potem otwórz `http://localhost:8000`.

**Uwaga:** dwukrotne kliknięcie `index.html` może nie działać, bo przeglądarki blokują pobieranie JSON z lokalnego `file://`.

## Dane i offline
Po pierwszym pełnym otwarciu online PWA buforuje pliki (service worker). Kolejne uruchomienia mogą działać offline. Postępy są przechowywane w `localStorage` **osobno dla adresu aplikacji i przeglądarki**, nie w chmurze. Usunięcie danych witryny powoduje utratę wyników — używaj eksportu kopii JSON w strefie rodzica. Zmiana repozytorium/adresu powoduje zmianę magazynu danych. Dostępność angielskiego głosu `speechSynthesis` offline zależy od tabletu i zainstalowanych głosów.

## Szczegóły gry i ograniczenia
- Poziomy klas sterują przede wszystkim trudnością losowania; słówka są pogrupowane w krainach. Na starcie polecamy klasę 2 dla dzieci mających już dwa lata nauki.
- Kolejną krainę odblokowuje się po **dwóch misjach** z bieżącej krainy, każdej z co najmniej 18 poprawnymi pytaniami.
- Za poprawną odpowiedź z podpowiedzią jest 3 pkt, bez podpowiedzi za pierwszym razem 10 pkt, za drugim 5 pkt; po 2 błędach 0 pkt.
- Misje korzystają z 25 różnych słów w miarę dostępności. Inteligentny dobór ma charakter prostego algorytmu priorytetów, bez AI online.
- Obrazki w zadaniach są reprezentowane przez emoji systemowe. Wygląd zależy od urządzenia; wersja z ilustracjami artystycznymi może zostać dodana później.
- W tej lekkiej wersji przechowywanie danych wykorzystuje `localStorage` (nie IndexedDB); jest wystarczające dla kilku profili i kilkuset słów, ale wymaga regularnych kopii zapasowych.
- Uzupełnianie zdania to na początek prosta rama językowa. W kolejnych aktualizacjach warto dodać autentyczne, zróżnicowane zdania i nagrania lektora.

## Licencja
Projekt stworzony na prywatne potrzeby edukacyjne. Słownictwo i kod są edytowalne.

## Aktualizacja v1.1.0
- Dostosowano 379 słówek do klas 1–3.
- Zadania z obrazkiem wymagają odpowiedzi po angielsku.
- Dodano polskie znaczenie w zadaniach z brakującą literą.
- Dodano odsłuch do każdego pytania.
- Zadania zdaniowe mają przygotowane przykłady.
- Ograniczono losowanie do słownictwa wybranej klasy.
- Dodano numer wersji i sprawdzanie aktualizacji.

Historyczne wyniki pozostają zapisane lokalnie; niezgodne niedokończone misje mogą zostać wyczyszczone.


## v1.2.0 – trzy etapy

Odkrywca: 18/25. Ekspert: 21/25. Mistrz: 22/25 oraz 18 poprawnych za pierwszym razem bez podpowiedzi. Krainy odblokowujemy od nowa; historia, wyniki, punkty i naklejki zostają zachowane. Dodano rozgrzewkę 10 pytań i preferencje dostępności.


## v1.2.1 — Wielki Sprawdzian

Każda kraina ma cztery etapy: Odkrywca (18/25), Ekspert (21/25), Mistrz Krainy (22/25 i 18 bez błędu) oraz Wielki Sprawdzian (22/25 i 18 bez błędu za pierwszym razem, bez podpowiedzi). Sprawdzian dobiera 25 różnych słów ze słownika danej krainy, preferując zadania pisowni, słuchania i zdań. Dopiero zaliczenie sprawdzianu odblokowuje kolejną krainę. Profile, stare wyniki, naklejki i ukończone etapy 1–3 pozostają zachowane; przy 3/4 gracz przechodzi do sprawdzianu.


## v1.4.0 — ciekawsze komentarze i rzadsza nagroda czasu
- 140 komentarzy pozytywnych, 24 zachęt do drugiej próby, 23 komunikatów do powtórki. Nie powtarzamy ostatnich 12 komentarzy.
- 240 różnych naklejek (emoji i warianty ozdobne), najpierw losujemy niezdobyte wzory.
- Bonus +5 minut wyłącznie za Wielki Sprawdzian (25/25 poprawnych, minimum 20 za pierwszym razem bez podpowiedzi, zero użytych podpowiedzi), maksimum jedna nagroda w danej krainie oraz jedna dziennie.
- Zwykły próg zaliczenia Wielkiego Sprawdzianu pozostaje bez zmian: 22/25 (88%) i 18 za pierwszym razem bez podpowiedzi.


## v1.4.0 – gra planszowa i program nauki
- Zachowano 10 krain jako interaktywną trasę na mapie; docelowo 12 po uzupełnieniu słownictwa.
- W każdej krainie 4 etapy i postać do uratowania. Wielki Sprawdzian obejmuje do 5/25 pytań z poprzednich krain.
- Pierwsze zaliczenie sprawdzianu i uratowanie postaci przyznaje informację o bonusie +5 min. Powtórne ukończenie tej samej krainy nie daje kolejnego bonusu.
- Księga Skarbów grupuje naklejki wg krain i pokazuje uratowanych bohaterów.
- Strefa rodzica zawiera 25 tematów gramatycznych z czterema statusami, osobno dla profilu. Zadania pozostają wyłącznie ze słówek.
- Historyczne profile, punkty i odblokowane krainy pozostają zachowane.


## v1.4.0 — rozszerzalne krainy
- Krainy i bohaterowie w `content/worlds.json`: można dodać następny rozdział z własną postacią, pod warunkiem uzupełnienia minimum 25 słówek z `grade: 1` i tym samym `world` w `vocabulary.json`.
- Księga, mapa, liczniki i odblokowania rosną automatycznie; poprzednie postępy nie są zerowane.
- Gramatyka w `content/grammar.json`: 25 tematów, statusy osobno dla profilu. `content/modules.json`: rejestr na przyszłość. Na razie pytania tylko ze słówek.
- Do 20% pytań Wielkiego Sprawdzianu przypomina poprzednie krainy.
- TypeScript/Vite i generowanie zadań gramatycznych pozostają osobnym etapem.
