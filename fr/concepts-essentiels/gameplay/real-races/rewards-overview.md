# Calcul des gains

Pour chaque course à laquelle participe un NFT, nous allouons un montant donné par notre modèle mathématique, entraîné sur des données historiques. Ce montant est toujours supérieur à ce que nous prévoyons de distribuer, car tous les participants n'ont pas de NFT, et nous surveillons le montant que nous distribuons.

## Catégories de course

Certaines courses sont plus importantes que d'autres, et la valeur d'une course est décrite comme suit.

$$
RacePool = RaceValue * PoolIndex
$$

`RaceValue` représente l'importance de la course. Cela dépend uniquement de l'attribution réelle de la course qui est fixée par les organisateurs.

`PoolIndex` varie dans le temps, il assure que les S-Points seront répartis équitablement tout au long de la carrière des chevaux d'une génération donnée.

## Distribution des gains

Pour répartir les gains sur les chevaux selon leur classement, nous appliquerons toujours le classement officiel du PMU. La plupart du temps c'est immédiat après la course, mais il peut y avoir un délai en cas de contestation.

La façon dont les chevaux reçoivent une récompense en fonction de leur classement est fixée par les organisateurs de courses (Le Trot et France Galop), avec quelques petites variantes.

| Classement | Part des gains (LeTrot) | Part des gains (France Galop) |
| ---------- | ----------------------- | ----------------------------- |
| 1          | 45%                     | 50%                           |
| 2          | 25%                     | 20%                           |
| 3          | 14%                     | 15%                           |
| 4          | 8%                      | 10%                           |
| 5          | 5%                      | 5%                            |
| 6          | 2%                      | 0%                            |
| 7          | 1%                      | 0%                            |
| >7         | 0%                      | 0%                            |

Plus de détails sur cette répartition : voir [LeTrot](https://www.france-galop.com/fr/devenir-proprietaire/faq) et [France Galop](https://devenir-proprietaire.letrot.com/gains-de-courses) selon votre race de cheval.

## Profils de gains (carrières)

Stables a développé un modèle mathématique pour distribuer des points (monnaie) aux NFT de chevaux qui courent et gagnent dans la vraie vie.

Nous avons observé la distribution suivante :

| Catégorie             | Share      | S-Points expectancy |
| --------------------- | ---------- | ------------------- |
| Chevaux Exceptionnels | Top 5%     | >5x 3.333 S-Points  |
| Bons Chevaux          | 5% à 20%   | \~2x 3.333 S-Points |
| Chevaux Moyens        | 20% à 50%  | \~1x 3.333 S-Points |
| Chevaux Irréguliers   | 50% à 100% | \~0x 3.333 S-Points |

La carrière d'un cheval peut durer jusqu'à 6 ans. Pour les meilleurs chevaux, les gains du NFT tout au long de la carrière peuvent être importants et générer une grande quantité de S-Points. Pourtant, on constate aussi qu'une bonne moitié des chevaux sélectionnés ne courent pas beaucoup dans leur carrière.

## Pool index (détails maths)

Les cagnottes de S-Points sont alimentées lors de la vente des NFT. Les chevaux peuvent courir jusqu'à 6 ans. Ainsi, la cagnotte constituée en 2023 finance des récompenses en 2029. Le calendrier des courses n'étant connu que 6 mois à l'avance, nous ne savons pas en 2023 quelles courses seront courues par quels NFTs en 2029.&#x20;

`PoolIndex`peut donc évoluer avec le temps et module les cagnottes selon l'évolution du calendrier des courses et de la population de coureurs. Nos lignes directrices pour assurer une équité entre les joueurs sont les suivantes :

* Il doit y avoir un pool pour chaque course à laquelle participe un cheval NFT qui a lieu dans les 5 ans suivant la vente du NFT
* `PoolIndex` doit rester aussi stable que possible : terminer 2e d'une course de 100 points devrait conduire aux mêmes gains en 2023 et en 2029
* La cagnotte de S-Points doit être entièreement distribuée lorsque les derniers chevaux d'une génération NFT terminent leur carrière.
* Si un cheval NFT participe à une course, sa récompense ne doit pas dépendre de la proportion de chevaux NFT parmi ses concurrents

Lors de la mise en œuvre de ces directives, nous devons tenir compte du fait que

1. les points doivent être distribués sur le long terme, et
2. les courses ont des concurrents NFT et non NFT

L'aspect à long terme est relativement simple. Nous n'avons qu'à économiser des points pour l'avenir, sur la base de statistiques sur les performances à long terme des chevaux.

La seconde est plus exigeante. En effet, le pool est distribué uniquement aux chevaux NFT, en fonction du classement de tous les chevaux. Ainsi, s'il y a peu de chevaux NFT sur une course, et si ces chevaux performent mal, seule une fraction du pool va être distribuée.

Ainsi, pour s'assurer que toute la cagnotte est distribuée, les pools de courses _Stables_ sont surabondées mais doivent cependant être définies avec soin. Elles ne doivent pas être trop grandes, car cela se ferait au détriment des _pools_ des années futures. Et elles ne doivent pas être trop petites, car _Stables_ veut distribuer toute la cagnotte à terme. C'est la raison pour laquelle la définition de notre pool index est assez technique.

En pratique, nos algorithmes fonctionnent comme suit :

Les données historiques permettent de prédire le revenu moyen d'un cheval à chaque année de sa carrière. On peut donc attribuer des points aux différentes années proportionnellement à cette performance moyenne. Chaque année des points sont ensuite attribués aux courses de l'année, proportionnellement à leur importance. Enfin, nous estimons la part du pool de course qui va être distribuée et redimensionnons le pool en conséquence.

L'indice du pool est donc défini comme suit :

$$
\text{pool index} = \frac{\text{économie annuelle pour une course à 1 point}}{\text{estimation de la part du pool qui va être distribuée}}.
$$
