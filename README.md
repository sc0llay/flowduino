# Flowduino

A visual block editor for Arduino sketches, for macOS. Build a sketch by
dragging blocks onto a canvas and wiring them together; Flowduino generates
real, readable Arduino C++ as you work, then compiles and uploads it to a
board.

This repository distributes the **compiled application only**. There is no
source code here.

## Download

**[Flowduino-1.0-macOS.zip](../../raw/main/Flowduino-1.0-macOS.zip)** — 4.1 MB,
universal binary (Apple Silicon and Intel), macOS 14 Sonoma or later.

Unzip it, drag `Flowduino.app` to your Applications folder, and read
[READ ME FIRST.txt](READ%20ME%20FIRST.txt) — in particular the note on opening
it the first time, because the app is not yet signed with a paid Apple
Developer certificate and macOS will refuse to launch it until you approve it
once in System Settings ▸ Privacy & Security.

## How it works

Two axes carry two different meanings, which is what keeps a large sketch
legible:

- **Vertical wires are control flow.** They set the order statements execute
  in. Chevrons on a block's top and bottom edges chain one statement to the
  next; chevrons on the right edge open a nested body, such as the inside of
  an `if` or a `for`.
- **Horizontal wires are data flow.** They carry typed values left to right
  into a block's inputs. Any input left unwired is edited inline on the block
  itself, so a simple sketch needs very few wires.

Each entry point — `setup()`, `loop()`, and any function you add — gets a tab
of its own across the top of the canvas, showing exactly the blocks that
compile into that function.

## What it does

- **A categorised block library** covering digital and analog I/O, timing,
  control flow, math, logic, strings, arrays, structs, serial, interrupts,
  EEPROM, servo, I²C and SPI, with search across names, summaries and keywords.
- **Live code generation.** The generated `.ino` sits in a panel below the
  canvas and updates as you edit. Clicking a line of code selects the block
  that produced it.
- **Compile and upload** to any board the Arduino CLI knows about, with
  compiler errors mapped back onto the blocks that caused them. Boards and
  libraries are installed from inside the app.
- **Import an existing sketch.** Point it at an `.ino` file and it parses the
  C++, rebuilds the control flow as blocks and wires, and lays the result out.
- **Serial monitor and plotter**, with named channels and per-channel display
  modes.
- **A canvas built for real sketches** — pan and zoom, grid snapping,
  collapsible blocks, marquee selection, hand-routed wires, and one-key
  commands to tidy the whole layout or align it to the grid.
- **Arrays, 2D grids and structs** as first-class values, drawn on the block so
  you can see their contents without opening anything.
- **Comments** that show their own text on the canvas, emitted as `//` or
  `/* … */` in the generated sketch.

## Compiling and uploading needs the Arduino CLI

Everything above — placing and wiring blocks, editing values, watching the
generated C++, saving and opening `.flowduino` documents, importing a sketch —
works with nothing else installed.

Compiling and uploading are the two exceptions. They need the
[Arduino CLI](https://arduino.github.io/arduino-cli/), which is deliberately
not bundled here. The first time you press Compile or Upload, Flowduino offers
to walk you through installing it. No Homebrew required.

## Status

Flowduino is not notarized yet; that follows an Apple Developer account. Until
then macOS treats it as an unidentified developer and you approve it once by
hand, as described in `READ ME FIRST.txt`.
