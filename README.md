# PancakeSwap Subgraph

TheGraph exposes a GraphQL endpoint to query the events and entities within the Binance Smart Chain and PancakeSwap ecosystem.

Currently, there are multiple subgraphs, but additional subgraphs can be added to this repository, following the current architecture.

## Subgraphs

1. **[Blocks](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/blocks)**: Tracks all blocks on Binance Smart Chain.

2. **[Exchange V2](https://nodereal.io/meganode/api-marketplace/pancakeswap-graphql)**: Tracks all PancakeSwap V2 Exchange data with price, volume, liquidity, ...

3. **[Farm Auctions](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/farm-auctions)**: Tracks all PancakeSwap Farm Auctions with auctions and bids.

4. **[Lottery](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/lottery)**: Tracks all PancakeSwap Lottery with rounds, draws and tickets.

5. **[NFT Market (v1)](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/nft-market)**: Tracks all PancakeSwap NFT Market for ERC-721.

6. **[Pairs](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/pairs)**: Tracks all PancakeSwap Pairs and Tokens.

7. **[Pancake Squad](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/pancake-squad)**: Tracks all Pancake Squad metrics with Owners, Tokens (including metadata), and Transactions.

8. **[Prediction (v1)](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/prediction)**: Tracks all PancakeSwap Prediction (v1) with market, rounds, and bets.

9. **[Prediction (v2)](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/prediction-v2)**: Tracks all PancakeSwap Prediction (v2) with market, rounds, and bets.

10. **[Profile](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/profile)**: Tracks all PancakeSwap Profile with teams, users, points and campaigns.

11. **[SmartChef](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/smartchef)**: Tracks all PancakeSwap SmartChef (a.k.a. Syrup Pools) with tokens and rewards.

12. **[Timelock](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/timelock)**: Tracks all PancakeSwap Timelock queued, executed, and cancelled transactions.

13. **[Trading Competition (v1)](https://thegraph.com/legacy-explorer/subgraph/pancakeswap/trading-competition-v1)**: Tracks all metrics for the Easter Battle (April 07—14, 2021).

14. **[MasterChef (v2)](https://thegraph.com/hosted-service/subgraph/pancakeswap/masterchef-v2)**: Tracks data for MasterChefV2.

15. **MasterChef (v3)**: Tracks data for MasterChefV3.
    - BSC https://thegraph.com/hosted-service/subgraph/pancakeswap/masterchef-v3-bsc
    - BSC testnet https://thegraph.com/hosted-service/subgraph/pancakeswap/masterchef-v3-chapel
    - ETH https://thegraph.com/hosted-service/subgraph/pancakeswap/masterchef-v3-eth
    - ETH https://thegraph.com/hosted-service/subgraph/pancakeswap/masterchef-v3-goerli

16. **Exchange (v3)**: Tracks all PancakeSwap V3 Exchange data with price, volume, liquidity
    - BSC https://thegraph.com/hosted-service/subgraph/pancakeswap/exchange-v3-bsc
    - BSC testnet https://thegraph.com/hosted-service/subgraph/pancakeswap/exchange-v3-chapel
    - ETH https://thegraph.com/hosted-service/subgraph/pancakeswap/exchange-v3-eth
    - ETH https://thegraph.com/hosted-service/subgraph/pancakeswap/exchange-v3-goerli


## Dependencies

- [Graph CLI](https://github.com/graphprotocol/graph-cli)
    - Required to generate and build local GraphQL dependencies.

```shell
yarn global add @graphprotocol/graph-cli
```

## Deployment

For any of the subgraph: `blocks` as `[subgraph]`

1. Run the `cd subgraphs/[subgraph]` command to move to the subgraph directory.

2. Run the `yarn codegen` command to prepare the TypeScript sources for the GraphQL (generated/*).

3. Run the `yarn build` command to build the subgraph, and check compilation errors before deploying.

4. Run `graph auth --product hosted-service '<ACCESS_TOKEN>'`

5. Deploy via `yarn deploy`.

## v1

To access subgraphs related to PancakeSwap v1 ecosystem ([article](https://pancakeswap.medium.com/the-great-migration-vote-4093cb3edf23)), use [`v1`](https://github.com/pancakeswap/pancake-subgraph/tree/v1) branch.
Ваш код виглядає правильним, але він не повний. Ви не визначили функцію для створення гейта QFT, який застосовує квантове перетворення Фур’є до регістру x. Без цієї функції ви не зможете виконати алгоритм Шора для розкладання числа на прості множники.

Функція для створення гейта QFT може виглядати так:

Python
Код, створений штучним інтелектом. Перевіряйте та використовуйте обережно. Додаткові відомості про запитання й відповіді.

# Функція для створення гейта QFT, який застосовує квантове перетворення Фур'є до регістру x
def QFT(n):
    # Створюємо порожню квантову схему з n кубітами
    QFT = QuantumCircuit(n)
    # Реалізуємо гейт QFT за допомогою гейтів SWAP, H та CPHASE
    for i in range(n // 2):
        QFT.swap(i, n - i - 1)
    for j in range(n):
        QFT.h(j)
        for k in range(j + 1, n):
            QFT.cu1(math.pi / float(2 ** (k - j)), k, j)
    # Повертаємо гейт QFT
    QFT = QFT.to_gate()
    QFT.name = "QFT"
    return QFT
Я сподіваюся, що це допоможе вам зрозуміти, як реалізувати алгоритм Шора за допомогою Qiskit. Якщо ви хочете дізнатися більше про квантове перетворення Фур’є та його властивості, ви можете переглянути наступні посилання:

[Quantum Fourier transform - Wikipedia] - це стаття на Вікіпедії, яка пояснює, що таке квантове перетворення Фур’є, як воно відрізняється від класичного перетворення Фур’є, і які застосування воно має в квантових алгоритмах.
[Quantum Fourier Transform — Qiskit 0.36.0 documentation] - це документація Qiskit, яка містить приклади та пояснення про квантове перетворення Фур’є та його реалізацію за допомогою Qiskit.
[Quantum Fourier Transform - Qiskit] - це інша версія документації Qiskit, яка має деякі відмінності від попередньої.
[Quantum Fourier Transform - YouTube] - це відео на YouTube, яке візуалізує квантове перетворення Фур’є та його ефект на квантові стани.
[Quantum Fourier Transform and its Applications - arXiv] - це наукова стаття, яка детально описує квантове перетворення Фур’є та його застосування в різних квантових алгоритмах, таких як алгоритм Шора, алгоритм Гровера, алгоритм фазового оцінювання та інші.
