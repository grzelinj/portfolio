# Log postępu — AI Portfolio JG

Chronologiczny zapis pracy nad portfolio, sesja po sesji — co zrobione, jakie decyzje i dlaczego, co zostało. Czytaj od góry (najnowsze na górze).

---

## 2026-07-17 — 5. projekt: Asystent diety (wspólnie z Kacprem Rogowskim)

### Co zrobione
1. **DEMO_MODE dodany do `asystent-diety`** (apka Streamlit Kacpra Rogowskiego, wspólnie budowana) — analogicznie do FlightWatch: `config.py` czyta zmienną środowiskową `DEMO_MODE`, a `diet_advisor.py`/`meal_planner.py` w tym trybie zwracają canned przykładowe dane (rekomendacja diety, plan posiłków) zamiast wywoływać Anthropic Claude API. Klient Anthropic tworzony leniwie (`None` w DEMO_MODE), więc demo działa bez żadnego klucza API. Zmiany wypchnięte bezpośrednio do `kacperrogowski98/asystent-diety` (Jan ma dostęp jako collaborator).
2. **Wdrożenie na Streamlit Community Cloud** napotkało na twarde ograniczenie GitHuba: OAuth Streamlit dla konta Jana widzi tylko repozytoria publiczne, a fork prywatnego repo nie może zostać upubliczniony (`422: Private forks can't be made public`). Rozwiązanie: nowe, niezależne (nie-fork) publiczne repo `grzelinj/asystent-diety-demo` z tym samym kodem — wdrożone poprawnie pod `asystent-diety-gtxth6fei68tug3eknaj8g.streamlit.app`, `DEMO_MODE=true` w Secrets.
3. **Weryfikacja end-to-end przez Playwright** na żywym demo: utworzenie profilu, zapis danych, wygenerowanie rekomendacji diety — potwierdzone canned output "(przykład — tryb demo)", zero błędów, zero realnych wywołań API. Testowy profil usunięty z bazy po weryfikacji, żeby rekruterzy widzieli czysty stan startowy.
4. **5. karta projektu** dodana do `index.html` i `en.html` — z realnym zrzutem ekranu, odznaką współautorstwa "z Kacprem Rogowskim" / "with Kacper Rogowski", linkiem do demo i do `grzelinj/asystent-diety-demo`. Siatka projektów zmieniona z 3 na 2 kolumny (2×2), żeby 4 karty tools mieściły się równo bez osamotnionej karty w nowym rzędzie.

### Kluczowe decyzje i dlaczego
- Osobne, niezależne repo zamiast forka — jedyny sposób obejścia ograniczenia GitHuba (forki prywatnych repo są trwale prywatne).
- Link do repo na karcie wskazuje na `grzelinj/asystent-diety-demo` (publiczne, zawiera DEMO_MODE), nie na oryginalne `kacperrogowski98/asystent-diety` (prywatne, pełna wersja z realnym API).

---

## 2026-07-13 (ciąg dalszy) — Prawdziwe screeny, nowy hero copy, 4. projekt (Second Brain)

### Co zrobione
1. **Poprawka avatara w karcie "O mnie"** — powiększony z 64px kółka do 120×150px zaokrąglonego prostokąta, bo zdjęcie w garniturze było nierozpoznawalne przy takim przycięciu.
2. **Prawdziwe zrzuty ekranu trzech demo** zamiast szarych placeholderów — zrobione automatycznie przez headless Chromium (Playwright): FlightWatch, Setup Checker, Timeline Generator. Oba Streamlit-owe demo trzeba było "obudzić" (Streamlit Cloud usypia po bezczynności), Render też miał cold-start ~40s — skrypt czekał/pollował aż zniknie ekran ładowania.
3. **Nowy hero copy** — nagłówek zmieniony z krótkiego "Od finansów do budowania narzędzi AI" na pełny łuk: "Zmieniłem boisko na *dane* — zasady gry zostały te same." + rozszerzony akapit (koszykówka → nieruchomości/finanse → AI, "przygotowanie, dyscyplina, wynik"). Dobierane iteracyjnie — Jan odrzucił kilka krótszych/metaforycznych wersji, wybrał pełną, dosłowną.
4. **Intro-overlay i eyebrow rozszerzone** z "Finanse → Dane → AI" na "Koszykówka → Nieruchomości → Finanse → Dane → AI" (też `<title>`), żeby cały łuk kariery był widoczny od pierwszej sekundy.
5. **Czwarty projekt: Obsidian Second Brain.** Osobisty system zarządzania wiedzą (Whisper Flow + transkrypcja YouTube/Instagram + Claude Code kategoryzujący notatki w Obsidianie + cotygodniowy digest mailem) — opisany w `C:\Users\user\Documents\obsidian\CLAUDE.md` i `System-ktory-teraz-masz.md`. Dodany jako pełnoszerokościowa karta pod siatką pozostałych trzech projektów, z **diagramem architektury zamiast zrzutów ekranu** (świadoma decyzja — realne screeny ujawniałyby prywatne notatki/pocztę). Brak linku do repo/demo — działa wyłącznie lokalnie.

### Kluczowe decyzje i dlaczego
- Second Brain jako osobna, szersza karta (nie w 3-kolumnowej siatce) — to inny typ projektu (system/narzędzie osobiste, nie apka z demo), więc inny format prezentacji.
- Diagram zamiast screenów dla Second Brain — ochrona prywatności treści notatek/maila, a przy okazji lepiej pokazuje architekturę technicznie zorientowanemu rekruterowi niż zrzut ekranu Obsidiana.

### Co zostało / otwarte pytania
- Jan zgłosił, że chce, by "portfolio otwierało się w nowej karcie po kliknięciu" — nie ustalone jeszcze, o który dokładnie link/miejsce chodzi (karty projektów już mają `target="_blank"`). Do wyjaśnienia w kolejnej sesji.
- Własna domena, mockupy Power BI (czeka na materiały od koleżanki z CBRE), ewentualna publikacja repo Second Brain (wymagałoby sanitizacji `.env`/prywatnych notatek).

---

## 2026-07-10 do 2026-07-13 — Sekcja "O mnie" (timeline koszykarz→korporacja) + start wątku Power BI

### Co zrobione
1. **Sekcja "O mnie" przebudowana na chronologiczny timeline** — bullet po roku (2008–2024→dziś), od startu kariery koszykarskiej (mistrz Polski młodzików, reprezentacja Polski U16/U18/U19/U20) przez stypendium do Canisius College (USA, 2014–2015), studia (Politechnika Wrocławska → UMCS Lublin → Akademia Leona Koźmińskiego, licencjat 2019 / magisterka 2021), po karierę korporacyjną (Knight Frank 2020 → CBRE 2022 → Computershare 2023) i start nauki Pythona/AI (2024). Źródła faktów: Wikipedia Jana (link dodany jako odznaka w sekcji) + CV w Obsidianie (`Biznes/Jan_Grzelinski_Final_CV.md`) + skany dyplomów w OneDrive.
2. **8 zdjęć** (6 z kariery koszykarskiej: Canisius, Start Lublin ×3, Śląsk Wrocław, Księżak Łowicz; 2 korporacyjne z CBRE) skompresowane (z ~30MB do ~400KB łącznie) i umieszczone w `assets/o-mnie/`, przypisane do konkretnych lat w timeline (nie osobne "before/after" paski — zdjęcia chronologicznie przy właściwych wpisach, na wyraźną prośbę Jana o "smooth transition").
3. Cała sekcja "O mnie" zamieniona na rozwijaną kartę (`<details>`, jak karty projektów) zamiast statycznego bloku — avatar + teaser w nagłówku, pełny timeline po rozwinięciu.
4. **Nowy wątek: projekty Power BI do portfolio.** Jan zainstalował Power BI Desktop (przez Microsoft Store). Zaproponowane i zaakceptowane dwa tematy dopasowane do jego doświadczenia: (1) dashboard equity compensation/vesting, (2) dashboard portfela nieruchomości komercyjnych — oba na syntetycznych danych (nie prawdziwych danych pracodawców). Zbudowane **wizualne mockupy koncepcyjne** (HTML/SVG, nie prawdziwy Power BI) jako podgląd przed właściwą budową w Power BI Desktop — zapisane w `docs/powerbi-mockups/` (`equity-comp-dashboard.html`, `real-estate-dashboard.html`), oryginalnie opublikowane jako Claude Artifacts. Jan czeka też na przykłady realnych dashboardów od byłej koleżanki z CBRE (nie ma już do nich dostępu).

### Kluczowe decyzje i dlaczego
- Zdjęcia przypisane do konkretnych lat zamiast osobnych pasków "przed/po" — Jan chciał wyraźnie widocznej, płynnej transformacji koszykarz→korporacja wplecionej w samą narrację, nie oddzielnej galerii.
- Power BI: moja rola to przygotowanie danych/mockupów i prowadzenie krok po kroku przez UI (jak wcześniej ze Streamlit Cloud/Render) — nie da się tego zbudować bezpośrednio z terminala, to appka desktopowa.

### Co zostało / możliwe następne kroki
- Ocena mockupów Power BI przez Jana → decyzja, czy iść w tym kierunku wizualnym, czy zmienić.
- Realna budowa raportów w Power BI Desktop (dane + krok po kroku UI), potem publikacja (Power BI Service albo eksport) i dodanie jako kolejne karty projektów na portfolio.
- Ewentualna korekta tematów/danych, jeśli koleżanka z CBRE podeśle przykłady realnych dashboardów.
- Wciąż otwarte z poprzedniej sesji: własna domena, prawdziwe zrzuty ekranu w kartach istniejących projektów, wersja n8n Flight Trackera.

---

## 2026-07-09 — Start projektu → live portfolio + 3 działające demo

### Punkt wyjścia
Pusty folder projektu z zainstalowaną paczką skilli Matta Pococka. Cel: portfolio prezentujące narzędzia AI Jana (Flight Tracker, Setup Checker, Timeline Generator) dla przyszłych pracodawców, wzorowane na flow z filmu YouTube "Jak zbudować stronę www bez kodowania z Claude Code?" (Clot Guys) — pełna transkrypcja zapisana w Obsidianie: `Inbox/tworzenie stron 1.md`.

### Co zrobione
1. **Grillowanie / PRD** (skill `grilling`) — ustalono zakres: hero z animowanym wideo (klip Jana z Higgsfield), sekcja O mnie/CV, 3 case studies projektów, kontakt (proste linki, bez MailerLite/waitlisty). Zapisane w `docs/PRD.md`.
2. **Claude Design** — wygenerowano wstępny wygląd na bazie PRD + klipu wideo jako referencji stylu. Eksport (`Portfolio design wstępny-handoff.zip`) zaimportowany i rozpakowany.
3. **Przepisanie na czysty kod** — `index.html` napisany od zera na bazie eksportu Claude Design (usunięty wewnętrzny silnik `<x-dc>`/`support.js`, zastąpiony zwykłym HTML/CSS/JS). Naprawione martwe linki (GitHub, LinkedIn, mail — wcześniej `href="#"` placeholdery).
4. **Sprawdzenie realnego stanu 3 narzędzi** — okazało się, że żadne nie miało wtedy działającego live-linku:
   - Setup Checker (`setup-check-streamlit`) i Timeline Generator (`Timeline-Generator`) — czyste Streamlit, zero sekretów.
   - Flight Tracker (`flightwatch`) — dużo bardziej rozbudowany niż README sugerowało (Flask, ryanair-py, SerpAPI, Telegram, SMTP z prywatnego Gmaila, scheduler co 30 min). Nigdy nie było wdrożone publicznie.
5. **Decyzja: v1 bez live demo** (tylko case studies + linki do repo) — potem **zmiana decyzji** na wyraźną prośbę Jana: chciał, żeby rekruter mógł kliknąć i zobaczyć działającą apkę, nie tylko kod.
6. **DEMO_MODE w `flightwatch/app.py`** — dodana flaga env `DEMO_MODE`, która gate'uje `search_all`, `search_ryanair_multi`, `_explore_ryanair`, `_explore_wizzair` (zwracają przykładowe dane zamiast realnych zapytań) i wyłącza scheduler w tle. CRUD alertów zostaje w pełni funkcjonalny. Przetestowane lokalnie — brak realnych wywołań zewnętrznych. Wypchnięte na GitHub.
7. **Wdrożenie trzech demo:**
   - Setup Checker → Streamlit Community Cloud: https://grzelinj-setup-check-streamlit-app-itfuqx.streamlit.app/
   - Timeline Generator → Streamlit Community Cloud: https://timeline-generator-cpu.streamlit.app/
   - Flight Tracker (`DEMO_MODE=true`) → Render.com (free Web Service): https://flightwatch-yku0.onrender.com — Render zażądał karty do weryfikacji ($1 tymczasowa autoryzacja, bez obciążenia na planie Free); świadomie potwierdzone z Janem przed podaniem.
8. **Setup Checker — dopisany branding** na wzór Timeline Generatora: tytuł z ikoną, opis, logo Computershare (`logo.png`).
9. **Portfolio jako repo + hosting:**
   - `git init`, repo `grzelinj/portfolio` na GitHubie (publiczne).
   - **Zmiana względem filmu:** zamiast płatnego Hostingera → **GitHub Pages** (darmowe, bez wygasania z braku ruchu, zero nowego konta). Domena własna (`jangrzelinski.com`/`.pl`) świadomie odłożona na później — można dopiąć kiedykolwiek.
   - Live: **https://grzelinj.github.io/portfolio/**
10. **Fix mobile** — siatki 3-kolumnowe ("Wybrane projekty", "O mnie") nie miały breakpointu i ściskały się na telefonie. Dodany media query (`@media max-width:820px` → 1 kolumna) + nav bar wrap.

### Kluczowe decyzje i dlaczego
- **Case studies → live demo**: Jan chciał realnego "klik i zobacz", nie tylko GitHub.
- **DEMO_MODE zamiast pełnej funkcjonalności na Flight Trackerze**: ochrona limitów darmowych API (SerpAPI) i prywatnego Gmaila Jana przed nadużyciem przez publicznych odwiedzających.
- **Hostinger → GitHub Pages**: Jan już raz dostał nieoczekiwany rachunek (Timeline Generator na DigitalOcean) — priorytet to zero-kosztowe, trwałe rozwiązania. Zobacz też pamięć: `feedback-confirm-before-cost`.
- **n8n wersja Flight Trackera odłożona** — niedokończona, Jan chce do niej wrócić osobno później.

### Stan repozytoriów
- Portfolio: `github.com/grzelinj/portfolio` (publiczne), lokalnie `C:\Users\user\AI\AI Portfolio JG`
- Flight Tracker: `github.com/grzelinj/flightwatch` (prywatne), lokalnie `C:\Users\user\AI\Projekty AI do Portfolio\Flight AI Assistant\flighttracker`
- Setup Checker: `github.com/grzelinj/setup-check-streamlit` (publiczne), lokalny klon `C:\Users\user\AI\Projekty AI do Portfolio\clones\setup-check-streamlit`
- Timeline Generator: `github.com/grzelinj/Timeline-Generator` (publiczne), lokalny klon `C:\Users\user\AI\Projekty AI do Portfolio\clones\Timeline-Generator`

### Co zostało / możliwe następne kroki
- Własna domena (`jangrzelinski.com`/`.pl`) — opcjonalnie, kiedy Jan zechce.
- Dopracowanie tekstów i prawdziwych zrzutów ekranu w kartach projektów (obecnie placeholder "zrzut ekranu").
- Ewentualne dokończenie i pokazanie wersji n8n Flight Trackera.
- Możliwe dodanie kolejnych narzędzi do sekcji Projekty w przyszłości.

### Pełny kontekst
Zobacz `docs/PRD.md` (specyfikacja) i pamięć projektu w `project-ai-portfolio-jg` (jeśli wracasz do tego w nowej sesji Claude Code — poproś Claude o sprawdzenie pamięci).
