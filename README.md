# EscapeRoom
var readlineSync = require('readline-sync');

var playerName = readlineSync.question("What is your name?");
var welcomeMessage = `Welcome ${playerName}, to the Escape Room Game!`;
console.log(welcomeMessage);

//Boolean Flags
var isAlive = true;
var hasKey = false;

//Gaming Loop
while(isAlive == true){
    var menuOption = readlineSync.keyIn("Enter 1 to put hand in hole, or Enter 2 to find the key, or Enter 3 to open the door: ", {limit: '$<1-3>'});
    if (menuOption == 1){
    //Player has selected option 1 "Put hand in the hole" You have died, Game Over.
    console.log(`Sorry, ${playerName}, You put your hand in the hole, You have DIED, Game Over`);
    isAlive = false;
}
else if (menuOption == 2 && hasKey == false){
    //Player has selected option 2 "Find the key" You have successfully found the key.
    console.log(`Congratulations ${playerName}, You have found the key! Continue to the next menu option`);
    hasKey = true;
}
else if (menuOption == 2 && hasKey == true){
    //Player has selected option 2 "Find the key" but they have already found the key
    console.log(`You found the key already! You should not waste time ${playerName}, Hurry to the next menu option!`);
}
else if (menuOption == 3 && hasKey == false){
    //Player has selected option 3 "Open the door" but has no key
    console.log(`Your attempt to open the door ${playerName} has failed, you must find the key first!`);
}
else if (menuOption == 3 && hasKey == true){
    //Player has selected option 3 "Open the door" and the door has succesfully opened with the key
    console.log(`Good work ${playerName}, you have unlocked to door with the key and have successfully escaped!`);
    isAlive = true;
}
}
