# AS

stake_list - list of validators stakes

```
average = mean(stake_list)
```

```
min_stake = min(stake_list)
max_stake = max(stake_list)
```

# Designation:

user_stake - size of user stake

user_reward - size of user reward in this round 

# Stake increase

```
MAX_REWARD_INCREASE = 0.5
```

(50%)

```
If user_stake<average:
  p = (average - user_stake)/(average - min_stake)
  user_increase = user_reward * MAX_REWARD_INCREASE * p
```

Part of user maning reward (user_increase) will go to stake. Other part will go to user as liquid reward

# Stake unblocking

```
MAX_REWARD_UNBLOCKING = 0.5
```

(50%)

```
If user_stake>average:
  p = (averuser_stakeage - average)/(max_stake - average)
  user_unblocking = user_reward * MAX_REWARD_UNBLOCKING * p
```

Part of user stake (user_unblocking) go to user liquid active