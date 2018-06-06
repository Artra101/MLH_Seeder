This is a copy of etcipnja's Farmware MLH that I changed a bit to my needs for the farmbot I had to make for a school project.

# Problem:

When you have to deal with a lot of plants you might be puzzled that you have to create a dedicated sequence for each
instance of a plant. For exmaple: if you have 10 carrots - you probably need to create a planting sequence for every carrot
individually. 

# Solution:

The idea is to write a loop that executes needed sequences for each eligible plant.
- Apply filters to select plants to be treated       		(Example: Select all Carrots with status "planned")
- Execute initial sequence                                  MLH Mount Seeder
- For each plant:
    - Execute a sequence before moving to plant's location  (Example: "Grab a seed")
    - Move to plant's location
    - Execute a sequence at plant's location                MLH Plant
    - Update plant tags 	                                "planted"
- Execute end sequence                                      MLH Dismount Seeder

# Reference:

- FILTER BY PLANT NAME
    - Filter by plant names (comma separated) for example "Carrot, Beets", case insensitive, '*' means select all
- FILTER BY META DATA
    - Planned
- INIT SEQUENCE NAME
    - MLH Mount Seeder
- SEQUENCE NAME BEFORE NEXT MOVE
    - Sequence to be executed before the head moves to the plant (for every plant)
- SEQUENCE NAME AFTER MOVE
    - MLH Plant
- END SEQUENCE NAME
    - MLH Dismount Seeder
- SAVE IN META DATA
    - Planted
- DEFAULT Z AXIS VALUE WHEN MOVING
    - 0
- WHAT TO DO
    - "test" to skip actual movements and sequences (but still update meta data)
    - OR "real" - for the real action


# Installation:

Use this manifest to register farmware
https://raw.githubusercontent.com/Artra101/MLH_Seeder/master/MLH/manifest.json

# Bugs:

I noticed that if you change a parameter in WebApplication/Farmware form - you need to place focus on some other
field before you click "RUN". Otherwise old value is  passed to farmware script even though the new value
is displayed in the form.


# Credits:

The original idea belongs to @rdegosse with his Loop-Plants-With-Filters. https://github.com/rdegosse/Loop-Plants-With-Filters/blob/master/README.md This Farmware - is a simplified version of it.


