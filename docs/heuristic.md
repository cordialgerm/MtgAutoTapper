# Part 2 - A Heuristic Approach

Last time, we discussed the concepts of **Mana** and **Tapping**, and walked through several examples of the types of decisions that an auto-tap algorithm needs to consider when making tapping decisions.

This time, we will develop a simple heuristic-based auto-tapping algorithm using a **Greedy Algorithm**.

## Getting Greedy

A Greedy Algorithm is a heuristic-based technique to solve complex problems by breaking them down into a set or series of sub-problems. Then, take each individual sub-problem and choose the best (or "greediest") solution. Finally, re-construct your solution by combining the solutions of all the sub-problems together.

Greedy Algorithms typically do not find the global optimal solution, but they have several benefits:

1. Fast and simple
1. Easy to explain
1. Good comparison point for more sophisticated techniques

We'll start with a greedy algorithm, refine it, and then compare it to other more sophisticated techniques.

In words, our greedy algorithm will be to **start by tapping the hardest to produce colored mana with the least important source that produces that mana, then repeat, end with colorless.**

To actually implement this heuristic, we will need to define some terminology and establish our objectives.

## Terminology

### Mana Sources

The problem that we are trying to solve is how to tap our mana sources to play a given card in the "best" way. First, let's define our **Mana Sources** as being any card in play that can produce mana.

Each source can then be represented with an array where each entry indicates how much mana of a given type it can produce, in WUBRGC order.

#### Basic Lands

![Plains](/docs/img/plains.jpg)
![Island](/docs/img/island.jpg)
![Swamp](/docs/img/swamp.jpg)
![Mountain](/docs/img/mountain.jpg)
![Forest](/docs/img/forest.jpg)

```python
#           W  U  B  R  G  C
plains   = [1, 0, 0, 0, 0, 0]
island   = [0, 1, 0, 0, 0, 0]
swamp    = [0, 0, 1, 0, 0, 0]
mountain = [0, 0, 0, 1, 0, 0]
forest   = [0, 0, 0, 0, 1, 0]
```

#### Colorless Lands

Colorless sources, like **Zhalfirin Void**, only produce colorless mana, so they have all zeros in the first five slots, and only have ones in the last colorless slot.

![Zhalfirin Void](/docs/img/zhalfirin_void.jpg)

```python
#                 W  U  B  R  G  C
zhalfirin_void = [0, 0, 0, 0, 0, 1]
```

#### Dual Lands

How do we then represent a **Dual Land** like **Sulfur Falls**, that can produce both U and R?

We can represent this by saying each **Mana Source** can have one or more **Modes**, and represent a source as a list of modes. If the source only has one mode, then it does not need to be represented as a 2d array.

![Sulfur Falls](/docs/img/sulfur_falls.jpg)

```python
sulfur_falls = [
    #W  U  B  R  G  C
    [0, 1, 0, 0, 0, 0],
    [0, 0, 0, 1, 0, 0]
]
```

### Maximum Mana

Next, let us define our **Max Mana** as the maximum amount of mana of a given color that we can produce with a given set of mana sources.

For example, if I have **Mountain**, **Island**, **Sulfur Falls**, **Zhalfirin Void**, then I have a maximum of 2R, 2U, 1C.

![Mountain](/docs/img/mountain.jpg)
![Island](/docs/img/island.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)
![Sulfur Falls](/docs/img/zhalfirin_void.jpg)

```python
#           W  U  B  R  G  C
max_mana = [0, 2, 0, 2, 0, 1]

```

### Source Priority

As we saw last time, not all mana sources are created equal. Some sources have powerful activated abilities that should be preserved (if possible), and other sources have negative costs associated with them that should be avoided, if possible.

![Azcanta](/docs/img/azcanta.jpg)
![Ipnu Rivulet](/docs/img/ipnu_rivulet.jpg)
![Ramanup Ruins](/docs/img/ramanup_ruins.jpg)

A simple way to implement this logic is to assign a **Priority** to each mana source based on the type of source. Then, when tapping, we can attempt to tap the lowest priority source at each step.

This technique has several downsides (especially when there are multiple lands of the same priority that offer competing trade-offs), but serves as an OK starting point.

We will start by categorizing our lands into one of the following prioritization buckets:

1. **Priority 0** - Basic sources _(tap first)_
1. **Priority 1** - Dual sources
1. **Priority 2** - Pain sources
1. **Priority 3** - Activated Ability sources _(tap last)_

```python
plains_priority = 0
sulfur_falls_priority = 1
ipnu_rivulet_priority = 2
azcanta_priority = 3
```

## Testing the Heuristic

Recall, our greedy algorithm is to **start by tapping the hardest to produce colored mana with the least important source that produces that mana, then repeat, end with colorless.**

Now we can define our **hardest to produce mana** as the mana source with the lowest **Max Mana**, and the **least important source** is the source with the lowest priority.

Let's test this heuristic on our simple example. You have in hand **Opt**, **Magma Spray**, and **Lightning Strike**:

![Opt](/docs/img/opt.jpg)
![Magma Spray](/docs/img/magma_spray.jpg)
![Lightning Strike](/docs/img/lightning_strike.jpg)

You have a **Mountain**, an **Island**, and a **Sulfur Falls** in play:

![Mountain](/docs/img/mountain.jpg)
![Island](/docs/img/island.jpg)
![Sulfur Falls](/docs/img/sulfur_falls.jpg)

You wish to cast your **Lightning Strike** to attack your opponent. Which lands should you tap?

![Lightning Strike](/docs/img/lightning_strike.jpg)

In this case, we have the following:

```python

sources = [
    #mountain
    #W  U  B  R  G  C
    [0, 0, 0, 1, 0, 0],

    #island
    #W  U  B  R  G  C
    [0, 1, 0, 0, 0, 0],

    #sulfur falls
    [
        #W  U  B  R  G  C
        [0, 1, 0, 0, 0, 0],
        [0, 0, 0, 1, 0, 0]
    ]
]

priorities = [
    0,  #mountain is basic
    0,  #island is basic
    1   #sulfur falls is dual
]

#           W  U  B  R  G  C
max_mana = [0, 2, 0, 2, 0, 0]
```

To cast the **Lightning Strike** we need **1R**.

In this case **R** is our only (and there hardest) colored mana that needs to be produced, so we start by tapping it. The lowest priority source that provides **R** is our **Mountain**, so we tap it.

There is no more colored mana required, so we end with colorless mana, which can be filled by any mana source. The remaining lowest priority source is the **Island**, so we tap it.

We did it - the heuristic generated the optimal solution for this simple example!

## What's Next?

Next time, we will discuss implementing the heuristic, look at some more examples where it does not do so well, and then look at how we can improve it.