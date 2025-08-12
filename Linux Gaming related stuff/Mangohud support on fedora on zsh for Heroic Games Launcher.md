
Heroic games launcher doesn't properly point to mangohud when you install it. 

Here's yet another step by step for set up:
1. Make sure mangohud is installed. `sudo dnf install mangohud`
	1. Once mangohud is installed, you can try using mangohud when you start a game by adding `ENABLE_MANGOHUD=1` in the environments section of the Heroic Games Launcher or `mangohud %command%` in the Heroic Games Launcher.
	2. If you want to manually add it to your $ PATH. ``echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc``  then run `source ~/.zshrc` and it should be added. change the config to bashrc if running bash etc for whatever shell you are using. 