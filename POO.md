
# Programmation Orientée Objet

## Classes et Instances
- **Classe :** Objet principal à partir duquel on crée d'autres objets plus ou moins similaires appelés instances.
- La classe a les mêmes attributs (caractéristiques) que les instances.
- **Méthode :** Fonction associée à une classe.
- `Class.attribut` : Retourne l'attribut de cette classe.
- Créer une instance : `instance = Class()` (Exemple : `Voiture_O1 = Voiture()`).
- **Méthode de classe `@classmethod` :** Permet d'initialiser les caractéristiques d'une instance.
- **Méthode statique `@staticmethod` :** Une méthode qui n'a pas besoin d'argument pour fonctionner.
- **Méthode `__str__` :** Permet de retourner une chaîne de caractères spécifique quand on imprime une instance.

## Héritage
- `class Eleve(Personne):` : La classe `Eleve` hérite de la classe `Personne`.
- `super().methode(caracteristiques)` : Appeler une méthode de la classe parent (ne pas mettre `self` parmi les caractéristiques).
- `EleveX = Personne("Caracteristiques")` : Créer une instance de la classe `Eleve`.

## Polymorphisme
```python
def une_methode_de_la_classe_mere():
    super().methode()
    # Le retour voulu
```

- Importance : Utiliser des méthodes de la classe mère qui ont le même nom mais qui ne font pas la même chose.

## Exemple de Classe Voiture
```python
class Voiture:
    Voitures_crees = 0

    def __init__(self, marque, couleur, prix):
        Voiture.Voitures_crees += 1
        self.marque = marque
        self.couleur = couleur
        self.prix = prix

    @classmethod
    def lamborghini(cls):
        return cls(marque="Lombarghini", couleur='Noir', prix=250)

    @classmethod
    def Porsch(cls):
        """[Les méthodes de classes]

        Returns:
            [instances]: [Permet de faciliter la création des instances]
        """
        return cls(marque='Porsch', couleur='Rouge', prix=225)

    @staticmethod
    def afficher_Voiture_crees():
        print(f"Vous avez {Voiture.Voitures_crees} voitures dans votre garage")

    def __str__(self):
        return f"La voiture {self.Voitures_crees - 2} est {self.marque} de couleur {self.couleur} et un prix = {self.prix}"

class Taxi(Voiture):
    def __init__(self, marque, couleur, prix):
        super().__init__(marque, couleur, prix)
        super().afficher_Voiture_crees()

Lambo = Voiture.lamborghini()
Porsch = Voiture.Porsch()
Voiture.afficher_Voiture_crees()
taxi = Taxi('taxi bleu', 'Bleu', 200)
print(f"{taxi}\n{Voiture.lamborghini()}\n{Voiture.Porsch()}") 
```