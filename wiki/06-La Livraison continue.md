# La Livraison continue

* 🔖 **Définition**
* 🔖 **Build**

___

## 📑 Définition

La livraison continue est une approche d’ingénierie logicielle dans laquelle les équipes produisent des logiciels dans des cycles courts, ce qui permet de le mettre à disposition à n’importe quel moment. Le but est de construire, tester et diffuser un logiciel plus rapidement

___

## 📑 Build

A chaque build vous pouvez récupérer le contenu en vous rendant dans la liste des commits. Pour peupler la liste des releases il faut créer et pousser un tag.

### 🏷️ **Tags**


* 🔗 [tag](https://git-scm.com/book/en/v2/Git-Basics-Tagging)

Obtenir la liste des tags

```bash
git tag
```

Ajouter un tag

```bash
git tag 1.0.0 -m "1.0.0"
```

Pousser les tags

```bash
git push origin master --tags
```

L'idéal serait de créer un tag à chaque build passing en configurant une action dans le fichier de configuration de l'outil d'intégration continue pour son hook onsuccess afin de ne pas le faire manuellement.

___

👨🏻‍💻 Manipulation

Le Scrum Master en local synchronise sa branche dev qui possède un build passing, la fusionne avec sa branche master, ajoute un tag et pousse sa branche master avec les tags.

___
