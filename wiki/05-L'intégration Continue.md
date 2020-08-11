# L'Intégration Continue

* 🔖 **Configuration**

___

## 📑 Configuration

Nos environnements de tests en place, nous pouvons utiliser un outil d'intégration continue. 
A chaque commit, un outil peut récupérer notre code source, mettre en place l'environnement, exécuter nos tests et nous avertir du passing ou du fail.

### 🏷️ **Travis**

* 🔗 [travis](https://travis-ci.org/)

Sur cet outil vous pouvez vous connecter avec votre compte github et ajouter des repositories. Une fois ajouté, dans l'onglet Settings/Webhooks vous devriez voir travis entant que service externe.

___

👨🏻‍💻 Manipulation

Ajouter le repository de votre projet sur Travis.

___

Nous pouvons avec Travis spécifier une plate-forme d'exécution et éxécuter des scripts en cas de succès ou d'échec.

**.travis.yml**

```yml
language: node_js
node_js:
    - "10"
before_script:
    - npm install
script:
    - npm test
```

___

👨🏻‍💻 Manipulation

Ajouter le fichier de configuration de Travis, pousser vers votre répertoire distant et observez votre build.

___
