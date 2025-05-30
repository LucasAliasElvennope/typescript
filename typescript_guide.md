# TypeScript - Guide Essentiel

## Qu'est-ce que TypeScript ?

**TypeScript** est JavaScript avec des **types statiques**. Il détecte les erreurs pendant l'écriture du code, pas à l'exécution.

**Formule simple :** TypeScript = JavaScript + Types

## Installation rapide

```bash
# Installation globale
npm install -g typescript

# Ou dans un projet
npm install --save-dev typescript
```

## Premier exemple

### JavaScript vs TypeScript

**❌ JavaScript - Erreur invisible :**
```javascript
function calculer(prix, taux) {
    return prix * taux;
}

let total = calculer("100", 0.2); // "1000000000000000000000" au lieu de 20 !
console.log(total);
```

**✅ TypeScript - Erreur détectée :**
```typescript
function calculer(prix: number, taux: number): number {
    return prix * taux;
}

let total = calculer("100", 0.2); // ❌ Erreur : string au lieu de number
console.log(total);
```

## Types de base

```typescript
// Types primitifs
let nom: string = "Alice";
let age: number = 25;
let estActif: boolean = true;

// Tableaux
let nombres: number[] = [1, 2, 3];
let noms: string[] = ["Alice", "Bob"];

// Objets
let personne: {
    nom: string;
    age: number;
} = {
    nom: "Alice",
    age: 25
};
```

## Exemple pratique : Gestion d'utilisateurs

```typescript
// Définir un type (interface)
interface Utilisateur {
    id: number;
    nom: string;
    email: string;
    estActif: boolean;
}

// Fonction avec types
function creerUtilisateur(nom: string, email: string): Utilisateur {
    return {
        id: Math.random(),
        nom: nom,
        email: email,
        estActif: true
    };
}

// Fonction de validation
function validerEmail(email: string): boolean {
    return email.includes("@");
}

// Utilisation
let nouvelUtilisateur = creerUtilisateur("Alice", "alice@email.com");

if (validerEmail(nouvelUtilisateur.email)) {
    console.log("Utilisateur créé :", nouvelUtilisateur.nom);
} else {
    console.log("Email invalide");
}

// ❌ Cette ligne produirait une erreur :
// nouvelUtilisateur.age = 30; // Propriété 'age' n'existe pas !
```

## Compilation et exécution

```bash
# 1. Créer le fichier app.ts avec le code ci-dessus

# 2. Compiler vers JavaScript
tsc app.ts

# 3. Exécuter le JavaScript généré
node app.js
```

## Configuration simple (tsconfig.json)

```json
{
  "compilerOptions": {
    "target": "ES2018",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

## Commandes utiles

```bash
tsc app.ts              # Compiler un fichier
tsc --watch             # Compilation automatique
tsc --init              # Créer tsconfig.json
npx tsc                 # Utiliser la version locale
```

## Avantages concrets

| Problème JavaScript | Solution TypeScript |
|---------------------|-------------------|
| `user.nam` (typo) → `undefined` | ❌ Erreur : propriété 'nam' n'existe pas |
| `addNumbers(5, "10")` → `"510"` | ❌ Erreur : string au lieu de number |
| `users.pus(item)` (typo) → crash | ❌ Erreur : méthode 'pus' n'existe pas |
| Code difficile à comprendre | ✅ Types = documentation automatique |

## Quand utiliser TypeScript ?

**✅ Recommandé pour :**
- Projets avec plusieurs développeurs
- Applications complexes
- Code critique (finance, santé...)
- Projets à long terme

**❌ Peut-être excessif pour :**
- Petits scripts simples
- Prototypes rapides
- Projets temporaires

## Résumé

TypeScript ajoute de la **sécurité** et de la **clarté** à JavaScript sans en changer la logique. C'est un investissement qui paie sur les projets moyens et grands.

**Prochaines étapes :** Explore les interfaces, les génériques et l'intégration avec ton framework préféré !