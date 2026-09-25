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
- Coffee spills, the shredder, the loading dock and the service pit cost one stroke, and you play again from where you hit.
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

There are two buildings, each with nine holes and a par of 26. Pick one on the setup card, or in the clubhouse for an online room.

### Head Office: day shift, 9 AM to 5 PM

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

### Factory Floor: second shift, 3 PM to 11 PM

It gets darker as the shift goes on; by the last holes you're putting under work lights and forklift headlights.

| Time | Hole | Par | What's on it |
| --- | --- | --- | --- |
| 3:00 PM | Clock In | 2 | A straight aisle with a cone slalom |
| 4:00 PM | Loading Dock | 3 | A forklift works the dock, and there's a drop where the trucks back in |
| 5:00 PM | Assembly Line | 3 | Two conveyor lines running opposite ways, carrying boxes, with robot arms by the cups |
| 6:00 PM | Oil Change | 3 | An oil slick that doesn't slow the ball, and a service pit in front of the cup |
| 7:00 PM | Break Room | 2 | Lunch tables, vending machines and a can pyramid |
| 8:00 PM | Robot Cell | 3 | Two robot arms sweep a fenced cell; time them or go around |
| 9:00 PM | Pallet Racks | 4 | A maze of racks; crates in one rack break if you hit them hard enough |
| 10:00 PM | Freight Lift | 3 | Time the gate; the lift drops you on the mezzanine |
| 11:00 PM | Last Truck | 3 | Up the dock plate and into the trailer, past a forklift |

## The campus

Both buildings sit on one campus map, with a pond, a coffee kiosk, a street, the parking lot and the loading yard. Open it with **Explore the campus** on the setup card, or **Campus map** in the pause menu.

- Drag to look around and pinch or scroll to zoom (arrow keys and +/− work too). Left alone, the camera takes itself on a slow tour.
- Coworkers walk the halls and say what's on their minds, cars drive down the street, a forklift works the yard, and ducks do laps of the pond.
- The sun follows your own clock: golden hour, then lights on at night. Tap the clock for a time-lapse.
- Tap a hole for its details, then **Practice this hole** to play it on its own as many times as you like, or play that building's full round.
- In an online room, the map shows everyone's ball on the hole they're playing.
- During a round, the camera flies across the campus from each hole to the next. Tap to skip it.

## Things to knock over

Cones, cup pyramids, boxes, office chairs, bins, water jugs and oil drums all move when the ball hits them, and they stay where they land for the next player. Hit a box, crate or water jug hard enough and it breaks. A burst jug or a tipped oil drum leaves a slippery spill, and a tipped bin scatters paper. The results give a *Property damage* award to whoever broke the most.

Each day, each group code, and each online room picks every hole's pin position, slope and green speed, and flips some holes left to right (all except the office's Clock Out).

## Hosting

Everything is in `index.html`. GitHub Pages publishes the `gh-pages` branch, so after changing `main`, update the site with `git push origin main:gh-pages`. You can also open the file directly in a browser to play offline; online rooms still need the relays.
