# Echoes in the Code

The website was a simple file download application with LFI vulerability. I spent lot of time trying to find the flag.txt path but then I saw the comment in main webpage - ``` <!-- hmm maybe there is a public.txt here --> ```. I quickly extracted the public.txt file - 

```
Welcome to our website!  
Enjoy your stay and download the files you need. 
Sometimes, all it takes is knowing where to look for some "secret". Maybe in /files?
```

This was an obvious clue that flag is in `/files/secret.txt` after trying different paths `../files/secret.txt` was the correct one.

Flag - `LakshyaCTF{yOu_sOlVeD_FiLe_TrAvErSaL}`
