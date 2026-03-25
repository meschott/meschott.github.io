---
title: "Trying Stockfish"

date: '2026-02-05T16:17:27-04:00'
draft: false

---

Just going to document the process of trying the stockfish engine on my local computer to analyze my games. And deep dive down rabbit holes of chess lines with the "Cod Almighty' of chess engines (shout out to Square One Chess on YT for the nickname).

* Step 1: go to website (https://stockfishchess.org/)[stockfish].

* Step 2: read a little bit
I want to build from src and the README gives very clear easy instructions.
```
cd src
make -j profile-build
```

* Step 3: clone the repo

* Step 4: build
This completed in just a couple minutes for me.

* Step 5: use
Now Stockfish doesn't come with a GUI. The output of the compilation is an executable file 'stockfish'. Running the program and it drops me into some stockfish environment. I found the help command but the output of that tells me to go to the README, and doesn't tell me about a command to list commands.

