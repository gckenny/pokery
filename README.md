pokery
======

Node poker library for poker crunchers.

Reviving the ghost of PokerStove for all platforms.


## EV Approximations

Use Pokery's Monte Carlo Simulator to run EV approximations.

The Simulator takes an array of ranges and an array of board cards.

```javascript
> import Simulator from 'pokery';
> new Simulator(['AhAd', 'KK', 'JTs', '72o'], ['Qd']).run();
[ { range: 'AhAd',
    wins: 605,
    losses: 395,
    ties: 0,
    lossPct: 39.5,
    tiePct: 0,
    winPct: 60.5,
    ev: 0.605 },
  { range: 'KK',
    wins: 120,
    losses: 880,
    ties: 0,
    lossPct: 88,
    tiePct: 0,
    winPct: 12,
    ev: 0.12 },
  { range: 'JTs',
    wins: 207,
    losses: 793,
    ties: 0,
    lossPct: 79.3,
    tiePct: 0,
    winPct: 20.7,
    ev: 0.207 },
  { range: '72o',
    wins: 68,
    losses: 932,
    ties: 0,
    lossPct: 93.2,
    tiePct: 0,
    winPct: 6.800000000000001,
    ev: 0.068 } ]
```

## Hand Evaluations

Pokery can evaluate and compare hands.

To be more portable and use less memory, Pokery currently does not use a lookup
table, which would be 250MB.

```javascript
> import Hand from 'pokery';
> new Hand(['Ac', 'Ad', 'Ah', 'As', 'Jc', 'Td', '2h']);
{ strength: 7,
  ranks: [ [ 14 ], [ 11 ] ],
  cards: [ 'Ac', 'Ad', 'Ah', 'As', 'Jc' ] }
> new Hand(['Kc', '3d', '4h', '7s', '6c', '5d', 'Kh']);
{ strength: 4,
  ranks: [ [ 7, 6, 5, 4, 3 ] ],
  cards: [ '3d', '4h', '7s', '6c', '5d' ] }
```

## Range Parsing

Pokery can expressively breakdown hand ranges and return random hands from a
range.

You can learn more about [hand range
grammar](http://pokerini.com/help/holdem_range_notation.php).

```javascript
> import Range from 'pokery';
> new Range('AKs').get();
[ 'Ad', 'Kd' ]
> new Range('AKs').get();
[ 'Ac', 'Kc' ]
> new Range('JQo').get();
[ 'Js', 'Qd' ]
> new Range('JQo').get();
[ 'Jh', 'Qs' ]
```
