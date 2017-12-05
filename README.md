## Overview

Typemax (TMX) is a configuration for single-hand chording keyboards that have a number of keys that is less than the 
number of letters in the English alphabet. TMX attempts to maximize the words-per-minute (WPM) typing speed when typing
with only single character chords (i.e. without using multi-character chords (MCC)). Since there are less keys than 
letters, many letters are assigned to single key chords (1KC) but other letters must be assigned to two key chords 
(2KC). Generally, more frequently used (MFU) letters are assigned to 1KC and less frequently used (LFU) letters are
assigned to 2KC. However, this rule is weighed against a full set of optimizations as outlined below.

Note: See http://norvig.com/mayzner.html for letter & bigram frequencies

| Pros                   | Cons                    |
| ---------------------- | -----------------------:|
| High WPM               | Disables mouse          |
| Often faster than MCC  | Must train "stutter"    |
| Natural type-ability   | Steeper training curve  |
| Intuitive to learn     | Requires "spacer"       |

## Twiddler: The "Spacer"
To make typing the inside row and furthest pinky key finger (OOOL) effortless, a "spacer" is required. The spacer is a 
solid block that widens the gap between the inside of the index finger knuckle and the side of the Twiddler. Expanding 
the gap between the index finger knuckle and the Twiddler realigns the fingers in such a way to allow strain-free 
typing of inside row and furthest pinky finger key. The size of the spacer will vary according to the user.

Note: Twiddler configuration requires firmware 15+

## Layout design

### Stride
A bigram (e.g. TE, HA, IX) has "stride" if the keys pressed one after the other occur on different fingers. Stride
allows finger(s) that just pressed a key to recover while the other finger(s) can begin travelling to the next
key-press(es) while the first key press is still finishing. More stride means faster typing. TMX main goal is enable 
stride for as many MFU bigrams as possible.

Example bigrams with stride:
* TH: MOOO(t) to OLOO(h)
* HE: OLOO(h) to OOLO(e)

Example bigrams without stride:
* MOOO to ROOO (index finger used in both chords)
* MROO to ORMO (middle finger used in both chords)

### Natural NGrams
Any string of characters (ngram) whose overlapping bigrams all contain stride is referred to as a "natural" ngram.

Example natural ngrams:
* the: MOOO(t) to OLOO(h) to OOMO(e)
* ent: OOMO(e) to OMOO(n) to MOOO(t)

When stride is maximized for MFU letters, natural ngrams happen more frequently without further design changes.

### Stutter
A 1KC+2KC or 2KC+2KC bigram may share a common key between chords. This common key will cause the same finger to press
the same key twice in quick succession. Note that for 2KC+2KC, this is optimally combined with stride in the other
fingers. Stutter is less type-able than stride but faster than having the same finger travel to another key.

Examples with stutter:
* CH: MLOO(c) to OROO(h)
* QU: MOOL(q) to OOOL(u)

Also, it has been my experience that stutter requires extra training focus. Natural reaction to stutter is to pause.


### Vowels and Consonant Divide
To optimize stride for most bigrams, TMX first divides 1KC consonants and vowels between upper and lower fingers.
1KC consonants are assigned to the index and middle fingers. Vowels are assigned to the ring and pinky fingers. Since
there are 6 1KC and only 5 vowels, every vowel is assigned to a 1KC. This ensures that any vowel to consonant or
consonant to vowel bigram has stride (e.g. TE, ER, AN, OW, etc).

### Center-line keys
Since the default hand position rests over center-line keys (MMMM), these are the quickest to press. Also, letters that
more frequently end words (ESDNT and spacebar) are center-lined to reset the hand to default hand position whenever
possible.

### Spacebar
The most frequently pressed key is not a vowel or consonant but spacebar. Ideally, spacebar would be placed center-lined
for the index finger but maximizing stride for vowels leaves a natural hole that can't be filled with any other letter.
This hole is assigned to spacebar.

### Vowel section layout
* E and spacebar are center-lined with OOMO(e) and OOOM(spacebar)
* Since U is the LFU vowel it is assigned the further stretch pinky finger key OOOL(u)
* A is assigned to pinky finger key OOOR(a) since bigrams AU/UA are the LFU U bigrams
* O is assigned to ring finger key OOLO(o) to give stride to MFU bigram OU
* This leaves I assigned to ring finger key OORO(i) which coincidentally gives it stride in common bigrams AI/IA and EA

### Mouse-button as keys
Since the overriding concern of TMX is to maximize type-ability, the mouse-buttons are re-purposed as single key chords
(effectively disabling the mouse). These three extra 1KC are then assigned to the index finger bringing the total keys
pressed by the index finger to six. While at first this is confusing and seems like it might be overwhelming for the index finger,

TMX assigns letters in order of their frequency [ETAOINSRHLDUMF][CPGWYBVKXJQZ] () with the exception of C which is optimized to take advantage of its common bigrams.




A secondary consideration is that each finger of the hand is ranked in order of its speed: index, middle, ring, pinky.
MFU letters. The first 3 letters
