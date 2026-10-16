# Photon War 

A competitive two-player sci-fi themed digital logic mini-game built entirely using TTL integrated circuits (74LS series) on breadboards as part of the **EEE231 Digital Electronics Laboratory** mini project at Universiti Sains Malaysia (USM)

---

## Game Rules & Mechanics

1. **Setup & Reset:** 
   - Press the **Restart** button to load the initial preset values, returning all active green "Photons" to the exact center (position 7) of each lane.
2. **Interface & Controls:**
   - The game features **3 concurrent lanes**, each consisting of 15 common-anode RGB LEDs.
   - **Player Red** uses red control buttons; **Player Blue** uses blue control buttons.
   - Players are restricted to using a **single finger** throughout the match.
3. **Gameplay:**
   - Each button press shifts the active green LED ("Photon") incrementally toward the opponent's side.
   - When a Photon reaches the opponent's end, that lane is **conquered** and lights up entirely in the winner's color (Red or Blue).
   - Once a lane is conquered, further button inputs for that specific lane are automatically locked out.
4. **Winning the Match:**
   - The match concludes when **all 3 lanes** have finished.
   - Total scores are tallied automatically; the player who conquered the most lanes wins the game.
   - A 16-segment display on the winner's side illuminates the letter **"W"** to announce the final victor.

---

## Video Demo

[![Photon War Video Demo](https://img.youtube.com/vi/vD4IVn6aZ1g/0.jpg)](https://www.youtube.com/watch?v=vD4IVn6aZ1g)

*(Click the image above or [watch the video demo on YouTube](https://www.youtube.com/watch?v=vD4IVn6aZ1g))*

---

## Hardware & Circuit Architecture

The physical prototype is constructed using several core digital logic modules:
* **Movement Control:** 74LS193 Up/Down BCD Counters paired with cascaded 74LS138 decoders (acting as a 4-to-16 decoder) to drive the LED array.
* **Debounce Circuitry:** RC low-pass filters combined with 74LS14 Schmitt Trigger inverters to eliminate mechanical switch bounce.
* **Glitch Prevention:** Cross-coupled 74LS00 NAND gates configured as an SR latch signal arbitrator to safely manage simultaneous button presses.
* **Score & Winner Logic:** 74LS283 4-bit binary adders, 74LS85 magnitude comparators, 74LS86 XOR gates, and 74LS08 AND gates to automate game completion and trigger the 16-segment "W" display.
* **Current Drivers:** PNP 2N2907 transistors and 150-ohm current-limiting resistors.
