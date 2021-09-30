

### Full example

``` html
<html>
    <head>
        <title>Cards</title>

        <link rel="stylesheet" href="node_modules/deck-of-cards/example/example.css">
    </head>
    <body>
        <script src="node_modules/deck-of-cards/dist/deck.min.js"></script>

        <div id="container"></div>

        <script>
            var $container = document.getElementById('container');

            // create Deck
            var deck = Deck();

            // add to DOM
            deck.mount($container);

            deck.cards.forEach(function (card, i) {
                card.setSide(Math.random() < 0.5 ? 'front' : 'back');

                // explode
                card.animateTo({
                    delay: 1000 + i * 2, // wait 1 second + i * 2 ms
                    duration: 500,
                    ease: 'quartOut',

                    x: Math.random() * window.innerWidth - window.innerWidth / 2,
                    y: Math.random() * window.innerHeight - window.innerHeight / 2
                });
            });
        </script>
    </body>
</html>
```

Available on JsFiddle: http://jsfiddle.net/x0gjood1/


### Javascript API

#### Deck

``` js
// Instantiate a deck
var deck = Deck();

// display it in a html container
var $container = document.getElementById('container');
deck.mount($container);
```

Deck example: http://jsfiddle.net/ec4kcx1k/

``` js
// Flip all cards in deck
deck.flip();

// Sort cards
deck.sort();

// Shuffle
deck.shuffle();

// Display fan
deck.fan();

// Remove deck from html container, hide it
deck.unmount();
```

Shuffle cards and fan: http://jsfiddle.net/favbdkta/

Deck with jokers:

``` js
// Instanciate a deck with jokers
var deck = Deck(true);
```


#### Card

``` js
// Select the first card
var card = deck.cards[0];

// Add it to an html container
card.mount($container);

// Allow to move/drag it
card.enableDragging();
card.disableDragging();

// Allow to flip it
card.enableFlipping();
card.disableFlipping();

// Flip card
card.flip();

// Display card front or back
card.setSide('front');
card.setSide('back');
```
