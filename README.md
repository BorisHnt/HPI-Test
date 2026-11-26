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
- data/hpi-fr.json : 20 profils actifs, 40 descriptions, 40 questions
- data/pictograms.json : références et sources Wikimedia Commons

Les SVG sont chargés à la demande après le premier résultat, depuis assets/signs si les fichiers ont été importés, sinon via Wikimedia Commons. Un pictogramme de secours dessiné par le site apparaît si le chargement échoue. Les crédits et conditions sont accessibles dans les résultats. Avant de redistribuer les SVG en local ou sur un certificat, vérifier individuellement les licences et ajouter les crédits requis. Les illustrations de secours ne sont pas normalisées. Aucun pictogramme n'est chargé durant un premier questionnaire.

Chaque question propose cinq réponses mélangées. Les 160 choix principaux valent 1 point ; 20 choix supplémentaires valent 0,5 point (un par profil) et 20 sont neutres. Les scores sont relatifs au maximum de 8,5 points par profil (8 ou 6–7 pour les résultats antérieurs). Un profil à zéro point ne peut pas être signe ni ascendant. Les résultats sans paire complète sont consultables et partageables, mais sans certificat PNG. Ce n'est pas une mesure de dangerosité, un percentile ou un diagnostic. Les égalités sont départagées automatiquement : score normalisé, points bruts, force des alternatives écartées, puis clé déterministe dérivée des réponses (et identifiant en ultime recours). Le classement est toujours unique, mais les pourcentages bruts peuvent être identiques. Une même série de réponses produit le même classement indépendamment de l’ordre des questions. Aucun départage manuel ni question supplémentaire. Les résultats déjà sauvegardés ne sont pas recalculés ; les six anciens profils restent disponibles uniquement dans l’historique. Les questionnaires interrompus de l’ancienne version sont invalidés.

L'historique (100 résultats max) et la progression sont enregistrés dans localStorage. Les réponses ne sont pas envoyées à un serveur. La fonctionnalité de partage native dépend du navigateur ; un téléchargement PNG ou une copie du lien est proposé en alternative.

Les phrases humoristiques sont associées aux signes, et les descriptions de signe/ascendant sont distinctes. Les 380 combinaisons ne disposent pas encore chacune d'un texte original spécifique.

## Répertoire des personnalités

Après un premier test sauvegardé, le menu, l’accueil et la page de résultat donnent accès aux 20 pictogrammes actifs et à leurs descriptions de signe et d’ascendant, qualités et précautions. Le répertoire est masqué tant qu’aucun résultat n’est disponible localement, y compris après suppression de tous les résultats. Les six anciens pictogrammes restent consultables uniquement dans leurs résultats historiques.
