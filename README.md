# Nine-to-Five Links

Office mini golf for the whole team: nine holes, one for every hour from 9 AM to 5 PM.

**Play it:** https://andrewwu12.github.io/nine-to-five-links/

## Ways to play

- **Online room.** Play together from anywhere. Choose *Online room*, join, and send your coworkers the invite link. Everyone plays the same hole at the same time on their own device and sees each other's balls roll live. The next hole starts once everyone has finished, or you can go on ahead. People who arrive late can jump in on the group's current hole.
- **Same screen.** Up to six players take turns on one device, which works well on a meeting-room TV.
- **On your own.** Pick *Today's pins* or a shared group code, play a round, and paste your score into the team chat. Everyone on the same course gets the same layout.

## Controls

- **Mouse or touch:** press anywhere on the course, drag back like a slingshot, and let go. The farther you pull, the harder you hit.
- **Keyboard:** arrow keys aim and set power (Shift for fine control), Space or Enter putts, Esc opens the menu.

## Rules

- Seven strokes max per hole.
- Coffee spills and the shredder cost one stroke, and you play again from where you hit.
- Par is 26. Online standings compare each player against par for the holes they've played.

## How online rooms work

The game is one static page with no server of its own. In an online room, each browser connects over secure WebSockets to three free public MQTT relays: shiftr.io's public instance, EMQX's public broker, and HiveMQ's public broker. Players exchange small messages on a topic named after the room code. Every message goes out through all three relays and duplicates are dropped, so a room keeps working as long as each player can reach at least one of them.

Worth knowing:

- These are free public services with no uptime guarantee.
- Anyone who knows a room code can read that room's messages: player names, ball positions and scores. Don't use a room code or a name you'd mind being public.
- Some work networks and VPNs block the relays; two of them use ports 8084 and 8884. If the clubhouse says it can't reach the relay servers, try another network, such as a phone hotspot.
- To use your own relay instead, add `?relay=wss://your-broker.example/mqtt` to the URL. It needs to speak MQTT 3.1.1 over WebSockets without a password. The invite link carries the parameter, so everyone in the room uses the same relay.

## The holes

| Time | Hole | Par | What's on it |
| --- | --- | --- | --- |
| 9:00 AM | Badge In | 2 | A straight hallway with two planters |
| 10:00 AM | Stand-up | 2 | A big round table to bank around |
| 11:00 AM | Inbox | 3 | A dogleg with a mail cart shuttling across the corridor |
| 12:00 PM | Lunch Rush | 3 | Two coffee spills with a narrow dry gap between them |
| 1:00 PM | Food Coma | 3 | A shag rug that slows the ball, plus beanbags that swallow shots |
| 2:00 PM | Copy Room | 3 | A paper-feed conveyor that pulls the ball toward the shredder |
| 3:00 PM | Coffee Run | 3 | An uphill ramp to a cup set in a bowl |
| 4:00 PM | Elevator | 3 | Time the doors; the car drops you off on the 12th floor |
| 5:00 PM | Clock Out | 4 | A giant wall clock whose hands sweep the green |

Each day, each group code, and each online room picks every hole's pin position and flips some holes left to right (all except Clock Out).

## Hosting

Everything is in `index.html`, served by GitHub Pages from this repository. Open the file directly in a browser to play offline; online rooms still need the relays.
