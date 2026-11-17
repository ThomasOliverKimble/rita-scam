# rita-scam — démonstration de clickjacking (audit de sécurité)

Page de **démonstration** créée pour un audit de sécurité du site
[atelierrita.org](https://www.atelierrita.org). Elle n'appartient pas à Atelier Rita.

## Ce qu'elle montre

Le site en ligne ne renvoie aucun en-tête anti-affichage (`X-Frame-Options` ou
`Content-Security-Policy: frame-ancestors`). Il peut donc être chargé dans le cadre
(`<iframe>`) de n'importe quelle page. `index.html` charge le vrai site et pose par-dessus
un faux formulaire « Session expirée » pour illustrer le risque.

## Garde-fous (ce n'est pas une vraie arnaque)

- Bandeau permanent « DÉMONSTRATION — exemple d'arnaque » qui ne peut pas être masqué.
- Le formulaire est factice : **il n'enregistre rien**, aucun envoi, aucun stockage.
- Le bouton renvoie vers une vidéo YouTube inoffensive, pour montrer qu'un clic peut mener ailleurs.
- `noindex, nofollow` sur la page.

## La correction

Côté Atelier Rita, ajouter un en-tête :

```
X-Frame-Options: DENY
```

ou, équivalent moderne :

```
Content-Security-Policy: frame-ancestors 'none'
```

Un site protégé afficherait alors un cadre vide au lieu du contenu.

## Usage

Ouvrir `index.html` dans un navigateur. Dépôt privé, à ne pas publier tel quel.
