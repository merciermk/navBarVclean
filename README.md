# Barre de navigation

Barre de Navigation alimentée par un tableau d'objets pour VueJs

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

- Les balises des icones attendent des icones du site font-awesome.
- L'implémentation des icones devra se faire suivant l'usage recommandé par la doc de fortawesome : 
[https://www.npmjs.com/package/@fortawesome/vue-fontawesome#recommended]


## Mise en route

La barre est à alimenter par un tableau dont le point d'entrée est
```typescript
/* ligne 143 */
navElements: Menu[]
```

navElements attend un tableau d'objects, chaque objet doit suivre le protocole d'interface Menu/SousMenu du fichier interfaceMenu.ts. Le fichier est commenté afin de faciliter la compréhension.

## Utilisation

### Usage Normal
Le menu fermé laisse apparaître les icônes, s'ouvre au mouseEnter puis se fermer, soit au clic d'un lien, soit au mouseLeave

### Usage TouchScreen
Quelle que soit la taille d'écran, si la personne est sur un appareil de type touchScreen, seul un menu hamburger est visible, le touché fait apparaître le menu.
Celui-ci se ferme au toucher à l'extérieur (représenté par un filtre) ou au touché d'un lien.

### Premier/ Derniers éléments
Le premier élément doit avoir la condition 'topElement: true' de l'interface Menu.
Il est possible d'afficher plusieurs élements en pied de menu, pour celà il faut mettre la condition 'bottomElement: true' au premier élement devant être en bas du menu.

## Personalisation

Toutes les personnalisations sont trouvables dans les premiéres lignes du style.scss, les variables sont commentées.
L'exception étant les icones toggle button en usage TouchScreen, pour les personnaliser, les variable se trouvent dans SideBarLeft.vue : 

```javascript
toggleBtnOpenIt = 'align-justify'; // icone de la version fermée
toggleBtnCloseBtn = 'times'; // icone de la version ouverte
```






