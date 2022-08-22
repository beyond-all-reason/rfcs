- Start Date: 2022-08-06
- Reference Issues: 
- Implementation PR: 

# Summary

I'm requesting the windspeed formula change, so it become more clear what average wind is since this value used for ingame decisions. For mechanics to become more transparent I suggest to make the average windspeed formula actually as simple as possible, so as (min+max)/2 as average windspeed.
The average wind speed in BAR is not really an arithmetic average of min and max wind speed of a map. Which is confusing the newbies and actually impact energy balance a lot. Also wrong formulas used in other places in the game e.g. buildmenu disables windgens on maps with 0-10 wind, while actually it is still better then solars there.

# Motivation

I want for wind more transparent mechanics, which are obvious for everyone. Also allow map designs with really risky winds like (1-25) and more stable winds (5-10).
Current mechanics are tend to stick to the maximum at the most part of gametime and confuse people with it's average speeds.
Also this will make windfarms riskier so more downtime will appear for them. That will force players make more energy storages and gives more diversity in the overall T1 eco. People have to decide for themself how much windgens should be in their T1 ec and also punish people with greedy 100% wind ecoing by the increasing probability of stalling.

# Detailed design
 
Overall idea is having real average wind near (min+max)/2.
The way it could be done is discussing. There are few possible ways such as:
1. Implement double dice check when picking the current wind speed, which result in more stable wind - though in my opinion that is wrong way since the main feature of wind power is it's randomness and instability, once we make it more stable it become more like solar which is constant and 100% predictable.
2. Add some tricky mechanics for wind not select total random value each time, but instead pick some value near the current wind for next step. As example speed should not be able to jump from 1 to 25 and then back to 1 in few steps,ut it can instead change it's power by some smaller value at once.

# Drawbacks

This will make winds really much worse on most maps, since current maps are usually having wind like 1-X and making real average will turn wind down is about 25%.

# Alternatives

Instead of changing the mechanics, there could be just printed the average wind for each map and also added note about it to the loading screen hint about windgens.
Also enable windgen construction on every map.

# Unresolved questions

What formula is better for windspeed calculation: complete random, some linear changing, soften wind changes, more stability etc.
