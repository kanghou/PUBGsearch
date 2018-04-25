# PUBGSearch
![Python 3.5](https://img.shields.io/badge/python-3.5-blue.svg)

PUBGSearch is a Python wrapper for pubg developer api for searching stats

Because of the "app rate limit", only the information from the last five games is retrieved

[PUBG Developer Portal](https://documentation.playbattlegrounds.com/)
## Installation

```python
pip install pubgSearch
```

## Usage

You must have [PUBG API KEY](https://documentation.playbattlegrounds.com/)


### import packages
##### 

```python
from pubgSearch import pubg_auth
from pubgSearch import pubg_data
```


### Set api_key
```python
api_key = "your_api_key_here"
```


### Make auth_info
```python
authinfo = pubg_auth.PubgAuth(api_key ,region="your_region_here")
```
##### [regions](https://documentation.playbattlegrounds.com/en/making-requests.html#regions)
##### default value of region is "pc-kakao"


### Make player object
```python
Player = pubg_data.PubgPlayer('pubg_nickname', authinfo)
```


### Get player's latest five matches
```python
matches = Player.get_latest_matches()
```
matches will have match-IDs 


### Make match object
```python
match = pubg_data.PubgMatch(matches, 'pubg_nickname', authinfo)
```


### Get match's data
```python
data_set, info_set = match.get_data()
```
get_data() method will return two lists that includes namedturple.

the latest match data is in data_set[0],<br>
the latest match info data is in info_set[0]


### Check the data
```python
print(data_set[0])
```
result:
```python
match_data(deathType='byplayer', heals=7, winPointsDelta=0, teamKills=0, mostDamage=0, killPlace=3 ...)
```
and you can
```python
print(data_set[0].heals)
```
result:
```python
7
```

you can use [property](https://documentation.playbattlegrounds.com/en/matches.html)
