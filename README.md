## Overview

Typemax (TMX) is a configuration for single-hand chording keyboards that have a number of keys that is less than the
number of letters in the English alphabet. TMX attempts to maximize the words-per-minute (WPM) typing speed when typing
with only single character chords (i.e. without using multi-character chords (MCC)). Since there are less keys than
letters, many letters are assigned to single key chords (1KC) but other letters must be assigned to two key chords
(2KC). Generally, more frequently used (MFU) letters are assigned to 1KC and less frequently used (LFU) letters are
assigned to 2KC. However, this rule is weighed against a full set of optimizations as outlined in [basic layout design](https://github.com/lancegatlin/typemax/blob/master/basic_layout_design.md).

Note: See http://norvig.com/mayzner.html for letter & bigram frequencies

| Pros                   | Cons                      |
| ---------------------- | -------------------------:|
| High WPM               | Disables mouse            |
| Often faster than MCC  | Must train "stutter"      |
| Natural type-ability   | Steeper training curve    |
| Intuitive to learn     | Can't use thumb shift key |

Note1: requires Twiddler firmware 15+
Note2: Twiddler firmware 15 thumb shift does not captialize letters typed by mouse buttons 
