Dla samej grafiki (podmiana pliku w images/ lub dodanie nowej) — ten sam, rutynowy flow co zawsze:

  cd /Users/jerry/dev/course-ai-research
  git add -A
  git commit -m "Aktualizacja ilustracji gXX"
  git push origin main

  Push do main automatycznie odpala workflow (images/** jest na liście wyzwalaczy), CI renderuje i
  podmienia stronę. Po ~1 min strona jest świeża.
  
  Dwie rzeczy warte uwagi przy grafikach:

  1. Podmiana istniejącego pliku pod tą samą nazwą (np. nadpisujesz images/g13-klastrowanie.png) —
  wystarczy powyższe. Ale przeglądarka może trzymać starą wersję w cache → po wejściu na stronę zrób
  twardy refresh Cmd+Shift+R.
  2. Nowa ilustracja pod nową nazwą — pamiętaj, że sam plik w images/ nic nie pokaże, dopóki nie ma do
  niego odwołania w rozdziale. Czyli oprócz wrzucenia PNG dodaj w .qmd:
  ![](images/gXX-nazwa.png){fig-align="center" width="100%"}
  2. (i to .qmd też złapie git add -A).

  Opcjonalnie przed pushem możesz lokalnie sprawdzić, że build jest czysty:
  quarto render        # lub: quarto preview — podgląd na żywo

  Cały ten przepis jest już w README.md w sekcji „Aktualizacja książki (kolejne update)", więc
  następnym razem masz go pod ręką w repo.