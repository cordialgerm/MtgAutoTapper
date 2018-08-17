# Introduction

This first article will introduce the concepts of **Mana** and discuss various trade-offs to consider when tapping for mana.

## Introduction to Mana

**Mana** is a core concept of MTG and is a resource that is used to pay for cards and abilities.

[From Gamepedia](https://mtg.gamepedia.com/Mana):

```quote
Mana is a form of magic used to pay the mana cost required to cast most of the cards in the game. It is also used to cover other costs, such as those to activate certain abilities. The most basic mana source is land, though certain spells and abilities can also produce mana.[1][4] A player taps land to add mana to his or her mana pool; one's mana supply regenerates naturally when lands untap during the beginning phase of his or her turn. A player that exhausts his or her supply of mana is considered "tapped out."

The mana system allows the design of cards that differ greatly in power level. Stronger cards with higher mana cost have the inherent drawback of being unusable early, and risk leaving the user tapped out when played. Also, by requiring specific types of mana, R&D can associate mechanics with specific colors. Mana cost is one of the chief tools R&D uses to balance the game.

As they play lands, players gain access to more mana over the course of the game, allowing the use of cards in greater power and numbers. This gives each Magic duel a natural sense of pacing and drama, by ensuring games start slow but eventually build up to an epic conclusion.
```

## Colors of Mana

**Mana** is produced in different **Colors**, representing magical energy drawn from different sources, including lands and artifacts. There are five colors of mana:

- <span class="w-m">**White**</span> mana is drawn from **Plains** and is the color of Law, Order, and Peace
- <span class="u-m">**Blue**</span> mana is drawn from **Islands** and is the color of Knowledge, Wisdom, and Self-Improvement
- <span class="b-m">**Black**</span> mana is drawn from **Swamps** and is the color of Power, Death, and Selfishness
- <span class="r-m">**Red**</span> mana is drawn from **Mountains** and is the color of Passion, Anger, and Aggression
- <span class="g-m">**Green**</span> mana is drawn from **Forests** and is the color of Nature, Harmony, and Destiny
- <span class="c-m">**Colorless**</span> mana is mana derived from unique lands or can be filled by any of the colored mana above

|Symbol|Color|Abbreviation|Basic Land Card|
|---   |---  |---         |---            |
|<span class="w-m">|White    |W| Plains   |
|<span class="u-m">|Blue     |U| Island   |
|<span class="b-m">|Black    |B| Swamp    |
|<span class="r-m">|Red      |R| Mountain |
|<span class="g-m">|Green    |G| Forest   |
|<span class="c-m">|Colorless|C| _Varies_ |

![Basic Lands](/docs/img/basic_lands.png)

## Producing Mana

**Mana** is produced by **Tapping** the associated mana source. In game, the card is turned sideways to indicate it is tapped. A source can generally only be tapped once per turn, so there is a finite amount of mana available from your mana sources in a given turn.

![Tapped Land](/docs/img/tapped_land.png)

## Mana Costs

These mana sources are used to pay for the cost of playing new cards in the game from the player's hand and to cover other costs, such as activating abilities of certain cards. The mana cost of playing a card is shown in the upper right-hand corner of that card.

For example, playing the **Lightning Strike** card costs **1R**, indicating 1 Red Mana and 1 Colorless mana is required.

![Lightning Strike](/docs/img/lightning_strike.png)

## Multi-Color Sources

Dual Lands allow the user to generate multiple different colors of mana from the same land. Due to the many different possible color combinations, there are many different types of **Dual Lands** , each with their advantages and disadvantages.

![Dual Lands](/docs/img/dual_lands.png)
![Dual Lands](/docs/img/dual_lands2.png)

## Optimal Tapping Strategy?

Where this starts to get interesting from an algorithmic perspective is thinking about an optimal tapping strategy. Given a variety of mana sources, a variety of cards in hand, and a desired card to cast, what is the optimal tapping strategy?

## Basic Example - Dual Land

Let us start with a simple example. You have in hand **Opt**, **Magma Spray**, and **Lightning Strike**:

![Opt](/docs/img/opt.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Lightning Strike](/docs/img/lightning_strike.png)

You have a **Mountain**, an **Island**, and a **Sulfur Falls** in play:

![Mountain](/docs/img/mountain.jpg)
![Island](/docs/img/island.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)

You wish to cast your **Lightning Strike** to attack your opponent. Which lands should you tap?

![Lightning Strike](/docs/img/lightning_strike.png)

Most players would immediately say that you should tap the **Mountain** and **Island**, leaving the **Sulfur Falls** available. This is because leaving the **Sulfur Falls** untapped allows the player to then follow up with either the **Magma Spray** or the **Opt**. This strategy maximizes the potential future actions of the player. In essence, the **Sulfur Falls** has a higher opportunity cost to tap, so we would prefer to leave it untapped.

## Intermediate Example - Land With Good Activated Ability

You have in hand **Strategic Plannnig**, **Magma Spray**, and **Wizard's Lightning**:

![Strategic Planning](/docs/img/strategic_planning.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Wizard's Lightning](/docs/img/lightning_strike.jpg)

You have a 4 **Mountain**, 1 **Sulfur Falls**, and 1 **Azcanta, the Sunken Ruin** in play:

![Mountain](/docs/img/mountain.jpg)
![Mountain](/docs/img/mountain.jpg)
![Mountain](/docs/img/mountain.jpg)
![Mountain](/docs/img/mountain.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)
![Azcanta, the Sunken Ruin](/docs/img/sulfur_falls.jpg)

You wish to cast your **Strategic Planning** to search for a powerful card. Which lands should you tap?

![Strategic Planning](/docs/img/strategic_planning.jpg)

If we followed our previous logic of avoiding tapping the **Sulfur Falls**, we would tap the **Mountain** and the **Azcanta, the Sunken Ruin** (as the only other blue source). However, tapping the **Azcanta, the Sunken Ruin** for blue mana would preclude us from utilizing its second, very powerful ability, so it would be better to tap the **Sulfur Falls** for blue mana. Sure, we lose out on some of the flexibility that the **Sulfur Falls** provides, but we already have a lot of outstanding red mana represented by the **Mountains**. In this case, the opportunity cost of tapping the **Azcanta, the Sunken Ruin** is much higher than the opportunity cost of tapping the **Sulfur Falls**, so we would prefer to tap the **Sulfur Falls**.

## Intermediat Example - Land with OK Activated Ability

You have in hand **Opt**, **Magma Spray**, and **Lightning Strike**:

![Opt](/docs/img/opt.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Lightning Strike](/docs/img/lightning_strike.png)

You have a 1 **Mountain**, 1 **Sulfur Falls**, and 1 **Memorial to Genius** in play:

![Mountain](/docs/img/mountain.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)
![Memorial to Genius](/docs/img/memorial_to_genius.jpg)

You wish to cast your **Lightning Strike** to attack your opponent. Which lands should you tap?

![Lightning Strike](/docs/img/lightning_strike.png)

If we follow the lessons from the last example, we would prioritize keeping the **Memorial to Genius** open because it has an activated ability that we want to preserve. There are two problems with this strategy:

1. We wouldn't be able to activate the ability anyway, so the ability is essentially irrelevant
1. The ability isn't particularily 'good'

So, we should tap the **Mountain** and the **Memorial to Genius** because it leaves us with the most avaiable options to play afterwards.

## Heuristic Based Approaches

A simple implementation of a tapping strategy would use a prioritization scheme, where each type of land is assigned a static priority based on certain attributes. One simple implementation would be (from lowest to highest priority):

- Basic Lands (tap first)
- Dual Lands
- Lands with Activated Abilities (tap last)

However, from the examples above, we can see that  example, we can see that a static heuristic-based approach of prioritizing certain types of lands over others will not yield good results due to the highly dynamic nature of the game and the many complex trade-offs that exist.

Join me next time for a discussion of how we can develop an algorithm that considers these complex trade-offs!