## Overview

Typemax (TMX) is a configuration strategy for single-hand chording keyboards (e.g. [Twiddler](http://twiddler.tekgear.com/))
that have a number of keys that is less than the number of letters in the English alphabet. TMX maximizes typing
speed by emphasizing efficent single character chord transitions ([stride](https://github.com/lancegatlin/typemax/blob/master/basic_layout_design.md#stride)). 
TMX derived configurations can optionally use multi-character chords (MCC), but MCC are not required as part of the core
typing layout. The design philosophy and explanation of all optimizations are outlined in [basic layout design](https://github.com/lancegatlin/typemax/blob/master/basic_layout_design.md).

| Pros                   | Cons                                                                     |
| ---------------------- | ------------------------------------------------------------------------:|
| High WPM without MCC   | Steeper initial training curve                                           |
| Natural typing flow    | Twiddler: Re-purposes mouse buttons as keys                              |
| Intuitive to learn     | Twiddler: Thumb modifier keys currently don't work on mouse buttons keys |
| Can customize with MCC |                                                                          |

Layout: https://github.com/lancegatlin/typemax/blob/master/typemax.txt

Note1: requires Twiddler firmware 15+

## Versioning

TMX uses a three number version scheme major.minor.fix (similar to semantic versioning):
* Major: incremented when a change occurs to the base layout. Users should expect that changes to the base layout will require significant retraining and will most likely result in downstream changes to other chords.
* Minor: incremented when a change occurs to anything other than the base layout e.g. symbols, numbers, MCCs, etc that will require users to retrain.
* Fix: incremented when a mistake in the config is corrected OR when new chords are added that don't impact existing chords. Users can safely upgrade to new fix versions without needing to retrain.
