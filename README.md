# bip
Transforming nutritional research with artificial intelligence. An Erasmus+ Blended Intensive Programme


Data and media assets for the Erasmus+ Blended Intensive Programme **"Transforming Nutrition with Artificial Intelligence"**, University of the Aegean, Department of Food Science & Nutrition — Lemnos, 28 Sep – 2 Oct 2026.

This repository exists so the course notebooks can load files **quickly and reliably** during class, without cloning, authentication, or large downloads. 
It is a teaching resource, not a research dataset.

## Structure

Files are organised **by type**, not by session — many assets are reused across several sessions.

* images/ food photographs used in image-recognition sessions
* datasets/ small tabular files (CSV) — nutrient tables, example records
* texts/ text corpora — example dietary recalls, prompts
* documents/ handouts, slides, reference PDFs


## How the notebooks use it

Everything is fetched by raw URL. Nothing needs to be cloned.

```python
BASE = "https://raw.githubusercontent.com/USERNAME/REPO/main/"
```

**Images**

```python
import requests
from PIL import Image
from io import BytesIO

def load_image(name):
    r = requests.get(BASE + "images/" + name, timeout=10)
    r.raise_for_status()
    return Image.open(BytesIO(r.content)).convert("RGB")

img = load_image("pizza.jpg")
```

**Tables**

```python
import pandas as pd
df = pd.read_csv(BASE + "datasets/nutrients.csv")
```

**Text**

```python
recalls = requests.get(BASE + "texts/example_recalls.txt", timeout=10).text.splitlines()
```

## Contents and sources

Each folder has its own `README.md` listing every file, what it contains, which session uses it, and where it came from. Start there.

| Folder | Index |
|---|---|
| `images/` | [images/README.md](images/README.md) |
| `datasets/` | [datasets/README.md](datasets/README.md) |
| `texts/` | [texts/README.md](texts/README.md) |
| `documents/` | [documents/README.md](documents/README.md) |



## Contact

Dr Stathis Kaloudis — stathiskaloudis@aegean.gr
Dr Vasiliki Bountziouka — vboun@aegean.gr

website [pygad.fns.aegean.gr/BIP](https://pygad.fns.aegean.gr/index.php/bip/)
[eclass course page]  https://eclass.aegean.gr/courses/FNS-OTHER166/ 
