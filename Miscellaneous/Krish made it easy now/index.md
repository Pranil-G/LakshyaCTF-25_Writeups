# Krish Made It Easy

## Description
"Oh, my God, look at that face You look like my next mistake Love's a game, wanna play?"  
 
 Hint: The flag may wave in silence, but the comments don't lie. Sometimes, the real message hides below the surface.

 Flag Format: LakshyaCTF{Text_number}

## Solve
We were provided with a question.txt file that looked empty but had whitespaces.
Song lyrics were from `Blank Space` by Taylor Swift which was a clue that the cipher in the txt was whitespace cipher.

We used `https://www.dcode.fr/whitespace-language` to decode the text which reaveled a  probability riddle and a link.
`
In a foggy town where secrets linger, four in ten believe in whispers, while eight in ten hear distant echoes. Yet, among those who believe, three in ten claim to have heard them first. But in this haze of half-truths, tell me--if you hear the echoes, what are the chances you already believed?
on solving this proceed here -> https://drive.google.com/drive/folders/10q87CQTbXhmiXr__j6RGPK5Ll7Sxvbu5?usp=drive_link
`
Answer to the riddle was 0.15, but the base64 string from the file from link led to a Rickroll link. The video description hinted at “Hand Thing” → Led to a YouTube video. After looking around a bit we found a comment from user Krish said “i am here”.

Krish’s channel description had a hex string:
`68747470733a2f2f74696e7975726c2e636f6d2f626d6d6a76776835`

Which decoded to:
`https://tinyurl.com/bmmjvwh5`

This link led to a Proton Drive file. Using 0.15 (from earlier) as the password, the file unlocked.

It revealed an image named InsideImage.jpg. Checking its metadata showed:
`Cicada_3301_logo.jpg`

Flag - `LakshyaCTF{Cicada_3301}`
