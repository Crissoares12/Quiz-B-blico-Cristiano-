# Quiz-B-blico-Cristiano-
var game = {

initialize: function(){

this.game canvas = document.createElement("canvas");

this.game canvas.width = 480;

this.game canvas.height = 320;

this.game context = this.game canvas.getContext("2d");



this.game board = [];

this.game pieces = [];

this.game currentPlayer = "white";

this.game blackPawns = [];

this.game whitePawns = [];

this.game timer = 0;

},

handleInput: function(){

var input = document.getElementById("input");

var key = input.value;

switch(key){

case "left":

this.game board[0] = this.game board[0] - 1;

break;

case "right":

this.game board[0] = this.game board[0] + 1;

break;

case "up":

this.game board[1] = this.game board[1] - 1;

break;

case "down":

this.game board[1] = this.game board[1] + 1;

break;

}

},

checkWin: function(){

var isWin = false;

for(var i = 0; i < 4; i++){

if(this.game board[i] == 8){

isWin = true;

break;

}

}

return isWin;

},

update: function(){

this.game timer++;

if(this.game timer > 30){

this.game timer = 0;

}

this.game board[0] = this.game board[0] + (this.game input.left * -1);

this.game board[1] = this.game board[1] + (this.game input.up * -1);

var isBlack = (this.game board[0] == 0 && this.game board[1] == 0);

var isWhite = (this.game board[0] == 7 && this.game board[1] == 7);

if(isBlack){

this.game blackPawns.push(new Pawn(this.game board[0], this.game board[1]));

}

else if(isWhite){

this.game whitePawns.push(new Pawn(this.game board[0], this.game board[1]));

}

},

draw: function(){

var context = this.game context;

context.clearRect(0, 0, this.game canvas.width, this.game canvas.height);

context.strokeStyle = "black";

context.lineWidth = 2;

context.strokeRect(0, 0, this.game canvas.width, this.game canvas.height);

context.fillStyle = "white";

context.fillRect(0, 0, this.game canvas.width, this.game canvas.height);

}

};

game.initialize();

game.handleInput();

game.checkWin();

game.update();

game.draw();
