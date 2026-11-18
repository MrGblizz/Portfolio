# A-01 — Contrôles locaux (18 novembre 2026)

Le lien public fourni par le propriétaire est `https://tally.so/r/Z9ORra`. Aucun dossier n'a été soumis, et aucune réception n'a été vérifiée.

## Vérifié

- URL publique et URL d'embed : HTTP 200.
- Depuis `index.html`, le bouton de l'offre A ouvre `brief-a01.html`. Le questionnaire Tally réel s'affiche avec le script officiel, le lien direct de secours et le retour au portfolio ; l'état « non configuré » est masqué. Aucune erreur console observée.
- Le formulaire Tally se présente comme un **audit de performances Minecraft Fabric**, à partir de 35 €, avec accès autorisé au code source avant l'audit. Les textes du portfolio et de la page A ont été alignés sur ce périmètre avec l'accord du propriétaire.
- Affichage Chromium : iframe à hauteur dynamique, sans débordement horizontal à largeur ordinateur (800 px) ni dans une simulation de largeur téléphone (375 px, formulaire à 307 px). Dans ce dernier contrôle, iframe et document Tally mesurent 1220 px de haut. Un téléphone physique reste à tester.
- B-01 conserve son lien `https://tally.so/r/2jAxyV`. Le formulaire général reste disponible pour les autres demandes, avec l'option « Autre demande » ; le mode copie Discord et Formspree facultatif ne changent pas.

## À corriger et à tester dans Tally

- Sur la première page A-01, « Nom du mod/projet » est techniquement **obligatoire** alors que son placeholder indique « Optionnel ». Aligner libellé, caractère obligatoire et validation dans Tally.
- Vérifier les autres pages, les pièces jointes/liens et les informations de confidentialité, puis faire un véritable envoi de test ; confirmer la réponse dans *Submissions* et la notification email. Ne pas considérer la réception testée à partir de l'affichage de l'embed.
- Refaire un contrôle sur téléphone physique et avec le script tiers bloqué ; le lien direct reste disponible en secours.
