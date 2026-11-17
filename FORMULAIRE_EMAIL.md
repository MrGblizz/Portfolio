# Activer ultérieurement la réception des demandes par email

Le portfolio est hébergé sur GitHub Pages : le site statique ne peut pas envoyer d'email directement. Tant que `FORM_ENDPOINT` vaut `''` dans `index.html`, le formulaire propose seulement de copier le brief pour Discord `mcadiie`.

1. Créer une adresse de réception professionnelle dédiée.
2. Créer un compte et un formulaire chez [Formspree](https://formspree.io/) ; vérifier les conditions du service, la confidentialité et les obligations applicables avant de l'activer.
3. Configurer l'adresse de réception dans le tableau de bord Formspree, sans placer cette adresse ou des identifiants privés dans le code du site.
4. Copier l'endpoint public `https://formspree.io/f/IDENTIFIANT` dans la variable `FORM_ENDPOINT` en haut du `<script>` de `index.html`. Ce lien public n'est pas un secret. Publier seulement après avoir vérifié la mention de confidentialité et les mentions légales applicables.
5. Tester avec un vrai message : confirmer sa présence **dans la boîte de réception et dans l'interface Formspree**. Tester les deux moyens de réponse (pseudo Discord seul ou email seul), et ne pas rendre l'email obligatoire dans les réglages du service si le pseudo suffit. Tester aussi un refus de validation, une erreur serveur et une connexion coupée ; le brief saisi doit rester disponible et copiable pour Discord.
6. Ne considérer le canal email comme actif qu'après ce test de bout en bout. Si besoin, remettre `FORM_ENDPOINT = ''` pour revenir au mode copie uniquement.

Le formulaire comporte un champ piège `_gotcha` contre les robots. Il n'emploie ni mot de passe SMTP ni service de stockage maison. Lorsqu'il est activé, le navigateur envoie les champs saisis à Formspree ; le propriétaire doit vérifier les informations de confidentialité à communiquer aux visiteurs. Les informations d'immatriculation, les mentions légales et les règles applicables à l'activité doivent être vérifiées avant commercialisation.

Références : [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site), [formulaire HTML Formspree](https://help.formspree.io/articles/building-your-form/building-an-html-form), [soumission AJAX](https://help.formspree.io/articles/building-your-form/submit-forms-with-javascript-ajax).
