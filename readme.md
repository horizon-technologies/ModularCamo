# ModularCamoChipV2
A chip for dynamically applying camoflage to contraptions

# Usage
- **Make sure to put the `camodata.txt` file under `data/sf_filedata/`**
- Instructions should be found in the chip, but we included them here.
- Spawn the chip wherever you like, but we recommend parenting it to your baseplate / wireplate.
- Wire the `Base` input to your baseplate
- You can interact with the chip through chat commands
    - Camo Misc Commands
        - Use `!camos` to print all the available camos you can use
        - Use `!camo <name>` to set your tank to a given camo
    - Camo Modification Commands
        - Use `!editcamo <name>` to spawn props representing the provided camo or a "blank" slate if none exists
        - Use `!savecamo <name>` to save a the colors from the spawned props to your camodata file
        - Use `!removecamo <name>` to remove a camo from your camo data file

# Modifying Camos
- Camos can be modified in two ways:
    - Modifying via the chip in game (The easier and recommended way)
        - Once your chip is spawned and wired, you can use the `!editcamo <name>` command, which will spawn down blocks, in the order defined by `ColorReadOrder`.
            - If you specified an existing camo name, it will load the appropriate colors/materials to each block, based on said camo scheme.
            - Apply a color/material to each block, in the order defined by above (by default it should be `Primary`, `Secondary`, `Tertiary`, `Glass`, `Wheel` from left to right).
        - Using `!savecamo <name>`, you can save the template blocks as a new camo. You can see these changes by trying `!camos`
    - Modifying directly from file (Understanding of json would be very helpful)
        - Inside your `data/sf_filedata/camodata.txt` file, you should see the following structure (may not be the exact same):
            ```json
            {
                "digital2": {
                    "Glass": "0,0,0,72|models/shiny",
                    "Secondary": "56,41,48,255|sprops/textures/sprops_metal5",
                    "Primary": "54,59,53,255|sprops/textures/sprops_metal5",
                    "Wheel": "109,109,109,255|sprops/textures/sprops_metal5",
                    "Tertiary": "199,174,108,255|sprops/textures/sprops_metal5"
                },
                "reset": {
                    "Glass": "0,255,255,255|sprops/sprops_grid_orange_12x12",
                    "Secondary": "0,255,0,255|sprops/sprops_grid_orange_12x12",
                    "Primary": "255,0,0,255|sprops/sprops_grid_orange_12x12",
                    "Wheel": "255,93,0,255|sprops/sprops_grid_orange_12x12",
                    "Tertiary": "182,182,182,255|sprops/sprops_grid_orange_12x12"
                }
            }          
            ```
            - In this case, `digital2` and `reset` are the names of camoflages.
            - `Primary`, `Secondary`, `Tertiary`, `Glass`, `Wheel` are the definitions of a camo's color scheme. 
                - They each have a string of the form `r,g,b,a|mat` where 
                    - `r`, `g`, `b`, `a` are the red, green, blue and alpha values of the color
                    - `mat` is the path to the material.
                - You can modify camos this way, or you can add/remove camos (just make sure to keep the JSON structure valid)

# Status
- Hopefully finished

# Notes:
- This project will not autoupdate your SF chips from it. If you desire a newer version, please download the new file.