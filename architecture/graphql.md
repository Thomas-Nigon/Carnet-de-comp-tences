# GraphQL

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL - ✅

### Différence entre REST et GraphQL - ✅

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

- les besoins auxquels répond GraphQL - ✅

### Les besoins auxquels répond GraphQL - ✅

#### 1. **Flexibilité des requêtes**

GraphQL permet aux clients de demander **exactement les données nécessaires**, ni plus ni moins. Cela évite les réponses contenant des données inutiles.

#### 2. **Réduction des appels multiples**

Grâce à sa capacité à regrouper plusieurs requêtes en une seule, GraphQL réduit la nécessité de faire des appels séparés pour récupérer des données provenant de différentes ressources.

#### 3. **Gestion des relations complexes**

Les requêtes GraphQL peuvent gérer facilement les relations entre différentes entités (ex. : utilisateurs et leurs articles). Cela simplifie l'extraction de données imbriquées.

#### 4. **Évolution de l'API**

Contrairement à REST, où l'ajout de nouvelles fonctionnalités peut nécessiter de nouveaux endpoints, GraphQL permet d'ajouter ou de modifier des types et des champs sans impacter les clients existants.

#### 5. **Réduction des surcharges réseau**

Utile pour les applications mobiles ou avec des connexions limitées, car GraphQL minimise le transfert de données.

#### 6. **Documentation et introspection automatiques**

- GraphQL propose des outils comme l'introspection, qui permettent aux développeurs d'explorer les types et les requêtes disponibles directement depuis l'API.
- la définition d'un schéma

### Définition d'un schéma - ✅

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
```

### QUERY - ✅

### Qu'est-ce qu'une Query ?

#### Définition

- Une **query** (ou requête) est une opération en GraphQL permettant de **récupérer des données** depuis le serveur.
- Elle est **lecture seule** : elle ne modifie pas les données, contrairement à une mutation.

#### Structure

- Une query spécifie :
  - Le type de données à récupérer.
  - Les **champs précis** nécessaires pour limiter la quantité de données retournées.
  - Éventuellement des **arguments** pour filtrer ou personnaliser la réponse.

#### Exemple de query

```graphql
query GetUser {
  user(id: "1") {
    id
    name
    email
  }
}
```

- Mutation - ✅

### Qu'est-ce qu'une Mutation ?

#### Définition

- Une **mutation** est une opération en GraphQL utilisée pour **modifier les données** sur le serveur (ajout, mise à jour ou suppression).
- Contrairement aux queries, les mutations peuvent entraîner des effets secondaires, comme le changement d'état de la base de données.

#### Structure

- Comme une query, une mutation spécifie :
  - Les données à modifier.
  - Les **champs spécifiques** à retourner en réponse (confirmation des modifications).

#### Exemple de mutation

```graphql
mutation CreateUser {
  createUser(name: "Thomas", email: "thomas@example.com") {
    id
    name
    email
  }
}
```

- Subscription - ✅

### Qu'est-ce qu'une Subscription ?

#### Définition

- Une **subscription** est une opération en GraphQL qui permet de **recevoir des mises à jour en temps réel** lorsque des changements se produisent sur les données du serveur.
- Elle utilise des **WebSockets** ou des protocoles similaires pour maintenir une connexion ouverte entre le client et le serveur.

#### Fonctionnement

- Contrairement aux queries et mutations, qui sont des opérations ponctuelles, une subscription reste active et envoie des notifications au client lorsque les événements définis se produisent.

#### Structure

- Une subscription définit :
  - L'événement ou l'action à surveiller.
  - Les **champs** à inclure dans les notifications envoyées au client.

#### Exemple de subscription

```graphql
subscription OnNewUser {
  userCreated {
    id
    name
    email
  }
}
```

#### Limitations

- Les subscriptions sont généralement plus complexes à mettre en place que les queries et mutations, nécessitant une gestion de connexion et de déconnexion. (web socket)
- Elles sont moins adaptées pour des applications avec des volumes de données très élevés.

## 💻 J'utilise

J'ai réalisé un projet de Deck Builder permettant d'afficher une liste de cartes et de les filtrer.
Lorsqu'un utilisateur se connecte, il peut voir les cartes disponibles et les ajouter à son deck.
FrontEnd : React TS, Apollo Client
BackEnd : NodeJS, Express, Apollo Server, GraphQL et SQlite

### Un exemple personnel commenté ✅

Voici un exemple de code typescript commenté :
Ici, j'ai défini un schéma pour un utilisateur. avec une entité, dans un fichier user.ts
dans le répertoire src/entities.

```typescript
@Entity()
@ObjectType()
export class User extends BaseEntity {
  @Field(() => ID)
  @PrimaryGeneratedColumn()
  id!: string;

  @Field()
  @Column({ length: 255 })
  username!: string;

  @Field()
  @Column({ length: 64, unique: true })
  email!: string;

  @Field()
  @Column({ length: 255 })
  password!: string;

  @BeforeInsert()
  @BeforeUpdate()
  async hashPassword() {
    this.password = await argon2.hash(this.password);
  }

  @Field(() => [Deck])
  @OneToMany(() => Deck, (deck) => deck.ownerId)
  decks!: Deck[];
}
```

J'ai ensuite défini un input pour créer un utilisateur, dans le même fichier user.ts

```typescript
@InputType()
export class UserInput extends BaseEntity {
  @Field({ nullable: true })
  username?: string;

  @Field({ nullable: true })
  email?: string;

  @Field({ nullable: true })
  password?: string;
}
```

J'ai ensuite défini un resolver pour la création d'un utilisateur, dans le fichier user.resolver.ts dans le répertoire src/resolvers afin de reste au plus proche d'une architecture MVC:

```typescript
@Resolver(User)
export class UserResolver {
  /**
   * Retrieves all users.
   * @returns {Promise<User[]>} A promise that resolves to an array of users.
   */
  @Query(() => [User])
  async getUsers() {
    const users = await User.find();
    if (!users) throw new Error("No users found");
    return users;
  }
}
```

### Utilisation dans un projet ❌ / ✅

[lien github](https://github.com/Thomas-Nigon/MTG_Backend_sqlite_TypeOrm/tree/feat/graphQlTransition)

Description :
J'ai réalisé un projet de Deck Builder permettant d'afficher une liste de cartes et de les filtrer.
Lorsqu'un utilisateur se connecte, il peut voir les cartes disponibles et les ajouter à son deck.
FrontEnd : React TS, Apollo Client
BackEnd : NodeJS, Express, Apollo Server, GraphQL et SQlite

### Utilisation en production si applicable❌ / ✅

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✅

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✅

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✅
- action 2 ❌ / ✅
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✅
- J'ai fait une [présentation](...) ❌ / ✅

```

```

```

```

```

```
