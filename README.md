# RoobetCrashDE1SOC
Roobet Crash compatible with the INTEL FPGA DE1-SOC Board

The code under Roobet.C contains all of the code for our (Mark Karlov && Christian Clarke) game, compatible on the Intel FPGA DE1-SOC Board

Taken from the Casino's definition of Roobet Crash, Roobet Crash is "A cryptocurrency gambling game on Crypto's Fastest Growing Casino. Players place a bet before each round starts. A multiplier starts at 1x and increases at a exponential rate. The player can cash out and receive their multiplied bitcoin/wager."

The game consists of 2 phases: The (1) Loading phase, as well as the (2) Rocket Phase

(1)
The Loading Phase contains a graphic display of a countdown from 5 seconds, as well as a rocket approaching the top. The 5 seconds are necessary for players to make their corresponding wagers
Wagers can be made from SW0-2 for Player 1, and SW 4-6 for Player 2. SW0 represents a 16% wager of total balance, SW1 represents a 34% wager of total balance, and SW2 represents a 50% wager of total balance. These percentages are summative, so if you apply all switches, then the total wager reflects 100% of the total balance. Vice Versa for Player 2's switches.

In order to be "IN" a game, Player 1 has to click on Button 0, while Player 2 has to click on Button 2. Afterwards, they can confirm their wagers by pressing Button 1 & 3 respectively. These can be updated at any point. Wagers can only be placed DURING the (1) Loading phase.

(2) Afterwards, we need to generate a stochastic multiplier. Our probability distribution is based on an exponential distribution obtained from other Crypto Casinos; this distribution uses SHA256 to obtain hashes of hashes in getting a completely random number. After collecting a number from a uniform distribution, we input that number into the exponential distribution to get the new multiplier. For example,there's a 11% chance that the multiplier will be <1.05. This number signifies an INSTANT BUST, where the players will automatically lose their wager no matter what, because they can't cash out in time.

The rocket goes off, and each player has an opportunity to cash out by clicking Button0 and Button2 respectively. If they don't cash out before the rocket reaches the random multiplier, then they lose their wager from their total balance. If they cash out in time, then they'll get their wage times the multiplier that they cashed out at.

This game goes on for 10 rounds, or until a player or both players bankrupt (go ALL IN (100% wager) and lose to a crash)

FEATURES

There are several important features, both (1) backend and (2) frontend

(1) 
-All sprites, images, and pixels were generated through back buffers; hence every animation is extremely smooth on the VGA display.
-Hardware interrupts were implemented for pushing of buttons, and polling of switch inputs was conducted to determine wager percentage
-Accurate Software Timers were used to count the clock down in the loading phase, and determine how fast the rocket should go up by in the game phase.
-Character Buffers were used to print important text.
-Exponential distribution that matches nested SHA256 hashes from casinos was used.

(2)
-Players Balances, Wagers, and whether they were "IN" the round or "OUT" of the round are all important text that were printed using the character buffers
-High definition sprites were picked to display the Rocket, loading sprites, flames, explosions, as well as countdown timers and multipliers.
-Unique endgame cases were chosen: Player 1 wins, Player 2 wins, or both players bankrupt themselves.

Run it on : https://cpulator.01xz.net/?sys=arm-de1soc
(1) Open File and Click on "C Code"
(2) Compile and Continue
(3) SW9 to RUN

CONTRIBUTIONS

-Backbuffering all sprites - Mark  
-Hardware Interrupts of Buttons - Christian
-Character Buffers - Mark
-Probabiliy Distribution - Christian
-Software Timers - Mark
-LoadingGame Sprites - Christian
-RocketPhase Sprites - Mark
-EndGame Cases - Christian



