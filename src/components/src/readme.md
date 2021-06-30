# Barre de navigation

barre de Navigation alimentée par un tableau pour VueJs

## dependancies

la barre utilise plusieurs dépendances : 
_
"@fortawesome/fontawesome-free": "^5.15.3",
"@fortawesome/fontawesome-svg-core": "^1.2.35",
"@fortawesome/free-solid-svg-icons": "^5.15.3",
"@fortawesome/vue-fontawesome": "^2.0.2",
"@popperjs/core": "^2.9.2",
"bootstrap-vue": "^2.17.3",
"bootstrap": "^5.0.0-beta2",
"vue-property-decorator": "^9.1.2"
 _

## Mise en route

La barre est alimentée par un tableau dont le point d'entré est :
```javascript
/* ligne 143 */
navElements
```

navElements attend un tableau d'objects, chaque object doit suivre le protocole d'interface Menu/SousMenu du fichier interfaceMenu.ts. Le fichier est commenté afin de facilité la comprehension.

## Utilisation

### Usage Normal
le menu fermé laisse apparaitre les icones, s'ouvre au mouseEnter puis se fermer, soit au clic d'un lien, soit au mouseLeave

### Usage TouchScreen
Quel que soit la taille d'écran, si la personne est sur un appareil de type touchScreen, seul un menu hamburger est visible, le touché fait apparaitre le menu.
Celui-ci se ferme au touché à l'exterieur (representé par un filtre) ou au touché d'un lien.




