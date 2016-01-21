# wanime
Watch and organize anime through the CLI

You can find the older version of this in my gists (wanime.py). In my free time I'm rewriting the old interactive, loopy, messy version of wanime to a more pythonic, object oriented, GNU tool style tool. It will lack the interactiveness of the old version, and be more of an API than a client. 
Don't get me wrong, it'll still be just as powerful, and way easier to use. For instance, 
```bash
#Watch remaining episodes of show labeled with custom slug 'sao2', without stopping, with mpv
wanime watch 'sao2' --no-brakes --player=mpv 
```
will start playing Sword Art Online after your last viewed episode, and continue playing episodes without stopping in between. I'm still brainstorming for a good way to track last viewed episode (LVE), for now it'll just be manual.

The rewrite is meant to make command chains like: 
```bash
#Watch the remainder of all the Sword Art Online seasons in alphanumeric order (by slug -> show name -> show id)
wanime ls 'sao' --status=watching --alpha | awk {'print $1'} | while read -r SHOW_ID; do wanime watch $SHOW_ID --no-brakes; done

#Marathon all seasons and episodes of log horizon, without touching stored show/episode values/status
wanime search 'log horizon' --alpha | awk {'print $1'} | while read -r SHOW_ID; do wanime watch $SHOW_ID --marathon; done
```
a fun and efficient possibility.
