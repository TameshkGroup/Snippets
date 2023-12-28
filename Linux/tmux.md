## How to make your session persistant

1. Install `Tmux Plugin Manager` AND `tmux-resurrect` plugin
      ```bash
      git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
      ```
      Put this at the bottom of ~/.tmux.conf ($XDG_CONFIG_HOME/tmux/tmux.conf works too):
      ```bash
      # List of plugins
      set -g @plugin 'tmux-plugins/tpm'
      set -g @plugin 'tmux-plugins/tmux-sensible'
      
      # My plugins:
      set -g @plugin 'tmux-plugins/tmux-resurrect'
      setw -g mouse on
      
      # Other examples:
      # set -g @plugin 'github_username/plugin_name'
      # set -g @plugin 'github_username/plugin_name#branch'
      # set -g @plugin 'git@github.com:user/plugin'
      # set -g @plugin 'git@bitbucket.com:user/plugin'
      
      # Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
      run '~/.tmux/plugins/tpm/tpm'
      ```
      Reload TMUX environment so TPM is sourced:
      
      ```bash
      # type this in terminal if tmux is already running
      tmux source ~/.tmux.conf
      ```
2. Open `tmux` and Hit `prefix + I` to install the plugins
3. Once your session config is ready you can save it via:
   - prefix + `Ctrl-s - save`
   - prefix + `Ctrl-r - restore`



      
