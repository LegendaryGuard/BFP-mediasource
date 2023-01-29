File: BFPQ3_Tools_Readme.txt
__________________________________________________________________________________________________
# BFP Tools / Bid For Power animation helpers
__________________________________________________________________________________________________

For more info or tutorials please check www.rodneyolmos.com or email rodney@rodneyolmos.com

This are provided "as is" I'm not responsible for anything that it may cause to your computer, not that it will, but have to say that just in case =).

The same `bfpq3.bip` will allow you to export to either quake3 or bidforpower, but you will need to use either `animationq3.cfg` for quake3 and `animationbfp.cfg` for bidforpower.


Files Included in this Zip:
- `BFPQ3_Tools_Readme.txt`: the file you are reading now (last modified: 23/05/2002 2:06)
- `BFPQ3-tagimporter.max`: max file that has tags needed for the quake3 engine and bidforpower (last modified: 16/05/2002 17:14)
- `BFPQ3.bip`: contains animation segments for the characters (last modified: 17/05/2002 8:42)
- `animationBFP.cfg`: contains the `animation.cfg` you need to use under bidforpower (last modified: 17/05/2002 8:29)
- `animationq3.cfg`: contains the `animation.cfg` you need to use under quake3 (last modified: 13/10/2001 8:35)

__________________________________________________________________________________________________

#### Requirements

- You will need 3dstudio max
- Character Studio
- Md3 exporter
- You will need to know how to create pk3 files
- Additional tools that you will need would be an md3 exporter for max to be able to export geometry out of max into the quake3 engine. You could find this at www.polycount.com under their resources section. The one I use is the Pop n Plugz md3 exporter, you can also find this at my website

___________________________________________________________________________________________________
__________________________________________________________________________________________________
#### Usage of bip and tags - `bfpq3-tagimporter.max` / `bfpq3.bip`


This assumes that you've got some understanding of 3dsmax and character Studio, and that you know how to export md3's out of 3dstudio max (if not please go to www.polycount.com for some resources and tutorials or hopefully soon I will have some tutorials made at my site) this also assumes that you already have physique assigned to your character,and that all that it needs, is the bip animation file and the tags.

- Inside of 3dsmax open the character you been working on.
- Set the Time frame to 20 frames a sec. (you can right click on the litle key where the play button is at)
- Merge the `BFPQ3-tagimporter.max` file into your scene. (under pulldown menu file/merge)
- Align the `tag_*` objects to their correct spots (use the move tool i wouldn't rotate them)
- Link the tags to the bip model not! the geometry
	* link `tag_head` to your head 
	* link `tag_eyes` to your head
	* link `tag_left` to your left wrist
	* link `tag_right` to your right wrist
	* link `tag_weapon` to your right wrist
	* link `tag_torso` to your pelvis
	* leave `tag_floor` alone for now
the tags already contain animations which will make the torso animate positioned correctly.
- select one of your bip models (arm,leg,head,et) and load the `bipq3.bip` file into your biped model. 
(this is located on your motion panel)
- go to frame 475 and adjust your tag_weapon, so that quake3 knows what the alignment of it is. (reference for weapon:based on its local pivot, z is up, x is forward and y should aim to the left of the character)
- Also at frame 475 move the tag_floor object to the bottom sole of your character's feet.
- thats it! you are ready to export.
 
#### Notes #####

Make sure that you have "In place mode" turned on under your character studio bip settings. 
_______________________________________________________________________________________________________
_______________________________________________________________________________________________________
### Usage of the Animation.cfg files - `animationq3.cfg` / `animationbfp.cfg` 

#### for quake3

- Use the animation set of `animationq3.cfg`
- put the `animactionq3.cfg` into your `models/players/yourcharacter/` folder and rename it to `animation.cfg`
- inside the `animation.cfg` you will be able to change some segments of animation to other ones.

 example: change the jump animation from "1 leg up" to "2 rolls forward" by copy pasting, like this
```
354	3	0	20		// LEGS_JUMP  (1 leg up)         <----paste here on top of it
//alternative jumps forward
//354	3	0	20		// LEGS_JUMP  (1 leg up)        
//358	15	0	20		// LEGS_JUMP  (2 rolls forward)  <----copy this
  ^-----------------from here---------------to here-------------------^
```
Result:
```
358	15	0	20		// LEGS_JUMP  (2 rolls forward)
//alternative jumps forward
//354	3	0	20		// LEGS_JUMP  (1 leg up)        
//358	15	0	20		// LEGS_JUMP  (2 rolls forward)  
```
#### for Bid For Power

- same as above but use `animationbfp.cfg`
- for some of the attacks you might need to copy paste more segments of animations.

example:
```
575	4	0	20		// TORSO_ATTACK14_PREPARE	(controlled sphere attack) 	<-you need this
579	9	0	40		// TORSO_ATTACK14_STRIKE					<-and this 
```
### Notes ####

If you want to add more attack animations to your character, you will need to add more animations to the end of the bip file, make sure that you don't rotate the pelvis because it will cause the characte to aim somewhere else or lean to the side. 
Make sure you save your bip file b4 closing max, and last add your new attacks to the `animation.cfg` list

You can use notepad or wordpad to see the *.cfg files
