# TA

Metaparameters:
- TA_COUNT
- GLOBAL_TOP_LIMIT
- GLOBAL_BOTTOM_LIMIT
- LOCAL_TOP_RATIO_LIMIT
- LOCAL_BOTTOM_RATIO_LIMIT
- SECURITY_RESERVE_RATIO

## Calculation

Each blocksigner calculate TA_COUNT of previus deltas. Each delta:

```
delta = timeslot_start - time_of_block_validation
```

Each blocksigner calculate median of delta list

```
m_delat = MEDIAN(deltas)
```

Each blocksigner will publish m_delta to block header

## Timeslot validaotor calculation

Each validator get list of m_delta from block header. List size - TA_COUNT. Each validator calculate raw_new_delta[i]:

```
raw_new_delta[i] = MEDIAN(m_deltas)
```

```
new_delta = LOCAL_TOP_RATIO_LIMIT*new_delta[i-1] if raw_new_delta[i]>LOCAL_TOP_RATIO_LIMIT*new_delta[i-1]
new_delta = LOCAL_BOTTOM_RATIO_LIMIT*new_delta[i-1] if raw_new_delta[i]<LOCAL_BOTTOM_RATIO_LIMIT*new_delta[i-1] 
new_delta = raw_new_delta[i] otherwise 
```

```
real_delta = GLOBAL_TOP_LIMIT if new_delta*SECURITY_RESERVE_RATIO>GLOBAL_TOP_LIMIT
real_delta = GLOBAL_BOTTOM_LIMIT if new_delta*SECURITY_RESERVE_RATIO<GLOBAL_BOTTOM_LIMIT 
real_delta = new_delta*SECURITY_RESERVE_RATIO otherwise
```
