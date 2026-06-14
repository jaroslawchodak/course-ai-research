# Kurs: Prompt engineering w badaniach naukowych

**Książka Quarto (format `book`)** do 3-dniowego kursu *„Od pojedynczych zapytań do agentów AI i inżynierii kontekstu"*. Renderuje się do **wielu plików HTML** (rozdział = osobna strona) z boczną nawigacją i wyszukiwarką — łatwa w czytaniu i poprawkach.

## Zawartość

| Plik / katalog | Rola |
|---|---|
| `_quarto.yml` | Konfiguracja książki (lista rozdziałów, motyw, output `_book/`). |
| `index.qmd` | Przedmowa. |
| `01-…` … `09-…qmd` | Rozdziały (każdy renderuje się do osobnego `.html`). |
| `theme/custom.scss` | Styl wizualny (motyw `litera`/`darkly`). |
| `images/` | Grafiki i zrzuty — wrzucaj wg oznaczeń `GRAFIKA [Gxx]/[Sxx]` w rozdziałach, **przed** renderem. |
| `_slajdy-kurs-AI.qmd` | Wersja **slajdowa** (revealjs) do projekcji; prefiks `_` → poza renderem książki. |
| `.github/workflows/publish.yml` | Automatyczna publikacja książki na GitHub Pages. |

> Materiały kursowe (szablony, demo agentowe, plan) są w głównym projekcie kursu, poza tym repozytorium.

## Render lokalny

```bash
quarto preview     # podgląd książki na żywo (odświeża się przy zapisie)
quarto render      # build całej książki → _book/
```

Wersję slajdową (do projekcji) renderujesz osobno:

```bash
quarto render _slajdy-kurs-AI.qmd --to revealjs
```

## Szybki start (następne kroki)

```bash
# 1) wrzuć grafiki do images/ (wg oznaczeń G01–G08, S01–S03 w rozdziałach)

# 2) pierwszy commit:
git -C /Users/jerry/dev/course-ai-research commit -m "Książka kursu AI — wersja startowa"

# 3) podłącz remote i wypchnij:
git -C /Users/jerry/dev/course-ai-research remote add origin git@github.com:<user>/course-ai-research.git
git -C /Users/jerry/dev/course-ai-research push -u origin main

# 4) na GitHub: Settings → Pages → Source: "GitHub Actions"
```

> Repo jest już zainicjalizowane (gałąź `main`). Jeśli `git commit` zgłosi brak tożsamości, ustaw raz: `git config --global user.name "…"` i `git config --global user.email "…"`.

## Publikacja na GitHub Pages

1. Wypchnij repozytorium na GitHub.
2. **Settings → Pages → Build and deployment → Source: „GitHub Actions".**
3. Każdy push do `main` (zmieniający rozdziały, `_quarto.yml`, `theme/**`, `images/**` lub workflow) odświeży stronę:
   `https://<użytkownik>.github.io/<repozytorium>/`

Workflow renderuje książkę w CI (`quarto render` → `_book/`, nie commitujemy HTML) i publikuje cały katalog `_book/`.

## Uwagi

- Stan narzędzi opisany w książce: **czerwiec 2026** — przed wykładem zweryfikuj liczby u źródeł.
- Książka ma `eval: false` (kod jest wyświetlany, nie wykonywany), więc CI nie potrzebuje Pythona/R.

---

## Wznowienie sesji

Po powrocie do pracy nad książką (kolejna sesja, dodanie grafik, drobne zmiany):

```bash
cd /Users/jerry/dev/course-ai-research
quarto preview     # podgląd książki na żywo
# opcjonalnie — asystent AI w kontekście tego repo:
claude
```

> **Nie potrzebujesz `claude --resume`.** Sesje są przypięte do katalogu, a kontekst do wznowienia
> masz w repo: `CLAUDE.md` (ładuje się automatycznie przy starcie `claude` w tym folderze) oraz to README.
