# Suivi de la paie

Tableau de bord de supervision de la paie. Application web **statique** : un seul
fichier `index.html`, aucune dépendance serveur.

## Où sont les données ?

**Dans votre navigateur**, jamais sur le serveur.

- Les bulletins saisis et les paramètres sont enregistrés dans le `localStorage`
  du navigateur (clefs `paie_config` et `paie_bulletins`).
- Le serveur ne fait que livrer la page : il ne reçoit, ne stocke et ne voit
  aucune donnee de paie.
- La page **n'effectue aucun appel reseau** vers un service tiers.

Consequence : les donnees sont propres a un navigateur et a un poste. Pour
basculer sur un autre appareil, on exporte un fichier JSON de sauvegarde et on
le reimporte.

## Utilisation

1. Ouvrir la page.
2. Bouton **Importer** : choisir un fichier `.json` de sauvegarde, ou saisir les
   bulletins directement.
3. Les onglets *Dashboard*, *Historique* et *Suivi* se remplissent.
4. Bouton **Exporter** : genere un fichier `sauvegarde-paie-AAAA-MM-JJ.json` a
   conserver.
5. Bouton **Reinitialiser toutes les donnees** : vide le `localStorage`.

## Structure

| Fichier | Role |
|---|---|
| `index.html` | L'application complete (HTML + CSS + JS), sans build |
| `static.json` | En-tetes de securite servis par Render (CSP, anti-framing, etc.) |

## Deploiement

Render *Static Site* :

- depot : `https://github.com/fares1919/supervision-paie`
- branche : `main`
- commande de build : *(vide)*
- chemin de publication : `.`

## Notes

- Les polices (Inter, JetBrains Mono) et la bibliotheque de graphiques
  (Chart.js) sont chargees depuis Google Fonts et jsDelivr : une connexion
  Internet est necessaire au premier affichage.
- La politique de securite de contenu (CSP) declare dans `static.json` est
  alignee sur ces dependances externes.
