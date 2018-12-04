---
layout: post
title: "SVG by Hand and by Code"
date: 2018-06-30 10:30
comments: false
categories:
---

This post is an attempt to walk through programattic generation of
SVG files, step by step.

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

 1. Skim the SVG tutorial at [W3 Schools SVG
    Tutorial](https://www.w3schools.com/graphics/svg_intro.asp)
 2. By hand, using the Kate editor, create an SVG document with three concentric
    circles, colored as a bullseye.

### Ex 3

 1. Create an SVG document that uses a path tag and the "h" and "v" commands to
    draw a square.
 2. Put the path in a group tag. Use the group tag to rotate the square into a
    diamond. Hint: look at the docs for the "transform" attribute.

# Part 2: SVG By Code

Prereqs: Kate Editor; Ruby w/ Nokogiri

```
$ sudo apt install ruby ruby-nokogiri kate
```

## Ruby Review

Here's a Ruby tutorial: [CodeCademy
Ruby](https://www.codecademy.com/catalog/language/ruby)

Go through the first 4 lessons of the "Learn Ruby" course.

### Quick Re-Review

Start the interactive ruby shell:

```
$ irb
irb> 
```

Try these commands and see what happens:

```
irb> text = "the quick brown fox"
irb> text
irb> words_array = text.split(/\s+/)
irb> words_array
irb> array2 = words_array.reverse
irb> array2
irb> array2.join(" + ")
irb> "word".upcase
irb> array3 = words_array.map {|w| w.upcase }
irb> array3
```

## Handling XML

XML describes a tree of tags. Take a look at the [diagram
here](https://www.w3schools.com/xml/xml_tree.asp).

Nokogiri is a library for writing Ruby programs to manipulate
XML documents.


Try this:

```
irb> require 'nokogiri'
irb> doc = Nokogiri::XML("<svg/>")
irb> root = doc.xpath("//svg")[0]
irb> circ = Nokogiri::XML::Node.new("circle", doc)
irb> circ["cx"] = 50
irb> circ["cy"] = 50; circ["r"] = 20
irb> circ
irb> root.add_child(circ)
irb> doc
irb> puts doc.to_xml
```

Now consider this program:

```
#!/usr/bin/env ruby

require 'nokogiri'

def add_node(parent, name, attrs)
  node = Nokogiri::XML::Node.new(name, parent.document)
  attrs.each do |kk,vv|
    node[kk.to_s] = vv.to_s
  end
  parent.add_child(node)
  node
end

doc = Nokogiri::XML('<svg width="100" height="100" />')
root = doc.xpath("//svg")[0]

group = add_node(root, "g", { transform: "translate(10 10)" })

20.times do |ii|
  x = 10 + 10 * (ii % 5)
  y = 10 + 10 * (ii / 5)
  add_node(group, "circle", { cx: x, cy: y, r: 5 })
end

puts doc.to_xml
```

Paste the above into Kate and save as "grid.rb". Then, in a terminal in the same
directory:

```
$ ruby grid.rb
$ ruby grid.rb > grid.svg
```

Then open grid.svg in Inkscape to see what you got.

### Ex 1

Modify grid.rb to draw a bullseye with N rings, where N
is a variable that can be changed.

## More stuff

Here are the official [Nokogiri Tutorials](http://www.nokogiri.org/).

