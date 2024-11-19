# GraphQL

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✔️

### Différence entre REST et GraphQL ✔️

#### REST

- **Structure** : Basé sur des **endpoints** multiples (ex. : `/users`, `/users/:id`), chaque endpoint correspondant à une ressource ou une action spécifique.
- **Données retournées** : Les réponses incluent souvent des données supplémentaires ou inutiles, ce qui peut augmenter la charge réseau.
- **Appels multiples** : Nécessite plusieurs appels pour obtenir des données provenant de différentes ressources.

#### GraphQL

- **Structure** : Utilise un **seul endpoint** (généralement `/graphql`) pour interroger une API.
- **Requêtes précises** : Permet de spécifier exactement les données souhaitées dans la requête, réduisant le volume des réponses.
- **Appels combinés** : Peut combiner plusieurs ressources dans un seul appel grâce à sa structure de requêtes imbriquées.

#### Avantages clés

- **GraphQL** : Plus flexible, réduit les surcharges réseau, idéal pour des interfaces complexes ou mobiles.
- **REST** : Plus simple et convient à des API classiques, bien établies.

- les besoins auxquels répond GraphQL ✔️

### Les besoins auxquels répond GraphQL ✔️

#### 1. **Flexibilité des requêtes**

- GraphQL permet aux clients de demander **exactement les données nécessaires**, ni plus ni moins. Cela évite les réponses contenant des données inutiles.

#### 2. **Réduction des appels multiples**

- Grâce à sa capacité à regrouper plusieurs requêtes en une seule, GraphQL réduit la nécessité de faire des appels séparés pour récupérer des données provenant de différentes ressources.

#### 3. **Gestion des relations complexes**

- Les requêtes GraphQL peuvent gérer facilement les relations entre différentes entités (ex. : utilisateurs et leurs articles). Cela simplifie l'extraction de données imbriquées.

#### 4. **Évolution de l'API**

- Contrairement à REST, où l'ajout de nouvelles fonctionnalités peut nécessiter de nouveaux endpoints, GraphQL permet d'ajouter ou de modifier des types et des champs sans impacter les clients existants.

#### 5. **Réduction des surcharges réseau**

- Utile pour les applications mobiles ou avec des connexions limitées, car GraphQL minimise le transfert de données.

#### 6. **Documentation et introspection automatiques**

- GraphQL propose des outils comme l'introspection, qui permettent aux développeurs d'explorer les types et les requêtes disponibles directement depuis l'API.

- la définition d'un schéma

### Définition d'un schéma ✔️

#### Qu'est-ce qu'un schéma ?

- Un schéma est une **description formelle de la structure des données** exposées par une application ou une API.
- Il définit les types de données disponibles, leurs relations, ainsi que les opérations possibles (requêtes, mutations, abonnements).

#### En GraphQL

- Le schéma est écrit en **GraphQL Schema Definition Language (SDL)**.
- Il précise :
  - Les **types** (ex. : `User`, `Post`, `Comment`).
  - Les **champs** de chaque type (ex. : `id`, `name`, `content`).
  - Les **requêtes** pour récupérer des données (`query`).
  - Les **mutations** pour modifier ou créer des données (`mutation`).
  - Les **abonnements** pour des mises à jour en temps réel (`subscription`).

#### Exemple simple

```graphql
type User {
  id: ID!
  name: String!
  email: String!
}

type Query {
  user(id: ID!): User
  allUsers: [User]
}

type Mutation {
  createUser(name: String!, email: String!): User
}

- Query ❌ / ✔️
- Mutation ❌ / ✔️
- Subscription ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
```
