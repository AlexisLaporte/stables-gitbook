# Jeu

(this is a branch from Github)

## Jeu

## Introduction

Ce document aborde l’ensemble des mécaniques du jeu, il est censé répondre à toutes les questions. Chaque sujet abordé se termine par un synthèse de ce qui serait écrit dans le whitepaper.

## Questions pratiques

#### Date de sortie

15 Octobre

#### Prix des chevaux

À définir

* [ZED.run](http://zed.run) floor price = 50 € (0.03 eth)

#### Reveal

À définir

## NFTs

La plupart des **jeux Web3** étudiés cherchent à créer une disponibilité quasi-infinie des NFTS :

* La plupart ont édité un nombre restreint par un drop, mais permis leur reproduction (en quantité illimitée).
* Sorare augmente progressivement le volume, sur le basket ils sont passés à une distribution de 1/100/1.000/5.000 par joueur par saison

À Stables, nous avons choisi d’éditer des NFTs pour les 8K nouveaux chevaux en course chaque année. L’obtention d’un NFT est aléatoire, c’est-à-dire qu’on ne peut pas choisir son cheval (mais que la revente est possible). _8K est un objectif ambitieux pour un drop de NFTs, toutefois en tant que jeu 8K joueurs n’est pas beaucoup._

Nous présentons une mécanique qui permet d’augmenter progressivement la disponibilité des NFTs, tout en créant des niveaux de rareté.

* Les niveaux de rareté sont organisés, classiquement, de manière pyramidale (en haut, le unique, est le plus rare), avec un ratio entre 2 et 10. Un ratio bas de 1:2 ou 1:3 nous paraît intéressant.
* Cela nous permet donc d’éditer 8K puis 16K puis 32K (1:2) ou 8K puis 24K puis 72K (1:3)
* L’ensemble des possesseurs de NFTs de la pyramide (que nous appelons une famille) se répartissent les gains du cheval de manière presque équitable : les couchent inférieures génèrent un bonus aux couches supérieures
* Ce bonus est activé si la famille est active, c’est-à-dire si elle joue au jeu de stratégie que nous allons mettre en place, cela incite les couches supérieures à inciter la famille à jouer (et donc à “représenter” leur cheval)
* Pour la couche la plus basse, un bonus est également activé si la famille joue plus ou mieux que les autres familles
* L’achat d’un nouveau NFT se fait toujours aléatoirement, sur une des couches d’un des cheval où il reste une place
* Nous pourrions facilement introduire la possibilité que de nouvelles places “uniques” soient disponibles (un nouveau cheval mis en vente), toujours aléatoirement, ce qui donne envie aux acheteurs d’avoir la chance de gagner cette place
* Plus tard, l’année prochaine, nous pourrions décider de vendre les couches supérieures (niveau 1 unique, niveau 2) à des prix plus importants, et séparer leur cagnotte (ils joueront à des enjeux supérieurs), tout en gardant le système de bonus
* Jusqu’à quand peut-on minter le cheval d’une année ?
  * Si c’est très longtemps après son début de carrière, il vaut peut-être baisser son prix (ou empêcher sa vente)
  * À un moment donné, il se pourrait qu’on puisse minter soit un cheval d’une année passée, soit de la nouvelle année (en unique)
* Tout en haut de la pyramide, une place spéciale est réservée au véritable propriétaire, qui lui aussi bénéficie des bonus (cette place lui serait cependant vendue, et non offerte)
* Un bonus pourrait aussi être prélevé lors du mint (voir du resell) et versé aux propriétaires uniques (par ex. déduit de nos 30%, on pourrait verser 0.5%)

**Atouts de cette solution**

* Cela créé une communauté autour du cheval au sein de la famille, et des incitations à jouer au jeu de stratégie
* Les premiers arrivés ont un avantage, mais cela ne ressemble pas à un Ponzi
* Des effets en hippodrome peuvent être imaginés, par exemple les couches inférieures gagnent temporairement les avantages des couches supérieures (”accès aux box”) si un des représentants supérieurs est présent sur l'hippodrome

📗 Ce qu’on met dans le whitepaper..

### Quantité

* Nombre de Unique maximal : 8K (Trot + Galop) à confirmer et préciser lesquels
* Nombre de drops :

### Quels chevaux mettons-nous en jeu ?

À quel âge ?

### Caractéristique des NFT

* Édition : real-owner

### Skins / Design des NFT

Les familles de chevaux pourraient collectivement personnaliser et améliorer le design de leur NFT, avec un visuel plus évolué pour les raretés supérieures.

## Jeu

À la manière d’un jeu de stratégie, des cartes qui doivent être jouées avant la course permettent de modifier le classement (relativement à un joueur). Cela permet de rendre Stables intéressant même si on a un cheval qui n’est pas bon.

Par exemple, la carte “Mon cheval gagne un rang” permet de toucher un meilleur prix si le cheval passe de 3ème à 2ème. Les autres joueurs ne seraient pas impactés, c’est-à-dire que le vrai 2ème touche la même somme que le 3ème boosté 2ème. En revanche si le cheval passe de 7ème à 6ème, il ne gagne quand même rien.

_Considérations importantes_

Le financement de jeu pourrait être autonome, entre les joueurs de cartes, et ne pas pénaliser indirectement les réels gagnants de la course. À vérifier mathématiquement.

Sinon, il faudra prélever une partie sur la cagnotte réelle, ce qui indirectement diminuera le montant de la cagnotte distribuée sur la course (mais ce qui renforce l’idée que Stables serait un _jeu_, puisque les _bons joueurs_ gagnent, pas que les chanceux qui ont un bon cheval).

Aussi, à l’inverse de ce qui a été dit auparavant, le classement final pourrait être impacté par les cartes, ce qui créerait une dynamique semblable au “pierre-feuille-ciseau” “je joue telle carte, connaissant mon cheval et connaissant les joueurs en face, car je pense que l’adversaire va jouer telle autre carte”. Cela mélange stratégie, psychologie, courses réelles (qui conditionnent tout le jeu) et aléatoire (je n’ai pas choisi mon cheval). L’effet des différentes cartes jouées par tous les joueurs de la course pourraient créer des dynamiques très intéressantes.

_Nature des effets des cartes_

Les cartes ont un impact sur le tableau de classement final, mais elles pourraient aussi dépendre du déroulé de la course (par exemple “action sur la dernière ligne droite”), ce qui permet des mécaniques plus sophistiquées. Cela nécessite une décomposition de chaque course (à la manière de Sorare) donc pas possible dans l’immédiat. Cependant, c’est déjà un peu le cas dans les résumé de course (”SuperSuperSonic remporte la course grâce à une derrière accélération et l’emporte sur le favori en tête jusqu’à la dernière ligne droite”).

_Type de carte_

* \+1
* Premier si 2 ou 3
* Anti-élimination : un cheval éliminé obtient un lot de consolation
* Ordre inverse
* Boost aléatoire
* etc.

_Prix des cartes / équilibre économique_

Si les chevaux étaient équitables, le prix de vente serait purement mathématique. Les chevaux étant cependant de performance différente, il faut viser à ce que le point d’équilibre de la carte soit fixée sur les chevaux auxquelles elle s’adresse.

Pour anti-élimination par exemple, la carte peut-être construite de sorte à contre-carrer un cheval éliminé 1 fois sur 2. Le prix de la carte pourrait aussi être évolutif et dépendre du cheval.

Quoi qu’il en soit, cet équilibre économique demande de la modélisation et probablement une phase de test.

*   Feedback Axel

    la carte coûte un prix dépendant de la course, ou n’est jouable que sur une catégorie de course (carte et cheval doivent être de la même catégorie). Prix fixe, aléatoire, les joueurs cherchent la bonne carte. Les cartes abondent la course sur laquelle elles sont jouées (et potentiellement prélèvement une petite partie). Pour le tester : soit ML, soit en vrai avec un groupe de test.

    (!) même un bon joueur de cartes ne peut pas changer son cheval s’il n’est pas bon.

    Il propose de faire un système de carte où on ne gagne pas un classement, mais on gagne oui/non sur son pari, ça incite à bien connaître son cheval et le contexte de la course.

_Comment achète-t-on des cartes ?_

Soit en direct, soit de manière aléatoire/groupée en NFT, ce qui permet la revente et créée une nouvelle dimension d’échange.

Des cartes pourraient être offertes aux joueurs sur des événements spéciaux.

📗 Ce qu’on met dans le whitepaper..

## Cagnotte

[Modèle de Own-to-Earn](https://www.notion.so/Mod-le-de-Own-to-Earn-f0e488a866bd4e9888e0de3deab52b6a)

* Quid des chevaux qui arrêtent de courir

## Économie

Économie : il est d’usage dans un jeu de créer une sorte d’économie parallèle avec un monnaie dédiée, ce qui a pour effet d’augmenter les revenus du studio (le montant est bloqué dans le jeu, l’achat est simplifié, etc.).

Naturellement, les projets Web3 ont tendance à adopter la même logique, et créent un token monétaire. Tant qu’il reste interne au jeu, non liquide, et que des tokens ne sont pas trop facilement distribués de manière inflationniste, tout va bien (ce que souhaite faire Dogami, ce que n’a pas fait Axie Infinity).

Créer un lien entre cette monnaie et le réel pourrait être intéressant, dans le cadre événements hippiques notamment, ou d’avantages à l’achat de produits PMU ou de partenaires hippiques.

📃 \[https://whitepaper.dogami.com/usddoga-tokenomics/usddoga-token-utility-and-token-flow]\(https://whitepaper.dogami.com/usddoga-tokenomics/usddoga-token-utility-and-token-flow)

*   Annexe Tokenomics

    Selon Nomiks, les avantages de la création d’un token sont :

    1. **Leviers de contrôle** : La création d’un token permet de créer ou de brûler des tokens pour stabiliser le marché (Use case : Gods Unchained a décidé de lancer le concept de “forge”, un outil pour détruire ses cartes en doublons afin de générer une carte de rareté supérieure (jusqu’à en faire une vraie NFT revendable), dans ce cas le token GODS sert de compensation lors de l’utilisation de la forge)
    2. **Décupler l’effet de réseau**
       1. La création d’un token augmente la portée du produit et facilité la communication en permettant de bénéficier des différentes places de listing.
       2. Le token apporte des possibilités de récompenses, d’adoption et d’évaluation que le trading card game n’offre pas.
       3. Créer la sensation d’appartenance à l’écosystème
       4. Tracer sur une Blockchain un token dédié à un écosystème est plus facile que de tracer le coin natif de celle-ci comme ETH.
    3. **Responsabiliser les acteurs**
       1. Un token au sein d’un écosystème induit la notion de TVL (Total Value Lock), cette même valeur bloquée appartient en majorité aux utilisateurs, ce qui représente pour eux une nécessité de sérieux et rigueur
       2. le token offre la possibilité de cadrer les acteurs responsables au travers du “slashing” (principe punitif au sein des environnements à responsabilité distribuée)

📗 Un token monétaire sera peut-être introduit en 2023, pour faciliter les transactions au sein du jeu. Il n'aura pas d'impact sur la \*mécanique\* de jeu. Il pourrait être lié à des possibilités d’achats réelles, dans l’univers hippique. Ce token n’aura pas pour vocation à être convertissable dans une monnaie \*fiat\* (il ne sera pas liquide).

## Gouvernance (DAO)

Certaines décisions peuvent être proposées à la communauté, ce qui donne une dimension de DAO, sans en être totalement une.

* Que faire de la cagnotte (convertir / investir)
* Valider les mécaniques de jeu (référendum, veto..)

Pour organiser un vote, nous devons l’organiser par nous-même ou utiliser une solution tierce de DAO.

📗 Nous mettrons au vote de nombreuses décisions auprès des joueurs, le droit de vote étant associé à la possession d’un NFT. C’est un moyen pour nous d’écouter les joueurs et de leur permettre d’intervenir dans certains choix importants : mécaniques de jeu, choix technologiques, choix d’investissement, etc. La première est particulièrement importante et sera proposée aux possesseurs de NFTs dans les prochaines semaines : que faisons-nous du montant de la cagnotte, qui sera distribuée sur plusieurs années. Nous pouvons la mettre en \*baking\* à des taux plus ou moins risqués, la convertir en stablecoin, l’investir dans l’économie réelle, etc.

## Metaverse

À ce jour, le lien entre Stables et le Metaverse est évident (Web3) mais manque de caractère concret. De nombreuses (bonnes) idées n’ont pas de lien direct avec nos NFTs. Liste des choses que nous envisageons :

* Reproduire les courses dans le Metaverse
* Proposer aux joueurs des mini-jeux dans les hippodromes virtuels
* Permettre à un propriétaire d’inclure son cheval NFT dans un autre jeu (type Red Dead Redemption ou Fortnite)

📗 Nous suivons de près le développement de plusieurs metaverse (Decentraland, The Sandbox). En association avec le PMU, qui a acheté 3 lands sur The Sandbox, nous participerons à l’ouverture des hippodromes dans le metaverse en créant plusieurs mini-jeux. Les possesseurs de NFTs y auront un accès privilégié.

## Encaissement/Décaissement

* Que devient la somme levée en XTZ ? On la garde, on la convertit ? Permet-on à la communauté d’influer sur cette décision ? Quand prélève-t-on la part réservée aux ayants-droit et au projet ?
* En quoi verser les gains aux joueurs, à quelle fréquence ?

## Whitepaper

* Comment sépare-t-on l’aide du white-paper ? Certains sujets (wallet connect) sont communs. Le format gitbook est-il finalement le bon ?
* Est-ce qu’on lui donne un autre nom (wittpaper, whip-paper,..) ?
* Publie-t-on la version complète du modèle mathématique ? Dans quelle mesure peut-on prouver que l’évolution de la “cagnotte moyenne” suit bien le modèle (publier les données de calcul progressivement ?)

Plan du whitepaper.

* Expérience de jeu. Quelqu’un possède un NFT, ça lui ouvre droit à quoi (combien il gagne)
  * Définition d’un NFT (avec niveau de rareté)
  * Définition de ce qu’est une course
  * Définition des gains
* Comment acheter des NFT
* Comment est calculée la valeur de la cagnotte course
* Questions blockchain

📃 \*Exemples de whitepapers\*

* [Dogami](https://www.notion.so/Dogami-0ff045324e0c4359b39cf35ee5a225f9) ([direct link](https://whitepaper.dogami.com/))
* [Zed Run](https://www.notion.so/Zed-Run-62bb730369534496997315e615a1d838) ([link](https://guide.zed.run/))
* [Axie Infinity](https://www.notion.so/Axie-Infinity-b9f9d0f46e1344aeab5905a13d260f38)([link](https://whitepaper.axieinfinity.com/d-a-o))
* [Pegaxy](https://www.notion.so/Pegaxy-79c8ac722e204dbd8f98b65b2ecd8e48)
* [StepN](https://www.notion.so/StepN-7008aa6f86ee4a23926b04203b16d35f) ([link](https://whitepaper.stepn.com/marketplace))

## Conditions d’utilisation

* La possession de NFT est associée à 2 principes fondateurs :
  * c’est une “carte de membre” qui donne accès à des accès privilégiés à l’univers hippiques
  * des gains sont reversés selon les résultats des courses réelles sur toute la carrière des chevaux, selon un un algorithme basé sur une modélisation mathématique équitable et qui s’auto-régule au fil du temps
* Il s’agit d’un jeu de stratégie, pas un jeu d’argent, ni un investissement
* Concernant le jeu, les règles du jeu peuvent évoluer, l’objectif étant de favoriser les bons joueurs

## Marketplace/marché secondaire

* Comment gérer le marché secondaire (marketplace in house ou objkt/rarible) ? Est-ce qu’on scénarise les enchères ?

## Oracle

* Résultats des course
* Décomposition des courses

## Communications au sein du jeu

## Plaisir de jeu et objectifs

## Difficulté et Courbe d’apprentissage

## Divers

* Headquarters in The Sandbox ? (inspiration [link](https://guide.zed.run/zed-run-guide/frequently-asked-questions/general-faq/zed-headquarters-dcl#what-is-zed-hq-and-where-is-it))
* Proof of Attendance ([poap.xyz](https://poap.xyz/#start)) (ZED.run)
* Peut-on louer l’usufruit du NFT ? (pour le droit d’accéder à l’hippodrome par exemple)
* Comment intègre-t-on les autres éléments de l’écosystèmes hippique ?
* Quel lien avec le réel créé-t-on via le NFT ?
* “Stableiser” les pseudo pour les rendre aussi beaux que les noms des chevaux (interdire toto\_du\_83)
* Est-ce qu’on limite le nombre de NFT par joueur ?
* Post-mint, affichera-t-on à la fois la possibilité de minter et de racheter un cheval ?

## Smart-contract

* Le smart-contract doit-il afficher les adresses auxquelles il envoie des fonds ?

## Références

## Lexique

* Paris : montant mis en jeu par les parieurs sur une course, majoritairement redistribué entre parieurs, et ponctionné pour le budget PMU, et donc le budget d’allocation
* Budget d’allocation : somme annuelle allouée par le PMU à l’opérateur des courses (LeTrot ou France Galop) pour récompenser les gagnants des courses
* Allocation : montant distribué par course par l’opérateur des courses aux propriétaires
* Propriétaire : propriétaire du cheval
* Double Numérique ou Cheval NFT : produit dérivé financier/ludique du cheval, pouvant exister en plusieurs copies
* Propriétaire NFT : propriétaire du cheval NFT
* Prize Pool — Cagnotte globale : montant levé par la vente des NFT, et distribué par course par l’opérateur du Jeu. Montant proportionnel à l’allocation
* Race Prize — Cagnotte course : montant prélevé de la cagnotte globale et distribué aux propriétaires NFT à chaque course, proportionnellement à l’allocation réelle. Note : le terme e-Allocation semble impropre car il n’est conceptuellement pas semblable à l’allocation

## Annexes

[Analyse des chevaux et des courses](https://www.notion.so/Analyse-des-chevaux-et-des-courses-0c47abb28e1a48aba291ce6ec6e3cd49)

[Whitepaper Stables](https://www.notion.so/Whitepaper-Stables-0791324229af42dda00f76d0d3abdec4)

## Helper

📃 Éléments externes qui alimentent la réflexion

* Lien 1

📗 Ce qu’on met dans le whitepaper..
