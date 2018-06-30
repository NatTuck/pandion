---
layout: post
title: "SVG by Hand and by Code"
date: 2018-06-30 15:30
comments: false
categories:
---

# Part 1: SVG By Hand

Prereq: Kate Editor

```
$ sudo apt install kate
```

Simple SVG document:

```
<?xml version="1.0" encoding="UTF-8"?> 
<svg width="100" height="100">
  <circle cx="50" cy="50" r="20" />
</svg>
```

## Exercises

### Ex 1
 
 1. Paste the above document into Kate.
 2. Save it as "circle.svg"
 3. Open it in Inkscape and Firefox to confirm that it's reasonable.

### Ex 2

 1. Skim the SVG tutorial at https://www.w3schools.com/graphics/svg_intro.asp
 2. Create an SVG document with three concentric circles, colored as a bullseye.

### Ex 3

 1. Create an SVG document that uses a path tag and the "h" and "v" commands
    to draw a square.
 2. Put the path in a group tag. Use the group tag to rotate the square into
    a diamond.

# Part 2: SVG By Code

Prereqs: Kate Editor; Ruby w/ Nokogiri

```
$ sudo apt install ruby ruby-nokogiri kate
```

## TODO: Finish this section.

