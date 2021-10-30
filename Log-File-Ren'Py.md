# Ren'Py Notes
## Asset Management
All assets should be lower case
Example: 
	
	caesar happy
	marcus sad
	bg pompeii street

## Tool Commands
*Auto Reload can be used to make a running game reload after modifying a script file*
	Shift + R

*Command Console for experiments*
	Shift + O
	
*Developer Menu*
	Shift + D

*Live Director Provides a Scripting GUI that streamlines the functions detailed below*'
	D
	
*Lint command is a debugger*

## Scripting

### Text
*A single string on a line by itself indicates the narrator with no character box*
		
		"Wow, It's really dark in here"

*Adding an addtional string before the dialogue will add a character text box*
   
   	"Eileen" "Examples will show up in a window like the one above. You'll need to click outside of the example window in order to advance the tutorial."

*Instead of typing in a character's name every time, a short-hand can be defined. Note: case-sensitive*

	define l = Character(_("Lucy"), color="#ffcccc")
 
 *Text Formating is designated through Bracer ex. {b} and closed with a slash {/b}*
 
 {b}bold{/b}, {i}italic{/i}, {s}struckthrough{/s}, {u}underlined{/u}, {a=https://www.renpy.org}link to a website{/a} , {a=jump:a_label}jump to a label{/a}, {alpha=.5}translucent{/alpha}, {cps=25}makes text type itself out slowly{/cps},  {cps=*2}doubling{/cps} or {cps=*0.5}halving{/cps} it, {font=DejaVuSans-Bold.ttf}DejaVuSans-Bold.ttf{/font},  {k=-.5}closer together{/k} or {k=.5}farther apart{/k},{size=+10}bigger{/size} or {size=-10}smaller{/size}, or set it to a {size=30}fixed size{/size}, {space=30} adds horizontal space in text.{vspace=30}
 
e "The p tag breaks a paragraph,{p}and waits for the player to click."

 e "If it is given a number as an argument,{p=1.5}it waits that many seconds."
 
 
 

### Starting a scene
	label start:

*scene- clears the screen and sets background*
    
	scene bg cave
*Calls Sprite assets on top of all other assets, replaces image with same tag*	
    
	show lucy happy

    l "Now that the lights are on, we don't have to worry about Grues anymore."
*Adding an **at** clause denotes postion (left righ center default)*
    
	show lucy mad at right
	show logo base at rightish *(user defined)* behind eileen
 
 *The Hide statement hides an object with a given tag*

    l "But what's the deal with me being in a cave? Eileen gets to be out in the sun, and I'm stuck here!"
 
 ### Positioning images
 
 *Aligned on the XY axis, with xalign 0.0 being left, 1.0 right*
     	
		show eileen happy:
        xalign 0.0
        yalign 1.0
 
 *Transforms can be defined, usually at initialization with characters*
 
	transform slightleft:
    xalign 0.25
    yalign 1.0
	
	
### Sounds
*play music replaces the current music with a filename. fadeout clause can be set*
      
	  play music "sunflower-slow-drag.ogg" fadeout 1
	  
*queue music is used to play after the end of a current song*
    
	queue music "sunflower-slow-drag.ogg"
	
*stop music can also take the fadeout clause*
     
	 stop music fadeout 1
 
 *play sound plays a oneshot sfx*
    
	play sound "tower_clock.ogg"
	
*queue sound ligns up sounds to play one after another*
 
 ### Choices and Pathing
 *The menu command calls a menu above the dialogue box*
     
	 menu:

*Choices are denoted by a Colon followed by a jump command to a specified label* 

        "Yes, I do.":
            jump choice1_yes
        "No, I don't.":
            jump choice1_no

    label choice1_yes:
	
*$ sets python code with the flag command, setting a flag that can be called with an if statement*

        $ menu_flag = True

        e "While creating a multi-path visual novel can be a bit more work, it can yield a unique experience."

        jump choice1_done

    label choice1_no:

        $ menu_flag = False

    if menu_flag:

        e "For example, I remember that you plan to use menus in your game."

    else:

        e "For example, I remember that you're planning to make a kinetic novel, without menus."
 
*Note: Menu statements can end with a colon and and indented say statement to use both menu and dialogue box*
 
 ### Input
 *Input is handled with python. Set variables are interpolated using square brackes*
    
	python:
        name = renpy.input(_("What's your name?"))

        name = name.strip() or __("Guy Shy")
		
	e "To interpolate a variable, write it in square brackets. Isn't that right, [name]?"
	
*Like character names, variable names can be defined by a shorthand*
 
 	define g = Character("[name]")
 
 *Other Variables and Flags*
 
     $ answer = 42
    $ flag = True

    e "Variable interpolation also works with other variables. Here, the answer is [answer] and the flag is [flag]."
 

 ### Videos
  *Images can be defined as a movie displayable and given position properties. Defined images can then be displayed using a show command, and hidden*
  
  	image launch = Movie(play="oa4_launch.webm", pos=(10, 10), anchor=(0, 0))
	
	show launch behind eileen
 
 	hide launch
	
*The python function can show cutscenes, until the end of the video or user click*

    $ renpy.movie_cutscene("oa4_launch.webm")
	

	
	

	
	
 

	


