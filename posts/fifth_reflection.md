# First Reflection
## What I learned this week:
### Log entry 1

  	while (gameOn == false) {
    if (mouseX>=820 && mouseX<=980 && mouseY>=200 && mouseY<=240) {
  			    gameOn = true;
 			     charPick = 100;
    }
    if (mouseX>=820 && mouseX<=980 && mouseY>=300 && mouseY<=340) {
  			    helpScreen();
 			   }
   		 if (mouseX>=helpSX && mouseX<= helpSX+20 && mouseY>= helpSY &&  mouseY<= helpSY +20) {
     			 helpSX = -10000;
 			     helpSY = -1000;
    
 			   }
  }



During the first day I focussed on figuring out the logic of the startup of the game, including the help screen. I mainly used the mousePressed() function to assign different methods to different buttons. When someone presses start game it calls the first method, which is an explanation for the storyline of the game. When someone clicks on the help button, it opens up a separate screen which provides them with general instructions for the game. I assigned variables for the button’s X and Y coordinates to ensure that it is not being used throughout, and only when the button is at that location.

### Log entry 2
objectX = new float[]{random(0, 900), random(0, 1000), random(0, 1000)}; 

objectY = new float[]{height+100, height+100, height+100}; 

randomSpeed = new float[]{random(5, 10), random(5, 10), random(5, 10)};

objectX2 = new float[]{random(0, 1000), random(0, 1000), random(0, 1000)}; 
  
objectY2 = new float[]{height, height, height}; 

randomSpeed2 = new float[]{random(5, 10), random(5, 10), random(5, 10)};

On day 2 I focussed on creating the mini game with dodging objects while falling down a rabbit hole. This required using arrays to repeat an image and allow it to move individually. We used this in one of our previous assignments so I used similar code but made a few changes to match the theme of the game, therefore, instead of objects falling down, they were going up as the character falls down. 

for (int i = 0; i<objectY.length; i++) {
      image(chair, objectX[i], objectY[i]);
      objectY[i] = objectY[i] - randomSpeed[i];

      image(mirror, objectX2[i], objectY2[i]);
      objectY2[i] = objectY2[i] - randomSpeed2[i];

      if (objectY[i]<-100) {
       	objectY[i] = height;
           	score++;
      }

      if (objectY2[i]<-100) {
        objectY2[i] = height;
        score++;
      }
    }
    
if (score>20)
    {
      stage2 = true;
    }

I also worked on the code to actually make the objects fall, which was also included in the previous assignment. You can see that when using speed I ensure that I decrement so that it gives the impression that the objects are moving upward, or that the player is moving down. I use a score to give a certain amount of time before the next method is called which allows the player to play without switching too fast, but also does not become endless.

### Log entry 3
if (mouseX>=drinkX&&mouseX<=drinkX+100&&mouseY>=drinkY&&mouseY<=mouseY+150) {
    drinkCheck = int(random(1, 3));
    print(drinkCheck);
    cut2 = true;

    if (drinkCheck == 1) {
      lives--;
      println("game over");
    } else if (drinkCheck == 2) {
      alice.resize(750, 520);
      image(alice, aliceX, aliceY);

For day 3 I worked on making the stages with the randomized drinks. I need to work on debugging because it causes a couple errors which can be improved by changing how my variables are used and making the code shorter and less messy to find errors more easily. This is used in the game to randomize whether the drinks move you onto the next stage, cause you to lose a life, or change the size of the character. This is done by assigning a random number to each of the drinks and then creating methods for each number so that those methods will occur based on the random selection of the user.

### Log entry 4
  if (riddle == true) {
    //checks which key is pressed and changes it to a char variable
    
    if(key == BACKSPACE){
      background = true;
      return;
      
    }
    if (key == CODED){
      return;
    }
    
    if(key != CODED){
      posX= 100;
    posY = 300;
    char c = Character.toLowerCase(key);
    
    //changes use input string based on letters inputed
    input = input + c;
    text(input, posX, posY);

    }
    


  }

On day 4, I focused on the stage with the Drink Me potions, which mainly involved the mousePressed function, randomized variables, and if and else statements. Something new I tried was using the keyPressed function to get the user to input a word. I did this by using keyPressed and setting a char variable to the key that was pressed. Then I added that to an empty string that was declared at the top so that when the draw function redrew it would add the typed in letter. I also used the back space function to remove the string and ensured that the background was drawn over it in void draw so that it wouldn't remain there.



## Topic(s):
The topic for our culminating was to create an original game using skills we have learned in class. I decided to make a Wonderland themed escape game where you play different mini games. I started by making an overal plan but I did not end up using all of the stages and methods I had planned due to lack of time and because I was working alone. I started by using a similar code to the Unit 4 project but with the objects moving upwards to show the idea of falling down a rabbit hole. Then I used a randomizer and mousePressed function to create drinks that either let you proceed, remove a life, or make you grow bigger. I also used the key pressed function to move the character with constraints and to take a user's input for the riddle and compare it to the actual answer.

## What I struggled with:
I struggled with finishing in time since I had orignally created a bigger plan but because I was working alone and there was a time limit, I was not able to entirely execute it. I also struggled with creating the random drinks and using the backspace to delete the user input. 

## What I’m proud of:
I am proud of being able to figure out the backspace deletion by redrawing the background since it made the game more user friendly. I am also proud of the overall idea since I think it is an original idea with an engaging theme. 
## Next steps:
Next steps would be to add in the methods and stages I had taken out to make the game last longer and also to improve stage one. Since the character is leaning towards the right the lives do not decrement properly with the information I added to check the collision.
