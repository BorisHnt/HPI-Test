# HPI / TEST

Test de personnalité humoristique, mobile-first, en français. Aucune inscription et aucun backend.

## Publication GitHub Pages

Dans Settings → Pages, choisir Deploy from a branch, branche main, dossier / (root), puis Save.

URL attendue : https://borishnt.github.io/HPI-Test/

## Développement

Servir le dossier avec un serveur HTTP local : `python3 -m http.server 8000`, puis ouvrir http://localhost:8000. Ne pas ouvrir index.html en file:// (les données JSON sont chargées via fetch).

- index.html : structure et métadonnées sans spoiler
- style.css : Neo-Brutalism responsive
- app.js : navigation, stockage, scoring, résultats et certificat PNG
- data/hpi-fr.json : 26 profils, 52 descriptions, 40 questions
- data/pictograms.json : références et sources Wikimedia Commons

Les SVG sont chargés à la demande après le premier résultat, depuis assets/signs si les fichiers ont été importés, sinon via Wikimedia Commons. Un pictogramme de secours dessiné par le site apparaît si le chargement échoue. Les crédits et conditions sont accessibles dans les résultats. Avant de redistribuer les SVG en local ou sur un certificat, vérifier individuellement les licences et ajouter les crédits requis. Les illustrations de secours ne sont pas normalisées. Aucun pictogramme n'est chargé durant un premier questionnaire.

Les scores indiquent une fréquence de sélection relative à l'exposition à chaque profil (6 ou 7 propositions). Ce n'est pas une mesure de dangerosité, un percentile ou un diagnostic. Les égalités sont départagées automatiquement : score normalisé, points bruts, force des alternatives écartées, puis clé déterministe dérivée des réponses (et identifiant en ultime recours). Le classement est toujours unique, mais les pourcentages bruts peuvent être identiques. Une même série de réponses produit le même classement indépendamment de l’ordre des questions. Aucun départage manuel ni question supplémentaire. Les résultats déjà sauvegardés ne sont pas recalculés.

L'historique (100 résultats max) et la progression sont enregistrés dans localStorage. Les réponses ne sont pas envoyées à un serveur. La fonctionnalité de partage native dépend du navigateur ; un téléchargement PNG ou une copie du lien est proposé en alternative.

Les phrases humoristiques sont associées aux signes, et les descriptions de signe/ascendant sont distinctes. Les 650 combinaisons ne disposent pas encore chacune d'un texte original spécifique.
