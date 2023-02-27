## :dart: Imploding Kitten
1.   `Speed`:  **100k Game**: ~150s
2. `Right Form`: **Tested ✓**
3. `Game Rule`: **Checked ✓**
4. `Infinite loop check`: **Tested** with 100k game ✓

## :globe_with_meridians: ENV_state
```
env[0:76]: 19 type of card
    0,1,2,3,4,5: id of player   
    7:card on Draw Pile
    6: card on Discard Pile

DrawPile: all card on Draw Pile with id. (len 28 - 0)
DiscardPile: all card on DiscardPile with id (len 13: 18 type)

env[76] (56): nope count(1 if other player use nope else 0)
env[77] (57): track player's main turn (0 to 4)
env[78:83] (58:62): track player's Nope turn (if is player 1 main turn then Nope turn is [2,3,4,0])
env[83:89] (62:67): check if player lose or not (1 if not lose else 0 if lose, default [1,1,1,1,1])
env[89] (67): check phase (0,1,2,3,4)
env[90] (68): number of card player env[57] have to draw
env[91:94]: (69:72) three card (See the future): id if player use else 0
env[94]: (72) env[57] last action(track in nope turn)
env[95] (73):  player id in Nope turn (Nope phase)
env[96]: (74) player id chosen in phase 2 (steal card turn)

env[97]: the direction of the player (1 if main direction else 0 if Reverse)
env[98]: state of the Imploding Kitten (1:face up,0:face down)
```
## :bust_in_silhouette: P_state
```
state[0:17]:number of card player hold:
    [0]: Nope
    [1]: Attack
    [2]: Skip
    [3]: Favor
    [4]: Shuffle
    [5]: See the future
    [6]: TACOCAT
    [7]: RAINBOW-RALPHING CAT
    [8]: BEARD CAT
    [9]: HAIRY POTATO CAT
    [10]: CATERMELON
    [11]: Reverse
    [12]: Draw from Bottom
    [13]: Feral Cat
    [14]: Alter the Future
    [15]: Targeted Attack
    [16]: Defuse
state[17:35](12:25):number of card in Discard Pile (same index as state[0:12],state[24]:Exploding card)
state[35] (25): number of card left in the Draw Pile
state[36] (26): number of player left
state[37] (27): 1 if player card is Nope by other player else 0
state[38:57](28:41):first card (See the future)
state[57:76](41:54):second card (See the future)
state[76:95](54:67):third card (See the future)
state[95:100](67:71):  {main turn,nope turn,steal turn, choose/take card turn}
state[100](71): number of card player have to draw
state[101:116](72:82): main player last action.
state[116:121]:(82:86) other player lose or not(1 if not lose else 0)
state[121](86): Exploding (0 if explode else 1)
state[122:127](87:91): number of card other player have (0 if lose or dont have card)
state[127]:check if Imploding Kitten explode or not(1 if explode else 0)
```
## :video_game: Action
```
Action index: 10 action
Phase 1: Main turn
    Action 0-9:
    Action 0: Nope
    Action 1: Attack
    ACtion 2: Skip
    Action 3: Favor
    Action 4: Shuffle
    Action 5: See the future
    Action 6: Draw card(end turn).
    Action 7: Steal a random card from other player (two of a kind).
    Action 8: Name the card you want from other player(three of a kind).
    Action 9: take any card from Discard Pile (5 different cards).
    Action 11(51): Reverse
    Action 12(52): Draw From Bottom
    Action 13(53): Alter the Future
    Action 14(54): Targeted Attack

Phase 2: Nope turn.
    Action 0: Nope
    Action 10: Not Nope


Phase 3: choose PLayer
        Action 15 to 19:  choose player to take / attack. (5 action)
Phase 4: choose card to give / take
    Action 3: 
        Action 20 to 36: player been chosen choose a card to give.. (17 action)
    Action 8:
        Action 37 to 53: ask the card you want from other player (17 action)
    Action 9:
        Action 54 to 70: choose card from Discard Pile (17 action)
Phase 5: Alter the Future
        3! = 6 combination of card
        Action 71 to 76: All 6 combination to Alter.  (6 action)
```
