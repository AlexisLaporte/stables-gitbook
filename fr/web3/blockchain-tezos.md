# ⛓️ Blockchain (Tezos)

Nous avons choisi Tezos après avoir analysé de nombreuses blockchains début 2022, notre choix final étant un Ethereum Layer 2 ou Tezos.

Nous pensons que Tezos a tout ce dont nous avons besoin pour développer le jeu pour l'instant, et a des fondamentaux solides pour l'avenir, l'argument principal étant la gouvernance en chaîne de Tezos qui permet au protocole d'être régulièrement mis à jour (sans avoir besoin d'un fork).

Cela permet à Tezos d'intégrer de nouvelles fonctionnalités au fur et à mesure que sa base d'utilisateurs et son volume de transactions augmentent. Cela ouvre également la possibilité de devenir compatible avec Ethereum à l'avenir, ce qui pourrait être dévoilé dans un avenir proche.

<figure><img src="../.gitbook/assets/stables_and_tezos.jpeg" alt=""><figcaption></figcaption></figure>

Voici le top 6 de nos raisons d'utiliser Tezos :

1. Un haut niveau de sécurité sur la blockchain (LPoS)
2. Un faible coût énergétique
3. Une bonne stabilité monétaire qui nous permet de miser des Tezos sans trop de risques
4. Une large communauté d'entreprises partenaires comme Ubisoft, Decathlon, EDF ou Casino
5. Une espérance de fonctionnement à moyen et long terme
6. La possibilité native de mettre à jour son logiciel

### Écuries et Tezos

Nous utilisons des nœuds fournis par Exaion et nous prévoyons de maintenir notre propre nœud, en particulier parce que nous voulons héberger notre propre Layer 2 pour gérer les transactions en S-Points du jeu.

Voici nos adresses de contacts intelligents :

* Stables Pass (NT NFT) : [`KT1RqXzEKaChWrBpmfWUmUbMJ7zLRCW2F6YL`](https://better-call.dev/mainnet/KT1RqXzEKaChWrBpmfWUmUbMJ7zLRCW2F6YL/operations)
* Stables NFT Collection: [`KT1MQL8VjVQckk5A6uBfN9Qv2YUVJstG1CyH`](https://better-call.dev/mainnet/KT1MQL8VjVQckk5A6uBfN9Qv2YUVJstG1CyH/operations)
* Stables Contrat Vente Vente: [`KT1JF9JfwRc9wwoMEQFUZDZBrVDvrazYdEFK`](https://better-call.dev/mainnet/KT1JF9JfwRc9wwoMEQFUZDZBrVDvrazYdEFK/operations)

Voici la liste des wallets sur lesquels vous pourrez trouver des NFTs unrevealed:

* Treasury wallet appartenant à Stables: tz1Maj1mK5MW7DW82qrWt1X4nuaQLmLVkvuT
* Wallet appartenant à PMU: tz1R3LNcWR1dpEs45Q4zzvzJYZhnYWnjj5jP

## Provenance Hash

Provenance Hash est une manière de prouver que les métadonnées des NFTs n'ont pas été modifiées à posteri (puisqu'elles ne sont pas stockées sur la chaîne).

* NFT Provenance Hash: il s'agit de l'ID du NFT, calculé comme suit:
  * nous utilisons les informations suivantes: numéro du NFT dans la collection, Code du Pays de Naissance, Année de Naissance, Date de Naissance, Nom Officiel du Cheval
  * toutes concaténées et séparées par des double-points, ce qui donne quelque chose comme `1:FR:2023:2023-01-01:NAME`
  * nous appliquons ensuite la transformation suivante :
    * _bytes_: `31 3a 46 52 3a 32 30 32 33 3a 32 30 32 33 2d 30 31 2d 30 31 3a 44 41 56 49 44`
    * _little_: `109732130401448801075897904080883403357190557740499221633972785`
    * _modulo 10^12_: `221633972785`, ce qui donne le token
* NFT List Provenance Hash: il s'agit du hash de la liste entière, nous le dévoilerons bientôt

## Qu'en est-il des autres blockchains ?

Nous étudierons des moyens de nous connecter avec d'autres chaînes, soit pour déplacer les NFTs entre les chaînes, soit pour accepter les inscriptions d'utilisateurs d'autres communautés.&#x20;

Cependant, nous pensons que Tezos restera notre principal backend pour, disons, un bon moment.
