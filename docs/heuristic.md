# Part 2 - A Heuristic Approach

In particular, algorithms based on a simple prioritization scheme, where each type of land is assigned a static priority based on certain attributes, are going to struggle quite a bit when it comes to evaluating these dynamic trade-offs.

A simple implementation of a tapping strategy would use a prioritization scheme, where each type of land is assigned a static priority based on certain attributes. One simple implementation would be (from lowest to highest priority):

- Colorless Lands with no possible activation (tap first)
- Basic Lands
- Dual Lands
- Pain Lands
- Lands with Activated Abilities (tap last)

However, from the examples above, we can see that a static heuristic-based approach of prioritizing certain types of lands over others will not always yield good results due to the highly dynamic nature of the game and the many complex trade-offs that exist.

Join me next time for a discussion of how we can develop an algorithm that considers these complex trade-offs!