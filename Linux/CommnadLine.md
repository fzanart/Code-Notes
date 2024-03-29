## Workflow to create n VM's and keep executing the code after logging off.

1. Send bash script to VM: `scp -p /path/to/file server@host:/path`

2. ssh VM `ssh -i /path/to/credentials server@host`

3. Follow the process as described [here](https://askubuntu.com/a/220880):
   
    start tmux: `tmux`  
    run script `sudo bash ./script.sh`  
    leave/detach the tmux <kbd>Ctrl</kbd> + <kbd>B</kbd> (hit control + B, release and then press D)  

4. log off ssh session.

**Extra notes:**  

Get a list of current sessions: `tmux ls`  
Enter into a session: `tmux attach-session -t <session-name>`  
Kill a particular session: `tmux kill-session -t <session-name>`  
Momentarily strore passphrase: `eval $(ssh-agent)` then `ssh-add /path/to/credentials`
