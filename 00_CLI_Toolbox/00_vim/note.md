Ctrl + f: Page Forward (Down one full screen)

Ctrl + b: Page Backward (Up one full screen)

Ctrl + d: Down half a screen

Ctrl + u: Up half a screen


ctrl + a for add number  5->6
ctrl + x for minius number 7 -> 6


find
/<keyword>
\ using for spactial char ex \. mean n, \/ mean /
. ignar


# repeat
:[range]s/old_word/new_word/[flag]
Scenario    Command     What it 
does Current line (First match only)    :s/old/new/         Replaces only the first occurrence in the current line.
Current line (All matches)              :s/old/new/g        Replaces all occurrences in the current line (g = global).
Entire file                             :%s/old/new/g       Replaces every occurrence in the whole file (% = all lines).
Entire file + Confirmation              :%s/old/new/gc      Asks for your permission before replacing each word (c = confirm).


How to Respond to the Confirmation Prompt (c flag)
y (yes) = Replace this match.
n (no) = Skip this match.
a (all) = Replace this and all remaining matches without asking again.
q (quit) = Stop the replacement process immediately.
l (last) = Replace this match and exit (this is the last one).

Replace within a selection (Visual Mode):
:'<,'>s/old/new/g
