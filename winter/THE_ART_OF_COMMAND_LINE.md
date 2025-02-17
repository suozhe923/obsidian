# Jobs_control
&: let the command work in the background
"%1 &" equal to "bg %1"
fg %1 brings job 1 from the background into the foreground
kill %1 can kill job 1


# SSH
ssh username@ip_addr


# USE_SKILL
***man readline*** check default shortcut key
***set -o vi/emacs***  change the style of shortcut
### for emacs:
- ctrl-r: search history by key words
	enter : execute
	-> : modify
- ctrl-w: delete the last word you type in
- ctrl-l: clean the screen
- ctrl-u: delete all contents before cursor(bash, fish), zsh will delete all 
- ctrl-a: move the cursor to the head of line
- ctrl-e: move the cursor to the end

***!n*** repeat the command n(in history)
***!$*** last parameter
***!!*** last command
***setopt interactive_comments*** : let # can make comments in interactive zsh
***pstree*** show the process(suggest pstree -p)
***pgrep*** search process by name
***pkill*** send signal to process by name