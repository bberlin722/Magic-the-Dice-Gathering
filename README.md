# Magic the Dice Gathering

A 3D dice-deck dueling game for 2–4 players that runs in the browser. Build a dice deck, summon creatures, cast potions and be the last duelist standing.

**Play:** https://bberlin722.github.io/Magic-the-Dice-Gathering/

## Modes

- **Solo / Local:** play against 1–3 bots. No network needed.
- **Online (up to 4 players):** peer-to-peer over WebRTC using [Trystero](https://github.com/dmotz/trystero). There's no game server: public MQTT brokers (or Nostr relays as a fallback) are used only to introduce players to each other.
  1. Enter your name and press **Create Room**. You become the host and get a 4-letter room code, and the page URL changes to `?room=CODE`.
  2. Friends open the invite link (the code fills in for them) or type the code, then press **Join Room**.
  3. The host can add bots to empty seats, then press **Start Multiplayer Game**.

## Multiplayer details

- The host's browser runs the game rules. Every player sees the table from their own seat.
- Rolling and rerolling happen at the same time for everyone. Each player gets only their own hand of cards; the other players' cards are sent as blanks.
- Players can only act on their own dice and cards.
- If a player disconnects in the lobby, their seat opens up. If they drop mid-game, a bot plays for them until they come back with **Rejoin room**. A seat left empty for 45 seconds can be taken by a new player.
- The host's game is saved in their browser, so a host who drops out can rejoin and pick up where the game left off.

Some school and office networks block peer-to-peer connections. If players can't see each other, try a different network.

## Running it

Everything is in the single file `index.html`. Open it from any web server (GitHub Pages works). three.js loads from cdnjs and Trystero loads from esm.sh.
