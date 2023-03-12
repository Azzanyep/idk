// create the game canvas
var canvas = document.getElementById('gameCanvas');
var context = canvas.getContext('2d');

// set the canvas dimensions
canvas.width = 800;
canvas.height = 600;

// define the player and the objects
var player = {
    x: canvas.width / 2,
    y: canvas.height - 20,
    width: 50,
    height: 50,
    speed: 10
};
var objects = [];

// define the object generator
function generateObject() {
    var object = {
        x: Math.random() * canvas.width,
        y: 0,
        width: 50,
        height: 50,
        speed: 5
    };
    objects.push(object);
}

// define the game loop
function gameLoop() {
    // clear the canvas
    context.clearRect(0, 0, canvas.width, canvas.height);

    // draw the player
    context.fillStyle = 'blue';
    context.fillRect(player.x - player.width / 2, player.y - player.height / 2, player.width, player.height);

    // move the objects
    for (var i = 0; i < objects.length; i++) {
        objects[i].y += objects[i].speed;
        // remove the object if it falls off the screen
        if (objects[i].y > canvas.height) {
            objects.splice(i, 1);
            i--;
        }
    }

    // draw the objects
    context.fillStyle = 'red';
    for (var i = 0; i < objects.length; i++) {
        context.fillRect(objects[i].x - objects[i].width / 2, objects[i].y - objects[i].height / 2, objects[i].width, objects[i].height);
    }

    // check for collisions
    for (var i = 0; i < objects.length; i++) {
        if (Math.abs(objects[i].x - player.x) < (objects[i].width + player.width) / 2 && Math.abs(objects[i].y - player.y) < (objects[i].height + player.height) / 2) {
            objects.splice(i, 1);
            i--;
        }
    }

    // handle player movement
    if (keys[37]) { // left arrow
        player.x -= player.speed;
    }
    if (keys[39]) { // right arrow
        player.x += player.speed;
    }

    // generate new objects randomly
    if (Math.random() < 0.02) {
        generateObject();
    }

    // request the next frame
    requestAnimationFrame(gameLoop);
}

// handle key events
var keys = {};
window.addEventListener('keydown', function(event) {
    keys[event.keyCode] = true;
});
window.addEventListener('keyup', function(event) {
    delete keys[event.keyCode];
});

// start the game loop
gameLoop();
