# 🏛️ POSSAD-Off

**Un comité de direction d'agents IA pour piloter une entreprise, construit avec Claude Code.**

Des agents IA spécialisés apportent des avis argumentés sur les sujets de l'entreprise,
dans un cadre où le dirigeant garde toujours la décision finale.

## 🧭 Principe fondateur

> **Le dirigeant décide. Les agents conseillent.**

Aucun agent ne signe, ne dépense, n'envoie ni ne déclare quoi que ce soit à la place du dirigeant.

## 🎯 Objectif

- Obtenir rapidement des avis spécialisés et argumentés sur les sujets de l'entreprise.
- Faire ressortir les contradictions entre domaines d'expertise.
- Garder une trace des décisions et de leurs raisons.
- Apprendre, étape par étape, la méthode de conception d'agents IA.

## 📌 État actuel

🚧 **Fondations en cours.** Les conventions sont posées ; la liste des agents est en discussion.

| Élément | État |
|---|---|
| Conventions du projet | ✅ validées |
| Liste et rôles des agents | 🚧 en discussion |
| Agents, modèles de documents, commandes | ❌ à faire |

## 📂 Structure

```text
POSSAD-Off/
├── README.md               présentation du projet (ce fichier)
├── CLAUDE.md               point d'entrée pour Claude Code → renvoie vers les conventions
├── AGENTS.md               point d'entrée pour Codex → renvoie vers les conventions
└── docs/
    ├── README.md           présentation du dossier docs
    └── conventions.md      toutes les règles du projet (source unique)
```

## 🚀 Démarrer

1. Ouvrir le dépôt dans **Claude Code** : `CLAUDE.md` charge automatiquement les conventions.
2. Avec **Codex**, `AGENTS.md` joue le même rôle.
3. Avant toute contribution, lire [`docs/conventions.md`](docs/conventions.md).

## 📏 Conventions en bref

| Sujet | Règle |
|---|---|
| Langue | contenu en français, noms de fichiers en anglais (`decision-register.md`) |
| Branches | `type/court-resume-en-anglais` depuis `main`, fusionnées dans `main` ; pas de `develop` |
| Pull Requests | `type: description courte en français` |
| Commits | `type(portée): description`, types `feat` `fix` `docs` `agent` `refactor` `chore`, **signés** |
| En-tête YAML | `titre`, `statut`, `mis-a-jour`, seulement sur les documents de référence |
| README | émojis obligatoires sur le titre et chaque section |

Le détail et les exemples sont dans [`docs/conventions.md`](docs/conventions.md).

## 🗺️ Feuille de route

1. ✅ **Conventions** : nommage, commits, branches, README.
2. 🚧 **Modèle de fonctionnement** : valider la liste des agents, leurs périmètres et le circuit des demandes.
3. ❌ **Agent pilote** : concevoir un premier agent, le tester sur un cas réel, puis en tirer le modèle de fiche.
4. ❌ **Comité complet** : autres agents, modèles de documents, mémoire de l'entreprise, commandes.
5. ❌ **Application** : envisager une vraie interface, en s'appuyant sur la [méthode BMAD](https://docs.bmad-method.org).

## 🔒 Données sensibles

Le dossier `private/` est ignoré par Git. Aucune donnée personnelle, bancaire ou contractuelle non publique
ne doit être commitée.

## 🌱 Origine

POSSAD-Off reprend les idées du projet POSSAD (gouvernance, agents spécialisés, registre des décisions)
dans une version allégée, pensée pour Claude Code, et s'inspire de la [méthode BMAD](https://docs.bmad-method.org).
