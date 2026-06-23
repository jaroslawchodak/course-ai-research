# Projekt: Książka kursu „Prompt engineering w badaniach naukowych"

Ten plik jest pamięcią/kontekstem projektu dla asystenta AI. Ładuje się automatycznie po uruchomieniu `claude` w tym katalogu. Język pracy: **polski**.

## Czym jest to repo
**Książka Quarto (format `book`)** do 3-dniowego kursu (24 godz.) o prompt engineeringu, inżynierii kontekstu i agentach AI dla multidyscyplinarnych pracowników naukowych. Renderuje się do **wielu plików HTML** (rozdział = osobna strona) → katalog `_book/`. Układ wzorowany na repo `/Users/jerry/dev/agentic-sociology`; styl wizualny: **Claude Design / japandi** — motyw `litera` + `theme/custom.scss` (kremowe matowe tło #F1ECE3, akcenty szałwia #8A9A82 / łupek #6B7B8C / atrament #26211C, bez trybu ciemnego), fonty Inter/JetBrains Mono.

Istnieje też **wersja slajdowa** `_slajdy-kurs-AI.qmd` (revealjs, do projekcji). Prefiks `_` → Quarto pomija ją przy renderze książki; renderuj osobno: `quarto render _slajdy-kurs-AI.qmd --to revealjs`.

## Lokalizacja i synchronizacja — WAŻNE
Repo celowo leży **poza iCloud** (`/Users/jerry/Documents/...` jest w iCloud), aby uniknąć konfliktów synchronizacji github/icloud. **Nie przenoś repo z powrotem do iCloud.**

## Struktura
- `_quarto.yml` — konfiguracja książki (lista rozdziałów, motyw, `output-dir: _book`)
- `index.qmd` — Przedmowa
- `01-fundament` · `02-zapytania` · `03-halucynacje-dane` · `04-kontekst` · `05-dane-rag` · `06-notebooklm` · `07-deep-research` · `08-lokalne-llm` · `09-agenci-srodowiska` · `10-clustering-demo` · `11-etyka` · `12-integracja-ewaluacja` (`.qmd`) — podział na „dni" usunięty (materiał przelewa się między dniami); 12 rozdziałów wywiedzionych ze slajdów `_slajdy-kurs-AI.qmd`
- `theme/custom.scss` — styl japandi (paleta Claude Design)
- okładka: prompt w `index.qmd` (`[COVER]`); po wygenerowaniu `images/cover.png` odkomentuj `cover-image` w `_quarto.yml`
- `images/` — grafiki/zrzuty; **11 miejsc** oznaczonych w rozdziałach:
  - `GRAFIKA [G01–G08]` → **TYP: GENERATOR** (ilustracje; w komentarzu HTML jest gotowy prompt do generatora obrazów),
  - `GRAFIKA [S01–S03]` → **TYP: SCREENSHOT** (zrzuty ekranu),
  - ścieżki `![](images/…)` są **już wpięte** — wystarczy wrzucić pliki przed renderem.
- `_slajdy-kurs-AI.qmd` — wersja slajdowa (revealjs)
- `.github/workflows/publish.yml` — auto-publikacja książki na GitHub Pages (`quarto render` → `_book/`; HTML nie jest commitowany)
- `README.md`, `.gitignore`

## Konwencje
- Pracuj domyślnie w **Markdown**; nie konwertuj do PDF/innych formatów bez wyraźnej prośby.
- Rejestr książki: „wersja do czytania" — spokojna proza rozwijająca tezy, callouty (`.callout-note/-tip/-important/-warning`), kolumny `::: {.columns}`, mostek do następnego rozdziału na końcu każdego.
- Render/preview: `quarto preview` (książka). Publikacja: zob. `README.md`.
- Stan narzędzi opisany w treści: **czerwiec 2026** — przed wykładem zweryfikuj liczby/nazwy modeli u źródeł.

## Materiały źródłowe (w katalogu TYMCZASOWYM)
Treść powstała z materiałów w `/Users/jerry/Documents/01-warsztat/cowork/` (**tymczasowy** — nie polegaj na nim długoterminowo):
`kurs-AI-reserach.md` (raport źródłowy), `plan-kursu-01.md`, `kurs-pe/` (szablony + `modul-clustering-demo.md`), `clustering-demo/` (demo agentowe), `NotebookLM-book-reading-PL.md`.
Książka renderuje się samodzielnie — nie zależy od tych plików.

## Kluczowe moduły merytoryczne
NotebookLM (parser/generator) · hierarchia agentów (Claude Code/Cowork → Codex → Antigravity → OpenCode → Hermes/Pi) · edytory Zed/Cursor/Warp · lokalne LLM (Dense vs MoE, agentic vs chatbot z przykładem Bielik, kwantyzacja qat, komendy `ollama launch …`) · Clustering Demo (live, `clustering-demo/`).

## Status (2026-06-23)
Totalna przebudowa książki ze zaktualizowanych slajdów `_slajdy-kurs-AI.qmd`: **13 plików (Przedmowa + 12 rozdziałów)** — z 9 rozdziałów rozbito na 12 i dodano nowe treści (odwrotne prawa AI/Asimov + mapa odruchów w Fundamencie, wydzielony rozdz. „Halucynacje i ochrona danych", wydzielony „Dane i RAG", cztery tryby porażki w Deep research, **nowy rozdz. „Etyka i granice AI"**, AI disclosure w ewaluacji). Render czysty (`quarto render` → `_book/`).
- **Nowe grafiki AI [G16–G27]** w standardowym formacie `<!-- GRAFIKA [Gxx] -->` (TYP/PLIK/PROMPT po polsku) + osadzone `![](images/gXX-…)`: g16 trzy filary, g17 prawa Asimova, g18 odwrotne prawa, g19 metafora-biurko (Fundament); g20 markdown-xml (Zapytania); g21 zakotwiczenie, g22 trzy-srodowiska (Halucynacje); g23 tryby-porazki (Deep research); g24 prywatnosc-jakosc (Lokalne LLM); g25 czlowiek-w-petli (Agenci); g26 odpowiedzialnosc (Etyka); g27 piec-stacji (Integracja). Pliki PNG do wygenerowania i wrzucenia do `images/`.
- **Brakujące zrzuty ekranu** oznaczone blokiem `> 📸 MIEJSCE NA ZRZUT EKRANU:` (`s01-konwersja-terminal` w rozdz. Kontekst; `s02-notebooklm` w rozdz. NotebookLM). `s03-clustering-demo.png` już istnieje.

## Status (2026-06-15)
Przekształcono z pojedynczej prezentacji revealjs na **książkę Quarto**. Repo na gałęzi `main`; **bez pierwszego commita i bez remote** (zostawione użytkownikowi; kroki w `README.md`).
