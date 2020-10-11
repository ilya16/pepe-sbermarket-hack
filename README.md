# Sbermarket product prediction hackathon

> Solution produced during "Sbermarket hackathon" as part of the "Hack Lab" course in Skotech, October 9-11, 2020
>
> Team PEPEtoners: [Ilya Borovik](https://github.com/ilya16), [Vladislav Kniazev](https://github.com/Vladoskn), [Vanessa Skliarova](https://github.com/Vanessik), [Bulat Khabibullin](https://github.com/MrWag2), and [Zakhar Pichugin](https://github.com/zakharpichugin)

[Kaggle link](https://www.kaggle.com/c/test-recsys/overview)

## Problem statement

***Task:*** Predict which products customers will buy next time.

***Metric:*** `MAP@K` with `K=50`.

## Solution

***Hypethesis:*** People tend to buy the same products and have preferences. 

***Idea***: Use information about most frequently bought products to make future predictions.

Final [solution](main_solution.ipynb) is a two-step prediction model:

1. Top user products sorted by
  * total number of product purchases
  * date of the last order
  * average position in all orders
2. Collaborative Filtering based on `implicit.nearest_neighbours.CosineRecommender` to recommend and fill remaining predictions in a list of K=50 ranked predictions. The model is trained on normalized `(user, product)` interactions for all users in the provided data.

Additionally, we crafted user and product features to build a two-level recommendation system: candidate recommendation + ranking. This repository provides only the feature crafting code and data insights.

## Files

Each file is a result of work of one team member:

* [main_solution.ipynb](main_solution.ipynb) – the final working solution with feature engineering, model training and predicitions.
* [feature_engineering.ipynb](feature_engineering.ipynb) – feature engineering for a potential two-level recommendation system.
* [data_exploration_1.ipynb](data_exploration_1.ipynb) – some data exploration and data insights (part 1)
* [data_exploration_2.ipynb](data_exploration_2.ipynb) – some data exploration and data insights (part 2)
* [basket_novelty.ipynb](basket_novelty.ipynb) – insight about the novelty of the basket novelty compared to previous orders for each user.
