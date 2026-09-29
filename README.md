# Nine-to-Five Links

Office mini golf for the whole team: five buildings of nine holes each, round the clock from the morning rush in the parking garage to the graveyard shift in the data center. Earn enough stars and a sixth, secret floor opens up.

**Play it:** https://andrewwu12.github.io/nine-to-five-links/

## Ways to play

- **Online room.** Play together from anywhere. Choose *Online room*, join, and send your coworkers the invite link. Everyone plays the same hole at the same time on their own device and sees each other's balls roll live. The next hole starts once everyone has finished, or you can go on ahead. People who arrive late can jump in on the group's current hole.
- **Same screen.** Up to six players take turns on one device, which works well on a meeting-room TV.
- **On your own.** Pick *Today's pins* or a shared group code, play a round, and paste your score into the team chat. Everyone on the same course gets the same layout.

Everyone can pick a department. When at least two departments are playing, the results rank them in a **Department cup** by average score against par.

## Controls

- **Mouse or touch:** press anywhere on the course, drag back like a slingshot, and let go. The farther you pull, the harder you hit. Slide back to where you started to cancel.
- **Keyboard:** arrow keys aim and set power (Shift for fine control), Space or Enter putts, Esc opens the menu.
- **Read the green:** every green slopes a little, and chevrons point downhill, so putts curve that way as they slow down. Greens vary in speed too; the bar at the top of the screen flags a fast or slow green. Fast greens roll out further, and slow ones come up short.

## Rules

- Seven strokes max per hole.
- Hazards cost one stroke, and you play again from where you hit: coffee spills, the shredder, the loading dock, the service pit, puddles, open floor tiles, pool pockets, gutters, the pinball drain and the CEO's koi pond.
- Par is 26 at Head Office and on the Factory Floor, 27 in the Parking Garage and the Data Center, and 28 in the Game Room and the CEO's Penthouse. Online standings compare each player against par for the holes they've played.

## Rage mode

Turn it on from the setup card, or from the clubhouse for an online room. Floors are waxed, walls are bouncier, the cup is smaller, greens tilt more, and everything moves faster. Your aim wobbles and there's no aim guide. A Roomba roams each hole and bumps your ball. Hazards send you back to the tee, and the elevator and the garage ramp sometimes take you to the wrong floor. The holes get new names to match, like Badge Declined, Lunch (Stolen) and Mandatory Overtime. It's ten strokes max per hole.

## Stars, the Locker and the Daily Hole

- **Stars:** every hole pays stars for your best score on it: one for par, two for a birdie, three for a hole in one or an eagle. They're saved in your browser, and on a shared screen they go to the first player.
- **Career:** stars promote you from Intern to Associate (10 stars), Senior Associate (25), Manager (45), Director (70), Vice President (95) and CEO (125). The setup card shows your stars, your title and your Daily Hole streak.
- **The Locker:** stars also unlock balls (a stress ball at 5, a coffee bean at 14, an eight ball at 30, a tennis ball at 40, a disco ball at 62, an eyeball at 88, solid gold at 115) and trails (a chalk line at 9, confetti at 22, neon at 50, flames at 75, a rainbow at 130). Open the Locker on the setup card to pick what to wear.
- **Daily Hole:** one hole a day from the five buildings, with a twist: a tiny or a huge cup, an icy floor or shag carpet, bouncy walls, rush hour (everything that moves goes faster), a steep green, or shaky hands. Everyone gets the same hole and twist that day. You get three tries and the best one counts; a try counts from its first putt. Then copy a card for the team chat:

  ```
  Nine-to-Five Links · Daily Hole #1
  Inbox (Head Office) · Icy floor · Par 3
  🟨 ⬜ 🟩  Best: 2 (Birdie)
  🔥 4-day streak
  https://andrewwu12.github.io/nine-to-five-links/
  ```

  Play one every workday to build a streak. Weekends never break it. The next Daily Hole opens at midnight on your own clock.
- **Ghosts:** play a hole again on the same layout (in practice, on your second and third Daily Hole tries, or in another round on the same pins) and a faint ball replays your best run on it, stroke by stroke.
- **The penthouse:** at 100 stars, your badge opens the CEO's private elevator. See below.

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
- Anyone who knows a room code can read that room's messages: player names, departments, ball positions, scores, taunts and workshop designs. Don't use a room code or a name you'd mind being public.
- Some work networks and VPNs block the relays; two of them use ports 8084 and 8884. If the clubhouse says it can't reach the relay servers, try another network, such as a phone hotspot.
- To use your own relay instead, add `?relay=wss://your-broker.example/mqtt` to the URL. It needs to speak MQTT 3.1.1 over WebSockets without a password. The invite link carries the parameter, so everyone in the room uses the same relay.

## The holes

There are five buildings of nine holes each, and a sixth for those who earn it. Pick one on the setup card, or in the clubhouse for an online room.

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

### Parking Garage: the morning rush, 7 to 9 AM

It's dim under the fluorescent lights until you come out on the roof.

| Time | Hole | Par | What's on it |
| --- | --- | --- | --- |
| 7:00 AM | Pull In | 2 | A barrier arm that lifts and drops across the entry lane |
| 7:15 AM | Compact Only | 3 | Rows of parked cars, and one backing out of its bay |
| 7:30 AM | Speed Bumps | 3 | Three speed bumps that eat your pace, and a car cruising the aisle |
| 7:45 AM | Spiral Ramp | 3 | Ramps that carry you down and round the ramp core |
| 8:00 AM | EV Charging | 3 | A row of chargers, a puddle and an oil stain |
| 8:15 AM | Car Wash | 3 | A conveyor through two spinning brushes, and soap suds |
| 8:30 AM | Door Ding | 3 | Car doors that fly open, and a car looking for a spot |
| 8:45 AM | Up to the Roof | 3 | Climb the ramp past a car coming down; it comes out on the roof |
| 8:59 AM | Last Spot | 4 | Two rows of cars, two more circling, and the last open spot |

### Game Room: after hours, 5 PM to 1 AM

The lights go down and the neon comes up as the night goes on.

| Time | Hole | Par | What's on it |
| --- | --- | --- | --- |
| 5:00 PM | Happy Hour | 2 | Bar stools, high-top tables and a cup pyramid |
| 6:00 PM | Air Hockey | 3 | A table with almost no friction, and a mallet guarding the goal |
| 7:00 PM | Foosball | 3 | Rows of little men sliding on their rods in front of the goal |
| 8:00 PM | Pinball | 4 | Launch up the plunger lane; pop bumpers kick, flippers flick, and the drain waits |
| 9:00 PM | Ball Pit | 3 | A ball pit that stops anything, and a slide round it |
| 10:00 PM | Pool Table | 3 | Break the rack to reach the cup, and stay out of the pockets |
| 11:00 PM | Bowling | 3 | An oiled lane between two gutters, and ten pins in front of the cup |
| 12:00 AM | Skee-Ball | 3 | Up the ramp and through the gaps in two rings to the 100 |
| 1:00 AM | Last Call | 4 | A spinning dance floor that flings you round, and the bar |

### Data Center: graveyard shift, 11 PM to 7 AM

| Time | Hole | Par | What's on it |
| --- | --- | --- | --- |
| 11:00 PM | Badge Scan | 2 | A security door that opens and shuts |
| 12:00 AM | Cold Aisle | 3 | Cold air blows down one aisle and back up the other |
| 1:00 AM | Hot Aisle | 3 | Exhaust fans that cycle on and off, blowing against you, and loose floor tiles |
| 2:00 AM | Raised Floor | 3 | Open floor tiles to fall through, and cable spaghetti |
| 3:00 AM | Tape Library | 3 | Two tape robots shuttling up and down the library |
| 4:00 AM | Cable Management | 3 | Tangles of cable that slow everything down |
| 5:00 AM | Power Outage | 3 | Battery cabinets in the dark, lit only by the emergency lights |
| 6:00 AM | Cooling Plant | 3 | Chiller fans that blast across the room in turns, over puddles |
| 7:00 AM | Five Nines | 4 | Racks, a crash cart, fans, and a cage door guarding the cup |

### The CEO's Penthouse: executive hours, 10 AM to 2 PM

It isn't on the campus map, and it isn't in the building list until you have 100 stars. Its holes pay stars too. In an online room, a host who has it can take the whole room up.

| Time | Hole | Par | What's on it |
| --- | --- | --- | --- |
| 10:00 AM | Private Elevator | 2 | Out of the elevator and across a polished marble lobby that speeds the ball up |
| 10:30 AM | Corner Office | 3 | Round the corner to the CEO's desk, over a Persian rug |
| 11:00 AM | Boardroom | 3 | Bank round the boardroom table and its wheeled chairs |
| 11:30 AM | Aquarium | 3 | Round a floor-to-ceiling fish tank, past the koi pond |
| 12:00 PM | Sushi Lunch | 3 | A sushi belt loops the counter; ride it or cross it, past a champagne tower |
| 12:30 PM | Private Gym | 3 | Rows of treadmills running back at you, or the long way over the yoga mats |
| 1:00 PM | Helipad | 4 | Time your putt through the helicopter's turning rotor, or go round it |
| 1:30 PM | The Vault | 3 | A round strongroom whose door swings open and shut; the cup is inside with the gold |
| 2:00 PM | Golden Parachute | 4 | The rooftop green: bunkers, a pond, a hill that runs back to it, and a soft landing round the cup |

## The campus

All five buildings sit on one campus map, with a pond, a coffee kiosk, two streets, the parking lot, the loading yard, a patio with a taco truck, and a sports field with a running track. Open it with **Explore the campus** on the setup card, or **Campus map** in the pause menu.

- Drag to look around and pinch or scroll to zoom (arrow keys and +/− work too). Left alone, the camera takes itself on a slow tour.
- Coworkers walk the halls and say what's on their minds, cars drive down both streets, a forklift works the yard, people jog round the track, and ducks do laps of the pond.
- The sun follows your own clock: golden hour, then lights on at night. Tap the clock for a time-lapse.
- Tap a hole for its details, then **Practice this hole** to play it on its own as many times as you like, or play that building's full round.
- In an online room, the map shows everyone's ball on the hole they're playing.
- During a round, the camera flies across the campus from each hole to the next. Tap to skip it.

## The Workshop: build your own holes

Press **Build a course** on the setup card to design up to three holes of your own. They're saved in your browser. In an online room, press **Build holes together** in the clubhouse: everyone in the room edits the same holes at once, sees each other's cursors, and changes merge as they happen.

- Pick a shape for each hole (big room, hallway, L-bend, zigzag or hairpin) and a look (office, factory, garage, game room or data center), then drag the tee and the cup where you want them.
- Choose pieces from the palette and tap the course to place them: walls, filing cabinets, couches, pallets, racks, parked cars, server racks and bar counters; planters, pillars, beanbags, tables, bollards, high-tops and pinball pop bumpers; rugs, oil slicks, ramps, conveyors, bowls, speed bumps, cooling fans, ball pits and spinning floors; coffee spills, service pits, shredders, puddles, open floor tiles and pool pockets; clock hands, robot arms, mail carts, forklifts, moving cars, barrier arms and tape robots; and props to knock over, from cones to bowling pins and a rack of pool balls. Select a piece to rotate or remove it.

Limits keep every hole fair:

- Each hole has a budget of 60 points, and bigger pieces cost more.
- At most 30 pieces, 3 movers, 4 hazards and 14 props per hole.
- Nothing but props within 3 feet of the tee or the cup, and the cup at least 10 feet from the tee.
- There has to be a way through from the tee to the cup.
- A test bot plays every design with a little human-sized error. It has to finish within 8 strokes, and its score sets the hole's par.

Once a hole passes, **Test drive** plays it on its own, and **The Workshop** shows up as a building on the setup card and in the clubhouse, so a room can tee off on the holes it just built.

## Things to knock over

Cones, cup pyramids, boxes, office chairs, bins, water jugs, oil drums, tape cartridges, pool balls, bowling pins, champagne glasses, gold bars and medicine balls all move when the ball hits them, and they stay where they land for the next player. Knock down all ten pins for a strike. Hit a box, crate or water jug hard enough and it breaks, and a champagne glass shatters. A burst jug or a tipped oil drum leaves a slippery spill, and a tipped bin scatters paper. The results give a *Property damage* award to whoever broke the most.

Each day, each group code, and each online room picks every hole's pin position, slope and green speed, and flips some holes left to right (all except the office's Clock Out and the game room's Pinball).

## Hosting

Everything is in `index.html`. GitHub Pages publishes the `gh-pages` branch, so after changing `main`, update the site with `git push origin main:gh-pages`. You can also open the file directly in a browser to play offline; online rooms still need the relays.
