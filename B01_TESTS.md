# B-01 — Contrôles locaux

**17 novembre 2026 — branche `feat/b01-tally-intake`.** Le propriétaire a fourni le lien public réel `https://tally.so/r/2jAxyV`. L'intégration est locale ; aucun envoi de réponse ni publication GitHub n'a été effectué. Les tests ci-dessous distinguent les contrôles antérieurs à l'URL des contrôles sur le vrai formulaire.

## Réalisé

- `python3 -m http.server 8765 --bind 127.0.0.1` : ouverture de `index.html` et `brief-b01.html` dans Chromium.
- Navigation : CTA « Demander un devis de mécanique » → `brief-b01.html`. CTA audit → ancien formulaire avec « Audit & diagnostic ciblé » sélectionné. Bouton générique « Décrire mon besoin » → ancien formulaire avec « Autre demande » sélectionné. L'option B a été retirée du formulaire général. Formspree reste non configuré et son mode copie Discord n'a pas été remplacé.
- Avant configuration : état « pas encore configuré » affiché ; aucun iframe actif, aucun script ou appel réseau Tally et aucun faux message de succès. Test **simulé en mémoire**, sans envoi, du lien direct et de son maintien en cas d'échec du script. Ce comportement de repli existe toujours si l'URL est vidée.
- Avec le vrai lien : `curl -I` des URL publiques et d'embed → HTTP 200. Clic sur le CTA B-01 → `brief-b01.html` ; l'état « non configuré » est masqué, le lien direct pointe vers `https://tally.so/r/2jAxyV`, le script officiel et l'iframe chargent le vrai formulaire. Aucune erreur de console observée.
- Dans Chromium, à largeur de page ordinateur (800 px lors du contrôle) : iframe à hauteur dynamique (980,5 px après chargement du thème clair), hauteur égale à celle du document intégré ; pas de défilement interne supplémentaire observé. Le fond transparent initial rendait les libellés foncés illisibles sur le panneau sombre : option retirée et lisibilité recontrôlée sur fond clair.
- Dans Chromium, **simulation d'une largeur de téléphone de 375 px** par iframe locale : pas de débordement horizontal sur la page, formulaire réel chargé à 307 px de large, hauteur de l'iframe 1079,5 px pour un document intégré de 1080 px, lien direct visible. Ce contrôle ne remplace pas un essai sur un téléphone physique.
- **Écart observé dans Tally :** les champs « Nom du projet (facultatif) » et « Public visé (facultatif) » de la première page portent l'astérisque et leurs éléments HTML sont `required`. Corriger les réglages *Required* dans Tally ; le site hôte ne peut pas modifier ces champs.
- Extraction des scripts de `index.html` et `brief-b01.html`, puis `node --check -` : syntaxe valide. `git diff --check` : aucune erreur d'espacement.
- Aucun média modifié ; ni dépendance nouvelle, ni secret, ni adresse email déduite dans les fichiers publiables.

## À valider avec le propriétaire avant publication

- Vérifier dans l'éditeur Tally les cinq pages du questionnaire réel, les champs requis (email et mécanique), les champs facultatifs, la logique de budget, l'information de confidentialité et les limites d'import.
- Tester le redimensionnement et l'absence de barre de défilement interne sur **téléphone physique**, avec et sans bloqueur.
- Soumettre un vrai dossier, confirmer sa présence dans *Submissions* et la notification reçue par email ; contrôler que seule la page de remerciement Tally s'affiche après cet envoi réussi.
- Valider l'adresse de réception, la durée de conservation, le texte et l'URL de la politique de confidentialité, ainsi que les mentions légales applicables. Voir `TALLY_SETUP.md`.
