# Notes

1. Setup the array of dipoles using any 2 shapes (a square is easiest). Set the values of each index to either 1 or -1. Split evenly using `Math.random() > 0.5`.
2. Show the initial display.
2. Set the temperature between 0.01 and 10.00.
3. Execute Monte Carlo Steps:
  1. Choose a random site (assign `i` and `j` to a random index)
  2. Calculate the energy change from potential flip.
    1. Find lattice site to the top, bottom, left, and right of current site.
    2. energy is `2 * currentLatticeEnergy * (sum of nearest neighbor energies)`
  3. If the change in energy will be lowered by making the potential flip, then make it.
  4. If the `Math.random() < Math.exp(-changeInEnergy/temp)` then it overcomes the odds and makes the flip anyway.
  5. Repeat 1-4 so many times.
4. Display the data.
5. Repeat step 3.

```javascript
  var canvas = document.getElementById("canvas");
  var context = canvas.getContext('2d');
  var image = context.createImageData(canvas.width, canvas.height);
  var size = 100; // dimensions of lattice ( 100 x 100 )
  var squareWidth = canvas.width / size;

  var r, g, b;
  if (dipoles[i][j] === 1) {
    r = 0;
    g = 0;
    b = 255;
  } else {
    r = 255;
    g = 255;
    b = 0;
  }

  // Need to do this for all pixels within a square that represents the given lattice site.
  // Use image.data[index] = r
  // Use image.data[index + 1] = g
  // Use image.data[index + 2] = b

```
