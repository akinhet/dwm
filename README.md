dwm - dynamic window manager
============================
dwm is an extremely fast, small, and dynamic window manager for X.


Requirements
------------
In order to build dwm you need the Xlib header files.


Installation
------------
Edit config.mk to match your local setup (dwm is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    make clean install


Running dwm
-----------
Add the following line to your .xinitrc to start dwm using startx:

    exec dwm

In order to connect dwm to a specific display, make sure that
the DISPLAY environment variable is set correctly, e.g.:

    DISPLAY=foo.bar:1 exec dwm

(This will start dwm on display :1 of the host foo.bar.)

In order to display status info in the bar, you can do something
like this in your .xinitrc:

    while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
    do
    	sleep 1
    done &
    exec dwm


Patches
-------
Patches applied to this build. All of them can be found in the patches/ folder.

- [alwayscenter](https://dwm.suckless.org/patches/alwayscenter/): 
in floating mode windows always appear in the center of the screen (as opposed to the default upper-left corner)

- [attachdirection](https://dwm.suckless.org/patches/attachdirection/):
new windows appear in the set direction instead of becoming the new master

Options:

```c
static const int attachdirection = 2; /* 0 default, 1 above, 2 right, 3 below, 4 bottom, 5 top */
```

- [cool-autostart](https://dwm.suckless.org/patches/cool_autostart/):
when starting dwm, executes commands from `autostart` array in config.h

Options:

```c
static const char *const autostart[] = {
	"nitrogen", "--restore", NULL,
	"picom", NULL,
	NULL /* terminate array */
};
```

- [restartsig](https://dwm.suckless.org/patches/restartsig/):
allows to restart dwm without killing the client windows

Options:

```c
static Key keys[] = {
	...
	{ MODKEY|ControlMask|ShiftMask, XK_q,	quit,	{1} },
	...
}
```

- [statusallmons](https://dwm.suckless.org/patches/statusallmons/):
shows the status on all monitors

- [systray](https://dwm.suckless.org/patches/systray/):
simply a systray 

Options:

```c
static const unsigned int systraypinning = 0;   /* 0: sloppy systray follows selected monitor, >0: pin systray to monitor X */
static const unsigned int systrayonleft = 0;   	/* 0: systray in the right corner, >0: systray on left of status text */
static const unsigned int systrayspacing = 2;   /* systray spacing */
static const int systraypinningfailfirst = 1;   /* 1: if pinning fails, display systray on the first monitor, False: display systray on the last monitor*/
static const int showsystray        = 1;     /* 0 means no systray */
```

- [tilegap](https://dwm.suckless.org/patches/tilegap/):
sets the size of gaps between windows in tile mode

Options:

```c
static const unsigned int gappx     = 10;       /* gap pixel between windows */
```

- [underlinetags](https://dwm.suckless.org/patches/underlinetags/):
adds underlines to the active tags on the bar

Options:

```c
static const unsigned int ulinepad	= 4;	/* horizontal padding between the underline and tag */
static const unsigned int ulinestroke	= 2;	/* thickness / height of the underline */
static const unsigned int ulinevoffset	= 0;	/* how far above the bottom of the bar the line should appear */
static const int ulineall 		= 0;	/* 1 to show underline on all tags, 0 for just the active ones */
```

Configuration
-------------
The configuration of dwm is done by creating a custom config.h
and (re)compiling the source code.
