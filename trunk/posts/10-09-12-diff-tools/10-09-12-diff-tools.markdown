This post is a stub.

I've been doing experiments using different diff tools than the one implemented in&nbsp;<a href="http://www.phpunit.de/">PHPUnit</a>. I might talk about changing the default PHPUnit diff tool in a later post but this posts only lists the diff tools I've found and my thoughts about them.
 
## Preparations
Here are some Ubuntu apt-get commands to install the mentioned tools:

    sudo apt-get install diffuse
    sudo apt-get install vim
    sudo apt-get install wdiff
    sudo apt-get install python-pygments
    sudo apt-get install meld
    sudo apt-get install colordiff

## Diff
The classic diff tool generates nice noncolored text diffs:

    rune@rune-laptop:~$ diff a b
    1c1,2
    < Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
    ---
    > Lorem dolor sit adipiscing elit. 
    > 
    4c5
    <      
    ---
    >     Nulla sed eros lacus.   
    
Somehow my brain keeps struggling understanding this format. But it get gets
immediately better when using the unified format which my brain likes a lot
better:

    rune@rune-laptop:~$ diff -u a b
    --- a	2010-09-12 14:59:06.524750583 +0200
    +++ b	2010-09-12 14:59:06.524750583 +0200
    @@ -1,7 +1,8 @@
    -Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
    +Lorem dolor sit adipiscing elit. 
    +
         Donec eget viverra lacus. 
         Nam vitae ante nunc.
    -     
    +    Nulla sed eros lacus.     
     Maecenas elementum.
     suscipit urna.


## Colordiff
Colordiff is a wrapper around diff which adds color. This makes the diff
understandable at the first glance.

![colordiff](http://i.imgur.com/KURvX.png)

## Pygmentize
Pygmentize's diff formatter creates very similar output as Colordiff.

![pygmentize](http://i.imgur.com/rqRzM.png)

## Wdiff
One thing missing from both diff, colordiff and pygmentize is the ability to
show changes inside the lines. This lead me to try wdiff, but it does not 
handle line changes very well.

![wdiff-colordiff](http://i.imgur.com/T4wFV.png)

## Meld
The failure of wdiff let me to try gui tools, one of them meld which creates
a very nice view. Handles inline changes.

![meld](http://i.imgur.com/ZXaWx.png)

## Diffuse
Python tool that also looks very nice. Handles inline changes.

![diffuse](http://i.imgur.com/CNSzz.png)

## Vimdiff
Part of vim and also looks very nice. Handles inline changes.

![vimdiff](http://i.imgur.com/nhfg9.png)

## Summary
I guess my favorites are colordiff/pygmentize or meld. But I will keep looking
for a command line diff tool that handles inline changes.
