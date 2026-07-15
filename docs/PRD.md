# PRD — Portfolio Jan Grzeliński

## Kontekst i cel

Jan Grzeliński (background: equity compensation / finanse w Computershare, wcześniej commercial real estate w CBRE i Knight Frank) przekwalifikowuje się w stronę danych i AI. Portfolio ma pełnić rolę wizytówki dla **przyszłych pracodawców** — pokazać nie tylko konkretne narzędzia AI, które zbudował, ale też narrację przejścia z solidnego zaplecza biznesowego w stronę data/analytics/AI.

**Grupa docelowa:** rekruterzy i hiring managerowie na role związane z danymi, analityką i automatyzacją/AI. Kluczowy przekaz: unikalne połączenie dojrzałości biznesowej (finanse/nieruchomości) z realnymi, wdrożonymi umiejętnościami budowania narzędzi AI.

## Zakres treści (v1)

### 1. Hero / strona startowa
- Ma robić spektakularne pierwsze wrażenie.
- **Element wow:** animowane hero na bazie wygenerowanego wideo (`ksiezyc koszykowka Higgsfield.mp4`, leży w root projektu) lub grafiki w podobnym stylu — ma być centralnym/tłowym elementem hero, nie osobną interakcją (bez logiki quizu/terminala — mniej pracy, ten sam efekt "wow" co w referencyjnym filmie).
- Krótki, mocny teaser tekstowy (do dopracowania na etapie Claude Design — na razie nie dopieszczamy tekstów, zgodnie z zasadą "done > perfect" z filmu referencyjnego).

### 2. O mnie / CV
- Pełne "O mnie": przebieg zawodowy (Computershare — equity compensation; CBRE, Knight Frank — commercial real estate).
- Narracja: budowanie narzędzi AI/automatyzacji jako świadoma, długoterminowa inwestycja w karierę data & analytics (nie tylko hobby).

### 3. Projekty — case studies (z live demo)

Każdy projekt jako karta: opis, stack, link "Zobacz demo" + link do repo. Wszystkie trzy narzędzia mają teraz darmowe, publicznie dostępne demo (patrz sekcja "Wdrożenie narzędzi" poniżej).

1. **Flight Tracker (FlightWatch)** — demo: https://flightwatch-yku0.onrender.com · repo: https://github.com/grzelinj/flightwatch (prywatne)
   System alertów cenowych dla lotów — monitoruje ceny 24/7, wysyła powiadomienia email, gdy cena spadnie poniżej limitu. Flask + SQLite, integracje z Ryanair/Wizz Air i SerpAPI (Google Flights). Publiczne demo działa w **trybie `DEMO_MODE`**: zwraca realistyczne przykładowe dane zamiast realnych zapytań do zewnętrznych API, a wysyłka e-maili/Telegrama jest wyłączona — CRUD alertów pozostaje w pełni interaktywny. Pełna, "żywa" wersja (prawdziwe API + prawdziwe powiadomienia) działa tylko lokalnie u Jana.

2. **Setup Checker** — demo: https://grzelinj-setup-check-streamlit-app-itfuqx.streamlit.app/ · repo: https://github.com/grzelinj/setup-check-streamlit (publiczne)
   Aplikacja Streamlit przetwarzająca dane z Excela i generująca gotowe zapytania SQL do setup checków — oszczędza do 70% ręcznej pracy.

3. **Timeline Generator** — demo: https://timeline-generator-cpu.streamlit.app/ · repo: https://github.com/grzelinj/Timeline-Generator (publiczne)
   Aplikacja Streamlit generująca harmonogramy projektów z szablonów Excel — zbudowana do automatyzacji tworzenia harmonogramów vestingowych (RSU/ESPP/SAYE) w Computershare; skróciła proces z godzin do minut.

4. **Obsidian Second Brain** — projekt osobisty, brak repo/demo (dotyka prywatnych notatek i poczty)
   System zarządzania wiedzą sterowany rozmową z Claude Code: transkrypcja (Whisper AI, youtube-transcript-api), automatyczna kategoryzacja/tagowanie/wikilinkowanie w Obsidianie, cotygodniowy digest mailem. Prezentowany jako pełnoszerokościowa karta z diagramem architektury (nie zrzutami ekranu — ochrona prywatności treści notatek), pod siatką pozostałych trzech projektów.

### 4. Kontakt
Proste linki kontaktowe: email, LinkedIn, GitHub (jako klikalne linki/ikony w hero i/lub stopce). Brak formularza, brak newslettera/MailerLite — to nie jest waitlista.

## Kierunek stylistyczny

- Punkt odniesienia stylu: wygenerowany klip wideo (`ksiezyc koszykowka Higgsfield.mp4`) — do wgrania jako referencja do Claude Design w kolejnym kroku.
- Tryb ciemny (dark mode) jako punkt wyjścia — do potwierdzenia/dopracowania na etapie Claude Design.
- Dopracowanie dokładnej palety, fontów i tekstów świadomie odłożone na etap Claude Design (iteracyjnie, żeby nie przepalać kredytów na tekstach, które i tak się zmienią).

## Podejście techniczne i wdrożeniowe

Replikujemy 1:1 flow z filmu referencyjnego ["Jak zbudować stronę www bez kodowania z Claude Code?" (Clot Guys)](https://www.youtube.com/watch?v=DKmgAsxFODg) — pełna transkrypcja zapisana w `tworzenie stron 1.md` w vaulcie Obsidian:

1. Paczka skilli Matta Pococka — już zainstalowana w tym projekcie.
2. Ten PRD (Krok 4 z filmu) — gotowy, zapisany tutaj.
3. **Claude Design** — nowy prototyp (high fidelity), upload tego PRD + `ksiezyc koszykowka Higgsfield.mp4` jako referencji stylu. Poprosić Claude Design o zadanie pytań doprecyzowujących i zaproponowanie 2–3 wariantów. Model: Opus, jeśli dostępny limit.
4. Eksport plików designu z powrotem do folderu tego projektu → dokończenie logiki w Claude Code.
5. GitHub repo dla strony: **`grzelinj/portfolio`, publiczne** — https://github.com/grzelinj/portfolio.
6. Hosting: **zmiana względem filmu.** Zamiast Hostingera (płatny plan + domena) wybraliśmy **GitHub Pages** — darmowy, zero dodatkowych kont, i kluczowe: **nie usypia/nie wygasa z braku ruchu** (w przeciwieństwie do Streamlit Cloud). Auto-deploy po `git push` do brancha `main`. Live pod: **https://grzelinj.github.io/portfolio/**. Własną domenę (`jangrzelinski.com`/`.pl`) można dopiąć w dowolnym momencie później (sama domena bez hostingu, tańsza opcja) — świadomie odłożone, nie blokuje niczego teraz.
7. Stack techniczny: zwykły statyczny HTML/CSS/JS (bez frameworka) — dopasowany do wyjścia Claude Design i najprostszy do wdrożenia na GitHub Pages.

## Wdrożenie narzędzi (live demo)

Zrobione po zbudowaniu portfolio, bo Jan chciał, żeby rekruter mógł kliknąć i zobaczyć działającą stronę, nie tylko kod na GitHubie:

- **Setup Checker** i **Timeline Generator** — bez zmian w kodzie, wdrożone na **Streamlit Community Cloud** (darmowe, logowanie przez GitHub, zero karty płatniczej).
- **Flight Tracker** — dodano flagę `DEMO_MODE` w `app.py` (gating realnych wywołań API, wyłączenie schedulera w tle), wdrożone na **Render.com** (darmowy "Web Service", wymagał podania karty do weryfikacji — $1 tymczasowa autoryzacja, bez obciążenia na planie Free). Auto-deploy po `git push`, tak jak reszta.

## Poza zakresem (v1)

- Wersja Flight Trackera w n8n (wspomniana w `Projekty AI do Portfolio/PROMPT_Claude_Projekty_Portfolio_v1.0 12.Jun.md`) — niedokończona, świadomie odłożona przez Jana na później.
- Pełna, "żywa" funkcjonalność Flight Trackera w publicznym demo (prawdziwe zapytania API, prawdziwe powiadomienia) — tylko bezpieczne dane przykładowe.
- Pełna ścieżka `to-spec` + issue tracker (projekt solowy — PRD jako zwykły plik markdown wystarcza).
