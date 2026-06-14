# Projekt: Książka kursu „Prompt engineering w badaniach naukowych"

Ten plik jest pamięcią/kontekstem projektu dla asystenta AI. Ładuje się automatycznie po uruchomieniu `claude` w tym katalogu. Język pracy: **polski**.

## Czym jest to repo
**Książka Quarto (format `book`)** do 3-dniowego kursu (24 godz.) o prompt engineeringu, inżynierii kontekstu i agentach AI dla multidyscyplinarnych pracowników naukowych. Renderuje się do **wielu plików HTML** (rozdział = osobna strona) → katalog `_book/`. Styl wizualny wzorowany na repo `/Users/jerry/dev/agentic-sociology` (motyw `litera`/`darkly`, `theme/custom.scss`, fonty Inter/JetBrains Mono).

Istnieje też **wersja slajdowa** `_slajdy-kurs-AI.qmd` (revealjs, do projekcji). Prefiks `_` → Quarto pomija ją przy renderze książki; renderuj osobno: `quarto render _slajdy-kurs-AI.qmd --to revealjs`.

## Lokalizacja i synchronizacja — WAŻNE
Repo celowo leży **poza iCloud** (`/Users/jerry/Documents/...` jest w iCloud), aby uniknąć konfliktów synchronizacji github/icloud. **Nie przenoś repo z powrotem do iCloud.**

## Struktura
- `_quarto.yml` — konfiguracja książki (lista rozdziałów, motyw, `output-dir: _book`)
- `index.qmd` — Przedmowa
- `01-fundament` · `02-dzien-1-zapytania` · `03-dzien-2-kontekst` · `04-notebooklm` · `05-deep-research` · `06-lokalne-llm` · `07-agenci-i-srodowiska` · `08-clustering-demo` · `09-integracja-ewaluacja` (`.qmd`)
- `theme/custom.scss` — styl
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

## Status (2026-06-15)
Przekształcono z pojedynczej prezentacji revealjs na **książkę Quarto** (10 plików: Przedmowa + 9 rozdziałów). Praca w toku — dochodzą grafiki i drobne zmiany. Repo na gałęzi `main`; **bez pierwszego commita i bez remote** (zostawione użytkownikowi; kroki w `README.md`).
