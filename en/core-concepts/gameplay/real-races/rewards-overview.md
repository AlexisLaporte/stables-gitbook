# Rewards overview

For every race where a NFT participate, we allocate an amount given by our math model, trained on historical data. _This amount is always higher that what we expect to distribute, since not all participants have an NFT, and we monitor how much we distribute._

## Race categories

Some races are more important than others, and the value of a race pool is described as follows.

$$
RacePool = RaceValue * PoolIndex
$$

`RaceValue` represents the importance of the race. It depends only on the real life allocation of the race which is fixed by the organizers.&#x20;

`PoolIndex` varies in time, it ensures that S-Points will be distributed fairly along all the career of the horses of a given generation.

## Reward distribution

To distribute rewards over horses according to their rank, we will always follow PMU's official ranking. Most of the time it's immediate after the race, but their may be a delay in case of contestation.

The way horses receive a reward based on their ranking is fixed by races organizers (Le Trot and France Galop), with some small variants.

<table><thead><tr><th width="121.66666666666666">Ranking</th><th>Percentage earned by the horse at "le TROT"</th><th>Percentage earned by the horse at "France Galop"</th></tr></thead><tbody><tr><td>1</td><td>45%</td><td>50%</td></tr><tr><td>2</td><td>25%</td><td>20%</td></tr><tr><td>3</td><td>14%</td><td>15%</td></tr><tr><td>4</td><td>8%</td><td>10%</td></tr><tr><td>5</td><td>5%</td><td>5%</td></tr><tr><td>6</td><td>2%</td><td>0%</td></tr><tr><td>7</td><td>1%</td><td>0%</td></tr><tr><td>>7</td><td>0%</td><td>0%</td></tr></tbody></table>

More details about this distribution: see [LeTrot](https://devenir-proprietaire.letrot.com/gains-de-courses) and [France Galop](https://www.france-galop.com/en/devenir-proprietaire/faq) according to your horse kind.

## Earning profiles (careers)

Stables has developed a mathematical model to distribute points (currency) to NFTs of horse that run and win in real life.&#x20;

We observed the following distribution:

| Horse Category     | Share       | S-Points expectancy |
| ------------------ | ----------- | ------------------- |
| Exceptional Horses | Top 5%      | >5x 3.333 S-Points  |
| Great Horses       | 5% to 20%   | \~2x 3.333 S-Points |
| Average Horses     | 20% to 50%  | \~1x 3.333 S-Points |
| Dismissed Horses   | 50% to 100% | \~0x 3.333 S-Points |

The career of a horse can last up to 6 years. For the best horses, the earnings of the NFT along the career can be significant and generate a great amount of S-Points. Yet, we also see that a good half of selected horses do not run much in their career.

## Pool index (math details)

Recall that prize pools are set-up in S-Points during the NFT drop. Horses may run up to 6 years. Hence, pool constituted in 2023 feeds prize pools in 2029. Since the race calendar is known only 6 months in advance, we do not know in 2023 how many races will be run in 2029.&#x20;

`PoolIndex` may therefore evolve with time. It modulates the prize pools to the evolution of the race calendar and racer population. Our guidelines to ensure a fair game are the following:

* There should be a pool for every race where a NFT horse participate that takes place in the 5 years following the sale of the NFT.
* The pool index should remain as stable as possible: finishing 2nd in a 100 points race in should lead to the same earnings in 2023 and in 2029
* All the prize pool should have been distributed when the last horses of an NFT generations finish their career.
* If a NFT horse participates in a race, its reward should not depend on the proportion of NFT horses among its competitors.

When implementing these guidelines, we must address the fact that&#x20;

1. points must be distributed on the long term, and
2. races have NFTs and non-NFT competitors

The long-term aspect is relatively straightforward. We only have to save points for the future, based on statistics on horse long term performances.&#x20;

The second is more challenging. Indeed, the pool is distributed only to NFT horses, based on the ranking of all horses. Hence, if there are few NFT horses on a race, and if these horses perform badly, only a fraction of the pool is going to be distributed.

To ensure that all the money is distributed, _Stables_ race pools are over allotted, knowing that only a share of the pool is going to be distributed. Race pools must however be defined with care. They should not be too large, as this would be at the expense of future years pools. And they should not be too small, as _Stables_ wants to distribute all prize pool. These are the reason why the definition of our pool index is quite technical.

In practice, our algorithms works as follows:

Historical data enable to predict the average earning of a horse in each year of its career. We can therefore allocate points to the different years proportionally to this average performance. Each year points is then allocated to the races of the year, proportionally to their importance. Finally, we estimate the share of the race pool that is going to be distributed, and rescale the pool accordingly.&#x20;

The pool index is therefore defined as follows:

$$
\text{pool index} = \frac{\text{yearly saving for a 1 point race}}{\text{estimation of the share of the pool that is going to be distributed}}.
$$
