# Vim for beginners

## 基本按键

## Viusal Mode

1. `v` change into the visul mode.
2. `ctrl + v` change into the block visual mode. we can also use `I` to get multi-cursor.
3. `V` change into the line visual mode. that you are my

## Move

### move in the line

`f` + character: use find command to move quickly. And `:` means the next one, `,` the previous one.
`0`: move to the begin of the line.
`$`: move to the end of the line.

### move by the words

`w/W` move to the bigen of the word, `e/E` move to the end of the word. `b/B` backwards.

### move in the page

The following commands act on **current** page.

1. `H`: Head.  `L`: Lower, the tail of the content. `M` the middle of the content.
2. `ctrl + O` return to the last place quickly.
3. `zz` set the line in the middle.
4. `ctrl + u`: page up. `ctrl + f`: page down.

## Delete  

### delete the content in the braket

They are in the normal mode.
`di(`: delete content in the braket.
`dt` + character: delete from the current character to the detemined character.
`dw`: delete a word.
`x`: delete a character.

The following is in the insert mode.
`ctrl + h` backspace a character.
`ctrl + w` backspace a word.

## Change

### change a word

in the normal mode: `cw` (it will transfer to the insert mode).

## Find  
