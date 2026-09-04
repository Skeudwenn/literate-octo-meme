# Gestion de Budget 💰

Une application web simple et intuitive pour gérer vos revenus et dépenses directement depuis votre navigateur. Aucune installation nécessaire, toutes les données sont sauvegardées localement.

![Capture d'écran de l'application](https://img.shields.io/badge/Statut-Actif-brightgreen) ![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

---

## ✨ Fonctionnalités

### 📊 Gestion des Transactions
- **Ajouter** des revenus et des dépenses avec nom, montant, catégorie, date et description
- **Modifier** les transactions existantes via une fenêtre modale
- **Supprimer** les transactions avec confirmation
- **Filtrer** par type (revenu/dépense) ou par catégorie

### 📈 Tableau de Bord
- **Solde actuel** affiché en temps réel (vert si positif, rouge si négatif)
- **Total des revenus** et **total des dépenses** calculés automatiquement
- **Graphique** de répartition par catégorie (top 5 catégories)

### 💾 Sauvegarde
- **Stockage local** : Toutes les données sont sauvegardées dans le `localStorage` du navigateur
- **Persistance** : Vos données restent disponibles même après fermeture du navigateur

### 📥/📤 Import/Export JSON
- **Exporter** vos données vers un fichier JSON
- **Importer** des données depuis un fichier JSON précédemment exporté
- **Validation** automatique du format JSON

---

## 🚀 Utilisation

### 1️⃣ Ouverture de l'application

Deux méthodes :

#### Méthode 1 : Directement depuis le fichier
```bash
# Ouvrez le fichier index.html dans votre navigateur
# Double-cliquez sur le fichier ou utilisez :
xdg-open index.html  # Linux
open index.html     # macOS
start index.html    # Windows
```

#### Méthode 2 : Via un serveur local (recommandé pour le développement)
```bash
# Avec Python 3
python3 -m http.server 8000

# Avec Node.js (npx)
npx serve

# Avec PHP
php -S localhost:8000
```
Puis ouvrez [http://localhost:8000](http://localhost:8000) dans votre navigateur.

---

### 2️⃣ Ajouter une transaction

1. Remplissez le formulaire en haut de la page :
   - **Nom** : Exemple "Salaire", "Courses", "Loyer"
   - **Montant** : Montant en euros (ex: 1500.50)
   - **Catégorie** : Sélectionnez ou ajoutez une catégorie
   - **Type** : Choisissez entre "Revenu" ou "Dépense"
   - **Date** : Date de la transaction (facultatif, par défaut aujourd'hui)
   - **Description** : Détails supplémentaires (facultatif)

2. Cliquez sur **Ajouter**

### 3️⃣ Gérer les transactions

- **Modifier** : Cliquez sur l'icône ✏️ à côté d'une transaction
- **Supprimer** : Cliquez sur l'icône 🗑️ (confirmation requise)
- **Filtrer** : Utilisez les menus déroulants pour filtrer par type ou catégorie

### 4️⃣ Importer/Exporter des données

#### Exporter
1. Cliquez sur **📥 Exporter (JSON)**
2. Un fichier JSON sera téléchargé automatiquement

#### Importer
1. Cliquez sur **📤 Importer (JSON)**
2. Collez le contenu de votre fichier JSON dans la zone de texte
3. Cliquez sur **Importer**

---

## 📦 Structure du Projet

```
literate-octo-meme/
├── index.html    # Application complète (HTML + CSS + JS)
└── README.md     # Ce fichier
```

---

## 🔧 Personnalisation

### Ajouter des catégories par défaut

Modifiez le tableau `categories` dans le `<script>` du fichier `index.html` :

```javascript
let categories = [
    "Salaire", 
    "Courses", 
    "Loisirs", 
    "Logement", 
    "Transport", 
    "Énergie", 
    "Santé", 
    "Autre",
    // Ajoutez vos catégories ici
    "Vacances",
    "Éducation"
];
```

### Modifier les couleurs

Les couleurs sont définies via des variables CSS dans le `<style>` :

```css
:root {
    --primary: #4f46e5;      /* Bleu principal */
    --success: #10b981;      /* Vert pour les revenus */
    --danger: #ef4444;       /* Rouge pour les dépenses */
    /* ... */
}
```

### Changer le format de devise

Modifiez la fonction `formatCurrency()` dans le JavaScript :

```javascript
function formatCurrency(amount) {
    // Format français avec virgule comme séparateur décimal
    return amount.toFixed(2).replace('.', ',');
}
```

---

## 📊 Format des Données JSON

Le fichier exporté a la structure suivante :

```json
{
  "transactions": [
    {
      "id": "1234567890123",
      "name": "Salaire",
      "amount": 2000,
      "category": "Salaire",
      "type": "income",
      "date": "2024-01-15",
      "description": "Salaire mensuel"
    },
    {
      "id": "1234567890124",
      "name": "Courses",
      "amount": 150.50,
      "category": "Courses",
      "type": "expense",
      "date": "2024-01-16",
      "description": "Supermarché"
    }
  ],
  "categories": [
    "Salaire",
    "Courses",
    "Loisirs",
    "Logement",
    "Transport",
    "Énergie",
    "Santé",
    "Autre"
  ],
  "exportedAt": "2024-01-20T12:00:00.000Z"
}
```

---

## 🌐 Compatibilité Navigateur

| Navigateur       | Support | Testé |
|-----------------|---------|-------|
| Chrome          | ✅ Oui  | ✅    |
| Firefox         | ✅ Oui  | ✅    |
| Safari          | ✅ Oui  | ❌    |
| Edge            | ✅ Oui  | ❌    |
| Opera           | ✅ Oui  | ❌    |

> ⚠️ **Note** : L'application utilise `localStorage` qui est supporté par tous les navigateurs modernes. Pour les anciens navigateurs, une alternative serait nécessaire.

---

## 💡 Conseils

1. **Sauvegardes régulières** : Exportez vos données régulièrement pour éviter toute perte en cas de problème avec le navigateur.

2. **Navigateur privé** : En mode navigation privée, le `localStorage` est effacé à la fermeture de la fenêtre.

3. **Synchronisation** : Pour synchroniser vos données entre plusieurs appareils, utilisez l'export/import avec un service de stockage cloud (Google Drive, Dropbox, etc.).

4. **Sécurité** : Les données sont stockées **uniquement dans votre navigateur**. Personne d'autre n'y a accès.

---

## 🤝 Contribuer

Les contributions sont les bienvenues ! Voici comment contribuer :

1. Fork le projet
2. Créez une branche pour votre fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Commitez vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Poussez vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

---

## 📜 Licence

Ce projet est sous licence **MIT**. Vous êtes libre de l'utiliser, le modifier et le distribuer.

---

## 📞 Contact

Pour toute question ou suggestion, n'hésitez pas à ouvrir une [issue](https://github.com/Skeudwenn/literate-octo-meme/issues) ou à me contacter.

---

**Bonnes économies !** 💸
