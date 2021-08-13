# About
This is a simple tool that reads screenshots of the Treasure Hunter Monolith puzzle minigame Danganronpa V3, and exports a CSV file representing the board, automatically. It uses Python and OpenCV.

The output CSV can be used in other tools, for example, https://github.com/DanLeEpicMan/UpdatedMonolithSolver.

# How to install
- Install Python 3 (any recent version should work)
- Install OpenCV with `python -m pip install opencv-python`

# How to use
This is a command line tool. Use the `-h` flag to get the help message:
```
usage: thm2csv.py [-h] [-o OUT] image

Parse a Danganronpa V3 Treasure Hunter Monolith screenshot and output a CSV
file representing the board. For mean difficulty boards (22x11)

positional arguments:
  image              Screenshot file in 16:9 aspect ratio, without black bars
                     (jpg, png, bmp...)

optional arguments:
  -h, --help         show this help message and exit
  -o OUT, --out OUT  Output file name (default out.csv)

```

Example of usage:
```
python thm2csv.py 20210813162043_1.jpg
```

Example input image:
![20210813162043_1a](https://user-images.githubusercontent.com/9512554/129323743-68d0b02a-9fc8-4d71-8134-9acd0faa51e2.jpg)

Output:
```
4,4,1,4,4,3,1,4,2,3,4,4,4,4,3,2,4,3,4,3,2,4
3,4,1,1,1,4,3,1,4,3,3,2,4,3,2,4,4,4,2,3,3,2
3,2,2,1,4,3,3,2,1,4,1,2,1,3,1,3,2,2,1,1,1,3
2,3,2,3,2,2,1,2,3,1,2,1,2,1,2,1,3,1,2,1,1,4
4,4,3,1,4,4,2,4,4,4,2,2,2,4,4,1,2,1,4,4,4,3
3,4,2,3,3,4,3,3,3,3,4,4,4,3,4,2,4,4,3,2,2,3
4,2,3,2,2,3,2,1,1,1,2,3,3,1,1,3,3,2,2,1,2,1
1,1,2,1,1,1,2,1,2,1,3,1,2,2,1,3,3,3,1,1,1,4
4,4,2,4,4,1,2,1,4,4,2,1,1,4,2,3,4,2,3,3,4,4
2,1,1,3,2,3,3,1,3,1,2,3,3,2,2,4,4,1,1,2,2,3
1,2,3,3,4,3,2,4,3,2,4,1,3,4,1,1,3,1,2,4,1,2

```

# How it works
The tool computes the dominant color of each cell, compares it to the 4 colors, and outputs the closest color for each cell. If none of the colors are similar enough, it outputs 0. This makes the tool robust to screenshots in JPG.

The image is resized, so the tool should work with any resolution, as long as the screenshot is 16:9 and doesn't have black bars around it. It only works on the Mean difficulty (22x11 boards). You can adapt it for other difficulties by editing the script yourself.

# Can I use/modify/redistribute this?
Yes, feel free to! I'm releasing this under the MIT License.
