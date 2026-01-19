# First Reflection
## What I learned this week:
### Log entry 1 - Variables and Data Selection
//images
PImage wonderland, caterpillar, cheshire, alice, forest, rabbit, chair, mirror, drinkme, flowerbed, flower, cave;

//boolean variables
boolean gameOn = false;
boolean complete;
boolean stage1, stage2, stage3, stage4, stage5, stage6, stage7;
boolean cut1, cut2;
boolean gameOver;
boolean riddle;
boolean end;
boolean background;

//riddle string
String answer;

int posX, posY;

//buttons
int charPick = -10000;
int helpY = 300;
int helpSX, helpSY = -1000;
int startY = 200;
int buttonX = 820;
int closeX, closeY = -1000;
int charX, charY;

//drink randomizer
float drinkCheck, dC2, dC3;

//game function ints
int lives = 3;
int score = 0;

//character ints
int aliceX = 2;
int aliceY = 300;
int aliceSpeed = 25;

//location of drink
int drinkX = -1000;
int drinkY = -1000;

//throughout strings
String instructions = "";
String life = "Lives: " + lives;
String input = "";

//arrays
float[] objectX, objectY, randomSpeed;
float[] objectX2, objectY2, randomSpeed2;

float[] drinkXs;

Throughout my game I use boolean, int, String, float, and PImage variables. The boolean variables are mostly used to check when each part of my game is currently active to ensure that certain pieces of code are only running during that time. I use int variables to keep track of different numerical values such as lives or the score, as well as the speed of moving characters and the coordinates of objects and characters. My string variables are used to add text onto the screen while being able to change what the text says whenever it is necessary. I also use it in one stage of my game to compare an answer to the user input. Float variables are used whenever a random number is necessary. For example, when deciding the speed of the falling objects or for checking the drink me potions.

### Log entry 2 - Arrays
objectX = new float[]{random(0, 900), random(0, 1000), random(0, 1000)}; 

objectY = new float[]{height+100, height+100, height+100}; 

randomSpeed = new float[]{random(5, 10), random(5, 10), random(5, 10)};

objectX2 = new float[]{random(0, 1000), random(0, 1000), random(0, 1000)}; 
  
objectY2 = new float[]{height, height, height}; 

randomSpeed2 = new float[]{random(5, 10), random(5, 10), random(5, 10)};

On day 2 I focussed on creating the mini game with dodging objects while falling down a rabbit hole. This required using arrays to repeat an image and allow it to move individually. We used this in one of our previous assignments so I used similar code but made a few changes to match the theme of the game, therefore, instead of objects falling down, they were going up as the character falls down. An issue I came across was resetting the arrays after the user loses because when you press replay they continue falling from where you lost. I resolved this by redefining the arrays after resetting the level. See Log entry 5 for use.

### Log entry 3 - Selection Structure
if (mouseX>=drinkX&&mouseX<=drinkX+100&&mouseY>=drinkY&&mouseY<=mouseY+150) {
 if (drinkCheck == 1) {
          //poison
          lives--;

          //decrement lives
          life = "Lives: " + lives;

          //checks if lives are at 0
          if (lives<=0) {
            //resets game
            stage2 = false;
            gameOver = true;
          }
        } else if (drinkCheck == 2) {
          //resizes to be bigger
          alice.resize(400, 400);
          image(alice, aliceX-200, aliceY-200);
        } else if (drinkCheck == 3) {
          //alice goes smaller
          alice.resize(100, 100);
          image(alice, aliceX, aliceY);
          stage4 = true;
          stage2 = false;
        }

For day 3 I worked on making the stages with the randomized drinks. The variable I use randomizes a number for the drink that is clicked and then the program uses selection structures (if and else statements) to check what the random number is. It then follows the code so that IF the number is 1 you lose a life, ELSE IF the number is 2, Alice gets bigger, and ELSE IF the number is 3 you move onto the next stage. I had issues with was that each statement did not work. If 2 was supposed to make the character larger, it would remove a life instead. To fix this, I rewrote the entirety of this code, being careful that there weren't any instances where it might result in the wrong thing happening. I think it had originally occurred because some of the if and else if statements were structured incorrectly.

### Log entry 4 - Custom functions and error checking
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

On day 4, I tried was using the keyPressed function to get the user to input a word. I did this by using keyPressed and setting a char variable to the key that was pressed. Then I added that to an empty string that was declared at the top so that when the draw function redrew it would add the typed in letter. I also used the back space function to remove the string and ensured that the background was drawn over it in void draw so that it wouldn't remain there. I used the CODED key check to ensure that the letters being inputted were actual letters and not keys such as ALT, CTRL, and ENTER which shows error checking. I had struggled with the backspace function because it would only temporarily remove the string but I realized that was happening because the background wasn't drawing over the text. I fixed this by adding a function that draws the background when you press backspace, and then after it has done that it stops redrawing the background until you press backspace again so that the string can be seen.

void startGame() {
  //sets lives as 3
  lives = 3;
  //makes cut1 true and sets alice's position
  cut1 = true;
  int aliceX = 2;
  int aliceY = 300;
  //draw background
  background(forest);
  text(life, 100, 100);
  //draw images
  image(alice, aliceX, aliceY);
  image(rabbit, 450, 300);

  //set instructions

  instructions = "You follow the white rabbit down the rabbit hole. Press enter to continue.";

  fill(255);
  text(instructions, 100, 50);
}
This is also one of the methods I created for my game. It is for the homescreen which involved all the set up of the game. Lives is set to 3 and it provides context for the user so that they know what is going on in the game. It also draws the characters and background to show what is happening and putting them at the correct coordinates.

### Log entry 5 - Repetition structure
 //goes through loop for each object in array
    for (int i = 0; i<objectY.length; i++) {
      image(chair, objectX[i], objectY[i]);
      //decrements speed from Y
      objectY[i] = objectY[i] - randomSpeed[i];

      image(mirror, objectX2[i], objectY2[i]);
      objectY2[i] = objectY2[i] - randomSpeed2[i];

      //checks when object goes below 0
      if (objectY[i]<-100) {
        //reset position
        objectY[i] = height + 200;

        //randomizes X and speed
        objectX[i] = random(0, 900);


        randomSpeed[i] = random(5, 10);

        //increments score
        score++;

For repetition structure I used a for loop to go through my arrays for my objects and I have each one fall at a random X coordinate and at a random speed. I use this to create the first stage and have the illusion of the character falling down the rabbit hole while different objects move up which you need to avoid. The loop also helps to reset the position of objects that have reached the top of the canvas. Because they are all falling at random speeds they will reach the top at different times, therefore, you cannot reset all the positions, and instead you must use the loop to pick out the particular object using [i]. I came across a few issues with having the objects fall from different positions each time. The loop worked fine, however, the objects would fall from the same 3 X intercepts instead of randomizing after each loop. To fix this I went through my code and realized that the reason this was happening was because the function was not being recalled in the draw function.



## Topic(s):
The topic for our culminating was to create an original game using skills we have learned in class. I decided to make a Wonderland themed escape game where you play different mini games. I started by making an overal plan but I did not end up using all of the stages and methods I had planned due to lack of time and because I was working alone. I started by using a similar code to the Unit 4 project but with the objects moving upwards to show the idea of falling down a rabbit hole. Then I used a randomizer and mousePressed function to create drinks that either let you proceed, remove a life, or make you grow bigger. I also used the key pressed function to move the character with constraints and to take a user's input for the riddle and compare it to the actual answer.

## What I struggled with:
I struggled with finishing in time since I had orignally created a bigger plan but because I was working alone and there was a time limit, I was not able to entirely execute it. I also struggled with creating the random drinks and using the backspace to delete the user input. I also struggled with having my code function properly based on each stage, since some had to be false in order for the next stage to run properly.

## What I’m proud of:
I am proud of being able to figure out the backspace deletion by redrawing the background since it made the game more user friendly. I am also proud of the overall idea since I think it is an original idea with an engaging theme. I also think I used a lot of the things that we learned in class to produce this game and that it showcases my learning very well.

## Next steps:
Next steps would be to add in the methods and stages I had taken out to make the game last longer and also to improve stage one. Since the character is leaning towards the right the lives do not decrement properly with the information I added to check the collision. I could also figure out new functions to make my game more entertaining and have more skill involved in the gameplay.
