# Future Sales Progress

## Competition Info and Overview

Competition: https://www.kaggle.com/competitions/competitive-data-science-predict-future-sales

Given sales data per store/item (50 stores, 21000+ total items, which rotate it/out)
- each month, about 5000 items are sold at all

Predicting the next month sales for each store/item combo
- all stores with min. 1 sale in test included
- all items with min. 1 sale in test included
- stores*items product is the rows to predict (even if the store-item combo historically has 0 sales)

## Own Findings

1. Exploring Missing Values

- learning from last competition, started by exploring which data
    - found that item categories share first word (often something like Games, or Accessories)
    - item names share common words (like PS5 Game, PS5 accessories, etc.)
    - shop names contain regional info in first word

- found counts of items sold in each month
    - most items (like 4k each month), had at least 1 sale the prev. month
    - a few hundred had no sales the prev. month, but had sales before
    - a few hundred are completely new

    - this seems to match with test/train --> TEST IS LIKELY JUST STORES/ITEMS WITH MIN. 1 SALES

2. Backtesting

- tried to see how predicing last month sales performs
    - 3 main categories of items: items entirely new, store-item combo was in prev. month, item is old but store-item combo not in prev. month
    - new items have high MSE (5+ avg), store-item present prev. month (1.5 avg), item old but store-item missing (0.1 avg)
    - the last category is low because it is included even though historically it is always 0 (only included because item has at least 1 sale in a different store)

    - MISTAKE: did not account for the 0.1 avg. type, led us to think that predictions were way off

- tried to improve upon 1.5 avg. type
    - sales in last month of train had bad predictions (b/c new items tended to spike, then fall off)
    - no encoding of release date (so items released in first week of month vs. last week treated the same)

## Big Picture

- First couple days was productive
    - got an understanding of the data, realized how TEST was constructed (big)

- Then, fell off
    - spent too long doing basic things like predicting last month sales and analyzing results
    - lost direction, wasted days not having a clear goal / fumbling around

- Possible improvement
    - make a long list of things to possibly do, just start brute forcing / doing it
    - need to make progress (ANY RAPID PROGRESS > sitting around not doing anything)

- Iterative improvement
    - rather than fumbling in the dark visualizing things, focus on what needs to be improved
    - create an initial model --> see what it is bad at, improve accordingly