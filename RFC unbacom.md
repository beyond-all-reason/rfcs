
- Start Date: (2022-07-22)
- Reference Issues: N/A
- Implementation PR: 

# Summary

As commanders gain XP from combat, they gain levelups which give them bonuses.

# Motivation

We want to impersonificate the player with the commander, allow the commander to stay relevant throughout the game.
Furthermore current gameplay has an exponential eco that leaves micro-oriented players out of options. With this, a player can scale up without investing in metal maker economy.

# Detailed design

The commander gains XP whenever he deals damage. This in turn gives him levelups which make the commander significantly better.
Armada commanders get their movement speed increased, as well as a large damage increase. Cortex get a slight movement decrease and a large range increase.
This is to ensure no commander can kite any other commander.
Arm also gets an EMP grenade instead of the regular dgun. This is a slow moving grenade that stuns units in an AoE.
Cortex keeps its regular dgun, but the damage to other commanders has been reduced to not insta-kill commanders.
Dguns also have a large 1200 E cost, and starts with a 10 sec cooldown.
This is to counterbalance the large health increase of commanders.


# Drawbacks

 - It's a significant change to a significant unit.
 - While the commander cannot overtake the game, it does slightly shift the focus away from macro to micro.

# Alternatives

 - Upgradable commanders, ZeroK style, but this simply offers another way to make a unit out of eco, and does not reward using micro.
 - Keeping the game as a mainly macro-oriented game.

# Unresolved questions

I suggest coupling this with the very controversial "comm death = autoresign".
This counterbalances aggressive use of the commander by making it riskier and further impersonificates the player with the commander. Although it does need a way for a player not to be left not-playing for a significant part of their playtime. (matchmaking?)
