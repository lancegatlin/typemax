## Basic Layout Design
* MCC = multi-character chord
* SCC = single-character chord
* MFU = most frequently used
* LFU = least frequently used
* 1KC = 1 key press chord (single character chord)
* 2KC = 2 key press chord (single character chord)
* bigram = a two character string
* ngram = a string of variable length
* Note: http://norvig.com/mayzner.html used for letter & bigram frequencies
* Note: Twiddler is used here to facilitate discussion but concepts apply to any single-hand chording keyboard

```
   C1    C2    C3
.-------------------.
| f▒▒▒* s▒▒▒* d▒▒▒* | mouse-buttons
.-------------------.
| m▒▒▒▒ t▒▒▒▒ r▒▒▒▒ | index finger
| l▒▒▒▒ n▒▒▒▒ h▒▒▒▒ | middle finger
| i▒▒▒▒ e▒▒▒▒ o▒▒▒▒ | ring finger
| a▒▒▒▒ SPACE u▒▒▒▒ | pinky finger
.-------------------.
C1 = Inside (R)
C2 = Middle (M)
C3 = Outside (L)
Orientation = face-away
```

### Stride
A bigram (e.g. TE, HA, IX) has "stride" if the keys pressed one after the other occur on different fingers. Stride
allows finger(s) that just pressed a key to recover while the other finger(s) can begin travelling to the next
key press(es) while the first key press is still finishing. More stride means faster typing. The main goal of TMX is to
allow for stride in as many MFU bigrams as possible.

Example bigrams with stride:
* TH: MOOO(t) to OLOO(h)
* HE: OLOO(h) to OOLO(e)

Example bigrams without stride:
* TR: MOOO(t) to ROOO(r) (index finger used in both chords)
* CK: MLOO(c) to OLMO(k) (middle finger used in both chords)

### Natural NGrams
Any string of characters (ngram) whose overlapping bigrams all contain stride is referred to as a "natural" ngram.

Example natural ngrams:
* the: MOOO(t) to OLOO(h) to OOMO(e)
* ent: OOMO(e) to OMOO(n) to MOOO(t)
* ing: OORO(i) to OMOO(n) to MOLO(g)

When stride is maximized for MFU letters, natural MFU ngrams are maximized without any extra design optimizations.

### Stutter
A 1KC+2KC or 2KC+2KC bigram may share a common key between chords. This common key will cause the same finger to press
the same key twice in quick succession. Note that for 2KC+2KC, this is optimally combined with stride in the other
fingers. Stutter is slower than stride but faster than having the same finger travel to another key.

Examples with stutter:
* CH: MLOO(c) to OLOO(h) (middle finger presses outside key in both chords)
* QU: MOOL(q) to OOOL(u) (pinky finger presses outside key in both chords)

Also, it has been my experience that stutter requires extra training focus. Natural reaction to stutter is to pause or
"flutter" (press key more than twice).

### Mouse-button as keys
Since the overriding concern of TMX is to maximize stride, the Twiddler mouse-buttons are re-purposed as single key chords
(effectively disabling the mouse). These three extra 1KC are then assigned to the index finger bringing the total keys
pressed by the index finger to six. While at first this is confusing and seems like it might be overwhelming for the
index finger, with enough training it becomes natural and very fast. Training data shows that the mouse button keys are
significantly faster than even normal keys.


### Vowels and Consonant Divide
To optimize stride for most bigrams, TMX first divides 1KC consonants and vowels between upper and lower fingers.
1KC consonants are assigned to the index and middle fingers. Vowels are assigned to the ring and pinky fingers. Since
there are six ring and pink finger 1KCs and only 5 vowels, every vowel is assigned to a 1KC. This ensures that any vowel
 to consonant or consonant to vowel bigram has stride (e.g. TE, ER, AN, OW, etc).

```
.-------------------.
| CONST CONST CONST |
.-------------------.
| CONST CONST CONST |
| CONST CONST CONST |
| VOWEL VOWEL VOWEL |
| VOWEL ▒▒▒▒▒ VOWEL |
.-------------------.
```

### Center-line keys
Since the default hand position rests over center-line keys (MMMM), these are the quickest to press. Also, letters that
more frequently end words (ESNT and spacebar) are center-lined to reset the hand to default hand position whenever
possible. Note: D frequently ends words but since it is overall less LFU than ESNT it is not center-lined.
* E is MFU vowel and is assigned to the ring finger OOMO
* T is MFU consonant and is assigned to index finger MOOO
* N is 2nd MFU consonant and is assigned to middle finger OMOO
* S is 3rd MFU consonant and is assigned to middle mouse button

```
.-------------------.
| CONST s▒▒▒▒ CONST |
.-------------------.
| CONST t▒▒▒▒ CONST |
| CONST n▒▒▒▒ CONST |
| VOWEL e▒▒▒▒ VOWEL |
| VOWEL ▒▒▒▒▒ VOWEL |
.-------------------.
```

### Spacebar
The most frequently pressed key is not a vowel or consonant but spacebar. Ideally, spacebar would be placed center-lined
for the index finger but maximizing stride for vowels leaves a natural hole that can't be filled with any other letter
without incurring stride penalties. This hole is assigned to spacebar.

```
.-------------------.
| CONST s▒▒▒▒ CONST |
.-------------------.
| CONST t▒▒▒▒ CONST |
| CONST n▒▒▒▒ CONST |
| VOWEL e▒▒▒▒ VOWEL |
| VOWEL SPACE VOWEL |
.-------------------.
```

### Vowel section layout
* Since U is the LFU vowel, it is assigned to the outside pinky finger key OOOL(u)
* A is assigned to inside pinky finger key OOOR(a) since bigrams AU/UA are the LFU U bigrams
* O is assigned to outside ring finger key OOLO(o) to give stride to common bigram OU
* This leaves I assigned to inside ring finger key OORO(i) which coincidentally gives it stride in common bigrams AI/IA and EA

```
.-------------------.
| CONST s▒▒▒▒ CONST |
.-------------------.
| CONST t▒▒▒▒ CONST |
| CONST n▒▒▒▒ CONST |
| i▒▒▒▒ e▒▒▒▒ o▒▒▒▒ |
| a▒▒▒▒ SPACE u▒▒▒▒ |
.-------------------.
```

### 1KC Consonants
TMX assigns consonants the renamining 1KC in order of their frequency RHLDMF (with the exception of C which is
stutter optimized to take advantage of its common bigrams CH and CT).
* R and H are assigned to outside keys since outside is slightly faster than inside keys
* To allow stride in MFU bigram TH, H is assigned to outside middle finger outside OLOO
* This leaves inside index finger LOOO for R
* Since bigrams NL/LN and LH/HL are rare or never occur (while LT is common), L is assigned to inside middle finger OROO
* To allow stride in MFU bigram ND, D must be either inside index finger or mouse button
* M is to inside index finger ROOO since it is slightly faster than mouse button 
* D is assigned to inside mouse button since it is slight faster than outside mouse button
* F is assigned to remaining outside mouse button

```
.-------------------.
| d▒▒▒▒ s▒▒▒▒ f▒▒▒▒ |
.-------------------.
| m▒▒▒▒ t▒▒▒▒ r▒▒▒▒ |
| l▒▒▒▒ n▒▒▒▒ h▒▒▒▒ |
| i▒▒▒▒ e▒▒▒▒ o▒▒▒▒ |
| a▒▒▒▒ SPACE u▒▒▒▒ |
.-------------------.
```

### 2KC Consonants

```
|-------------------|-------------------.-------------------.
| •••••             |       •••••       |             ••••• |
| ▒▒▒▒▒ ▒▒▒▒▒ ▒▒▒▒▒ | v▒▒▒▒ ▒▒▒▒▒ c▒▒▒▒ | ▒▒▒▒▒ z▒▒▒▒ ▒▒▒▒▒ |
| ▒▒▒▒▒ x▒▒▒▒ ▒▒▒▒▒ | y▒▒▒▒ p▒▒▒▒ g▒▒▒▒ | ▒▒▒▒▒ b▒▒▒▒ w▒▒▒▒ |
| ▒▒▒▒▒ ▒▒▒▒▒ ▒▒▒▒▒ | j▒▒▒▒ ▒▒▒▒▒ q▒▒▒▒ | ▒▒▒▒▒ ▒▒▒▒▒ ▒▒▒▒▒ |
|-------------------|-------------------|-------------------|
|                   |                   |                   |
| •••••             |       •••••       |             ••••• |
| ▒▒▒▒▒ ▒▒▒▒▒ ▒▒▒▒▒ | ▒▒▒▒▒ CAPS▒ ▒▒▒▒▒ | ▒▒▒▒▒ k▒▒▒▒ ▒▒▒▒▒ |
| ▒▒▒▒▒ ▒▒▒▒▒ ▒▒▒▒▒ | ENTER ▒▒▒▒▒ ▒▒▒▒▒ | ▒▒▒▒▒ ▒▒▒▒▒ ▒▒▒▒▒ |
|-------------------|-------------------|-------------------|
••••• = hold key
▒▒▒▒▒ = unassigned
```

Remaining consonants are assigned to 2KC in frequency order: PGWYBVKXJQZ with the exception of C which was
intentionally skipped while assigning 1KC to allow for stutter optimization. The 2KC assignments are the hardest to optimize
and probably have the most room improvement.

* C is assigned to MLOO for stutter in common bigrams CH and CT
* P is assigned to MOMO for stride in PL, stutter in PE and PA and weak travel in MP,OP,PO and PR
* G is assigned to MOLO for stride in NG and GH, stutter in GO and weak travel in GE and GR (note: IG is low)
* W is assigned to LOLO for stride in WH and WA, stutter in OW and weak travel in WE (note: WI is slow)
* Y is assigned to MORO for stride in LY and AY, stutter in TY and weak travel in RY, EY and YE (note: YO is slow)
* B is assigned to LOMO for stride in AB and BL and stutter in BE
* V is assigned to MROO for stride in vowel bigrams and weak travel in NV
* K is assigned to OLMO for stride in RK,KS stutter in CK,KE and weak travel in OK,KI,KN
* X is assigned to LOMO for stutter in EX and weak travel in IX
* J is assigned to MOOR for stride in NJ,JE,JO and stutter in JA (note: BJ and JU are slow)
* Q is assigned to MOOL for stutter in QU
* Z is assigned to LMOO for stride in vowel bigrams (note: ZY is slow)


### QU MCC
Since 99% of words containing Q use the bigram QU, a fast QU MCC is provided as alternative to default stutter
optimized Q-U bigram.

```
|-------------------|
|       •••••       |
|             ••••• |
| ▒▒▒▒▒ ▒▒▒▒▒ qu▒▒▒ |
| ▒▒▒▒▒ ▒▒▒▒▒ ▒▒▒▒▒ |
|-------------------|
```
