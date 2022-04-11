import requests
import json

client_id = '...'
client_secret = '...'

key = requests.post("https://api.artsy.net/api/tokens/xapp_token",
                  data={
                      "client_id": 'd39394fb10cb4bcb2551',
                      "client_secret": 'a7e100c2ded69159e0be2a2d36184ca4'
                  })

j = json.loads(key.text)
token = j["token"]
headers = {"X-Xapp-Token" : token}

url = 'https://api.artsy.net/api/artists/'
artists_data = {}
with open('dataset_24476_4 (1).txt', 'r') as f:
    for line in f:
        res = requests.get(url + line.strip(), headers = headers)
        res.encoding = 'utf-8'
        res = res.json()
        artists_data[res['sortable_name']] = res['birthday']

print(artists_data)
sorted_artists_data = [name for name in sorted(artists_data.items(), key = lambda x: (x[1], x[0]))]
for artist in sorted_artists_data:
    print(artist[0])
