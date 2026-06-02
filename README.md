# Telegram ChatExport — tekst og thumbnails

Korte Python-notebooks til behandling af data fra Telegram ChatExport. Velegnet til videre analyse i f.eks. Orange og Voyant Tools.

---

## Dansk

### Notebooks

**[Extract text from messages.ipynb](Extract%20text%20from%20messages.ipynb)**  
Parser *messages.html* fra en Telegram-eksport, udtrækker metadata og beskedtekst, renser teksten og gemmer output som CSV og TXT-filer (per besked, dag, uge og måned).

**[Copy thumbnails from Telegram export.ipynb](Copy%20thumbnails%20from%20Telegram%20export.ipynb)**  
Finder thumbnail-billeder i mappen *photos* og kopierer dem til *thumbnail_photos* til lettere videre arbejde med billedmaterialet.

### Vejledninger

- [VEJLEDNING - Extract text from messages.md](VEJLEDNING%20-%20Extract%20text%20from%20messages.md)
- [VEJLEDNING - Copy thumbnails from Telegram export.md](VEJLEDNING%20-%20Copy%20thumbnails%20from%20Telegram%20export.md)

### Krav

Anaconda og Python 3.11. Eksterne pakker: *pandas*, *beautifulsoup4*, *tqdm*, *jupyter*.

```bash
conda create -n telegram-export python=3.11 pandas beautifulsoup4 tqdm jupyter -y
conda activate telegram-export
```

---

## English

### Notebooks

**[Extract text from messages.ipynb](Extract%20text%20from%20messages.ipynb)**  
Parses *messages.html* from a Telegram export, extracts message metadata and text, cleans the text, and saves outputs as CSV and TXT files (per message, day, week, and month).

**[Copy thumbnails from Telegram export.ipynb](Copy%20thumbnails%20from%20Telegram%20export.ipynb)**  
Finds thumbnail images in the *photos* folder and copies them to *thumbnail_photos* for easier further work with the image material.

### Guides

- [VEJLEDNING - Extract text from messages.md](VEJLEDNING%20-%20Extract%20text%20from%20messages.md)
- [VEJLEDNING - Copy thumbnails from Telegram export.md](VEJLEDNING%20-%20Copy%20thumbnails%20from%20Telegram%20export.md)

### Requirements

Anaconda and Python 3.11. External packages: *pandas*, *beautifulsoup4*, *tqdm*, *jupyter*.

```bash
conda create -n telegram-export python=3.11 pandas beautifulsoup4 tqdm jupyter -y
conda activate telegram-export
```
