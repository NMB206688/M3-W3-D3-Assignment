# M3-W3-D3-Assignment
Sure! Here's a sample `README.md` file that explains the project, setup instructions, and how to run the code.

### `README.md`

```markdown
# PacMan Motion Lab

This project involves creating and moving PacMan characters across the screen using JavaScript. The objective is to make the PacMan characters appear at random positions and move with random velocities, bouncing off the edges of the screen.

## Project Structure

- `index.html`: The main HTML file that sets up the buttons and links the JavaScript file.
- `pacmen.js`: The JavaScript file that contains the logic for creating and moving the PacMan characters.
- `images/`: The directory containing the images used for the PacMan characters.

## Setup Instructions

1. **Clone the Repository**:
    ```sh
    git clone https://github.com/yourusername/m3-w3-d3-assignment.git
    cd m3-w3-d3-assignment
    ```

2. **Download `pacman.zip`**:
    Download the file `pacman.zip` from GAP Week 3 Day 3, unzip it, and move the content into the cloned folder.

3. **Open in VS Code**:
    Open the project folder in Visual Studio Code.

## How to Run

1. **Open `index.html`**:
    Open the `index.html` file in your browser.

2. **Add PacMan**:
    Click the "Add PacMan" button to add a new PacMan character at a random position on the screen.

3. **Start Game**:
    Click the "Start Game" button to start moving all the PacMan characters across the screen.

## Functionality

### `makePac`

This function creates a new PacMan character with a random position and velocity, and adds it to the game area.

```javascript
function makePac() {
  let velocity = setToRandom(10);
  let position = setToRandom(200);

  let game = document.getElementById('game');
  let newimg = document.createElement('img');
  newimg.style.position = 'absolute';
  newimg.src = './images/PacMan1.png'; // Change the source to an animated PacMan gif or different images
  newimg.width = 100;

  newimg.style.left = position.x + 'px';
  newimg.style.top = position.y + 'px';

  game.appendChild(newimg);

  return {
    position,
    velocity,
    newimg,
  };
}
```

### `update`

This function updates the position of each PacMan character in the `pacMen` array and handles collisions with the window edges.

```javascript
function update() {
  pacMen.forEach((item) => {
    checkCollisions(item);
    item.position.x += item.velocity.x;
    item.position.y += item.velocity.y;

    item.newimg.style.left = item.position.x + 'px';
    item.newimg.style.top = item.position.y + 'px';
  });
  setTimeout(update, 20);
}
```

### `checkCollisions`

This function checks if a PacMan character hits the edges of the window and reverses its velocity to make it bounce back.

```javascript
function checkCollisions(item) {
  if (item.position.x + item.velocity.x + item.newimg.width > window.innerWidth || item.position.x + item.velocity.x < 0) {
    item.velocity.x = -item.velocity.x;
  }
  if (item.position.y + item.velocity.y + item.newimg.height > window.innerHeight || item.position.y + item.velocity.y < 0) {
    item.velocity.y = -item.velocity.y;
  }
}
```

### `makeOne`

This function adds a new PacMan character to the `pacMen` array by calling `makePac`.

```javascript
function makeOne() {
  pacMen.push(makePac());
}
```

## Submission

Post the GitHub URL link in the dropbox at GAP Week 3 Day 3 Assignment by Sunday 10.30PM PT.

## License

This project is licensed under the MIT License.
```

This `README.md` file provides a comprehensive overview of the project, including setup instructions, a brief explanation of the main functions, and how to run the code. You can modify it as needed based on your specific project details.