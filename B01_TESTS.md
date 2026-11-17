# B-01 — Contrôles locaux

**17 novembre 2026 — branche `feat/b01-tally-intake`.** Aucun formulaire Tally réel, identifiant, compte ou destinataire n'a été fourni ou créé.

## Réalisé

- `python3 -m http.server 8765 --bind 127.0.0.1` : ouverture de `index.html` et `brief-b01.html` dans Chromium.
- Navigation : CTA « Demander un devis de mécanique » → `brief-b01.html`. CTA audit → ancien formulaire avec « Audit & diagnostic ciblé » sélectionné. Bouton générique « Décrire mon besoin » → ancien formulaire avec « Autre demande » sélectionné. L'option B a été retirée du formulaire général. Formspree reste non configuré et son mode copie Discord n'a pas été remplacé.
- Page B-01 sans URL : état « pas encore configuré » affiché ; aucun iframe actif, aucun lien vers un formulaire inventé, aucun script ou appel réseau Tally et aucun faux message de succès. Lien retour vers `index.html#offres` présent.
- Test **simulé en mémoire**, sans envoi réseau ni identifiant réel : URL de test temporaire, insertion du script Tally interceptée. Vérification de la création de l'URL d'embed standard avec `dynamicHeight=1`, de l'appel `Tally.loadEmbeds()`, du lien direct et de son affichage même quand le script échoue. Aucune URL de test n'est inscrite dans le dépôt.
- Dans Chromium, test de mise en page par iframes de **375 px et 1200 px** : pas de débordement horizontal, état non configuré lisible, lien retour présent.
- Extraction des scripts de `index.html` et `brief-b01.html`, puis `node --check -` : syntaxe valide. `git diff --check` : aucune erreur d'espacement.
- Aucun média modifié ; ni dépendance nouvelle, ni secret, ni adresse email déduite dans les fichiers publiables.

## Impossible sans la configuration du propriétaire

- Créer/publier le questionnaire réel et vérifier ses cinq pages, ses champs requis (email et mécanique), les conditions de budget et la limite d'import dans Tally.
- Tester un véritable lien et un véritable code d'embed, le redimensionnement dynamique et l'absence de barre de défilement interne sur téléphone réel, avec et sans bloqueur.
- Soumettre un vrai dossier, confirmer sa présence dans *Submissions* et la notification reçue par email ; contrôler que seule la page de remerciement Tally s'affiche après cet envoi réussi.
- Valider l'adresse de réception, la durée de conservation, le texte et l'URL de la politique de confidentialité, ainsi que les mentions légales applicables. Voir `TALLY_SETUP.md`.
