- Start Date: 2022-07-29
- Reference Issues: None
- Implementation PR: 

# Summary

Factories to gain experience as units they created gain experience. This experience is then gifted to new units created by the factory. The result will be an established and long-lasting factory which has been doing damage will produce stronger units.

# Motivation

This is to encourage:
- Helping to dent the initial advantage of a T2 rush, the T1 player's T1 units won't be as weak as they would have been (though it is worth noting it can also provide an advantage to getting T2 first)
- Forward factories now become targets of value, adding an additional value to taking ground in larger team games
- Helps move value away from pure eco and help dampen the advantage conferred by exponential eco
- Promotes conflict and aggression, even if you don't take ground you will start producing better units

# Detailed design

- Factories start (as now) with 0 XP
- On death, a unit sends the XP value back to the factory where it is multiplied by a coefficient (e.g. 0.01) and added to the Factory XP
- Units produced from the factory have their initial XP set based on the Factory XP
- Units track the amount of XP gained since creation to prevent a feedback loop and exploits
- Resurrected units do not recall their factory, thus if XP is ever preserved on resurrected units it would not break this though a resurrected factory would retain it's XP inline with that change were it made

# Drawbacks

- Possible slowdowns on mass death (e.g. nukes)
- It would not be immediately obvious this happens and while not a hidden mechanic it would need a guide page added to the site and be added to tutorials
- It may mean in a team game when a good player is matched against a poorer player they may gain a snowball advantage or be able to exploit the situation to better increase their factory experience
- It will discourage factory switching and in smaller games may well reduce unit diversity

# Alternatives

- There is no inherent disadvantage in not implementing this, the game works as is
- All other suggestions to curb exponential economic growth hit the economy with a nerf, this would give a buff to the unit production system and may well be better received and less controversial

