

# Stables pools

This section details how the value of the [race pool](https://app.gitbook.com/o/zs4z9h43TOoCKG4xpY8f/s/6Zlr2NZWiAUeTkpsK0oc/own-to-earn/own-to-earn) is fixed. It is much more technical than other sections and requires some background in mathematics to be understood.

## Some notations

We start by introducing some mathematical notations for the concepts introduced more pedagogically in previous sections on the whitepaper.

### Horses and races
Let $H$ be the set of horses $h$ that participate in races.
We denote by $T$ the set of time instants $t$ corresponding to each period of race.
Let $R$ be the set of all races $r$. 
As there can be several races in parallel, we denote by $R_t$ the set of races taking place at time $t$.
All the races are not of the same importance, so they give right to different prize pools.
We denote by $v_r$ the value of a race. This value is measured as a multiple of the basic prize pool.
The [value](https://app.gitbook.com/o/zs4z9h43TOoCKG4xpY8f/s/6Zlr2NZWiAUeTkpsK0oc/own-to-earn/own-to-earn) $v_r$ of each race is published when the race calendar is fixed, i.e., six months in advance.
We denote by $P_r$ the prize pool that will be shared between the horses in race $r$.


### NFTs

When horse $h$ makes gain on a race, these gains are shared among the different NFT corresponding to horse $h$. This [documentation](https://app.gitbook.com/o/zs4z9h43TOoCKG4xpY8f/s/6Zlr2NZWiAUeTkpsK0oc/own-to-earn/own-to-earn) details the share of gains that is attributed to each NFT.
We denote by $\mathcal{T}$ the set of all the tokens $\tau$ of all the horses. 
We denote by $\mathcal{T}_h$ the set of all horses corresponding to the horse $h$ and $h_\tau$ the horse to which corresponds the token $\tau$.

### Distribution of prize pools among NFTs

At each time $t$ we have a prize pool $P_t$ which will be shared between the races taking place at time $t$.
The prize pool $P_t$ is shared between all races that take place at $t$ in proportion to their respective importance.
$$P_r = \frac{v_r}{\sum_{r' \in R_{t_r}}v_{r'}} P_t $$

> $P_t$ is convenient mathematical concept that conveys the same information as the [pool index](https://app.gitbook.com/o/zs4z9h43TOoCKG4xpY8f/s/6Zlr2NZWiAUeTkpsK0oc/own-to-earn/own-to-earn).

For each race $r$ and for each possible ranking $\rho$ of a horse on the race $r$, we denote by $w_{\rho r}$ the part of the prize pool $P_r$ 
which will be paid to the horse which arrives in position $\rho$ on the race.
$$ \sum_{\rho} w_{\rho r} = 1$$
This [page](https://app.gitbook.com/o/zs4z9h43TOoCKG4xpY8f/s/6Zlr2NZWiAUeTkpsK0oc/own-to-earn/own-to-earn) provides the value of the $w_{\rho^r}$ for the different races when the competing horses are known.
The payoff for the horse $h$ that participates in the race $r$ at the end of the race is
$$ W_{hr} = P_r w_{\rho_{hr} r}, $$
where $\rho_{hr}$ is the ranking of $h$ on $r$.

Each NFT $\tau$ is entitled to a share $s_\tau$ of the winnings of its horse $h_\tau$. These shares are detailed [here](https://app.gitbook.com/o/zs4z9h43TOoCKG4xpY8f/s/6Zlr2NZWiAUeTkpsK0oc/own-to-earn/own-to-earn). For our purpose here, we just remark that
$$ \sum_{\tau \in \mathcal{T}_h} s_\tau = 1. $$
The winnings of the owner of the $\tau$ token at the end of a $r$ race in which $h_\tau$ participates is 
$$ W_{\tau r} = s_\tau W_r. $$
Let us finally denote by $W_{\tau t}$ the payoff for $\tau$ at $t$. This gain is equal to $0$ if $h_\tau$ does not participate in any race in $R_t$, and to $W_{\tau r}$ if it participates in $r \in R_t$.

## Definition of prize pools

NFTs are sold simultaneously for horses of a given generation. The money raised from the sell of these NFTs is used to fuel the race pools. 

### Money allocation across time

Pools are share by horses of the same generation. 
In this section, we therefore consider all the horses of a given generation.
$T_{y}$ the set of time instants the $y^{\mathrm{th}}$ year of the horses of the generation. 
We denote by $g_{y}$ the average share of earnings that a horse of realizes during its $y^{\mathrm{th}}$ year. 
This is defined as
$$ g_{y} = \frac{\text{Expectation of winnings of a horse during its $y^{\text{th}}$ year}}{\text{Expectation of winnings of a horse over its lifetime}}. $$
We have 
$$ \sum_{y \geq 0} g_{y} = 1$$
The [value](link_to_page) of $g_{y}$ have been computed on historical data. 

For every sale of a horse, the PMU takes a tax at the rate of $\alpha$. The rest of the sale is used to feed the pools for the following years' races, in proportion to the horse's expected winnings in the various following years and the value of the races. 
Let $f_{tt'}$ be the share of the sale of a horse at $t$ that will feed the pools at $t'$.

To define $f_{tt'}$, we first allocate the sum to each year: we weight $g_{Dy}$ again in proportion to the races not yet completed at the time of the sale. Let $T_y$ be the set of time steps in year $y$ and $\tilde f_{ty}$ be the expected revenue of a horse in year $y$ reweighted by the proportion of races that have still not been run at time $t$.

$$\tilde f_{ty} = g_{Dy} \underbrace{\Bigg[\frac{\sum_{t' \in T_{y} \colon t' \geq t}\sum_{r \in R_{t'}}v_r}{\sum_{t' \in T_{y}}\sum_{r \in R_{t'}}v_r}\Bigg]}_{\substack{\text{share of races in year $T_{y}$}\\\text{not yet realized at $t$}}}$$

Then we define the share of winnings going to a race as the share of winnings going to the race among the winnings going to the year
$$ f_{tt'} = (1 - \alpha) 
\underbrace{\frac{ \tilde f_{ty_{t'}}}{\sum_{y \geq 0} \tilde f_{ty}}}_{\text{year share}} \underbrace{\frac{\sum_{r \in R_{t'}}v_r}{\sum_{t'' \in T_{y_{t'}} \colon t'' \geq t}\sum_{r \in R_{t''}}v_r}}_{\text{timestep share}}\quad \text{for all $t$, $t' \geq t $ and $h$,} $$
where $y_{t'}$ is year of $t'$, i.e., $t' \in T_{y_{t'}}$.

> Money from the sale of a NFT must be immediately allocated to prize pool races 5 years later. However, race calendar is known only 6 month in advance. This is the reason why money is first allocated on a yearly based, and then allocated to the race of the year once the race scchedule is known.

### Prize pool definition

Let $\mathcal{S}_{=t}$ be the set of tokens that are sold at time $t$, and $F_{tt'}$ the amount collected in $t$ that is used to replenish the pool in $t'$. 
We have
$$ F_{tt'} = \sum_{\tau \in \mathcal{S}_{=t}} c_{\tau} f_{tt'},$$
where $c_{\tau}$ is the price at which NFT $\tau$ has been sold.
Since some horses may not be from the NFT generation, only a part of the pool is distributed at each time $t$. 
Let us denote $W_t$ this quantity.
We have 
$$W_t = \sum_{\tau \in \mathcal{S}_{\leq t}} W_{\tau t}, \quad \text{where} \quad \mathcal{S}_{\leq t} = \bigcup_{t'\leq t}\mathcal{S}_{=t},$$
and $W_{\tau t}$ has been previously defined as the winnings of NFT $\tau$ at time $t$.

To make things simpler, consider what would happen if there was a single NFT for each and every horse that participate in the races. For a given race, there is a single NFT for all the participants of the race. Hence, money from the sale each of this NFT has been allocated to the race pool. And all the money in the pool is distributed. In that case, we could therefore define $P_t$ as the money collected for time $t$
$$ F_t = \sum_{t'\leq t}F_{t't}$$
The definition of $P_t$ is complicated by the fact that there is not an NFT for each horse that participate in the races. Hence, only some horses contribute to the pools and receive winnings. Hence, if we defined $P_t$ as $F_t$, only a small amount of the money collected would be distributed. We therefore need to weight $F_t$ to ensure that the money collected for the pool is indeed distributed.
More precisely, we must predict which share of the pool will be distributed, and correct $F_t$ in proportion.

Let $Y_t$ be the share of the jackpot distributed at $t$.
$$ Y_t = \frac{W_t}{P_t} $$
Note that $Y_t$ does not depend on the amount of the prize pool: this variable only reflects the performance of the horses for which NFT have been sold.
Since this random variable typically has a large variance, it is natural to average it over a given period of time.
Let $$Y^{\Delta}_t = \frac{1}{\Delta} \sum_{t' = t- \Delta}^{t-1} Y_t$$ 
be the average share distributed over the period $\Delta$ before $t$. 
The prize pool value is defined as
$$ P_t = \frac{F_t}{Y^{\Delta}_t}.$$

## Illustration on historical data

We now illustrate on some historical data how the prize pools behave. The results are illustrated supposing that !!! NFT have been sold for horses born in !!! and sold in !!!.

The following figure illustrates the value of $P_t$ from !!! to !!!.

![Value of P_t](p_t.jpg)

The oscillations are due to the fact that, on different days, more or less important races are run. Let us now look at what $P_r$ would be for a [100 points](https://app.gitbook.com/o/zs4z9h43TOoCKG4xpY8f/s/6Zlr2NZWiAUeTkpsK0oc/own-to-earn/own-to-earn) race on each of these days.

![Value of P_r](p_t.jpg)
