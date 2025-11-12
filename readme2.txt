Génère un fichier HTML complet (une seule page autonome : index.html) prêt à l'emploi pour une landing page d'INTRODUCTION À L'INFORMATIQUE. Le fichier doit intégrer via CDN : Tailwind CSS, anime.js, Font Awesome et Google Fonts. Le code doit être propre, commenté et accessible (balises sémantiques, alt sur images, focus pour éléments interactifs) et responsive.

Spécifications fonctionnelles et UI (strictes) :
1. Header / Hero
   - Hero section en haut avec : 
     - une image illustrative (utiliser des images publiques via CDN/Unsplash ; ex. `https://source.unsplash.com/1600x900/?computer,programming,education`), responsive.
     - un titre accrocheur.
     - une citation/injonction informatique (ex : "L'informatique, c'est...") qui **change automatiquement toutes les 5 secondes**. Il doit y avoir exactement **10 citations** pré-définies. Chaque 5s on affiche la suivante (boucle cyclique). L'animation de transition entre citations doit être faite avec **anime.js** (fondu + translation douce).
   - Affichage clair et centré du texte sur le hero, overlay sombre si nécessaire pour lisibilité.

2. Section « Catalogue des cours »
   - Grille responsive présentant **12 cours** (3 colonnes sur desktop, 2 sur tablette, 1 sur mobile).
   - Chaque carte de cours contient : image (placeholder/Unsplash basée sur le sujet), titre du cours (Cours 1 -> Cours 12), courte description (1-2 lignes), et un bouton **"Accéder au cours"** avec icône Font Awesome.
   - Chaque cours doit avoir un **code secret unique** (ex. `CODE-C1-XXXX`), stocké dans une structure JavaScript (tableau/dictionnaire). Insère 12 codes d'exemple distincts dans le JS.

3. Comportement du bouton "Accéder au cours"
   - Quand l'utilisateur clique, ouvre une **petite fenêtre modale** (dialog accessible) demandant :
     - le **code secret** du cours (champ required),
     - son **nom** (optionnel mais ajouter champ),
     - son **téléphone ou email** (optionnel; utile pour message WhatsApp).
   - Validation côté client en JS : si le code est **exact** pour ce cours → fermer la modale puis **rediriger** vers la page correspondante `cours1.html`, `cours2.html`, ... `cours12.html` (chaque cours vers sa page dédiée).
   - Si le code est **incorrect** → dans la modale afficher un message clair : "Code incorrect — veuillez contacter le professeur pour acheter le cours." et proposer un bouton **"Contacter"**.
     - Le bouton "Contacter" ouvre WhatsApp via un lien `https://wa.me/{WHATSAPP_NUMBER}?text={texte prérempli}` (utiliser un placeholder `{WHATSAPP_NUMBER}` que l'utilisateur remplacera par son numéro au format international, ex. 33612345678). Le texte prérempli doit inclure : nom du cours (ex. "Cours 3"), le nom de l'utilisateur s'il l'a renseigné, et son téléphone/email si fourni. Exemple de message prérempli : `"Bonjour, je souhaite acheter le Cours 3 (code incorrect entré). Nom: Jean Dupont. Contact: jean@example.com"`. Encode correctement l'URL (encodeURIComponent).
   - La vérification des codes peut être faite en JS client-side (pour cette version). Stocke les mappings `{"cours1":"CODE1", ...}` et compare avec ce que l'utilisateur entre.

4. Sécurité / UX
   - Indiquer clairement dans un petit texte que les codes sont uniquement côté client pour le prototype et que pour production il faudra vérifier côté serveur.
   - Les pages `cours1.html` etc. peuvent être de simples pages d'exemple (ou, si tu préfères, redirection vers `cours1.html` qui existe ou 404 si pas encore créé) — dans le fichier final, crée **au moins une page d'exemple minimale** `cours1.html` (fichier séparé) ou générer un fragment HTML commenté expliquant comment créer ces pages. (Si possible, fournir un petit fichier `cours1.html` minimal dans un commentaire ou dans un second `<!-- -->` bloc pour que l'utilisateur les copie.)

5. Animations & esthétique
   - Utilise **anime.js** pour :
     - la transition des citations (fondu + translation verticale),
     - animations d'apparition des cartes au scroll (légère translation + opacité),
     - animation sur le bouton quand on passe la souris (scale/shine).
   - Intègre une Google Font moderne (ex. "Inter" ou "Poppins") via CDN.
   - Utilise Tailwind pour le layout et les styles. Ne pas écrire CSS inline excessif ; privilégier Tailwind + un petit `<style>` pour règles spécifiques si nécessaire.

6. Accessibilité & mobile
   - Les modales doivent être focus-trap-friendly: autofocus sur champ code, bouton fermer accessible via clavier (Esc), aria-attributes (`role="dialog"`, `aria-modal="true"`, `aria-labelledby`, etc.).
   - Images avec `alt`, boutons avec `aria-label` si nécessaire.
   - Contraste suffisant pour textes.

7. Code & commentaires
   - Fournis tout le HTML, CSS (si nécessaire), et JavaScript dans un seul fichier `index.html`.
   - Ajoute des commentaires clairs dans le JS indiquant où changer :
     - les codes secrets,
     - le numéro WhatsApp `{WHATSAPP_NUMBER}`,
     - les textes des 10 citations,
     - les données de chaque cours (titre, description, image).
   - À la fin du fichier, ajoute une courte section de documentation en commentaire expliquant comment remplacer les codes par une vérification serveur (endpoints recommandés), et comment créer les pages `coursX.html`.

8. Bonus pratique (optionnel mais souhaité)
   - Inclure un petit script qui permet de **générer aléatoirement** 12 codes secrets si l'utilisateur veut les remplacer automatiquement (mais laisser des codes exemples lisibles).
   - Ajouter un champ "Se souvenir de moi" localStorage pour pré-remplir le nom/phone si l'utilisateur revient.

Livrable demandé :
- Réponse = **le prompt ci-dessous** (tu réponds ici par le code du prompt). Quand tu exécutes ce prompt, l'assistant doit **retourner directement** le contenu de `index.html` complet, prêt à être sauvegardé. Le code HTML doit être prêt à copier/coller et fonctionner tel quel (après remplacement de `{WHATSAPP_NUMBER}`).

Important : fournis tout en **français** (les labels, messages d'erreur, textes UI) et écris le prompt de façon impérative pour que l'assistant génère le HTML complet. Ne pose pas de question, fournis tout ce qui est demandé dans le prompt pour produire le code final.

Fin du prompt — génère maintenant le fichier HTML complet en respectant exactement ces instructions.
