<!DOCTYPE html>

<html lang="en" xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="utf-8" />
    <title>YocoJack</title>
</head>
<body>
    <div class="Game">
        <h1>YocoJack</h1>
        <input type="button" class="btn" value="begin" onclick="begin()" />
        <input type="button" class="btn" value="click" onclick="clickMe()"/>
        <input type="button" class="btn" value="stay"onclick="stay()"/> 

        <div id="players" class="players">
        </div>

        <div id="deck" class="deck">
            <div class="card" id="deckcount">52</div>
            <div class="status" id="status"></div>
        </div>
        <div class="clear"></div>
    </div>
</body>
<script lang="javascript">
    function handCards()
    {
        var suits = ["Spades", "Diamonds", "Clubs", "Hearts"];
        var values = ["2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A"];
        var deck = new Array();

        deck = new Array();
        
        for (var y = 0; y < values.length; y++)
        {
            for (var x = 0; x < suits.length; x++)
            {
                var weight = parseInt(values[y]);
                if (values[y] == "J" || values[y] == "Q" || values[y] == "K")
                {
                    weight = 10;
                }
                if (values[y] == "A")
                {
                    weight = 11
                }
                var card = { Value: values[y], Suit: suits[x], Weight: weight }
                deck.push(card);
            }
        }
    }

    function creatPlayers()
    {
        var players = new Array();

        players = new Array();
        for (var x = 1; x <= num; x++)
        {
            var hand = new Array();
            var player = { Name: 'Player ' + x, ID: x, Points: 0, Hand: hand };
        player.push(player);
        }
    }
    
    function yocoJack()
    {
        document.getElementById('btnBegin').value = 'Restart';
        document.getElementById('status').style.display = "none";

        currenPlayer = 0;
        handCards();
        createPlayers(2);

        document.getElementById('player_' + currenPlayer).classList.add('active');
    }

    function clickMe()
    {
        var currentPlayer = 0;

        var card = deck.pop();
        players[currentPlayer].Hand.push(card);
        renderCard(card, currentPlayer)
        updatePoints();
        check();
    }
</script>
</html>
