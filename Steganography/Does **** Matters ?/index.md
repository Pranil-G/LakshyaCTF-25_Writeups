# Does **** Matter?

## Description

You got an image. It looks... normal. But someone swears the flag is hidden in the **** of it.

Whatever that means.

Maybe it's time to ask yourself: Does **** matters?

Flag Format: LakshyaCTF{}

## Solve

We were given total 6 images. Each had a valorant character in it.
- `Bhagoda.png`  
- `Chall_Hatt.png`  
- `Fade.png`  
- `I_Miss_Her.png`  
- `Monster.png`  
- `Reyna.png`

This challenge was particularly hard and took lot of time... We used every single stego tool out there to see if we get anything but we didn't. It turns out that the hint was in the title itself **** had to be the word 'size', so we checked size and dimensions of every image and converted it into ASCII

- Image Name     | Dimensions | Full ASCII (W × H)
- Bhagoda.png    | 121 × 89   | 121 → 'y', 89 → 'Y'     ⇒ "yY"
- Chall_Hatt.png | 118 × 105  | 118 → 'v', 105 → 'i'    ⇒ "vi"
- Fade.png       | 79 × 98    | 79 → 'O', 98 → 'b'      ⇒ "Ob"
- I_Miss_Her.png | 111 × 117  | 111 → 'o', 117 → 'u'    ⇒ "ou"
- Monster.png    | 115 × 108  | 115 → 's', 108 → 'l'    ⇒ "sl"
- Reyna.png      | 101 × 115  | 101 → 'e', 115 → 's'    ⇒ "es"

after trying different anagrams the answer was `Obviously Yes`

Flag - `LakshyaCTF{ObviouslyYes}`
