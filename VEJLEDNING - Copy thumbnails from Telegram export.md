# Copy thumbnails from Telegram export

Kort vejledning til at køre notebook'en *Copy thumbnails from Telegram export.ipynb*, som finder thumbnail-billeder i en Telegram-eksport og kopierer dem til en separat mappe.

## Forudsætninger

- Anaconda er installeret
- Du har downloadet og udpakket en Telegram-eksport (mappen skal indeholde undermappen *photos*)

## Biblioteker

Notebook'en bruger disse eksterne Python-pakker:

| Pakke | Formål |
|-------|--------|
| tqdm | Progress bar under kopiering |
| jupyter | Til at køre notebook'en |

Resten (*pathlib*, *shutil*) følger med Python.

## Opsætning (anbefalet)

Opret et dedikeret conda-miljø, så projektet er adskilt fra andre installationer.

Åbn Anaconda Prompt og kør:

```bash
conda create -n telegram-export python=3.11 tqdm jupyter -y
conda activate telegram-export
```

Tjek at pakkerne virker:

```bash
python -c "from tqdm import tqdm; print('OK')"
```

Hvis du også skal køre *Extract text from messages.ipynb*, kan du installere alle pakker i samme miljø:

```bash
conda install pandas beautifulsoup4 -y
```

## Start notebook

Gå til mappen med notebook'en og start Jupyter:

```bash
cd "sti\til\Telegram Desktop"
jupyter notebook
```

Åbn *Copy thumbnails from Telegram export.ipynb* og vælg kernel/interpreter fra miljøet *telegram-export*.

## Før du kører

Ret stierne i kodecellen, så *source_dir* og *dest_dir* matcher din eksport. Første del af stien skal pege på din ChatExport-mappe:

```python
source_dir = Path(r'din\ChatExport_mappe\photos')
dest_dir = Path(r'din\ChatExport_mappe\thumbnail_photos')
```

- *source_dir* — mappen *photos* fra Telegram-eksporten
- *dest_dir* — destinationsmappe (oprettes automatisk ved kørsel)

Kør derefter de to kodeceller (import og kopiering).

## Hvad scriptet gør

Scriptet gennemgår alle filer i *photos/* og kopierer dem til *thumbnail_photos/*, hvis filnavnet indeholder *thumb* eller *thumbnail* (uanset store/små bogstaver). Thumbnails er mindre filer, som tager mindre plads og ofte er nemmere at arbejde videre med.

## Output

Mappen *thumbnail_photos/* oprettes i din eksportmappe med kopier af de fundne thumbnail-filer. Antal kopierede filer vises til sidst i notebook'en.

## Videre arbejde med billedmaterialet

Orange kan bruges til videre analyse af det indsamlede billedmateriale. Inspiration findes i denne [YouTube-playlist om Orange](https://youtube.com/playlist?list=PLmNPvQr9Tf-aRstY69vGAPO_c5RaceBhN&si=aUMSOPfzmJefq17Q).

## Fejlfinding

| Problem | Løsning |
|---------|---------|
| *ModuleNotFoundError* for *tqdm* | Aktivér miljøet og installer: `conda install tqdm -y` |
| *FileNotFoundError* for *photos* | Tjek at *source_dir* peger på den rigtige *photos*-mappe |
| 0 filer kopieret | Bekræft at eksporten indeholder thumbnail-filer (typisk med *thumb* i filnavnet) |
| Forkert kernel i Jupyter | Vælg kernel/interpreter fra miljøet *telegram-export* |

## Hurtig reference: pakker i eksisterende miljø

Hvis du allerede bruger Anaconda base og bare vil installere det nødvendige:

```bash
conda install tqdm jupyter -y
```

Et dedikeret miljø anbefales dog til bedre reproducerbarhed.
