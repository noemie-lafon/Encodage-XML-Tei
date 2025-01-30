## Documentation encodage XML-TEI

### Œuvres complètes de Voltaire, Tome XII, Poésies, Tome I

**Auteur :** Noémie Lafon  
**Master 1 :** Humanités numériques  
**Date :** 22/12/2024  

---

## Choix pour l’OCRisation
L’outil ABBYY a été utilisé pour effectuer l’OCRisation du texte initialement au format PDF. Après la numérisation, les erreurs dues à l’OCR ont été corrigées manuellement. Le document a ensuite été exporté en `.docx` pour être intégré dans Oxygen. L’utilisation de **Regex** aurait pu faciliter la suppression des tirets de coupure de mots, mais le faible nombre d’erreurs a conduit à une correction manuelle directement dans Oxygen avant l’encodage.

---

## Documentation : codification du texte et encodage XML-TEI

### Structure `<teiHeader>`
La balise `<teiHeader>` contient les métadonnées du projet numérisé et de la source originale :
- `<fileDesc>` : comprend `<titleStmt>`, qui contient le `<title>` (ex. "Œuvres complètes de Voltaire, Tome XII, Poésies, Tome I") et `<author>` (Noémie Lafon).
- `<publicationStmt>` : spécifie l’autorité (`<authority>` : "Cours M1 données textuelles") et la date de numérisation (`<date>` : 22/12/2024).
- `<sourceDesc>` : englobe `<listBibl>` avec les références bibliographiques d’origine.

---

## Structure du texte

### `<text>`
- **Section `<front>`** : Contient les trois premières pages, encapsulées dans `<titlePage>` et `<titlePart>` pour structurer les éléments bibliographiques.
- **Section `<body>`** :
  - Chaque **poème**, **note**, et **avertissement** débute avec `<head>` (titre) avec attributs `type` et `rend`.
  - L’ensemble des poèmes et notes est placé dans une balise `<div>`, chaque poème ayant sa propre `<div>` avec des attributs `type` et `n`.
  - Exemple :
    ```xml
    <div>
      <div type="poem" n="2.1.1">Poème La Bastille</div>
      <div type="notes" n="2.1.2">Notes du poème La Bastille</div>
    </div>
    ```

### Structuration des titres
- Utilisation de deux `<head>` (`type="title"` et `type="subtitle"`) pour différencier titre et sous-titre.

### Structuration des poèmes
- Utilisation de `<lg>` (groupement de vers) et `<l>` (vers).
- Les sauts de ligne sont marqués avec `<lb/>` et les alinéas avec `<l rend="indent">`.
- Les strophes ne sont pas explicitement définies en raison de leur non-correspondance avec la source originale.

### Structuration des notes
- Les exposants sont indiqués avec :
  ```xml
  <ref target="#note1b"><hi rend="sup">1</hi></ref>
  ```
- Lien avec les notes grâce à `<note xml:id="note1b">`.
- Notes organisées par identifiant (`a` pour poème 1, `b` pour poème 2, `c` pour poème 3).

---

## Tableau récapitulatif

| TEI Élément        | Description | Attributs |
|--------------------|------------|-----------|
| `<teiHeader>` | En-tête TEI, fournit des métadonnées | Aucun |
| `<fileDesc>` | Description bibliographique | Aucun |
| `<titleStmt>` | Informations sur le titre et l’auteur | Aucun |
| `<title>` | Titre principal du document | Aucun |
| `<author>` | Nom de l’auteur de l’édition numérique | Aucun |
| `<publicationStmt>` | Informations de publication | Aucun |
| `<authority>` | Nom de l’autorité responsable | Aucun |
| `<date>` | Date de publication | Aucun |
| `<sourceDesc>` | Description de la source originale | Aucun |
| `<listBibl>` | Liste des références bibliographiques | Aucun |
| `<bibl>` | Référence bibliographique | `n="1"`, `n="2"` |
| `<publisher>` | Éditeur de la source originale | Aucun |
| `<pubPlace>` | Lieu de publication | Aucun |
| `<text>` | Contient le texte (avertissement, poème, note) | Aucun |
| `<front>` | Texte préliminaire (titre, préface, etc.) | Aucun |
| `<titlePage>` | Page de titre | Aucun |
| `<titlePart>` | Partie du titre | `rend="center"` |
| `<body>` | Corps du texte | Aucun |
| `<div>` | Division du texte (avertissement, poème, notes) | `type`, `n` |
| `<head>` | En-tête (titre d’une section) | `type`, `rend="center"` |
| `<p>` | Paragraphe | Aucun |
| `<lg>` | Groupe de vers (poème) | Aucun |
| `<l>` | Vers | `rend="indent"` |
| `<pb/>` | Saut de page | `n="x"` |
| `<note>` | Note | `xml:id="notex"` |
| `<hi>` | Mise en évidence (gras, italique, exposant) | `rend="sup"`, `rend="italic"`, `rend="bold"` |
| `<ref>` | Référence vers une note | `target="#noteX"` |

---

## Liens utiles
- [TEI Header](https://tei-c.org/release/doc/tei-p5-doc/fr/html/ref-teiHeader.html)
- [File Description](https://tei-c.org/release/doc/tei-p5-doc/fr/html/ref-fileDesc.html)
- [Title Statement](https://tei-c.org/release/doc/tei-p5-doc/fr/html/ref-titleStmt.html)
- [Publication Statement](https://www.tei-c.org/release/doc/tei-p5-doc/fr/html/ref-publicationStmt.html)
- [Text](https://tei-c.org/release/doc/tei-p5-doc/fr/html/ref-text.html)
- [Divisions](https://tei-c.org/release/doc/tei-p5-doc/fr/html/ref-div.html)
- [Poems](https://tei-c.org/release/doc/tei-p5-doc/fr/html/ref-lg.html)
