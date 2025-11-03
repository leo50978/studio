**Objectif :** Donne-moi **le code HTML complet, prêt à ouvrir dans un seul fichier .html**, pour un site web inspiré de TikTok qui présente des *templates de sites web à vendre*.  
Le fichier doit utiliser des CDN (pas d’outils de build) : **Tailwind (CDN)**, **Google Fonts**, **anime.js**, **Font Awesome**. Fournis aussi tout le CSS/JS dans le même fichier (ou via CDN) et commente le code.

**Exigences fonctionnelles et UX (détaillées) :**
1. **Splash / Opening**
   - Au chargement, affiche au centre le **logo de l’entreprise** (utilise un placeholder SVG) et un **sous-titre** : *« Les meilleurs sites web au meilleur prix »*.  
   - L’opening doit être **synchronisé au chargement** du site : la page doit rester sur le splash tant que les ressources critiques (CSS, fonts, JS et mini set d’images d’aperçu) ne sont pas prêtes. Utilise **anime.js** pour une animation d’ouverture fluide (logo qui pulse/scale + fade).  
   - Après fin chargement / animation, transition fluide vers l’interface principale.

2. **Interface principale — style TikTok vertical**
   - Layout vertical **full-screen par template** (scroll vertical plein écran, `scroll-snap` pour chaque carte/template), comme TikTok.  
   - La **première image** doit apparaître en grand plan full-écran en haut (première carte visible).  
   - **En haut** : une rangée de **boutons de filtre** (catégories) qui filtrent les templates affichés (ex : « E-commerce », « Portfolio », « Blog », « Landing »). Les filtres doivent réordonner / masquer les cartes de façon fluide (animation).  
   - **À droite**, superposés sur chaque carte (alignés verticalement, comme sur TikTok) : icônes **Like**, **Achat (Commander)**, **Compteur de commandes** (affiche le nombre de commandes effectuées pour le template). Utilise **Font Awesome** pour les icônes.
   - Le bouton **Commander** ouvre une **fenêtre modal** centrée avec : image plus grande, titre, prix, description, raisons d’achat (« pourquoi acheter »), et un bouton **Commander** final.
   - Le bouton de la modal **envoie l’utilisateur sur WhatsApp** (lien API wa.me / `https://wa.me/<num>?text=...`) en **pré-remplissant un message** qui contient : ID du template, titre, prix, et options sélectionnées.  
     - **Numéro WhatsApp à utiliser** dans le lien (tel que dans le message) : **+50935601379** (format international Haïti +50935601379).  
   - Après la confirmation d’achat (lorsque l’utilisateur clique sur le bouton « Commander » dans la modal), **incrémente et affiche le compteur de commandes** pour ce template. Persiste le compteur localement en **localStorage** (ex : `orders_<templateId>`).

3. **Lazy loading des images**
   - Le site aura beaucoup d’images : **ne charge pas toutes les images d’un coup**. Implémente `loading="lazy"` et **IntersectionObserver** qui remplace `data-src` → `src` quand une image entre en viewport. Fournis un petit placeholder flou (blur) ou une base64 tiny inline en attendant le chargement.  
   - Le prompt doit demander explicitement l’usage combiné `loading="lazy"` + IntersectionObserver + placeholder.

4. **Sons sur boutons**
   - Chaque bouton interactif (filtre, like, ouvrir modal, commander, fermer modal, etc.) joue **un son différent**. Intègre **de petites sources audio** (tu peux utiliser de courts fichiers audio encodés en base64 directement dans le JS pour que tout reste en un seul fichier). Fournis au moins 6 sons distincts (ils peuvent être très courts : click/confirm/pop). Assure une gestion correcte : une seule instance jouée, et volume raisonnable.

5. **Interactions Like / Animation**
   - Le bouton **Like** doit pouvoir être toggle (aimer / retirer) et déclencher une animation (scale + heart burst) via **anime.js** et jouer son son distinct. Le nombre de likes peut être simulé et stocké en localStorage (persistant).

6. **Accessibilité & Responsive**
   - Le site doit être responsive (mobile d’abord), accessible (attributs ARIA, labels pour boutons, éléments focusables, gestion du clavier — tab / escape pour fermer modal).

7. **Données & exemples**
   - Inclure un **jeu d’exemple** d’au moins 8 templates (objet JS) : `id`, `title`, `category`, `price`, `shortDescription`, `imageUrl` (utiliser images d’Unsplash ou placeholders dynamiques), `orders` initial (nombre). Le code doit générer les cartes automatiquement à partir de ce dataset.

8. **Performance & SEO**
   - Minimise le travail JS bloquant au chargement initial ; assures-toi que l’opening n’attende que les ressources critiques. Ajoute des meta tags basiques (charset, viewport, description).

9. **Instructions sur la livraison du code**
   - Rends **un seul fichier HTML** auto-contenu (avec liens CDN pour Tailwind, Google Fonts, anime.js, Font Awesome).  
   - Commente les parties importantes (splash, lazy loading, IntersectionObserver, modal + WhatsApp link, stockage localStorage, sons encodés).  
   - **Ne** pas utiliser d’outils externes (WebPack, npm) — juste CDNs.  
   - Les URL d’images peuvent pointer vers Unsplash (ex: `https://source.unsplash.com/collection/XXXXXXXX/1080x1920`) ou des placeholders, et inclure l’attribut `loading="lazy"` + `data-src`.  
   - Le code doit implémenter le lien WhatsApp **avec le numéro fourni** : `+50935601379`. Le message pré-rempli doit ressembler à :  
     `Bonjour, je veux commander le template [ID: {{id}}] - "{{title}}" au prix {{price}} HTG. Détails / options : ...`

**Extras souhaités (optionnel mais apprécié) :**
- Indique où et comment remplacer le logo, la police Google Font (propose une police par défaut), et comment changer les sons.  
- Ajoute un petit compteur global de templates vendus (sum des `orders`) visible quelque part sur la page.

**Contraintes techniques :**
- Utilise `scroll-snap-type: y mandatory` (ou équivalent) pour l’effet TikTok.  
- Utilise `IntersectionObserver` pour le lazy-loading (et pour déclencher les animations d’entrée si pertinent).  
- Les animations d’ouverture et d’UI doivent utiliser **anime.js** (pas uniquement CSS).

**Format de la réponse attendue :**
- Fournis **uniquement** le code complet du fichier HTML (avec commentaires).  
- Après le code, ajoute une courte section (max 6 lignes) qui explique comment personnaliser rapidement : changer logo, numéro WhatsApp, images, et où modifier les sons.

**Important :** le numéro WhatsApp à utiliser pour la redirection pré-remplie est **+50935601379**.  

Merci — génère maintenant **le fichier HTML complet** selon ces consignes.
