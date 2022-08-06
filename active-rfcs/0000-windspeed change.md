- Start Date: 2022-08-06
- Reference Issues: 
- Implementation PR: 

# Summary

The average wind speed in BAR is not really an arithmetic average of min and max wind speed of a map. Which is confusing the newbies and actually impact energy balance a lot. Also wrong formulas used in other places in the game e.g. buildmenu disables windgens on maps with 0-10 wind, while actually it is still better then solars there.

# Motivation

I want for wind more transparent mechanics, which are obvious for everyone. Also allow map designs with really risky winds like (1-25) and more stable winds (5-10).
Current mechanics are tesnd to stick to the maximum at the most part of gametime and confuse people with it's average speeds.
Also this will make windfarms riskier so more downtime will appear for them. That will force players make more energy storages and gives more diversity in the overall T1 eco. People have to decide for themself how much windgens should be in their T1 ec and also punish people with greedy 100% wind ecoing by the increasing probability of stalling.

# Detailed design
 
Not sure what should be there.
Probably we should consider making wind not completely random, but a bit more stable, tend to the average values.
Probably the wind should not change steep, can not jump from 1 to 16 in one step.

But overall idea is having real average wind is near (min+max)/2

# Drawbacks

This will make winds really much worse on most maps, since current maps are usually having wind like 1-X and making real average will turn wind down is about 25%.

# Alternatives

Instead of changing the mechanics, there could be just printed the average wind for each map and also added note about it to the loading screen hint about windgens.
Also enable windgen construction on every map.

# Unresolved questions

What formula is better for windspeed calculation: complete random, some linear changing, soften wind changes, more stability etc.
