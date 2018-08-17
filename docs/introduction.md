# Part 1 - Introduction to Mana and Tapping

This first article will introduce the concepts of **Mana** and discuss various trade-offs to consider when tapping for mana. Any auto-tapping algorithm must consider these trade-offs.

## Introduction to Mana

**Mana** is a core concept of MTG and is a resource that is used to pay for cards and abilities.

[From Gamepedia](https://mtg.gamepedia.com/Mana):
> Mana is a form of magic used to pay the mana cost required to cast most of the cards in the game.
> It is also used to cover other costs, such as those to activate certain abilities.
> The most basic mana source is land, though certain spells and abilities can also produce mana.
> A player taps land to add mana to his or her mana pool;
> one's mana supply regenerates naturally when lands untap during the beginning phase of his or her turn.
> A player that exhausts his or her supply of mana is considered "tapped out."

## Colors of Mana

**Mana** is produced in different **Colors**, representing magical energy drawn from different sources, including lands and artifacts. There are five colors of mana:

- <span class="w-m">![W](/docs/img/white.png) **White**</span> mana is drawn from **Plains** and is the color of Law, Order, and Peace
- <span class="u-m">![U](/docs/img/blue.png) **Blue**</span> mana is drawn from **Islands** and is the color of Knowledge, Wisdom, and Self-Improvement
- <span class="b-m">![B](/docs/img/black.png) **Black**</span> mana is drawn from **Swamps** and is the color of Power, Death, and Selfishness
- <span class="r-m">![R](/docs/img/red.png) **Red**</span> mana is drawn from **Mountains** and is the color of Passion, Anger, and Aggression
- <span class="g-m">![G](/docs/img/green.png) **Green**</span> mana is drawn from **Forests** and is the color of Nature, Harmony, and Destiny
- <span class="c-m">![C](/docs/img/colorless.png) **Colorless**</span> mana is mana derived from unique lands or can be filled by any of the colored mana above

|Symbol|Color|Abbreviation|Basic Land Card|
|---   |---  |---         |---            |
|<span class="w-m"></span>![W](/docs/img/white.png)|White    |W| Plains   |
|<span class="u-m"></span>![U](/docs/img/blue.png)|Blue     |U| Island   |
|<span class="b-m"></span>![B](/docs/img/black.png)|Black    |B| Swamp    |
|<span class="r-m"></span>![R](/docs/img/red.png)|Red      |R| Mountain |
|<span class="g-m"></span>![G](/docs/img/green.png)|Green    |G| Forest   |
|<span class="c-m"></span>![C](/docs/img/colorless.png)|Colorless|C| _Varies_ |

![Basic Lands](/docs/img/basic_lands.png)

## Producing Mana

**Mana** is produced by ![T](/docs/img/tap_symbol.png)**Tapping** the associated mana source. In game, the card is turned sideways to indicate it is tapped. A source can generally only be tapped once per turn, so there is a finite amount of mana available from your mana sources in a given turn.

![Tapped Land](/docs/img/tapped_land.png)

## Mana Costs

These mana sources are used to pay for the cost of playing new cards in the game from the player's hand and to cover other costs, such as activating abilities of certain cards. The mana cost of playing a card is shown in the upper right-hand corner of that card.

For example, playing the **Lightning Strike** card costs **1R**, indicating 1 Red Mana and 1 Colorless mana is required.

![Lightning Strike](/docs/img/lightning_strike.jpg)

## Multi-Color Lands

Dual Lands allow the user to generate multiple different colors of mana from the same land. Each of these dual lands can be tapped for either one of the specified mana colors, but not both. Due to the many different possible color combinations, there are many different types of **Dual Lands** , each with their advantages and disadvantages.

![Dual Lands](/docs/img/dual_lands.png)
![Dual Lands](/docs/img/dual_lands2.png)

## Colorless Lands

Some lands are **Colorless**, meaning that they do not produce any colored mana. While this is generally a downside, such lands often have other benefits to compensate.

![Zhalfirin Void](/docs/img/zhalfirin_void.jpg)

## Lands With Activated Abilities

Some lands have **Activated Abilities**, which means the land can be ![T](/docs/img/tap_symbol.png) **tapped** either to produce mana, or to activate that ability. Oftentimes, these abilities are powerful, so you should avoid tapping these lands to produce mana in many situations.

![Azcanta, Sunken Ruin](/docs/img/azcanta.jpg)
![Spire of Orazca](/docs/img/spire_of_orazca.jpg)

## 'Painful' Lands

Some lands produce colorless mana, but can also produce colored mana if the player is willing to pay a cost. In this case, the land should oftentimes only be used to produce colored mana if there is no other choice, and should instead be used to produce colorless mana if possible.

![Ipnu Rivulet](/docs/img/ipnu_rivulet.jpg)
![Ramanup Ruins](/docs/img/ramanup_ruins.jpg)

## Examples

Now that we've surveyed some of the different mana sources, let's go through some examples of how they interact.

### Example - Dual Land

Let us start with a simple example. You have in hand **Opt**, **Magma Spray**, and **Lightning Strike**:

![Opt](/docs/img/opt.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Lightning Strike](/docs/img/lightning_strike.jpg)

You have a **Mountain**, an **Island**, and a **Sulfur Falls** in play:

![Mountain](/docs/img/mountain.jpg)
![Island](/docs/img/island.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)

You wish to cast your **Lightning Strike** to attack your opponent. Which lands should you tap?

![Lightning Strike](/docs/img/lightning_strike.jpg)

Most players would immediately say that you should ![T](/docs/img/tap_symbol.png) **tap** the **Mountain** and **Island**, leaving the **Sulfur Falls** available. This is because leaving the **Sulfur Falls** untapped allows the player to then follow up with either the **Magma Spray** or the **Opt**. This strategy maximizes the potential future actions of the player. In essence, the **Sulfur Falls** has a higher opportunity cost to tap, so we would prefer to leave it untapped.

### Example - Colorless Lands

You again have in hand **Opt**, **Magma Spray**, and **Lightning Strike**:

![Opt](/docs/img/opt.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Lightning Strike](/docs/img/lightning_strike.jpg)

You have a **Mountain**, an **Island**, and a **Zhalfirin Void** in play:

![Mountain](/docs/img/mountain.jpg)
![Island](/docs/img/island.jpg)
![Zhalfirin Void](/docs/img/zhalfirin_void.jpg)

You wish to cast your **Lightning Strike** to attack your opponent. Which lands should you tap?

![Lightning Strike](/docs/img/lightning_strike.jpg)

You must ![T](/docs/img/tap_symbol.png) **tap** the **Mountain**, which leaves the decision between **Zhalfirin Void** and **Island**. In this case, you should clearly tap the **Zhalfirin Void** because it has the lowest opportunity cost (tapping the **Island** would preclude you from casting **Opt**).

### Example - Pain Lands

You again have in hand **Opt**, **Magma Spray**, and **Lightning Strike**:

![Opt](/docs/img/opt.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Lightning Strike](/docs/img/lightning_strike.jpg)

You have a **Ramanup Ruins**, an **Ipnu Rivulet**, and a **Sulfur Falls** in play:

![Ramanup Ruins](/docs/img/ramanup_ruins.jpg)
![Ipnu Rivulet](/docs/img/ipnu_rivulet.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)

You wish to cast your **Lightning Strike** to attack your opponent. Which lands should you tap?

This situation is not as clear-cut. You have three choices:

1. ![T](/docs/img/tap_symbol.png) **Sulfur Falls** and **Ipnu Rivulet**
1. ![T](/docs/img/tap_symbol.png) **Sulfur Falls** and **Ramanup Ruins**
1. ![T](/docs/img/tap_symbol.png) **Ipnu Rivulet** and **Ramanup Ruins**

The first two options will not cause you to lose life, but will leave you with the least options (either **Opt** or **Magma Spray**).
The third option will cause you to lose 2 life, but will leave you with the most options (both **Opt** and **Magma Spray**).

In this case, the auto-tapping algorithm must be able to identify how important life is to the player at this point in time so that it can choose between (3) or either (2) or (1). To choose between (2) or (1), the algorithm must have some idea of whether or not **Opt** or **Magma Spray** is more likely to be useful! Already, we can see that this is not a simple problem.

### Example - Land with Activated Ability

You have in hand **Strategic Plannnig**, **Magma Spray**, and **Wizard's Lightning**:

![Strategic Planning](/docs/img/strategic_planning.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Wizard's Lightning](/docs/img/wizards_lightning.jpg)

You have a 3 **Zhalfirin Void**, 2 **Sulfur Falls**, and 1 **Azcanta, the Sunken Ruin** in play:

![Zhalfirin Void](/docs/img/zhalfirin_void.jpg)
![Zhalfirin Void](/docs/img/zhalfirin_void.jpg)
![Zhalfirin Void](/docs/img/zhalfirin_void.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)
![Azcanta, the Sunken Ruin](/docs/img/azcanta.jpg)

You wish to cast your **Strategic Planning** to search for a powerful card. Which lands should you tap?

![Strategic Planning](/docs/img/strategic_planning.jpg)

If we followed our previous logic of avoiding tapping the **Sulfur Falls**, we would tap the **Zhalfirin Void** and the **Azcanta, the Sunken Ruin** (as the only other blue source). However, tapping the **Azcanta, the Sunken Ruin** for blue mana would preclude us from utilizing its second, very powerful ability, so it would be better to tap the **Sulfur Falls** for blue mana. In this case, the opportunity cost of tapping the **Azcanta, the Sunken Ruin** is much higher than the opportunity cost of tapping the **Sulfur Falls**, so we would prefer to tap the **Sulfur Falls**.

### Example - Land with Activated Ability Continued

You have in hand **Opt**, **Magma Spray**, and **Lightning Strike**:

![Opt](/docs/img/opt.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Lightning Strike](/docs/img/lightning_strike.jpg)

You have a 2 **Mountain**, 1 **Island**, 1 **Spires of Orazca**, in play:

![Mountain](/docs/img/mountain.jpg)
![Mountain](/docs/img/mountain.jpg)
![Island](/docs/img/island.jpg)
![Spires of Orazca](/docs/img/spire_of_orazca.jpg)

You wish to cast your **Lightning Strike** to attack your opponent. Which lands should you tap?

![Lightning Strike](/docs/img/lightning_strike.jpg)

You have three choices:

1. ![T](/docs/img/tap_symbol.png) **Mountain** and **Mountain**
1. ![T](/docs/img/tap_symbol.png) **Mountain** and **Island**
1. ![T](/docs/img/tap_symbol.png) **Mountain** and **Spires of Orazca**

Option 1 precludes you from **Magma Spray**, but allows you to activate **Spires of Orazca** if your opponent attacks.
Option 2 precludes you from **Opt**, but allows you to activate **Spires of Orazca** if your opponent attacks
Option 3 precludes you from **Spires of Orazca**, but allows you to cast both **Opt** and **Magma Spray**.

Choosing which of these options is highly dependent on the current game state. Which is more likely to be useful, **Opt**, **Magma Spray**, or **Spires of Orazca**?

The answer to this question, of course, depends on the game state. If your oponent has many creatures, then **Spires of Orazca** is generally a better option to leave open. If they have no creatures that are likely to attack you, then leaving the **Sulfur Falls** is probably better.

## Can we make a good Auto-Tapping Algorithm?

Based on the above examples, it should be clear that there is a wide variance in how complex a tapping situation can be. Some situations have only one tapping solutions, and some have a limited number of solutions where one solution clearly dominates the other. However, there can also be many dynamic interactions and complex tradeoffs that can occur when trying to determine a tapping strategy, particularly when there are a large number of multi-colored or specialized lands in play and the player has a variety of cards with differing costs and colors in hand.

Players are extremely good at evaluating these tradeoffs instantly (and often subconsciously). Algorithms, on the other hand, have a much harder time with these sort of trade-offs.

Join me next time for a discussion of how we can implement an auto-tapping algorithm and the different techniques we can employ.