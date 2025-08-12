
Heroic games launcher doesn't properly point to mangohud when you install it. 

Here's yet another step by step for set up:
1. Make sure the flatpak version of mangohud is installed. 
	 - You can install it/ verify the installation with `sudo flatpak install org.freedesktop.Platform.VulkanLayer.MangoHud`. 
	 - Verify heroic games launcher's runtime however, as you must match the run time with that of the heroic games launcher. you can check with `sudo flatpak info com.heroicgameslauncher.hgl | grep Runtime`
 2. Once mangohud is installed, you can try using mangohud when you start a game by adding `ENABLE_MANGOHUD=1` in the environments section of the Heroic Games Launcher or `mangohud %command%` in the Heroic Games Launcher.
	- If you want to manually add it to your $ PATH. ``echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc``  then run `source ~/.zshrc` and it should be added. change the config to bashrc if running bash etc for whatever shell you are using. 