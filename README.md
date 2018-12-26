

```
import pandas as pd
from sklearn import linear_model
import matplotlib.pyplot as plt
import seaborn as sns

data = pd.read_csv('PUBG_train_V2.csv')
```


## clean the data

drop the rows with 'NA'
 
```
data = data.dropna(axis=0)
```

### understand the data

print the columns available in dataset

```
print(data.columns)
```

Index(['Id', 'groupId', 'matchId', 'assists', 'boosts', 'damageDealt', 'DBNOs',
       'headshotKills', 'heals', 'killPlace', 'killPoints', 'kills',
       'killStreaks', 'longestKill', 'matchDuration', 'matchType', 'maxPlace',
       'numGroups', 'rankPoints', 'revives', 'rideDistance', 'roadKills',
       'swimDistance', 'teamKills', 'vehicleDestroys', 'walkDistance',
       'weaponsAcquired', 'winPoints', 'winPlacePerc'],
      dtype='object')


print the top rows from the dataset

```
print(data.head())
```

get more insights of the data
```
print(data.describe())

```

### understand data

explore correlation among the features provided

filter data, 'Id', 'groupId', 'matchId', 'matchType' are unique entries and should be neglected 
```
cols_to_drop = ['Id', 'groupId', 'matchId', 'matchType']
cols_to_fit = [col for col in data.columns if col not in cols_to_drop]
```
find correlation
```
corr = data[cols_to_fit].corr()
```

plot a heatmap to visualize the corrrelation data
```
sns.heatmap(
    corr,
    xticklabels=corr.columns.values,
    yticklabels=corr.columns.values,
    linecolor='white',
    linewidths=0.1,
    cmap="YlRd"
)
plt.show()
```
