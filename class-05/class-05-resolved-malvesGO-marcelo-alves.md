# MongoDB - Aula 04 - Exercício
autor: Marcelo Alves

## 1. Importar as collections `restaurantes` e `pokemons`

### Pokemons
```
marcelo@marcelo-js:~$ mongoimport --db be-mean --collection pokemons --drop --file Projetos/json/pokemons.json 
connected to: 127.0.0.1
2015-11-24T21:47:57.493-0200 dropping: be-mean.pokemons
2015-11-24T21:47:57.555-0200 check 9 610
2015-11-24T21:47:57.581-0200 imported 610 objects
marcelo@marcelo-js:~$ 
```

### Restaurantes
```
marcelo@marcelo-js:~$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file Projetos/json/restaurantes.json
connected to: 127.0.0.1
2015-11-24T21:45:10.117-0200 dropping: be-mean.restaurantes
2015-11-24T21:45:11.054-0200 check 9 25359
2015-11-24T21:45:11.269-0200 imported 25359 objects
```

## 2. Distinct por `cuisine` na restaurantes

Ordenando alfabeticamente os resultados

```
marcelo-js(mongod-2.6.11) be-mean> db.restaurantes.distinct('cuisine').sort()
[
  "Afghan",
  "African",
  "American ",
  "Armenian",
  "Asian",
  "Australian",
  "Bagels/Pretzels",
  "Bakery",
  "Bangladeshi",
  "Barbecue",
  "Bottled beverages, including water, sodas, juices, etc.",
  "Brazilian",
  "CafÃ©/Coffee/Tea",
  "Café/Coffee/Tea",
  "Cajun",
  "Californian",
  "Caribbean",
  "Chicken",
  "Chilean",
  "Chinese",
  "Chinese/Cuban",
  "Chinese/Japanese",
  "Continental",
  "Creole",
  "Creole/Cajun",
  "Czech",
  "Delicatessen",
  "Donuts",
  "Eastern European",
  "Egyptian",
  "English",
  "Ethiopian",
  "Filipino",
  "French",
  "Fruits/Vegetables",
  "German",
  "Greek",
  "Hamburgers",
  "Hawaiian",
  "Hotdogs",
  "Hotdogs/Pretzels",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Indian",
  "Indonesian",
  "Iranian",
  "Irish",
  "Italian",
  "Japanese",
  "Jewish/Kosher",
  "Juice, Smoothies, Fruit Salads",
  "Korean",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Mediterranean",
  "Mexican",
  "Middle Eastern",
  "Moroccan",
  "Not Listed/Not Applicable",
  "Nuts/Confectionary",
  "Other",
  "Pakistani",
  "Pancakes/Waffles",
  "Peruvian",
  "Pizza",
  "Pizza/Italian",
  "Polish",
  "Polynesian",
  "Portuguese",
  "Russian",
  "Salads",
  "Sandwiches",
  "Sandwiches/Salads/Mixed Buffet",
  "Scandinavian",
  "Seafood",
  "Soul Food",
  "Soups",
  "Soups & Sandwiches",
  "Southwestern",
  "Spanish",
  "Steak",
  "Tapas",
  "Tex-Mex",
  "Thai",
  "Turkish",
  "Vegetarian",
  "Vietnamese/Cambodian/Malaysia"
]

```

## 3. Distinct por `types` na pokemons
```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.distinct('types').sort()
[
  "bug",
  "dark",
  "dragon",
  "electric",
  "fairy",
  "fighting",
  "fire",
  "flying",
  "ghost",
  "grass",
  "ground",
  "ice",
  "normal",
  "poison",
  "psychic",
  "rock",
  "steel",
  "water"
]

```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

Página 1:
```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.find().limit(5).skip(5 * 0)
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"
  ]
}
Fetched 5 record(s) in 2ms
```

Página 2:
```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.find().limit(5).skip(5 * 1)
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.285736",
  "defense": 35,
  "height": "3",
  "hp": 45,
  "name": "Caterpie",
  "speed": 45,
  "types": [
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.310402",
  "defense": 30,
  "height": "3",
  "hp": 40,
  "name": "Spearow",
  "speed": 70,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.439497",
  "defense": 55,
  "height": "8",
  "hp": 52,
  "name": "Farfetchd",
  "speed": 60,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.435237",
  "defense": 70,
  "height": "3",
  "hp": 25,
  "name": "Magnemite",
  "speed": 45,
  "types": [
    "steel",
    "electric"
  ]
}
Fetched 5 record(s) in 6ms
```

Página 3:
```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.find().limit(5).skip(5 * 2)
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.290411",
  "defense": 50,
  "height": "11",
  "hp": 60,
  "name": "Butterfree",
  "speed": 70,
  "types": [
    "flying",
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.445749",
  "defense": 55,
  "height": "11",
  "hp": 65,
  "name": "Seel",
  "speed": 45,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "attack": 85,
  "created": "2013-11-03T15:05:41.441502",
  "defense": 45,
  "height": "14",
  "hp": 35,
  "name": "Doduo",
  "speed": 75,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "attack": 25,
  "created": "2013-11-03T15:05:41.294947",
  "defense": 50,
  "height": "6",
  "hp": 45,
  "name": "Kakuna",
  "speed": 35,
  "types": [
    "poison",
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.437483",
  "defense": 95,
  "height": "10",
  "hp": 50,
  "name": "Magneton",
  "speed": 70,
  "types": [
    "steel",
    "electric"
  ]
}
Fetched 5 record(s) in 3ms
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

O resultado esperado é:

```
[
  {
    "total" : 796,
    "fire" : 41,
    "water" : 92,
    "bug" : 54,
    "flying" : 67,
    "normal" : 59,
    "steel" : 37,
    "electric" : 31,
    "poison" : 45,
    "ice" : 21,
    "fighting" : 33,
    "grass" : 67,
    "ground" : 47,
    "fairy" : 21,
    "psychic" : 55,
    "rock" : 45,
    "dark" : 30,
    "dragon" : 20,
    "ghost" : 31
  }
]
```

### Com `group`
```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.group({
...   initial: { total: 0 },
...   reduce: function(current, result) {
...     current.types.forEach(function(type) {
...       if (result[type]) {
...         result[type]++;
...       } else {
...         result[type] = 1;
...       }
...       result.total++;
...     });
...   },
... })
[
  {
    "total": 915,
    "normal": 78,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "steel": 37,
    "electric": 40,
    "poison": 54,
    "ghost": 34,
    "ice": 24,
    "fighting": 38,
    "psychic": 62,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
]
```

Para se obter o resultado esperado, é necessário acrescentar uma condição:

```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.group({
...    initial: { total: 0 },
...    cond: { defense: { $gt: 40 } },
...    reduce: function(current, result) {
...      current.types.forEach(function(type) {
...        if (result[type]) {
...          result[type]++;
...        } else {
...          result[type] = 1;
...        }
...        result.total++;
...      });
...    },
...  })
[
  {
    "total": 796,
    "fire": 41,
    "water": 92,
    "bug": 54,
    "normal": 59,
    "flying": 67,
    "steel": 37,
    "electric": 31,
    "poison": 45,
    "ice": 21,
    "fighting": 33,
    "grass": 67,
    "ground": 47,
    "psychic": 55,
    "fairy": 21,
    "rock": 45,
    "dragon": 20,
    "dark": 30,
    "ghost": 31
  }
]
```

## 6. Realizar 3 counts na pokemons.

### Todos

```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.count()
610
```

### Só do tipo `fire`

```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.count({types: 'fire'})
47
```

### Só dos que tem defesa maior que 70

```
marcelo-js(mongod-2.6.11) be-mean> db.pokemons.count({defense: { $gt: 70}})
250
```
