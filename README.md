# COSC 312: Turing Machine Team Project

## Summary
The configuration for our final machine to be submitted for grading is the file "tm_final.txt".
The file "scratch.pdf" is the final set of notes corresponding to the final design configuration.
That PDF should be a good reference when writing the final version of the paper.  Notably, the
top left of the PDF shows the alphabet over which we can encrypt.  Our machine accepts ALL alphabetical
characters, but it WILL NOT handle numbers!  While it will handle all letters, it only processes those
in its alphabet for encryption.  In the PDF, there is an abbreviated version of the machine at the top
and a more complete drawing below.  A full drawing was impossible given the number of states and transitions.
However, sufficient information is present for you to fully understand the design.  You'll just have to
imagine a similar nine-state cluster at the very bottom for every one of the ten states in the row above.
I was only able to draw them out for the left-most state.  In the top right of the PDF is a table of the
alphabetical shifts.  The top row is our machine's alphabet.  The next row is the same shifted by one, the
second row shifted by two, and so on.  It is noteworthy and should DEFINITELY be included in the paper that
this alphabet was chosen as it represents the top ten most frequently used letters in the English language.
My thoughts in choosing these were motivated by maximizing the words and letter that our machine would
actively encrypt while editorializing the project such that it was manageable while meeting the requirements.
In the top, most abbreviated version of the machine, the magenta color denotes cases where there would need
to be multiple states/transitions, and I summarize them with one for clarity.  So if you see magenta, think
there is one thing representing many things.  In the case of the magenta '*', that signifies one of the
letters in our machine alphabet of which there are ten possibilities.  For the magenta "1-9", that means
we need a separate transition and corresponding states for every possible shift choice the user could make,
of which there are nine total.  The bottom machine expands these as much as possible.  I may expand this
summary if I think of anything else I forgot to mention.  Below is a bulleted list of important information
regarding our machine that you either need to know or need to include in the paper or both:

* Proper input is of the form "[shift number: 1-9]:[string]$".  Note, we no longer lead with '#'!
* Our ten letter alphabet is: 'e', 't', 'a', 'o', 'i', 'n', 's', 'h', 'r', 'd'.  These are, in order
the top ten most frequently used letters of the English language.
* Our machine will allow the use of other non-numerical symbols and letters, however, it will neither
encrypt nor decrypt them.  E. g., 5:encrypted NOT ENCRYPTED$ -> 5:necoypsni NOT ENCRYPTED$.
* Again, our machine WILL NOT process numerals!  This is because after reading past a numeral, when
the machine backs up looking for the shift number, it will read the numeral as the shift number and
change the cipher going forward.
* Also, '#' and '$' are not valid members of any input string, as they are used by the machine to remember
the character slot being processed and to recognize the end of the input string, respectively.
* If the shift number x is used to encrypt a string, then the number y = 10 - x will decrypt the ciphertext
generated with the x shift.  E. g., 3:test$ -> 3:iodi$ and 7:iodi$ -> 7:test$.
* We use ten letters in our alphabet because that allows a maximum of nine shifts.  If we have eleven or
more letters, then we'd have the capability of utilizing ten or more shifts.  This causes states and transitions
to start blowing up, as we have to account for reading one or two numbers and processing many other letter
combinations.  With ten letters and nine shifts, we are able to limit ourselves to 103 states 294 transitions.
* A textual summary of the machine's operation is roughly something like this: "First it finds the ':' and
assumes a character immediately follows the colon.  If it is a character not in the machine alphabet, then it is
essentially left alone and skipped.  If it is a character that is in the machine alphabet, then it is overwritten
with a '#' to mark its place (a form of memory), and transitions to a state which seeks out the shift number 1-9.
Based on the shift number it finds, it transitions to a state which seeks out the '#' which marks the character
slot being processed.  Upon finding it, the machine overwrites the '#' with the new ciphertext letter and transitions
back to the "read char" state and continues processing the string.  Upon encountering a '$', the machine regards
that as the end of the input string and transitions to a final accept state.  Nothing past the '$' should ever
be processed.
* I think my handwritten notes will be very helpful toward creating visual aids for our paper, but I hope you can
make them nicer/more professional than my scratch work.  I seem to recall some flow chart software package that I
used in an earlier engineering class that might make quick work of this part, but I cannot recall its name.
* If you need anything from me to help with the paper, do not hesitate to ask.  But I spent a great deal of time
on the machine design and really need to turn my focus to other work for a while.  So I'm really hoping you won't
need much from me on the paper.  Please make sure we all sign off on the final version of the paper and machine,
and remember that we're apparently each supposed to submit a copy for grading.
* If I think of anything else, I'll add it and notify you in the group chat.
