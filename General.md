# MARKDOWN
* markdown table converter: https://tableconvert.com/

# GIT/GITHUB

- FIRST-TIME CONFIG
    - `git config --global user.name "Mona Lisa"`
    - `git config --global user.email "email"  >


# SSH AND SCREEN 

- CREATING SSH KEY
    - github: `ssh-keygen -t ed25519 -C "your_email@example.com"`

- ADDING SSH KEY TO GITHUB
    - `cat` the pub SSH key, paste it into the Github SSH section. 
    - test that it worked: `ssh -T git@github.com`, enter past warnings

- SSH COMMAND
    - `ssh <address>` in linux
    - with SSH key path specified: `ssh -i </path/to/key> <address>`
    - Create SSH key:
        - 

- SCREEN SESSION BASICS
    - Make sure its installed: `apt get install screen`
    - Make screen session: `screen -S <screen-name>`
        - Note CAPITAL “s”
    - Detach from screen session (go back to “base” command line): `CTRL + A, D`
    - Reattach to screen session: `screen -r <screen-name>`
    - Kill a screen session: type `exit` in the session

- SCREEN SESSION: LAYOUTS AND MULTIPLE SCREENS WITHIN SAME SESSION
    - Instead of creating mulitple screens from the terminal, you might well only want to create on screen “session”, and create multiple sessions within that. [Video demonstration](https://www.youtube.com/watch?v=Mw6QvsChxo4).
    - Split screen:
        - Horizontally: `Ctrl+A, |`
        - Vertically: `Ctrl+A, S`
        - Change between splits: `Ctrl+A, Tab`
    - Create a new screen within a session: `Ctrl+A, c`
    - Cycle between screens: `Ctrl+A, N` for next, `Ctrl+A, P` for previous
    - [Good discussion on saving layouts](https://superuser.com/questions/687348/how-to-persist-gnu-screen-layout-after-restart)
        - Basically, `Ctrl+A, :layout save default`
    - Get all screen commands: `Ctrl+A, ?`

# LINUX


## Arch install

- Guide: https://www.makeuseof.com/install-arch-linux-on-virtualbox-guided-installer/
    - `python -m archinstall guided` 

## i3/sway shortcuts

- **General**
    - `Mod + Enter`: Open terminal
    - `Mod + Shift + Q`: Close window
    - `Mod + D`: Dmenu (search for apps)
    - `Mod + Shift + Arrow`: Move window in given direction
- **Tiling**
    - Windows are automatically tiled horizontally
    - `Mod + V`: Next window to be tiled vertically
    - `Mod + Arrow`: Move focus to window in direction
        - Also supports `jkl;` - maybe I can remap this to vim bindings? 
- **Modes**
    - `Mod + S`: Stacking mode
    - `Mod + E`: Back to tiling mode       
    - `Mod + W`: Tab mode
    - `Mod + R`: Resize
- **Workspaces**
    - `Mod + Shift + Number`: Move focused window to workspace number given
    - `Mod + Number`: Shift to workspace with given number   


## Something