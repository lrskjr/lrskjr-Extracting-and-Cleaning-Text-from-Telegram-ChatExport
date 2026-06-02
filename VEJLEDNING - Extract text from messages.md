# Extract text from messages

Kort vejledning til at køre notebook'en *Extract text from messages.ipynb*, som parser en Telegram ChatExport, renser tekst og gemmer output til videre analyse.

## Forudsætninger

- Anaconda er installeret
- Du har downloadet og udpakket en Telegram-eksport (mappen skal indeholde *messages.html*)

## Biblioteker

Notebook'en bruger disse eksterne Python-pakker:

| Pakke | Formål |
|-------|--------|
| pandas | DataFrame, CSV-eksport, gruppering efter dag/uge/måned |
| beautifulsoup4 | Parsing af *messages.html* |
| jupyter | Til at køre notebook'en |

Resten (*pathlib*, *re*, *os*) følger med Python. BeautifulSoup bruger *html.parser*, som også er indbygget — *lxml* er ikke nødvendig.

## Opsætning (anbefalet)

Opret et dedikeret conda-miljø, så projektet er adskilt fra andre installationer.

Åbn Anaconda Prompt og kør:

```bash
conda create -n telegram-export python=3.11 pandas beautifulsoup4 jupyter -y
conda activate telegram-export
```

Tjek at pakkerne virker:

```bash
python -c "import pandas; from bs4 import BeautifulSoup; print('OK')"
```

## Start notebook

Gå til mappen med notebook'en og start Jupyter:

```bash
cd "sti\til\Telegram Desktop"
jupyter notebook
```

Åbn *Extract text from messages.ipynb* og vælg kernel/interpreter fra miljøet *telegram-export*.

## Før du kører

Ret stien i setup-cellen, så *folder* peger på din Telegram-eksportmappe (den med *messages.html*):

```python
folder = r'C:\sti\til\din\ChatExport_mappe'
os.chdir(folder)
```

Kør derefter alle celler (Run All).

## Output

Notebook'en opretter bl.a.:

- En CSV-fil med alle beskeder og metadata
- *clean_txt_files/* — én renset TXT-fil per besked
- *txt_files_grouped_by_day/* — tekst samlet per dag
- *txt_files_grouped_by_week/* — tekst samlet per uge
- *txt_files_grouped_by_month/* — tekst samlet per måned

Output er velegnet til videre analyse i f.eks. Voyant Tools, Orange eller R.

## Fejlfinding

| Problem | Løsning |
|---------|---------|
| *ModuleNotFoundError* | Aktivér miljøet: `conda activate telegram-export` |
| *FileNotFoundError* for *messages.html* | Tjek at *folder*-stien peger på den rigtige eksportmappe |
| Forkert kernel i Jupyter | Vælg kernel/interpreter fra miljøet *telegram-export* |
| *beautifulsoup4* mangler | Kør: `conda install beautifulsoup4 -y` |

## Hurtig reference: pakker i eksisterende miljø

Hvis du allerede bruger Anaconda base og bare vil installere det nødvendige:

```bash
conda install pandas beautifulsoup4 jupyter -y
```

Et dedikeret miljø anbefales dog til bedre reproducerbarhed.
