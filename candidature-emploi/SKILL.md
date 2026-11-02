---
name: candidature-emploi
description: Analyser une offre d'emploi (score de matching sur 100) et préparer un CV, une lettre de motivation ou une note de projet adaptés au poste, à partir du profil du candidat, sans rien inventer.
---

# Candidature emploi

Utilise ce skill quand l'utilisateur envoie une offre d'emploi (lien, capture, texte) en demandant une analyse ou un avis, ou quand il demande un CV, une lettre de motivation, un message à un recruteur ou une note de projet pour un poste.

Réponds dans la langue de l'utilisateur, avec des phrases courtes.

## 0. Le profil du candidat
Le profil se trouve dans `profil.md`, à côté de ce fichier. S'il n'est pas rempli :
- demande le CV actuel de l'utilisateur et extrais-en le profil ;
- pose au plus 3 questions sur ce qui manque (zone géographique, salaire visé, contraintes, compétences à ne pas revendiquer) ;
- propose de compléter `profil.md` pour les fois suivantes.

Tout ce qui n'est pas dans le profil ou confirmé par l'utilisateur est considéré comme non acquis.

## 1. Lire l'offre
- Ouvre l'annonce avec l'outil de lecture web disponible. Si le site bloque la lecture (LinkedIn notamment), cherche la même offre sur le site carrière de l'employeur ou sur un autre site d'emploi, ou dans les alertes e-mail si une messagerie est connectée.
- Un lien de redirection (par ex. `linkedin.com/safety/go/?url=…`) contient l'URL réelle encodée : décode-la et ouvre-la.
- Si rien n'est lisible, analyse sur ce qui est connu, dis-le clairement et demande le texte ou une capture de l'offre.
- Relève : intitulé, employeur (ou client probable si l'offre est confidentielle), lieu et mode de travail, missions, profil demandé, conditions éliminatoires (diplôme, équivalence, années d'expérience, pièces à fournir), date limite.

## 2. Score de matching (sur 100)
- Fonction et niveau de responsabilité : /30
- Secteur : /25 (même secteur que le candidat = 20-25 ; secteur voisin = 10-20 ; autre = 0-10)
- Compétences demandées couvertes par le profil : /25
- Lieu et conditions : /10 (selon la zone et le mode de travail souhaités dans le profil)
- Formation et langues : /10 (pénalité si une langue exigée n'est pas maîtrisée)

Présente un tableau Critère | Note | Pourquoi, puis :
- ce que fait réellement le poste, en quelques lignes ;
- les atouts du candidat, concrets et tirés du profil ;
- les écarts, honnêtement ;
- les points bloquants (diplôme, équivalence, pièces exigées, salaire probable) ;
- une recommandation : Postuler, À considérer ou Passer.

Seuil de pertinence par défaut : 50 %. Signale quand le score est estimé faute d'annonce complète.

## 3. Règles pour les CV
- Ne jamais inventer d'expérience, de chiffre, de diplôme ou de certification. Demander avant d'ajouter une compétence non confirmée.
- Ne pas recopier l'intitulé du poste visé dans le titre du CV : le titre met en avant le parcours réel sous l'angle utile au poste.
- Respecter la liste « à ne jamais mentionner » du profil.
- Réorganiser et reformuler les expériences pour faire ressortir ce que demande l'annonce, avec ses mots-clés quand ils correspondent à une expérience réelle.
- CV compatible ATS : une colonne, 2 pages maximum, vrai texte sélectionnable, pas de tableau de mise en page ni d'image. Sections : Profil, Chiffres clés, Expérience professionnelle, Compétences clés, Formation et langues.
- Version anglaise si l'annonce est en anglais.

## 4. Lettres et messages
- Ton naturel et direct. Éviter les tournures toutes faites (« moteur de la transformation », « concrets et mesurables », « de bout en bout », « je suis convaincu que »), les tirets longs en incise et les énumérations en trois temps systématiques.
- Une page. Ouvrir sur un élément réel et vérifié de l'employeur quand c'est possible.
- Assumer franchement un écart et dire comment il est compensé.
- Messages aux recruteurs : courts, sans détails de salaire ou de conditions sauf demande explicite.

## 5. Note de projet (ou « business plan » pour un poste)
Deux pages maximum :
- contexte chiffré et sourcé (recherche web) ;
- 3 ou 4 priorités calées sur les missions de l'annonce ;
- feuille de route (mois 1-3, 4-6, 7-12) ;
- indicateurs de suivi ;
- organisation de l'équipe ;
- ce que le candidat apporte.

## 6. Production des fichiers
- Rédiger le document en HTML/CSS (format A4, police sans empattement lisible, titres en majuscules avec `letter-spacing: 0` pour que l'extraction de texte reste propre, blocs en `page-break-inside: avoid`), puis le convertir en PDF (par ex. avec weasyprint).
- Vérifier le nombre de pages, l'aperçu visuel et le texte extrait (pdfinfo, pdftoppm, pdftotext).
- Renseigner les métadonnées du PDF (par ex. avec pypdf) : Author, Creator et Producer = nom du candidat, Title explicite. Aucun filigrane.
- Nommer les fichiers `CV_[Nom]_[Cible].pdf`, `Lettre_Motivation_[Nom]_[Cible].pdf`.

## 7. Suivi des candidatures
Le dépôt contient un tableau de bord vierge (`tableau-de-bord/tableau-de-bord.html`) qui s'ouvre dans un navigateur et garde les candidatures en local. Après chaque analyse, rappelle à l'utilisateur d'y reporter le poste, l'entreprise, le lien, le score, le statut et la date de relance prévue (en général une semaine après l'envoi).

## 8. Limites
- Ne jamais saisir un numéro d'identité ou bancaire dans un formulaire, ni déposer une candidature à la place de l'utilisateur : c'est lui qui soumet.
- Les informations de salaire trouvées en ligne sont des estimations : le dire.
