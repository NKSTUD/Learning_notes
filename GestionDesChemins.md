```python
# Gestion de fichiers et dossiers avec Python

## Modules utilisés :
- `os`: Création de fichiers et de dossiers
- `shutil`: Déplacement de fichiers
- `glob`: Recherche de chemins de fichiers

## Fonctions :
- `os.path.dirname`: Récupérer le dossier parent
- `os.path.splitext`: Récupérer l'extension d'un fichier
- `shutil.rmtree(p)`: Supprimer un dossier contenant d'autres dossiers (path=p)
- `del dictionnaire[Key]`: Supprimer une clé dans un dictionnaire

## Méthodes utiles de pathlib :
- `home()`: Retourne le dossier de l'utilisateur
- `cwd`: Retourne le dossier de travail actuel
- `mkdir()`: Crée un dossier
- `touch()`: Crée un fichier
- `write_text("Texte")`: Écrit un texte dans un fichier
- `read_text()`: Lit le texte d'un fichier
- `iterdir`: Récupère tous les fichiers et dossiers dans un dossier
- `glob("*.type de fichier")`: Récupère tous les fichiers d'un type donné
- `rglob("*.type")`: Récupère tous les fichiers, même dans les sous-dossiers
- `rename(Fichier1/f.name)`: Déplace un fichier dans Fichier1 avec son nom

## Exemples de manipulation de fichiers et dossiers :

### Création de dossiers et fichiers :
```python
p = Path.cwd() / "Dossier d'exemples" / "1" / "2" / "3"
p.mkdir(exist_ok=True, parents=True)
p = p / "python.json"
p.touch()
```

### Lecture et écriture dans un fichier :
```python
p = Path.cwd() / "Fichier d'ecriture"
p.touch()
p.write_text("Nouhan est un grand")
TEXTE = p.read_text()
print(TEXTE)
```

### Récupération de fichiers dans un dossier :
```python
p = Path.cwd()
for f in p.iterdir():
    print(f.name)
```

### Récupération de fichiers d'un type précis :
```python
p = Path.cwd()
for f in p.glob("*.json"):
    print(f.name)
```

### Tri des fichiers dans des dossiers spécifiques :
```python
dirs = {".png": "images", ".jpeg": "images", ...}
p = Path.home() / "Downloads"
for f in p.iterdir():
    Fichiers_Tries = p / dirs.get(f.suffix, "Autres")
    Fichiers_Tries.mkdir(exist_ok=True)
    f.rename(Fichiers_Tries / f.name)
```

## Constantes de projet définies :
```python
SOURCE_FICHIER = Path(__file__).resolve()
SOURCE_DOSSIER = SOURCE_FICHIER.parent
ROOT_DOSSIER = SOURCE_DOSSIER.parent
DATA_DOSSIER = SOURCE_DOSSIER / "DATA"
```

## Manipulation de dictionnaires :
```python
dictionnaire = {"Prenom": "Nouhan", "Ville": "Meknès", "Profession": "Ingénieur"}
PRENOM = dictionnaire.get("Prenom")
dictionnaire["Prenom"] = "Mohamed"
del dictionnaire["Ville"]

for cle, valeur in dictionnaire.items():
    print(f"{cle}: {valeur}")
```

## Exercice : Calcul de la somme des prix des films
```python
films = {"Le Seigneur des Anneaux": 12, "Harry Potter": 9, "Blade Runner": 7.5}
prix_total = sum(films.values())
print(prix_total)
```
