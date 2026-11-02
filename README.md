# Skill « candidature-emploi »

Un skill pour Claude qui aide à chercher un emploi sérieusement :

- **analyse d'offre** avec un score de matching sur 100 (fonction, secteur, compétences, lieu, formation et langues), les atouts, les écarts et une recommandation claire ;
- **CV adapté au poste**, compatible ATS, sans jamais inventer d'expérience ;
- **lettre de motivation** au ton naturel, sans formules toutes faites ;
- **note de projet** (« business plan » du poste) pour les candidatures qui en demandent une ;
- **PDF propres**, vérifiés, avec des métadonnées au nom du candidat ;
- **tableau de bord de suivi** : un fichier HTML à ouvrir dans le navigateur pour suivre ses candidatures (statuts, scores, relances, export CSV et JSON).

## Installation
1. Télécharge le dossier `candidature-emploi`.
2. Remplis `candidature-emploi/profil.md` avec ton parcours (ou laisse-le vide : Claude te demandera ton CV la première fois).
3. Ajoute le dossier à tes skills dans Claude (Paramètres > Capacités > Skills, en important le dossier zippé), ou place-le dans `~/.claude/skills/` pour Claude Code.

## Tableau de bord
Ouvre `tableau-de-bord/tableau-de-bord.html` dans ton navigateur. Les données restent sur ton ordinateur, dans ce navigateur : exporte-les régulièrement en JSON pour garder une sauvegarde, et réimporte le fichier sur un autre appareil.

## Utilisation
Envoie une offre à Claude (« analyse cette offre », avec le lien ou le texte), puis demande « prépare le CV et la lettre ».

## Licence
MIT
