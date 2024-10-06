x - delete character
A - move the cursor to the to the end of the line
a - append after the cursor
dw - to delete word
d$ - delete line
de - delte to the end of current word
[number]w - move the cursor to start of the word
[number]e - move the cursor to end of the word
d[number]w/e - to mutiple words
dd - to delete line
[number] - delete multiple lines
u - undo 
U - toggle undo
r[character] - replace the character
R - replace
ce - change untile the end of word
cc - change the whole line
c$ - change from cursor to the end of line

[number]G - nav through diffrent lines
:/[letter] - search letter forward
:?[letter] - search letter backword
n/N - to nav search letter
ctrl+o - to go back where you came from
ctrl+i - to back futher

% - match prenthese search
:s/[old]/[new] - replace the letter in the line

:![terminal command] - run terminal command
:w [fil name] - create and copy current file 
V [motion] [:'<,'>w [file name]] - create a new file with selected text
:r [file name] - past the file to the current file 

o - one new line below with insert mode
O - open new line above with insert mode

yw - one word
yl - whole line
