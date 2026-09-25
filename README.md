# Nine-to-Five Links

Office mini golf for the whole team: nine holes, one for every hour from 9 AM to 5 PM.

**Play it:** https://andrewwu12.github.io/nine-to-five-links/

## Ways to play

- **Online room.** Play together from anywhere. Choose *Online room*, join, and send your coworkers the invite link. Everyone plays the same hole at the same time on their own device and sees each other's balls roll live. The next hole starts once everyone has finished, or you can go on ahead. People who arrive late can jump in on the group's current hole.
- **Same screen.** Up to six players take turns on one device, which works well on a meeting-room TV.
- **On your own.** Pick *Today's pins* or a shared group code, play a round, and paste your score into the team chat. Everyone on the same course gets the same layout.

Everyone can pick a department. When at least two departments are playing, the results rank them in a **Department cup** by average score against par.

## Controls

- **Aim:** press and drag anywhere on the course to turn the putter toward that spot, or use the arrow keys (Shift for fine steps).
- **Swing:** hold **Swing** (or Space) to draw the putter back. The meter's marks show how far a putt rolls on a flat green of medium speed. Hold too long and the putter comes forward again. Let go to start the stroke, then tap again as the needle crosses the green zone. Tap early and the putt pushes right; tap late and it pulls left. Miss the tap entirely and you shank it. Esc cancels a swing.
- **Read the green:** every green slopes a little, and chevrons point downhill, so putts curve that way as they slow down. The swing meter shows the distance to the pin and the green's speed. Fast greens roll out further, and slow ones come up short.

## Rules

- Seven strokes max per hole.
- Coffee spills and the shredder cost one stroke, and you play again from where you hit.
- Par is 26. Online standings compare each player against par for the holes they've played.

## Rage mode

Turn it on from the setup card, or from the clubhouse for an online room. Floors are waxed, walls are bouncier, the cup is smaller, greens tilt more, and everything moves faster. The swing meter speeds up and its sweet spot shrinks. Your aim wobbles and there's no aim guide. A Roomba roams each hole and bumps your ball. Hazards send you back to the tee, and the elevator sometimes takes you to the wrong floor. The holes get new names to match, like Badge Declined, Lunch (Stolen) and Mandatory Overtime. It's ten strokes max per hole.

## Taunts and office life

- Coworkers comment on your putting in notification pings: lip-outs, coffee spills, wall-banging, and taking too long to putt. Press **Heckle** for a line on demand, or turn taunts off in the menu.
- In an online room, **Taunt** sends everyone a line of your choice, which appears as a speech bubble over your ball.
- The Safety Board tracks putts since the last incident. The hole summary carries an office memo, and the results hand out awards like *So close* (most lip-outs) and *Roomba's favorite*.

## Celebrations

Holing out starts a show, picked by how well you scored. You see every show for a score before any of them repeats.

- **Hole in one and eagle:** confetti cannons, fireworks over the office, a *PROMOTED* stamp with your new job title, a disco ball with dancing mascots, a mascot parade, or Employee of the Month.
- **Birdie:** paper airplanes, balloons (a few pop), donuts from the ceiling, sticky notes from the team, a dot-matrix banner, two coffee mugs clinking, the rubber debugging duck, an office-chair joyride, or an itemized receipt.
- **Par:** a stamp like *MEETS EXPECTATIONS* or *LGTM*, the duck, or a quieter show.
- **Bogey or worse:** *PER MY LAST EMAIL*, a tangle of HDMI cables rolling by like tumbleweed, a sad deflating balloon, or a rain cloud parked over the cup.

In Rage mode, a good hole often gets a follow-up stamp such as *BEGINNER'S LUCK* or *HR HAS BEEN NOTIFIED*.

## How online rooms work

The game is one static page with no server of its own. In an online room, each browser connects over secure WebSockets to three free public MQTT relays: shiftr.io's public instance, EMQX's public broker, and HiveMQ's public broker. Players exchange small messages on a topic named after the room code. Every message goes out through all three relays and duplicates are dropped, so a room keeps working as long as each player can reach at least one of them.

Worth knowing:

- These are free public services with no uptime guarantee.
- Anyone who knows a room code can read that room's messages: player names, departments, ball positions, scores and taunts. Don't use a room code or a name you'd mind being public.
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

Each day, each group code, and each online room picks every hole's pin position, slope and green speed, and flips some holes left to right (all except Clock Out).

## Hosting

Everything is in `index.html`. GitHub Pages publishes the `gh-pages` branch, so after changing `main`, update the site with `git push origin main:gh-pages`. You can also open the file directly in a browser to play offline; online rooms still need the relays.
