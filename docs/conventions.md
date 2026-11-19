---
titre: Conventions du projet POSSAD-Off
statut: valide
mis-a-jour: 2026-11-19
---

# Conventions du projet POSSAD-Off

Ce document est la **source unique** des règles du projet.
`CLAUDE.md` (Claude Code) et `AGENTS.md` (Codex) se contentent d'y renvoyer : aucune règle n'est recopiée ailleurs.

Les mots **DOIT**, **NE DOIT PAS** et **PEUT** ont leur sens habituel : obligation, interdiction, faculté.

---

## 1. Langue

- Le **contenu** des documents, des messages de commit et des échanges DOIT être en **français**.
- Les **noms** de fichiers, de dossiers et de branches DOIVENT être en **anglais** (voir section 2).

## 2. Noms de fichiers et de dossiers

### Règle générale

Un nom de fichier ou de dossier DOIT être :

- en **anglais** ;
- en **minuscules** ;
- en **kebab-case** : mots séparés par des tirets `-` ;
- **sans accents, espaces ni caractères spéciaux**.

| ✅ Correct | ❌ Incorrect | Problème |
|---|---|---|
| `decision-register.md` | `registre-decisions.md` | nom en français |
| `risk-register.md` | `Risk_Register.md` | majuscules et underscore |
| `company-profile.md` | `company profile.md` | espace |
| `ceo-summary.md` | `synthèse-ceo.md` | accent et français |

### Exceptions

| Fichier | Raison |
|---|---|
| `README.md`, `CLAUDE.md`, `AGENTS.md` | noms imposés par GitHub, Claude Code et Codex |
| `SKILL.md`, `.github/…` et autres fichiers d'outils | format imposé par l'outil |
| contenu de `private/` | données personnelles, jamais versionnées |

### Éléments numérotés ou datés

| Élément | Format | Exemple |
|---|---|---|
| Décision du dirigeant | `DEC-NNN` (dans le registre) | `DEC-007` |
| Dossier de travail | `AAAA-MM-JJ-sujet-court/` | `2026-11-18-pricing-review/` |

## 3. En-tête YAML

### Documents concernés

L'en-tête est **obligatoire uniquement sur les documents de référence** :

- les documents de `docs/` (méthode, conventions, modèle de fonctionnement) ;
- les registres et fiches de la mémoire de l'entreprise (profil, chiffres clés, registres de décisions et de risques).

Il NE DOIT PAS être ajouté :

- aux `README.md` ;
- aux fichiers d'outils (`CLAUDE.md`, `AGENTS.md`, `.claude/**`) ;
- aux notes et livrables des dossiers de travail.

### Format

Trois champs, dans cet ordre :

```yaml
---
titre: Registre des décisions
statut: brouillon
mis-a-jour: 2026-11-18
---
```

| Champ | Valeurs autorisées |
|---|---|
| `titre` | titre du document, en français |
| `statut` | `brouillon` · `valide` · `obsolete` |
| `mis-a-jour` | date de la dernière modification significative, au format `AAAA-MM-JJ` |

L'auteur, l'historique et les versions ne sont **pas** dans l'en-tête : Git les conserve.
Il n'y a donc **pas de journal des modifications** dans les documents.

## 4. Fichiers README.md

### Rôle

Un `README.md` est la **porte d'entrée d'un dossier**. Il explique en peu de lignes :

1. à quoi sert le dossier ;
2. ce qu'il contient ;
3. les règles propres à ce dossier, s'il y en a.

Le `README.md` racine présente le projet dans son ensemble et explique comment démarrer.
Chaque dossier principal DOIT avoir son `README.md` (5 à 30 lignes suffisent hors racine).

### Émojis : obligatoires

Les `README.md` DOIVENT utiliser des émojis **pertinents** pour structurer et dynamiser la lecture :

- le **titre principal** (`#`) DOIT commencer par un émoji ;
- chaque **titre de section** (`##`) DOIT commencer par un émoji ;
- **un seul émoji par titre**, choisi pour son sens, pas pour décorer ;
- dans le corps du texte, les émojis PEUVENT servir de repères dans les listes et tableaux (statuts, avertissements) ;
- les émojis NE DOIVENT PAS apparaître dans les blocs de code, les noms de fichiers ni les messages de commit.

Pour que les mêmes émojis aient toujours le même sens d'un README à l'autre :

| Émoji | Usage |
|---|---|
| 🎯 | objectif, raison d'être |
| 🧭 | principe, règle fondatrice |
| 📂 | structure, contenu du dossier |
| 🚀 | démarrage, mise en route |
| 🤖 | agents IA |
| 📏 | conventions, règles |
| 🗺️ | feuille de route |
| 📌 | état actuel |
| 🔒 | données sensibles, confidentialité |
| ⚠️ | avertissement |
| ✅ / ❌ | correct / incorrect, fait / non fait |
| 🚧 | en construction |

### Exemple de README de dossier

```markdown
# 🏢 company

## 🎯 Rôle
Mémoire durable de l'entreprise, lue par tous les agents avant d'agir.

## 📂 Contenu
| Fichier | Contenu |
|---|---|
| `company-profile.md` | identité, activité, juridiction |
| `decision-register.md` | décisions prises par le dirigeant |

## 📏 Règles
Seul le dirigeant valide une modification de ces fichiers.
```

## 5. Branches et Pull Requests

Le modèle est volontairement simple : **pas de branche `develop`**, et une seule règle de nommage,
quel que soit l'outil utilisé (humain, Claude Code, Codex).

### Nom des branches

```text
type/court-resume-en-anglais
```

- `type` : uniquement `feat`, `fix`, `docs`, `agent` ou `chore` (même sens que pour les commits, section 6) ;
- `court-resume-en-anglais` : quelques mots en anglais, en minuscules et en kebab-case.

| ✅ Correct | ❌ Incorrect | Problème |
|---|---|---|
| `docs/add-project-conventions` | `claude/business-guidance-o3ahmg` | préfixe d'outil interdit |
| `feat/add-agent-registry` | `feature/agent-registry` | type non autorisé |
| `agent/define-cfo-scope` | `agent/définir-le-cfo` | français et accent |
| `fix/broken-register-link` | `fix/Broken_Link` | majuscules et underscore |

Aucun préfixe propre à un outil (`claude/`, `codex/`…) n'est toléré.
La seule branche permanente est `main`, version de référence toujours propre.

### Cycle de vie

- une branche = **un seul sujet**, de courte durée ;
- elle part de `main` et revient dans `main` par une Pull Request ;
- **la fusion est décidée par le dirigeant** ;
- la branche est supprimée après la fusion.

### Titre des Pull Requests

```text
type: description courte en français
```

- `type` : le même que celui de la branche ;
- description à l'infinitif, sans point final.

| Branche | Titre de la Pull Request |
|---|---|
| `docs/add-project-conventions` | `docs: établir les conventions du projet` |
| `feat/add-agent-registry` | `feat: ajouter le registre des agents` |

## 6. Commits

### Format du titre

```text
type(portée): description en français
```

- `type` : obligatoire, choisi dans la liste ci-dessous ;
- `(portée)` : facultative, le dossier ou le sujet concerné (`agents`, `company`, `docs`, `templates`, `config`…) ;
- `description` : en français, à l'infinitif, sans point final, **72 caractères maximum** pour le titre entier.

### Types autorisés

| Type | Usage |
|---|---|
| `feat` | nouvelle fonctionnalité, nouveau workflow, nouvelle commande |
| `fix` | correction d'une erreur |
| `docs` | documentation (README, conventions, guides) |
| `agent` | création ou modification d'une fiche agent |
| `refactor` | réorganisation sans changement de comportement (renommage, déplacement) |
| `chore` | maintenance technique (configuration, dépendances, `.gitignore`) |

### Exemples

| ✅ Correct | ❌ Incorrect | Problème |
|---|---|---|
| `docs(conventions): définir la règle des émojis` | `update` | aucune information |
| `agent(cfo): préciser le périmètre trésorerie` | `Agent CFO modifié.` | pas de type, point final |
| `fix: corriger le lien vers le registre` | `fix: Fixed broken link` | description en anglais |
| `chore: ignorer le dossier private` | `chore: 🔧 ignorer private` | émoji interdit dans un commit |

### Corps et pied du message

- Le **corps** est facultatif. Il explique le *pourquoi*, séparé du titre par une ligne vide.
- Le **pied** peut contenir des mentions de co-auteur (`Co-Authored-By: …`).
- Le titre décrit **l'ensemble** des changements du commit, pas seulement le premier fichier touché.
  Si un commit mélange deux sujets, il DOIT être découpé.

### Signature obligatoire

Tout commit DOIT être **signé** et apparaître comme **Verified** sur GitHub avant d'être fusionné dans `main`.

Mise en place sur un poste (une seule fois), avec une clé SSH :

```bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgsign true
```

Ajouter ensuite la même clé publique sur GitHub comme **clé de signature** :
*Settings → SSH and GPG keys → New SSH key → Key type : Signing Key*.

Vérification : badge **Verified** à côté du commit sur GitHub.

Si un commit ne peut pas être signé ou n'apparaît pas comme vérifié, l'agent DOIT le signaler au dirigeant
au lieu de le présenter comme conforme.

## 7. Données sensibles

- Tout le contenu du dossier `private/` est **ignoré par Git** (`.gitignore`), **sauf** les `README.md` et `.gitkeep`
  qui décrivent sa structure. Ces fichiers NE DOIVENT contenir **aucune donnée sensible**.
- Pièces d'identité, relevés bancaires, contrats non publics, données personnelles de salariés ou de clients :
  **uniquement dans `private/`**, jamais dans un commit.
- Un agent qui rencontre une donnée sensible hors de `private/` DOIT le signaler avant tout commit.

## 8. Faire évoluer ces conventions

- Toute modification de ce document est proposée au dirigeant, puis appliquée par un commit
  `docs(conventions): …` après son accord.
- Une règle n'existe que si elle est écrite ici. Une règle écrite ailleurs n'est pas applicable.
