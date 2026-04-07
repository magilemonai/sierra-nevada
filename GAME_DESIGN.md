# The Lighthouse of Meridia - Game Design Spec

## Story
You are Captain Elara Voss, a cartographer who washes ashore on the legendary Lost Isle of Meridia after a terrible storm. Legend says Meridia was once home to an ancient civilization that vanished overnight, leaving behind only their enchanted lighthouse. You must explore the island, solve ancient puzzles, and relight the lighthouse to signal for rescue before the rising tide traps you forever.

## EGA Palette (16 colors)
```
BLACK:    #000000    BLUE:      #0000AA    GREEN:     #00AA00    CYAN:      #00AAAA
RED:      #AA0000    MAGENTA:   #AA00AA    BROWN:     #AA5500    LTGRAY:    #AAAAAA
DKGRAY:   #555555    LTBLUE:    #5555FF    LTGREEN:   #55FF55    LTCYAN:    #55FFFF
LTRED:    #FF5555    LTMAGENTA: #FF55FF    YELLOW:    #FFFF55    WHITE:     #FFFFFF
```

## Room Map & Connections

```
                    [temple_interior]
                          |
[cave] -- [coastal_path] -- [jungle] -- [temple_exterior]
                |                              |
            [beach]                      [cliff_overlook]
                                               |
[hidden_cove] --------- [lighthouse_base] -----+
                               |
                        [lighthouse_top]
```

## Rooms (10 total)

### 1. beach (START)
- Description: A white sandy beach littered with wreckage from your ship. Broken timbers and torn sails scatter the shore. Foamy waves crash rhythmically. The coastal path leads NORTH.
- Exits: north → coastal_path
- Visible items: wooden plank (in debris), rope (tangled in broken mast)
- Art: Ocean on bottom half, sandy beach, ship debris, seagulls

### 2. coastal_path
- Description: A rocky path winds along dramatic sea cliffs. To the SOUTH lies the beach. A DARK CAVE opens in the cliff face to the WEST. Dense jungle growth blocks the path EAST. The path continues NORTH toward what appears to be ruins.
- Exits: south → beach, west → cave, east → jungle (BLOCKED by vines until machete used), north → village
- Art: Rocky path, cliff edge, ocean view, cave entrance, jungle wall

### 3. village
- Description: The crumbling remains of an ancient village. Stone huts with collapsed roofs line a mossy cobblestone path. An old well sits in the village square. A merchant's stall still displays rusty wares.
- Exits: south → coastal_path
- Visible items: oil lamp (inside hut, must SEARCH HUT or LOOK HUT), machete (on merchant stall), bucket (by well)
- Puzzle: Use PLANK on well (bridge the gap), then use BUCKET to get RUSTY KEY from well bottom
- Art: Ruined stone huts, well, market stall, overgrown vegetation

### 4. cave
- Description: A dark cave carved into the sea cliffs. Near the entrance, dim light reveals rocky walls glistening with moisture. Deeper in, absolute darkness swallows everything.
- Exits: east → coastal_path
- Light area items: flint_and_steel (on rock ledge near entrance)
- Dark area items (need lit lamp): oil_flask (on natural shelf), old_journal (on the ground)
- Puzzle: Must LIGHT LAMP (with flint) or USE FLINT ON LAMP to see deeper area
- Art: Dark cave, stalactites, water drips, glow from entrance

### 5. jungle
- Description: Dense tropical jungle. Vibrant green foliage presses in from all sides. Colorful birds call from the canopy. A worn stone path leads deeper east toward ancient architecture. A bright-feathered PARROT watches you from a branch.
- Exits: west → coastal_path, east → temple_exterior
- Blocked initially by vines (from coastal_path side). Use MACHETE to clear.
- Items: exotic_fruit (hanging from a low branch)
- The parrot repeats clues: "Maaap! The answer is a maaap! Squawk!"
- Art: Lush jungle, large leaves, parrot on branch, stone path

### 6. temple_exterior
- Description: A magnificent stone temple covered in moss and carved with strange symbols. A massive stone door blocks the entrance. Above the door, an inscription reads: "I have cities but no houses, forests but no trees, and water but no fish. What am I?"
- Exits: west → jungle, south → cliff_overlook
- Puzzle: Type the answer to the riddle. Answer: MAP. Door opens → temple_interior
- Art: Grand stone temple facade, carved symbols, massive door, jungle frame

### 7. temple_interior
- Description: A vast chamber lit by shafts of light from cracks in the ceiling. Ancient murals depict the lighthouse beaming across the sea. On a stone pedestal in the center rests a brilliant CRYSTAL LENS. The walls tell of the Meridians who built a lighthouse to guide lost souls home.
- Exits: south → temple_exterior
- Items: crystal_lens (on pedestal - TAKE it)
- Lore: Murals describe how the lighthouse needs: a Crystal Lens, sacred oil, and fire
- Art: Grand interior, light shafts, pedestal with glowing crystal, murals

### 8. cliff_overlook
- Description: A windswept cliff with a breathtaking view of the island. Far below, you can see a lighthouse standing on a rocky promontory. The cliff is too steep to climb down without a rope. A sturdy iron ring is bolted into the rock at the edge.
- Exits: north → temple_exterior
- Puzzle: TIE ROPE TO RING or USE ROPE ON RING → enables "down" exit to lighthouse_base
- After rope: down → lighthouse_base
- Art: Dramatic cliff view, distant lighthouse, iron ring, vast ocean

### 9. lighthouse_base
- Description: The base of an ancient stone lighthouse. The tower stretches high above, its lamp dark and lifeless. A heavy wooden door with a rusted iron lock bars entry. Waves crash against the rocks below. A narrow path leads to a HIDDEN COVE to the west.
- Exits: up → cliff_overlook (via rope), west → hidden_cove
- Puzzle: USE KEY ON DOOR or UNLOCK DOOR → enables "enter/in/north" to lighthouse_top
- Art: Lighthouse base, heavy door, crashing waves, rocky ground

### 10. hidden_cove
- Description: A small, sheltered cove with calm turquoise water. An old rowboat is pulled up on the pebble beach, but it has a large hole in the hull. This would be your way off the island... if only someone could see you.
- Exits: east → lighthouse_base
- Purpose: Establishes the rowboat ending and provides atmosphere
- Art: Peaceful cove, damaged rowboat, clear water, distant horizon

### 11. lighthouse_top
- Description: The top of the lighthouse. A complex brass mechanism holds an empty socket where a lens should go. An oil reservoir sits dry beside it. The view is magnificent - you can see the entire island and the vast ocean beyond. Wait... is that a ship on the horizon?
- Exits: down → lighthouse_base
- Puzzle sequence:
  1. USE CRYSTAL LENS ON MECHANISM / PUT LENS IN SOCKET → lens placed
  2. USE OIL FLASK ON RESERVOIR / POUR OIL → oil filled
  3. USE FLINT ON MECHANISM / LIGHT MECHANISM → VICTORY!
- Art: Lighthouse lamp mechanism, brass fittings, panoramic ocean view, distant ship

## Items (10 items)

| ID | Name | Found In | How to Get |
|---|---|---|---|
| plank | Wooden Plank | beach | TAKE PLANK |
| rope | Sturdy Rope | beach | TAKE ROPE (untangle from mast) |
| oil_lamp | Oil Lamp | village | SEARCH HUT / LOOK IN HUT |
| machete | Rusty Machete | village | TAKE MACHETE |
| bucket | Old Bucket | village | TAKE BUCKET |
| rusty_key | Rusty Key | village (well) | USE BUCKET ON WELL (after plank placed) |
| flint | Flint & Steel | cave | TAKE FLINT |
| oil_flask | Flask of Oil | cave (dark) | TAKE FLASK (need lit lamp) |
| crystal_lens | Crystal Lens | temple_interior | TAKE LENS |
| exotic_fruit | Exotic Fruit | jungle | TAKE FRUIT |

## Puzzle Chain (Critical Path)

1. **Beach**: Take PLANK and ROPE
2. **Village**: Take MACHETE, take BUCKET, SEARCH HUT → OIL LAMP
3. **Village Well**: USE PLANK ON WELL, then USE BUCKET ON WELL → RUSTY KEY
4. **Cave entrance**: Take FLINT
5. **Cave**: USE FLINT ON LAMP (lights the lamp), explore dark area → OIL FLASK
6. **Coastal Path → Jungle**: USE MACHETE ON VINES (clears path east)
7. **Jungle**: Note parrot's hint (optional). Go east.
8. **Temple Exterior**: Answer riddle: type MAP → door opens
9. **Temple Interior**: Take CRYSTAL LENS
10. **Cliff Overlook**: TIE ROPE TO RING → can climb down
11. **Lighthouse Base**: USE KEY ON DOOR → can enter lighthouse
12. **Lighthouse Top**: USE LENS ON MECHANISM, USE OIL ON RESERVOIR, USE FLINT ON MECHANISM → **VICTORY!**

## Optional/Fun Interactions
- TALK TO PARROT → hints about the riddle
- READ JOURNAL → backstory about the Meridians
- LOOK AT MURALS → lore about the lighthouse
- EAT FRUIT → funny message ("Tastes like a mix of mango and regret")
- SWIM → "The currents are too dangerous!"
- PET PARROT → "The parrot tolerates your affection briefly"

## Parser Verbs
LOOK/EXAMINE, TAKE/GET/PICK UP, USE/PUT, OPEN, TALK/SPEAK, READ, GO/WALK, 
NORTH/SOUTH/EAST/WEST/UP/DOWN/ENTER/IN, INVENTORY/I, HELP, 
TIE, LIGHT, POUR, UNLOCK, SEARCH, ANSWER, PUSH, PULL, EAT, SWIM, CLIMB, SAVE

## Score System (100 points total)
- Take plank: 5
- Take rope: 5
- Get oil lamp: 5
- Take machete: 5
- Take bucket: 5
- Get rusty key from well: 10
- Take flint: 5
- Light the lamp: 5
- Get oil flask: 10
- Clear jungle vines: 5
- Solve temple riddle: 10
- Get crystal lens: 10
- Tie rope at cliff: 5
- Unlock lighthouse: 5
- Place lens: 5
- Pour oil: 5
- Light the lighthouse (WIN): 0 (total already 100... adjust)

Adjusted: total = 100pts at victory

## Death/Failure States
- None! Sierra-style but merciful. Funny refusals instead.

## Technical Spec
- Single HTML file
- Canvas: 640x400 (doubled from 320x200 EGA resolution)
- Render at 320x200, scale 2x with image-rendering: pixelated
- Text area below canvas for output
- Input field at bottom for parser
- Retro font (use system monospace or embed a pixel font)
- Optional: simple beep sounds using Web Audio API
