SAR
===

+----------+-------------------------------------------------------------------+
| Syntax   |  SAR file, array                                                  |
+----------+-------------------------------------------------------------------+
| Location |  ARRAY                                                            |
+----------+-------------------------------------------------------------------+

 The command SAR allows you to save a given array quickly (so that it
can later be reloaded) as a whole to a specified file. The Toolkit II
default data device for the file name is supported, although an existing
file is not overwritten (use SARO) - the error 'Already exists' will be
generated instead. array is stored in an internal coded but portable
format, which makes it extremely fast to save and load arrays when
compared to storage by writing and reading each individual element of an
array. The file format is quite simple, it is basically the same as the
way in which SuperBASIC itself would store the array. The first four
bytes of the stored array are the characters WLAF. SAR will identify
dimensions and the type of array on its own and accordingly store it.
Sub-arrays are handled, but please note that, since stored data can only
be reloaded into a readily dimensioned array (see LAR), it is important
to remember the dimensions and type of the array before loading.

**Example**

Save and load an array: 100 DIM a%(1000) 110 SAR file$, a% 120 LAR
file$, a%

**NOTE**

SAR's file format is not compatible with that used by Toolkit 3 (a
commercial Toolkit which has nothing to do with the famous Toolkit II),
produced with SARRAY.

**CROSS-REFERENCE**

`SARO <KeywordsS.clean.html#saro>`__ and `LAR <KeywordsL.clean.html#lar>`__.
`DIM <KeywordsD.clean.html#dim>`__ sets-up an array while
`DIMN <KeywordsD.clean.html#dimn>`__ and `NDIM <KeywordsN.clean.html#ndim>`__ read
the dimensions.

--------------

SARO
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SARO file, array                                                 |
+----------+-------------------------------------------------------------------+
| Location |  ARRAY                                                            |
+----------+-------------------------------------------------------------------+

 SARO is almost the same as SAR except that it overwrites an existing
file without reporting an error.

--------------

SAUTO
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SAUTO seconds                                                    |
+----------+-------------------------------------------------------------------+
| Location |  Ecran Manager                                                    |
+----------+-------------------------------------------------------------------+

 This is yet another screen saver.... It is activated by specifying how
many seconds the computer should wait for a key to be pressed before it
turns the screen blank. Once the screen is blank, any key will display
the screen again. Negative seconds de-acticate this most useful of all
computer utilities.

**Example**

SAUTO 180
 blanks the display if no key is pressed for three minutes.

**NOTE 1**

seconds = 0 gives an annoying flashing screen, so avoid it.

**NOTE 2**

See SSAVE.

**CROSS-REFERENCE**

`SCRON <KeywordsS.clean.html#scron>`__, `SCROFF <KeywordsS.clean.html#scroff>`__,
`MODE <KeywordsM.clean.html#mode>`__

--------------

SAVE
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SAVE device\_filename :sup:`\*`\ [,range]\ :sup:`\* ` or SAVE [device\_] filename :sup:`\*`\ [,range]\ :sup:`\*`\ (Toolkit II only)  or SAVE(SMS only)  |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM, Toolkit II                                               |
+----------+-------------------------------------------------------------------+

 If no line range is given, this command saves the whole of the
currently loaded SuperBASIC program to the given directory device, under
the given filename. However, a range of lines can be given (as with
LIST), in which case only the given lines will be saved. If the filename
already exists on that device, the error 'Already Exists' is reported,
unless you have Toolkit II present, in which case, a prompt will be
printed in #0 asking you whether it is okay to overwrite that file. If
the device is already full, the 'Device Full' error is reported,
however, the effects should the drive become full during the actual SAVE
command, depends upon the implementation (see below). The file is saved
in pure ASCII format, which means that it can be COPYed to the screen or
a printer (using COPY\_N). The Toolkit II variant of the command will
add the data default directory to the filename if it cannot find the
given device, or no device is specified.

**Examples**

Save the whole of the current program to microdrive 1 with the filename
BOOT: SAVE mdv1\_BOOT
 Save the whole of the current program to the current data default
directory with the filename prog\_bas: SAVE prog\_bas
 Save lines 1, 100 to 150 (inclusive) and 300 to the end of the program
to the current data default directory with the filename cut\_bas: SAVE
cut\_bas,1,100 TO 150,300 TO

**NOTE 1**

SAVE can lead to incomplete files if the Break key is pressed or the
device fills up during access, although Toolkit II (v2.13+) will report
any file errors during output (other than the Break key being pressed),
leaving the incomplete file on the device.

**NOTE 2**

Minerva (pre v1.80) deleted the file if SAVE was aborted for any reason.

**NOTE 3**

If you try to SAVE a file on top of a sub-directory name, Toolkit II
will repeatedly ask if it is OK to overwrite that file until you answer
<N> (for No).

**SMS NOTES**

The third variant of the command will allow you to SAVE the program in
memory under the same filename as when LOAD or QLOAD
 was last used (with the \_BAS suffix appended if necessary). If the
original filename used when the program was LOADed ended in \_SAV, then
SAVE will alter this to be the \_BAS suffix. This variant will also take
the version number of the file when it was LOADed (or QLOADed) and then
increase this by one. If you SAVE a file on a disk, then use DELETE to
remove that file, and then change the disk before issuing the SAVE
command without a filename being specified, SMSQ/E fails to recognise
that the disk has been swapped and repeatedly tries to write out the
file using the old directory map. Further, if you enter SAVE without a
parameter and no disk is in the drive - SMSQ/E asks if it is OK to
overwrite the file!!

**CROSS-REFERENCE**

`LOAD <KeywordsL.clean.html#load>`__ loads a saved file from the given device
into memory. `SAVE\_O <KeywordsS.clean.html#save-o>`__ is another variant of
this command. See also `QSAVE <KeywordsQ.clean.html#qsave>`__ for a different
means of `SAVE <KeywordsS.clean.html#save>`__\ ing a SuperBASIC program.

--------------

SAVE\_O
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SAVE\_O device\_filename \*[,range]\*(THOR XVI)  or SAVE\_O [device\_] filename \*[,range]\*(Toolkit II)  or SAVE\_O (SMS only)  |
+----------+-------------------------------------------------------------------+
| Location |  THOR XVI, Toolkit II                                             |
+----------+-------------------------------------------------------------------+

 This command operates in exactly the same manner as SAVE, except that
the file is automatically overwritten if it already exists.

**NOTE**

This will not overwrite a sub-directory file and will create the same
problem as SAVE.

**CROSS-REFERENCE**

See `SAVE <KeywordsS.clean.html#save>`__!

--------------

SAVEPIC
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SAVEPIC file$                                                    |
+----------+-------------------------------------------------------------------+
| Location |  PICEXT                                                           |
+----------+-------------------------------------------------------------------+

 This command saves the screen contents (from $20000) to the specified
file, which has to be given as a string and must include the full
filename. The file which will be created is 32K long. SBYTES
file$,SCREEN,32768
 does exactly the same.

**NOTE**

SAVEPIC makes the same assumptions and suffers from the same
compatibility problems as LOADPIC.

**CROSS-REFERENCE**

`LOADPIC <KeywordsL.clean.html#loadpic>`__ displays the saved screen file.

--------------

SB\_THING
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SB\_THING                                                        |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ                                                             |
+----------+-------------------------------------------------------------------+

 This command is found in versions of SMSQ which do not have the Hotkey
System II built in (most QXL versions of SMSQ). It is used to create the
SBASIC Executable Thing so that you can start SBASIC up from a Hotkey or
by using the EXEC set of commands.

**NOTE**

You must only use this command after the file HOT\_REXT has been loaded,
for example with LRESPR flp1\_HOT\_REXT.

**CROSS-REFERENCE**

Please refer to `EW <KeywordsE.clean.html#ew>`__ and
`SBASIC <KeywordsS.clean.html#sbasic>`__. Also see the Appendix on Mutliple
BASICs.

--------------

SBASIC
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SBASIC [pos] or SBASIC pos$                                      |
+----------+-------------------------------------------------------------------+
| Location |  SMS                                                              |
+----------+-------------------------------------------------------------------+

 This command is used to start up a Multiple SBASIC interpreter, which
is nearly an exact copy of the main interpreter (Job 0) and will contain
a copy of all of the toolkit commands used by the parent Job when this
command is invoked. Any toolkits subsequently loaded into the new SBASIC
interpreter cannot be used by its parent and vice versa. In its simplest
form: SBASIC
 a new Interpreter will be started up which has windows #0,#1 and #2
open as per Job 0. You can however pass either a one or two digit number
(either as a numeric pos or a string pos$), in which case only #0 will
be opened and its position will depend upon the number which has been
passed as a parameter. This enables you to start up a new SBASIC
Interpreter without its windows overlapping existing programs. If only
one digit is passed, this is taken to be the SBASIC row number. Row 0 is
at the top of the screen, Row 1 is 64 pixels from the top, Row 2 128
pixels from the top and so on... If two digits are passed, the first
digit is taken to be the SBASIC column number, the second becomes the
SBASIC row number (see above). The column number is calculated as,
Column 0 being the left hand side of the screen, Column 1 is 256 pixels
from the left, Column 2 512 pixels from the left and so on....

**CROSS-REFERENCE**

See `MB <KeywordsM.clean.html#mb>`__ and `EW <KeywordsE.clean.html#ew>`__ for other
ways of starting up additional interpreters. In addition SMS users can
use `EXEP SBASIC <KeywordsE.clean.html#exep20sbasic>`__ or even use the Exec
button from QPAC II and Minerva users can use `EX
PIPEP <KeywordsE.clean.html#ex20pipep>`__. `WMON <KeywordsW.clean.html#wmon>`__ and
`WTV <KeywordsW.clean.html#wtv>`__ can be used to reposition the SBASIC
windows. Also see the appendix on Multiple BASICs.
`JOB\_NAME <KeywordsJ.clean.html#job-name>`__ can be used to alter the name of
a SBASIC Job.

--------------

SBYTES
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SBYTES device\_file,start,length  or SBYTES device\_file,start[,length[,data[,extra[,type]]] (Minerva v1.80+)  or SBYTES [device\_]file,start,length(Toolkit II)  or SBYTES #channel,start,length(SMS only)  |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM, Toolkit II                                               |
+----------+-------------------------------------------------------------------+

 It can sometimes be useful to save part of the QL's memory to a file so
that it can be loaded back into the computer at a later date. The area
of memory saved may for example, contain a program, some machine code or
some data. The command SBYTES allows you to save length number of bytes
from the QL's memory, starting from the specified start address. The
area of memory is saved to the specified file which must include the
name of the device to be used, unless Toolkit II is present, in which
case the default data device is supported. The Toolkit II variant will
also provide you with the option of overwriting the file if it already
exists.

**Example**

(1) To save the currently displayed screen on a standard QL, use the
command: SBYTES flp1\_Example\_scr,SCREEN,32768
 Or under SMS, you can save any size screen using: SBYTES
flp1\_Example\_scr,SCR\_BASE,SCR\_LLEN\*SCR\_YLIM
 (2) The start of a program which was protected by a password could be
written along the lines of this:- 100 a=ALCHP(100) 110 IF
FTEST(flp1\_pass)=0 120 LBYTES flp1\_pass,a 130 END IF 140 pass$='' 150
PAPER#0,0:CLS#0:INK#0,7 160 PRINT #0,'Enter Password :'; 170 FOR
letter=1 TO 4 180 pass$=pass$&INKEY$(-1) 190 PRINT#0,'\*'; 200 END FOR
letter 210 PRINT #0 220 IF PEEK(a)=0 230 offset=RND(1 TO 50) 240 POKE
a,offset 250 FOR i=1 TO 4 260 POKE a+i,CODE(pass$(i))+i+offset 270 END
FOR i 280 FOR i=5 TO 100:POKE a+i,RND(100) 290 SBYTES flp1\_pass,a,100
300 ELSE 310 offset=PEEK(a) 320 FOR i=1 TO 4

330 IF CODE(pass$(i))<>PEEK(a+i)-i-offset 340 PRINT 'Access
Denied':RECHP a:STOP 350 END IF 360 END FOR i 370 END IF 380 PRINT
'Access Granted' 390 RECHP a

**NOTE 1**

On Minerva ROMs (pre v1.80), if SBYTES was aborted for some reason
whilst writing to a file, the file would be deleted. On later versions
of Minerva and all other QL ROMs, the incomplete file is kept and on
Toolkit II, the error 'Medium Full' is reported.

**NOTE 2**

On Minerva ROMs (pre v1.83) SBYTES set the wrong file type.

**NOTE 3**

The Minerva variant is unfortunately overwritten by the Toolkit II
version of this command.

**MINERVA NOTES**

On Minerva v1.80 (or later) the commands SBYTES and SEXEC have
practically become interchangeable, as both support exactly the same
parameters. All of the parameters except for the start address and
device\_file where the data is to be stored, are optional and will
default to 0 if not specified. These additional parameters have the
following uses: extraThis sets the value which is normally returned with
FXTRA (which would normally have to be altered with SetHEAD). typeThis
allows you to set two file attributes: (a) the file type - this is
normally 0 for data, or 1 for executable programs. This is calculated by
PRINT type && 255. (b) the file access key - it is generally used by
Toolkits such as QL-System to store various file attributes (such as
whether a file is read-only). This is calculated by PRINT type DIV 256.
The only problem with using this extended version of SBYTES
 instead of using SEXEC is that you must remember to specify a file type
of 1 if the file is later to be EXECuted (as this defaults to 0 in the
case of SBYTES!). For example, both of these are the same:- SBYTES
ram1\_test\_exe,code\_start,20000,500,0,1
 SEXEC ram1\_test\_exe,code\_start,20000,500

**SMS NOTE**

The fourth variant of the command allows you to save the bytes to an
existing channel which is already OPEN to a file, thus allowing you to
work more efficiently. You can use the following to error trap the
saving routine: 100 REPeat loop 110 ch=FOP\_NEW (ram1\_test\_bin) 120 IF
ch<0 130 REPORT ch 140 PRINT "Press <y> to retry, <n> to stop" 150
REPeat kLoop 160 key$=INKEY$(-1) 170 IF key$ INSTR 'yn':EXIT kLoop 180
END REPeat kLoop 190 IF key$=='y':NEXT loop 200 STOP 210 END IF 220
SBYTES #ch,131072,32768 230 EXIT loop 240 END REPeat loop 250 CLOSE #ch

**CROSS-REFERENCE**

`SBYTES\_O <KeywordsS.clean.html#sbytes-o>`__ and
`SEXEC <KeywordsS.clean.html#sexec>`__ are very similar.
`DATA\_USE <KeywordsD.clean.html#data-use>`__ allows you to alter the current
default data device. `LBYTES <KeywordsL.clean.html#lbytes>`__ allows you to
load in a block of code which has been saved with
`SBYTES <KeywordsS.clean.html#sbytes>`__ or `SEXEC <KeywordsS.clean.html#sexec>`__.

--------------

SBYTES\_O
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SBYTES\_O [device\_]file,start,length(Toolkit II only)  or SBYTES\_O device\_file,start,length (THOR XVI)  or SBYTES\_O #channel,start,length (SMS only)  |
+----------+-------------------------------------------------------------------+
| Location |  Toolkit II, THOR XVI                                             |
+----------+-------------------------------------------------------------------+

 This command is exactly the same as SBYTES except that it will
automatically overwrite an existing file of the same name.

**NOTE**

The Toolkit II version of the command supports the default data device.

**CROSS-REFERENCE**

See `SBYTES <KeywordsS.clean.html#sbytes>`__.

--------------

SCALE
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SCALE [#ch,] size,x,y  or SCALE [#ch,] -size,x,y (Minerva v1.76+)  |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 Many of the QL's graphics commands rely upon the graphics co-ordinate
system to dictate whereabouts in a window they should appear. The
command SCALE allows you to set the graphics scale in a specified window
(default #1). size dictates the graphics scale for that window by
representing the length of a line which would be drawn from the bottom
left hand corner of a window to the top left hand corner, hence the
larger the size, the more information which can appear on screen
(although this is somewhat limited by the actual resolution of the
screen!). The default size is 100. The co-ordinates x,y specify the
co-ordinate which appears in the bottom left hand corner of the screen.
When a window is opened, the scale is reset with the equivalent of SCALE
#ch,100,0,0. Although a line drawn up the side of a window will be size
 units long, the length required to draw a line along the whole of the
bottom of the window, not only depends on the value of size, but also on
the screen resolution and the shape of the given window. size\| y\| \|
\| \| \|
\|\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
(0,0) size\*factor
 x

**Example**

The following short program will draw a diagonal cross through the
middle of any given size of window, on any given screen resolution:- 100
INPUT 'Screen Resolution Width :'!ScreenX 110 INPUT 'Screen Resolution
Height :'!ScreenY 120 INPUT 'Window Width : ';wid 130 INPUT 'Window
Height : ';hi 140 INPUT 'Scale : ';size 150 WINDOW wid,hi,32,16 160
PAPER 2:INK 7:CLS 170 SCALE size,0,0 180
Xratio=ScreenX/512:Yratio=ScreenY/256 190
line\_diff=(101\*Yratio/hi)\*wid/('135.5041505'\*Xratio) 200 LINE 0,0 TO
size\*line\_diff,size 210 LINE 0,size TO size\*line\_diff,0

**NOTE 1**

Graphics drawn using the QL graphics co-ordinate system will appear in
the same place on screen in any screen MODE.

**NOTE 2**

Due to the QL's arithmetic routines, the maximum length of a line which
can be drawn upwards in a window is slightly larger than size.

**NOTE 3**

On JSU ROMs, the screen ratio is different to other ROMs, presumably due
to the different number of lines on American TVs - you would need to
change line 190 in the above example to read: 190
line\_diff=(101\*Yratio/hi)\*wid/('159.593001'\*Xratio)

**MINERVA NOTES**

Minerva ROMs (v1.76 or later) allow you to use a negative SCALE, so that
you may easily draw a picture upside down without altering all of the
different drawing commands. This is achieved by using the second syntax
of the SCALE command. Before trying to use this new variant of the
command, you will have to give your drawing some careful thought. For
instance, when designing a screen, it is best to draw this using the
normal SCALE command, and then to use Minerva's new syntax at that
stage. For example, take the following short demonstration drawing: 100
MODE 8 110 WINDOW 448,200,32,16 120 SCALE 100,0,0:PAPER 0:CLS 130 INK
2:FILL 1 140 LINE 0,0 TO 0,10 150 LINE 0,10 TO 40,30 TO 60,27 160 LINE
60,27 TO 40,24 TO 10,0 TO 0,0 170 FILL 1 180 LINE 166,0 TO 166,10 190
LINE 166,10 TO 126,30 TO 106,27 200 LINE 106,27 TO 126,24 TO 156,0 TO
166,0 210 INK 4,3 220 FILL 1:CIRCLE 83,50,32:FILL 0
 Now, to turn it upside down on Minerva, try changing line 120 to read:
120 SCALE -100,0,0:PAPER 0:CLS
 If you now try running the program, you will find that your picture no
longer appears! This is because instead of Minerva moving the graphics
origin to the top right hand corner of the window (as you might have
expected), Minerva has in effect turned the graphics output around by
180 degrees about the graphics origin (ie. the bottom left hand corner
of the window). This means that to get your picture to re-appear on
screen, you will need to redefine the graphics origin so that it has the
same values as you would expect to be in the top right hand corner of
the screen before it was turned around. Thus, the following diagram will
explain the current layout of the screen:- -size\| y\| \| \| \| \|
\|\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ (0,0)
-size\*factor
 -x In other words, in the above example, you will need to alter line
120 to read: 120 SCALE -100,166,100:PAPER 0:CLS
 The program will now display the picture upside down, having now
altered the orientation of the display to the following diagram:- x
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_(0,0)
size\| \| \| \| \|\| \| \| \|\| \|\| y
\|\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\|
(166,100) size\*factor

**CROSS-REFERENCE**

`CIRCLE <KeywordsC.clean.html#circle>`__, `ARC <KeywordsA.clean.html#arc>`__,
`LINE <KeywordsL.clean.html#line>`__ and `POINT <KeywordsP.clean.html#point>`__ all
rely on the current `SCALE <KeywordsS.clean.html#scale>`__.

--------------

SCLR
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SCLR colour                                                      |
+----------+-------------------------------------------------------------------+
| Location |  Fast PLOT/DRAW Toolkit                                           |
+----------+-------------------------------------------------------------------+

 This command causes the screen (pointed to by SCRBASE) to be cleared
with the given colour. This colour ranges from 0 (black) to 7 (white).
There is no default.

**Example**

Run this small program and watch how your screen seems to change size.
The greater the difference in apparent size, the worse your monitor
(there are more intelligent criteria as to the capability of your
monitor, for example radiance): 100 MODE 4:SCRBASE 110 REPeat
screen\_test 120 FOR n=0,2,4,6: SCLR n 130 END REPeat screen\_test

**NOTE**

See REFRESH !

**WARNING**

Never use SCLR without a parameter! The system will crash!

**CROSS-REFERENCE**

`PLOT <KeywordsP.clean.html#plot>`__, `DRAW <KeywordsD.clean.html#draw>`__,
`REFRESH <KeywordsR.clean.html#refresh>`__ and
`SCRBASE <KeywordsS.clean.html#scrbase>`__ are the other commands connected
with this one.

--------------

SCRBASE
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SCRBASE [adress]                                                 |
+----------+-------------------------------------------------------------------+
| Location |  Fast PLOT/DRAW Toolkit                                           |
+----------+-------------------------------------------------------------------+

 All commands belonging to the fast graphics Toolkit use the specified
parameter set with this command as the base address for their
operations: SCLR, PLOT, DRAW and REFRESH. This is intended to allow
background drawing. The default address is the address of the visible
screen, SCREEN.

**Example 1**

A simple demonstration and an animated version. 100 SCRBASE
ALCHP(32768): SCLR 0 110 FOR t=0 TO 2\*PI STEP PI/32 120
x1=188\*SIN(t)+255: y1=127\*COS(t)+127 130 x2=188\*SIN(t+PI)+255:
y2=127\*SIN(t+PI)+127 140 DRAW x1,y1 TO x2,y2 ,7 150 END FOR t 160
REFRESH: CLCHP 100 Pics=INT((FREE\_MEM-4096)/32768) 110 DIM base(Pics)
120 FOR c=2\*PI/Pics TO 2\*PI STEP 2\*PI/Pics 130
base(c/2/PI\*Pics)=ALCHP(32768) 140 SCRBASE base(c/2/PI\*Pics): SCLR 0
150 FOR t=0 TO 2\*PI STEP PI/4 160 x1=188\*SIN(t)+255:
y1=127\*COS(t)+127 170 x2=188\*SIN(t+c)+255: y2=127\*SIN(t+c)+127 180
DRAW x1,y1 TO x2,y2 ,7 190 END FOR t 200 END FOR c 210 : 220 REPeat
Animation 230 FOR c=1 TO Pics: SCRBASE base(c): REFRESH 240 IF
KEYROW(1)=8 THEN EXIT Animation 250 END REPeat Animation 260 CLCHP

**Example 2**

Varying the base address by steps equal to the value of SCRINC (normally
128) simulates vertical scrolling. The first program views memory, the
other one loads an uncompressed 32K screen and then 'scrolls it in'. 100
FOR A=0 TO 786432 STEP 128 110 SCRBASE A 120 REFRESH 130 END FOR A
 The second program appears on the next page. 100
SCRFILE$="MDV1\_SCREEN\_SCR" 110 SCROLLSPEED=4 120 : 130
ADR=ALCHP(65536) 140 LBYTES SCRFILE$,ADR+32768 150 POKE$
ADR,FILL$(CHR$(0),32767): POKE SCREEN+32766,0 160 FOR A=ADR TO ADR+32768
STEP SCROLLSPEED\*SCRINC 170 SCRBASE A 180 REFRESH 190 END FOR A 200
RECHP ADR

**CROSS-REFERENCE**

See `SCLR <KeywordsS.clean.html#sclr>`__, `PLOT <KeywordsP.clean.html#plot>`__,
`DRAW <KeywordsD.clean.html#draw>`__ and `REFRESH <KeywordsR.clean.html#refresh>`__
for fast background drawing. `SCR\_STORE <KeywordsS.clean.html#scr-store>`__
and `SCR\_REFRESH <KeywordsS.clean.html#scr-refresh>`__ are ideal to create
and display animated displays. Compare
`SCR\_BASE <KeywordsS.clean.html#scr-base>`__!

--------------

SCREEN
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SCREEN  or SCREEN [(#ch)] (FN Toolkit only)                      |
+----------+-------------------------------------------------------------------+
| Location |  Beuletools, Fn                                                   |
+----------+-------------------------------------------------------------------+

 The visible screen on a standard QL is actually 32K of memory. The
start address of the screen is normally 131072, but can change on
Minerva and higher resolution implementations of the QL, so the start
address should be determined before accessing the screen directly. The
function SCREEN returns that start address.

**NOTE**

The FN Toolkit version allows you to specify a channel - if the channel
is specified, then the start address for the screen on which that
channel is open is returned. This is mainly only of use to Minerva and
Amiga QDOS users who can have windows open on either the Default Screen
or the Other Screen (provided their dual screen mode is active). Thus
SCREEN(#3) can be used to find the start address of the second screen if
that is where #3 is located.

**CROSS-REFERENCE**

See `SCR\_BASE <KeywordsS.clean.html#scr-base>`__.

--------------

SCRINC
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SCRINC [(#ch)]                                                   |
+----------+-------------------------------------------------------------------+
| Location |  Fn                                                               |
+----------+-------------------------------------------------------------------+

 The screen width is not fixed on QDOS computers, QL Emulators and
future hardware expansions (graphic cards) offer different screen modes
with different resolutions. The function SCRINC returns the screen width
relating to the screen upon which the given channel (default #0) is
located. The width is returned as the number of bytes needed to store a
line of pixels: the standard QL mode 4 and mode 8 therefore always
return 128 = 512/4. However, it is not always true that the number of
bytes required to store a line of pixels is equal to the number of
pixels DIV 4 and you should therefore use this function or similar.

**Example**

See the second listing at the second example for SCRBASE.

**CROSS-REFERENCE**

`SCREEN <KeywordsS.clean.html#screen>`__ returns the start address of the
screen. See also `SCR\_LLEN <KeywordsS.clean.html#scr-llen>`__

--------------

SCROLL
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SCROLL [#ch,] distance [,area]                                   |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 This command allows you to move the contents of a given window (default
#1) up or down by a specified number of pixels (distance). A positive
value for distance will move the contents of the window downwards,
whereas a negative distance will move them upwards. As the contents are
moved, if they move outside of the limits of the window, they will be
lost. The space left by the movement of the window's contents, will be
filled with the current PAPER colour. If you use the third parameter
(area), you can specify that only part of the window is to be moved, by
using the following values:- 0 This is the default - move whole window.
1 Move the area above the text cursor line. 2 Move the area below the
text cursor line. If you wish to move other areas of a window, the
easiest method is to open another window over that part of the window
which you want to move, and then use SCROLL and/or PAN on that new
window (see example below).

**Example**

A short demonstration routine of SCROLL and PAN: 100 MODE 4 110 WINDOW
440,200,32,16:PAPER 2:CLS 120 INK 7:CSIZE 3,1 130 AT 0,6:PRINT 'QL
KEYWORD MANUAL' 140 OPEN #3,scr\_448x200a32x16:PAPER#3,2 150 AT
5,6:PRINT 'QL KEYWORD MANUAL' 160 FOR i=1 TO 37 170 WINDOW
#3,40,200,432,16 180 SCROLL #3,20 190 PAUSE 5 200 WINDOW #3,440,20,32,16
210 PAN #3,40 220 PAUSE 5 230 WINDOW #3,40,200,32,16 240 SCROLL #3,-20
250 PAUSE 5 260 WINDOW #3,440,20,32,196 270 PAN #3,-40 280 PAUSE 5 290
END FOR i 300 CSIZE 0,0

**NOTE**

QL ROMs (other than v6.41 of THOR XVI, SMS and v1.63/v1.64 of Minerva)
allow SCROLL to be used to access various direct TRAP #3 calls to the
operating system (as with PAN and CLS). The first parameter to be
supplied represents the D1 parameter in machine code, whereas the second
parameter represents D0. In any case, both parameters must be integers
(ie. in the range -32768..32767). Normally to find out number to give
D0, take the routine's D0 value and subtract 24 (eg. IOG.DOT=48,
48-24=24). However, if the routine's value is 24 or less, subtract 24
and then add this negative value to 128. Some useful routines which can
be accessed are: SCROLL #3,0,121 moves the cursor to column 0 in #3
(IOW.SCOL, D0=$11) SCROLL 0,24 has the same effect as CLS 16, ie. it
calls (IOG.DOT - D0=$30), which effectively carries out the command
POINT 0,0. SCROLL x,17 sets the ink colour to x
 (IOW.SINK,D0=$29) SCROLL #3,n%,42 sets the file pointer in #3 to n%
 (IOF.POSA,D0=$42) SCROLL #3,n%,43 should move the file pointer in #3 on
n%
 places (IOF.POSR,D0=$43) Unfortunately, not all values for both
parameters will work on all ROMs and this is a hit and miss way of
programming the QL. Luckily, the wealth of Toolkits available should
mean that there is a legal means of accessing these routines, using
Toolkit keywords, including MTRAP and QTRAP.

**CROSS-REFERENCE**

`PAN <KeywordsP.clean.html#pan>`__ allows you to move the contents of a window
sideways. `WINDOW <KeywordsW.clean.html#window>`__ allows you to specify the
area of the screen which a window covers.
`IO\_TRAP <KeywordsI.clean.html#io-trap>`__ allows you to access machine code
routines directly. See also `QTRAP <KeywordsQ.clean.html#qtrap>`__,
`BTRAP <KeywordsB.clean.html#btrap>`__ and `MTRAP <KeywordsM.clean.html#mtrap>`__.

--------------

SCROF
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SCROF                                                            |
+----------+-------------------------------------------------------------------+
| Location |  Ecran Manager                                                    |
+----------+-------------------------------------------------------------------+

 This command forces the current screen to become invisible - the effect
of SCROF lasts until the next task switch under the Pointer Environment
or until one of the standard MODE commands (ie. not dealing with dual
screen mode) or NEW are issued.

**Example**

SCROF

**NOTE**

See SSAVE.

**CROSS-REFERENCE**

`SCRON <KeywordsS.clean.html#scron>`__ switches the screen to visible.

--------------

SCRON
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SCRON                                                            |
+----------+-------------------------------------------------------------------+
| Location |  Ecran Manager                                                    |
+----------+-------------------------------------------------------------------+

 The SCRON command makes the screen visible once again after it has been
disabled with SCROF.

**Example**

SCRON

**NOTE**

See SSAVE.

**CROSS-REFERENCE**

`SCROF <KeywordsS.clean.html#scrof>`__.

--------------

SCR2DIS
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR2DIS                                                          |
+----------+-------------------------------------------------------------------+
| Location |  Super Gold Card                                                  |
+----------+-------------------------------------------------------------------+

 Some programs make use of the QL's ability to support a second screen
(on a standard QL this is normally stored at $28000 (hex) - it
overwrites the system variables which are moved to another area in
memory). You can therefore see why it is important never to make
assumptions about the location of the screen or system variables in
memory (use SCREEN or SYS\_BASE instead). Minerva extends this second
screen even further, allowing you to operate the computer in two-screen
mode, with programs being started up on one of two screens (thus
allowing you to have completely different displays on each screen) see
MODE. The main problem with this second screen is that it slows down the
operation of the computer and therefore if you do not intend to use the
second screen, you may wish to disable it. You can disable the second
screen with the command SCR2DIS - this setting will be stored in memory
by the Gold Card and the second screen will henceforth always be
disabled.

**WARNING**

Some programs (mainly games) will not work properly with the second
screen disabled.

**CROSS-REFERENCE**

`SCR2EN <KeywordsS.clean.html#scr2en>`__ re-enables the second screen again.

--------------

SCR2EN
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR2EN                                                           |
+----------+-------------------------------------------------------------------+
| Location |  Super Gold Card                                                  |
+----------+-------------------------------------------------------------------+

 This command is the complementary command to SCR2DIS - it enables the
QL's second screen and is also memorised by the Super Gold Card so that
the second screen will always be available for use by programs.

**NOTE**

In order to make proper use of the second screen, you will still need to
startup Minerva in dual screen mode and use the appropriate MODE
commands. Non-Minerva QLs can still use the second screen by using
various machine code techniques.

**CROSS-REFERENCE**

See `SCR2DIS <KeywordsS.clean.html#scr2dis>`__ for more information.

--------------

SCR\_BASE
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR\_BASE [(#ch)]                                                |
+----------+-------------------------------------------------------------------+
| Location |  ATARI\_REXT (v2.25+), SMSQ/E                                     |
+----------+-------------------------------------------------------------------+

 This function returns the base address of the screen linked to the
specified channel (default #0), this is normally 131072 on standard QLs
but can alter on other resolutions or if dual screen mode is supported.
On machines which support higher resolutions, the screen base will only
be at the standard address of 131072 if you configure the machine to
start up in 512x256 and even here there is no guarantee - see the
documentation for the particular QL resolution you are using.

**NOTE**

If the specified channel is not open then Invalid Channel ID will be
reported. However, if no channel is specified and #0 is not open, then a
special window will be opened for #0 on screen, which may destroy what
is already on screen.

**CROSS-REFERENCE**

`SCREEN <KeywordsS.clean.html#screen>`__ is similar. See also
`SCR\_XLIM <KeywordsS.clean.html#scr-xlim>`__,
`SCR\_YLIM <KeywordsS.clean.html#scr-ylim>`__ and
`SCR\_LLEN <KeywordsS.clean.html#scr-llen>`__.
`A\_OLDSCR <KeywordsA.clean.html#a-oldscr>`__ can help some older software to
work. You can also use `PRINT
CHAN\_L(#1,50) <KeywordsP.clean.html#print20chan-l(#1,50)>`__ instead of
`SCR\_BASE <KeywordsS.clean.html#scr-base>`__.

--------------

SCR\_LLEN
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR\_LLEN [(#ch)]                                                |
+----------+-------------------------------------------------------------------+
| Location |  ATARI\_REXT (v2.25+), SMSQ/E                                     |
+----------+-------------------------------------------------------------------+

 This function returns the number of bytes required to hold one line of
pixels on the current screen resolution attached to the specified
channel (default #0). On a standard QL 512x256 resolution, this is
normally 128 bytes but can alter on other resolutions.

**NOTE**

As with SCR\_BASE, if the specified channel is not open then Invalid
Channel ID will be reported. However, if no channel is specified and #0
is not open, then a special window will be opened for #0 on screen,
which may destroy what is already on screen.

**WARNING**

You should never assume that the number of bytes required to store a
line is the number of pixels DIV 4 - always use this function instead.

**CROSS-REFERENCE**

`SCRINC <KeywordsS.clean.html#scrinc>`__ is similar. See also
`SCR\_XLIM <KeywordsS.clean.html#scr-xlim>`__,
`SCR\_YLIM <KeywordsS.clean.html#scr-ylim>`__ and
`SCR\_BASE <KeywordsS.clean.html#scr-base>`__. On QL ROMs after JM, you can
also use `PRINT
CHAN\_B%(#1,104) <KeywordsP.clean.html#print20chan-b(#1,104)>`__.

--------------

SCR\_REFRESH
~~~~~~~~~~~~

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR\_REFRESH address                                             |
+----------+-------------------------------------------------------------------+
| Location |  SuperWindow Toolkit                                              |
+----------+-------------------------------------------------------------------+

 This command copies a screen (or a portion of a screen) which has been
saved in memory at the specified address using SCR\_STORE back to the
same position on the visible display screen.

**NOTE**

It is unknown at present whether these commands check for the start
address of the screen and its dimensions and therefore they may not work
on some higher resolutions. Unfortunately, we do not have access to the
toolkit at present.

**CROSS-REFERENCE**

`SCR\_STORE <KeywordsS.clean.html#scr-store>`__ stores a window or rectangle
taken from the display. See also `W\_SHOW <KeywordsW.clean.html#w-show>`__ and
`REFRESH <KeywordsR.clean.html#refresh>`__.

--------------

SCR\_SAVE
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR\_SAVE flag                                                   |
+----------+-------------------------------------------------------------------+
| Location |  MutiBASIC v4.0+ (DIY Toolkit - Vol M)                            |
+----------+-------------------------------------------------------------------+

 This command is used to specify whether the current screen display and
mode should be stored along with the program when the UNLOAD or RESAVE
commands are used. The setting depends on the value of flag: 0 Do not
store the screen display and mode. 1 (This is the default). Store the
screen display and mode so that it is redisplayed when RELOAD is used.
-1This tells RELOAD to ignore the screen details (if any) stored with
the program - use SCR\_SAVE 1 if you want to see them.

**NOTE**

Beware that this toolkit only supports 512x256 resolution and expects
the screen base to be at 131072.

**CROSS-REFERENCE**

`UNLOAD <KeywordsU.clean.html#unload>`__ contains more details about this
toolkit.

--------------

SCR\_SIZE
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR\_SIZE [(#channel)] or SCR\_SIZE (width\_x,width\_y [[,pos\_x],pos\_y] )  |
+----------+-------------------------------------------------------------------+
| Location |  SuperWindow Toolkit                                              |
+----------+-------------------------------------------------------------------+

 This function will return the space in bytes, a window (default #1) or
rectangle on the screen, needs to be stored with SCR\_STORE. Windows are
specified just by reference to their channel number, whereas rectangles
by their width and height. Naturally, the size of any shape is
independent from its position but the co-ordinates may be also added as
parameters without invoking an error message - or influencing the result
of SCR\_SIZE.

**WARNING**

SCR\_SIZE with a channel number will not work correctly if the Window
Manager is present because of the different window definition blocks.
Use either the second syntax or on a standard QL calculate the size
yourself: size=8+width\_x\*width\_y/4

**CROSS-REFERENCE**

`SCR\_STORE <KeywordsS.clean.html#scr-store>`__ stores a part of the screen in
RAM and `SCR\_REFRESH <KeywordsS.clean.html#scr-refresh>`__ copies it back.
See also `WMAN$ <KeywordsW.clean.html#wman>`__.
`CHAN\_W% <KeywordsC.clean.html#chan-w>`__ is much more flexible.

--------------

SCR\_STORE
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR\_STORE [#channel,] address  or SCR\_STORE width,height,x,y TO address  |
+----------+-------------------------------------------------------------------+
| Location |  SuperWindow Toolkit                                              |
+----------+-------------------------------------------------------------------+

 This command allows you to store a part of the screen at the given
address in RAM. The section of the screen to be stored can be either a
window channel number (default #1) or the dimensions of a rectangle. The
amount of memory SCR\_STORE needs is returned by SCR\_SIZE. SCR\_STORE
needs eight bytes plus the actual amount of space taken up by the
section of the screen. These four words (one word consists of two bytes)
are kept at the start of the storage area and contain the size and
position of the screen part as passed by the second syntax above. They
can easily be read like this: width = PEEK\_W (adress) height = PEEK\_W
(adress+2) x = PEEK\_W (adress+4) y = PEEK\_W (adress+6)

**Example**

The SCR\_STORE and SCR\_REFRESH commands are ideal tools to create and
show animations. The actual speed of SCR\_REFRESH is independent from
the contents of the screen, so it does not matter how long it took to
create the pictures... Enjoy it. 100 wx=70: wy=70: px=100: py=100 110
OPEN#3,"scr\_"&wx&"x"&wy&"a"&px&"x"&py: CLS#3 120 size=SCR\_SIZE(wx,wy):
DIM adr(20) 130 bx=2: by=2: pmax=10 140 : 150 FOR p=1 TO pmax 160
adr(p)=ALCHP(size) 170 FOR x=0 TO wx-bx STEP bx 180
a=2\*SQRT(p)\*x/wx-SQRT(p) 190 FOR y=0 TO wy-by STEP by 200
b=2\*SQRT(p)\*y/wy-SQRT(p) 210 z=((a\*a+b\*b)^^(a\*b-b\*b)) MOD 7 220
BLOCK#3,bx,by,x,y,z 230 END FOR y 240 END FOR x 250 SCR\_STORE
wx,wy,px,py TO adr(p) 260 END FOR p 270 : 280 REPeat Animation 290 FOR
p=1 TO pmax: SCR\_REFRESH adr(p) 300 FOR p=pmax-1 TO 2 STEP -1:
SCR\_REFRESH adr(p) 310 IF KEYROW(1)=8 THEN EXIT Animation 320 END
REPeat Animation 330 CLCHP

**CROSS-REFERENCE**

See `SCR\_REFRESH <KeywordsS.clean.html#scr-refresh>`__ and
`SCR\_SIZE <KeywordsS.clean.html#scr-size>`__. See also
`W\_STORE <KeywordsW.clean.html#w-store>`__ and
`W\_CRUNCH <KeywordsW.clean.html#w-crunch>`__. Use
`ALCHP <KeywordsA.clean.html#alchp>`__ to set aside some memory to hold the
copy of the window. Use `RECHP <KeywordsR.clean.html#rechp>`__ to remove that
memory definition.

--------------

SCR\_XLIM
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR\_XLIM [(#ch)]                                                |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E                                                           |
+----------+-------------------------------------------------------------------+

 This function is the same as QFLIM(#ch,0) except that the channel
parameter is optional (it defaults to #0).

**NOTE**

As with SCR\_BASE, if the specified channel is not open then Invalid
Channel ID will be reported. However, if no channel is specified and #0
is not open, then a special window will be opened for #0 on screen,
which may destroy what is already on screen.

**CROSS-REFERENCE**

`QFLIM <KeywordsQ.clean.html#qflim>`__ and `XLIM <KeywordsX.clean.html#xlim>`__ are
similar. See also `DISP\_SIZE <KeywordsD.clean.html#disp-size>`__ and
`SCR\_YLIM <KeywordsS.clean.html#scr-ylim>`__

--------------

SCR\_YLIM
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SCR\_YLIM [(#ch)]                                                |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E                                                           |
+----------+-------------------------------------------------------------------+

 This function is the same as QFLIM(#ch,1) except that the channel
parameter is optional (it defaults to #0).

**NOTE**

As with SCR\_BASE, if the specified channel is not open then Invalid
Channel ID will be reported. However, if no channel is specified and #0
is not open, then a special window will be opened for #0 on screen,
which may destroy what is already on screen.

**CROSS-REFERENCE**

`QFLIM <KeywordsQ.clean.html#qflim>`__ and `YLIM <KeywordsY.clean.html#ylim>`__ are
similar. See also `SCR\_XLIM <KeywordsS.clean.html#scr-xlim>`__,
`SCR\_BASE <KeywordsS.clean.html#scr-base>`__ and
`SCR\_LLEN <KeywordsS.clean.html#scr-llen>`__.

--------------

SDATE
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SDATE year,month,day,hours,minutes,seconds  or SDATE year,month,day,hours,minutes (SMS v2.57+)  or SDATE time (Minerva, SMS)  or SDATE TO time (THOR XVI)  |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 The QL has an internal clock which contains the current date and time.
Unfortunately, this clock is corrupted every time that the QL is
switched on and off (and even in some cases when the QL is reset). This
means that the clock has to be set manually every time that the system
is re-booted. Because of this, various battery-backed clocks have
appeared on the market which retain the time whilst the QL is turned off
and then the QL clock is generally reset to the same time as the battery
backed clock when it is switched back on. This command allows you to set
the internal QL clock to a specified date and time. Each parameter in
the first syntax must be a numeric value. The second syntax is similar
to the first, but is only supported on later versions of SMS. This
variant accepts just five parameters and assumes that the seconds is to
be set to zero. The third and fourth syntaxes allow you to set the time
and date by the number of seconds since Midnight on 1st January 1961.
This thus allows you to copy the date from one QL to another very simply
over the Network: 100 temp\_file$='n1\_ram1\_temp' 110
er=FOP\_NEW(temp\_file$) 120 IF er>0 130 CLOSE #er:SDATE TO
FUPDT(\\temp\_file$) 140 DELETE temp\_file$ 150 END IF

**Example**

SDATE 1993,1,1,0,0,0
 sets the internal clock to the start of 1993.

**NOTE 1**

This may also affect battery backed clocks - see their instructions. In
particular on the THOR XVI the battery backed clock is automatically
reset, whereas on earlier THORs the command SET\_CLOCK was needed.

**NOTE 2**

Unfortunately, current versions of Minerva and SMS will not accept the
THOR's syntax, nor vice versa.

**NOTE 3**

On the QXL, before v2.57 of SMS the time would not be set correctly if
seconds=0 or seconds=1. The clock could still be wrong by 1 second until
v2.73 which fixed this problem on MOST PCs.

**CROSS-REFERENCE**

`PROT\_DATE <KeywordsP.clean.html#prot-date>`__ allows you to prevent
`SDATE <KeywordsS.clean.html#sdate>`__ from altering a battery backed clock.
`ADATE <KeywordsA.clean.html#adate>`__ allows you to alter the time by a
specified number of seconds. `DATE <KeywordsD.clean.html#date>`__ lets you
read the current date and time as a single figure.
`DATE$ <KeywordsD.clean.html#date>`__ and `DAY$ <KeywordsD.clean.html#day>`__
return various details about the current date and time. These functions
can also be used to find out details concerning a given date without
having to use `SDATE <KeywordsS.clean.html#sdate>`__ beforehand to change the
system date. `A\_SDATE <KeywordsA.clean.html#a-sdate>`__ and
`SET\_CLOCK <KeywordsS.clean.html#set-clock>`__ alter the battery backed
clocks on the ST/QL Emulator and THOR respectively.

--------------

SDP\_DEV
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SDP\_DEV device                                                  |
+----------+-------------------------------------------------------------------+
| Location |  Gold Card, Trump Card, SDUMP\_REXT, ST/QL                        |
+----------+-------------------------------------------------------------------+

 The command SDP\_DEV allows you to dictate where output from the SDUMP
device should be sent. Initially, all output is sent to ser, however you
may wish to alter this. Under SMS, you will need to LRESPR SDUMP\_REXT
provided on the distribution disk.

**Example**

SDP\_DEV n1\_flp1\_Dump
 will cause all future output from the SDUMP device to be sent to a file
flp1\_Dump on the machine with NetID=1 in the Network.

**CROSS-REFERENCE**

`SDUMP <KeywordsS.clean.html#sdump>`__ allows you to send output to the
specified device from SuperBASIC.

--------------

SDP\_KEY
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SDP\_KEY [key$]                                                  |
+----------+-------------------------------------------------------------------+
| Location |  Gold Card, Trump Card, SDUMP\_REXT,                              |
+----------+-------------------------------------------------------------------+

ST/QL
 In order to facilitate easy screen dumps, the command SDP\_KEY will set
up a hotkey which when pressed together with <ALT> will cause the whole
of the screen starting at $20000 to be sent to the SDUMP device. Under
SMS, you will first need to LRESPR SDUMP\_REXT provided on the
distribution disk to use this command. As with ALTKEY, if the specified
key$ is in upper case, you will need to press <ALT><SHIFT> together with
the key, or <ALT> with the key if capslock is on. SDP\_KEY without any
parameters inhibits the hotkey.

**Example**

SDP\_KEY p
 will cause the screen to be dumped each time that <ALT><P> is pressed.

**CROSS-REFERENCE**

`SDP\_DEV <KeywordsS.clean.html#sdp-dev>`__ allows you to alter where the
output is to go. See `SDP\_SET <KeywordsS.clean.html#sdp-set>`__ and
`SDUMP <KeywordsS.clean.html#sdump>`__.

--------------

SDP\_SET
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SDP\_SET printer [,scale [,inverse [,random]]]                   |
+----------+-------------------------------------------------------------------+
| Location |  Gold                                                             |
+----------+-------------------------------------------------------------------+

Card, Trump Card, SDUMP\_REXT, ST/QL
 SDP\_SET allows you to choose the type of printer attached to the
output device, together with how the output is to appear. Under SMS, you
will first need to LRESPR SDUMP\_REXT provided on the distribution disk
to use this command. There are currently 23 types of printer supported,
numbered 1...23. You can also specify the print scale to be used and
whether or not the screen is to be printed in inverse colours (by
setting the inverse parameter to 1). You can even specify that a random
element is to be taken into account in converting the colours to gray
shades on the printer (again by setting the random parameter to 1). The
effects of these different parameters all depend upon the printer
attached to the output port and the size and shape of the area being
dumped. The scale will affect the density of the dots on the printed
page. Unfortunately, this does mean that at some of the lower densities,
not all of the screen can be printed on an 80 column printer (See the
columns headed Max Width in the table below). If any one of the
parameters is not specified, that particular setting will remain
unchanged. If you do not have one of the printers currently supported,
try out the various dump routines to see which one best suits your
needs. For example, users of the Epson Inkjet range of printers will
find that the Epson LQ2500 24 pin colour driver is very effective. The
range of printers and scales currently supported is as follows:

MODE 4 SCREENS MODE 8 SCREENS PrinterScaleDotsLines\|DotMax
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

--------------

Ratio\|DotMax
~~~~~~~~~~~~~

--------------

Ratio Per InPer In\|RatioWidth\|RatioWidth
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1 Epson MX80112072\|1x1512

--------------

1.23\| or similar16072\|\|1x1256

--------------

1.23 26072\|1x2480

--------------

1.23\|2x2240

--------------

1.23 312072\|2x2480

--------------

1.23\|4x2240

--------------

1.23 \|\| 2 Epson FX8019072\|1x1512

--------------

0.92\| additional16072\|\|1x1256

--------------

1.23 formats29072\|1x1512

--------------

0.92\|2x1256

--------------

0.92 39072\|2x2360

--------------

0.92\|4x2180

--------------

0.92 \|\| 3 Epson FX10019072\|1x1512

--------------

0.92\| wide16072\|\|1x1256

--------------

1.23 carriage290 72 \| 1x1512 0.92 \| 2x1 256

--------------

0.92 390 72 \| 2x2512

--------------

0.92\| 4x2 256

--------------

0.92

MODE 4 SCREENS MODE 8 SCREENS PrinterScaleDotsLines\|DotMax
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

--------------

Ratio\|DotMax
~~~~~~~~~~~~~

--------------

Ratio Per InPer In\|RatioWidth\|RatioWidth
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

4 Epson JX80190 72 \| 1x1512 0.92 \| 160 72 \| \|1x1256

--------------

1.23 290 72 \| 1x1512

--------------

0.92\| 2x1256

--------------

0.92 39072 \| 2x2360

--------------

0.92 \| 4x2 180

--------------

0.92 \|\| 5 Epson LQ250018060 \| 1x1512

--------------

0.99 \| 8 pin160 60 \| \| 1x1 256

--------------

1.48 2120 60 \| 2x1512

--------------

0.74 \| \|\| 5 Epson LQ250028060 \| \| 2x1 256

--------------

0.99 8 pin380 60 \| 2x2512

--------------

0.99 \| 4x2 256

--------------

0.99 \|\| 6 Epson LQ25001120180 \| 1x2512

--------------

0.99 \| 1x1 256

--------------

0.99 24 pin2180 180 \| 2x3512

--------------

1.11 \| 3x2 256

--------------

0.99 3180 180 \| 3x4512

--------------

0.99 \| 6x4 256

--------------

0.99 \|\| 7 Epson LQ2500180 60 \| 1x1512

--------------

0.99 \| 8 pin 160 60 \| \| 1x1256

--------------

1.48 colour 2120 60 \| 2x1512

--------------

0.74 \| 28060 \| \| 2x1256

--------------

0.99 380 60 \| 2x2512

--------------

0.99 \| 4x2 256 0.99 \|\| 8 Epson LQ25001120 180 \| 1x2512 0.99 \| 1x1
256 0.99 24 pin 2180180 \| 2x3 512 1.11 \| 3x2 256

--------------

0.99 colour 3180 180 \| 3x4512 0.99 \| 6x4 256

--------------

0.99 \|\| 9 Brother HR4112072 \| 1x1512

--------------

1.23 \| 16072 \| \| 1x1 256

--------------

1.23 26072 \| 1x2480

--------------

1.23 \| 2x2 240 1.23 3120 72 \| 2x2480

--------------

1.23 \| 4x2 240 1.23 \|\| 10 Olivetti 1110 72 \| 1x1512

--------------

1.13 \| JP101 1110 108\| \|1x1256

--------------

0.75 2110 108 \| 1x1 512

--------------

0.75 \| 3x2 256

--------------

1.00 3110 72 \| 2x2 440 1.13\|4x2 220 1.13 \|\| 11 Seikosha 16063 \|
1x1480

--------------

0.70 \| 1x1 256

--------------

1.41 GP-100A 260 63 \| 1x2 480 1.41 \| 2x2 240 1.41 \|\| 12 Seikosha 160
72 \| 1x1 480 0.61 \| 1x1256

--------------

1.23 GP-250X 260 72 \| 1x2 480 1.23 \| 2x2 240 1.23 \|\| 13 Seikosha 180
80 \| 1x1 512 0.74 \| 1x1256 1.48 GP-700A 280 80 \| 1x2 512 1.48 \| 2x2
256 1.48 380 80 \| 1x2512 1.48 \| 3x2 212 0.99 \|\| 14 Canon180 80 \|
1x1 512 0.74 \| 1x1 256 1.48 PJ1080A 280 80 \| 1x2 512 1.48 \| 2x2 256

--------------

1.48 38080 \| 1x2 512 1.48 \| 3x2 212 0.99 \|\| 15 Centronics 17572 \|
1x1 512 0.77 \| 1x1 256 1.42 739 275 72 \| 1x1 512 0.77 \| 2x1 256 0.77
375 72 \| 2x2 300

--------------

0.77 \| 3x2 200 1.03 \|\|

MODE 4 SCREENS MODE 8 SCREENS PrinterScaleDotsLines\|DotMax
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

--------------

Ratio\|DotMax
~~~~~~~~~~~~~

--------------

Ratio Per InPer In\|RatioWidth\|RatioWidth
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

16 C.Itoh 7500112072 \| 1x1 512 1.23 \| 160 72 \| \| 1x1 256 1.23 2160
72 \| 2x1512 0.82 \| 2120 72 \| \| 2x1 256 1.23 3120 72 \|2x2 480 1.23
\| 4x2 240 1.23 \|\| 17 Toshiba 1180 180 \| 1x2 512

--------------

1.48 \| 2x2 256 1.48 TH 2100H2180 180 \| 2x3 512 1.11 \| 3x2 256 0.72 24
pin 3180 180 \| 3x4 512 0.99 \| 6x4 256 0.99 \|\| 18 Brother170 72 \|
1x1 512 0.72 \| 1x1 256 1.44 8056270 72 \| 1x1 512 0.72 \| 2x1 256 0.72
370 72 \| 2x2 280 0.72 \| 3x2 186 0.96 \|\| 19 Epson MX1001120 72 \| 1x1
512 1.23 \| or similar 160 72 \| \| 1x1 256 1.23 260 72 \| 1x2512 1.23
\| 2x2 256 1.23 3120 72 \| 2x2 512 1.23 \| 4x2 256 1.23 \|\| 20 Tandy
1100 72 \| 1x1 512 1.03\| DMP 105 160 72 \| \| 1x1 256 1.23 260 72 \|
1x2 512 1.23\| 2100 72 \| \| 2x1 256

--------------

1.03 3100 72 \| 2x2 400 1.03 \| 4x2 200 1.03 \|\| 21 OKI 1100 66 \| 1x1
512 1.12 \| Microline 160 66 \| \| 1x1256

--------------

1.35 82 /84 2100 66 \| 1x1 512 1.12 \| 2x1 256 1.12 OK Writer3100 66 \|
2x2 400 1.12 \| 4x2 200 1.12 \|\| 22 Fastext 80 172 72 \| 1x1512 0.74 \|
160 72 \| \| 1x1 256 1.23 260 72 \| 1x2 480 1.23 \| 2x2 240 1.23 372 72
\| 2x3 288 1.11 \| 3x2 192 0.99 \|\| 23 MT-80185 82 \| 1x1 512 0.77 \|
1x1 256 1.53 2170 82 \| 2x1 512 0.77 \| 3x1 256 1.02 3170 82 \| 3x2 425
1.02 \| 6x2 212 1.02
 The resultant dump will depend both on the current screen mode and the
chosen scale. The dot ratio column shown above represents the size of
the resultant picture as a ratio of the original. For example, if the
Dot ratio is 1x1 and you are outputting a screen of 512x256 pixels at
120 dots per inch and 72 lines per inch, you can expect the resultant
picture to be 512/120 inches across by 256/72 inches down. If however,
the Dot ratio was 1x2 (with the same number of dots per inch and lines
per inch as above), then the resultant picture will be 512/120 inches
across by 2\*256/72 inches down. The ratio column in the above table
shows the resultant ratio between the vertical size/horizontal size. The
nearer that this ratio is to 1.00, the more circular your screen circles
will appear on paper. The default is printer 1, scale 1, inverse 1,
random 0.

**NOTE**

There is no check on the parameters, other than to ensure that there are
the correct number of parameters.

**CROSS-REFERENCE**

`SDUMP <KeywordsS.clean.html#sdump>`__ actually prints the screen using the
chosen format.

--------------

SDUMP
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SDUMP #ch  or SDUMP [width,height,xpos,ypos] or SDUMP [{address \| address,width,height,xpos,ypos}] |
+----------+-------------------------------------------------------------------+
| Location |  Gold Card, Trump Card,                                           |
+----------+-------------------------------------------------------------------+

SDUMP\_REXT, ST/QL
 The command SDUMP allows you to dump a screen (or part of a screen) to
a printer (or a file), using one of the in-built formats (one of which
will hopefully work on your printer!) - see SDP\_SET. Under SMS, you
will first need to LRESPR SDUMP\_REXT provided on the distribution disk
to use this command. The first variant is the simplest, it will dump the
whole of the contents of the specified window #ch to the printer. If the
second variant is used, SDUMP will dump the whole of the screen defined
by widthXheightAxposXypos (using absolute pixel co-ordinates). If no
parameters are supplied, SDUMP will dump the whole screen. The third
variant of the command is intended to dump a screen which has been
stored under the Pointer Environment's PSAVE function. The address
returned by PSAVE should be used as the first parameter of the SDUMP
command. If no further parameters are specified, the whole area stored
at the specified address will be dumped, otherwise you can specify the
area of that buffer to be dumped in much the same way that you can
specify an area of the screen to be dumped.

**Example**

OPEN #3,scr\_448x200a32x16:SDUMP #3:CLOSE #3
 and SDUMP 448,200,32,16
 are the same.

**NOTE 1**

Some early versions of SDUMP expect the screen to start at 131072 and be
512x256 pixels in size and can therefore get very confused in dual
screen mode on Minerva and Amiga QDOS. However, later versions supplied
with SMS check the screen size and base when the toolkit is linked into
memory and expect it to remain the same afterwards!

**NOTE 2**

SDUMP does not work on Minerva, unless you have v2.23 (or later) of the
Trump Card / Gold Card. If you have an earlier version of Toolkit II and
want to use SDUMP, you have to ensure that another Job (such as FSERVE)
is running when SDUMP is issued.

**NOTE 3**

Once SDUMP has started its work, it is not easy to abort it early - any
further attempt to use the serial port will result in the error 'In
Use'.

**NOTE 4**

If you have directed the output to a file, the file will be
automatically overwritten if necessary.

**CROSS-REFERENCE**

`SDP\_SET <KeywordsS.clean.html#sdp-set>`__ allows you to alter the printer
format. `SDP\_KEY <KeywordsS.clean.html#sdp-key>`__ allows you to set up a
hotkey to dump the screen. `SDP\_DEV <KeywordsS.clean.html#sdp-dev>`__ allows
you to alter the device where the dump is to be sent.

--------------

SEARCH
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SEARCH (add1 TO add2, tofind$)  or SEARCH (add1 TO add2, tofind$ [!] )(BTool only)  |
+----------+-------------------------------------------------------------------+
| Location |  TinyToolkit, BTool                                               |
+----------+-------------------------------------------------------------------+

 This function scans RAM memory from address add1 to add2 for the given
string tofind$ and returns the address of its first occurrence or zero
if it was not found. The search is not case-dependent in the TinyToolkit
version whilst BTool introduces an optional switch: a '!' after tofind$
 disables case-sensitivity and reduces speed.

**Example**

The following small program will scan the whole memory, ROM included,
from adr onwards for string$. Tiny-Toolkit SEARCH is assumed, PHYSTOP is
also necessary: 100 string$="dev v" : REMark what we are looking for 110
add=0 : REMark start address 120 MODE 4: CSIZE 0,0: PAPER 0: INK 5: CLS
130 REPeat searching 140 add=SEARCH(add+1,PHYSTOP-add,string$) 150 IF
NOT add THEN EXIT searching 160 PRINT \\"Address ="!add 170 PRINT
PEEK$(add-20,19); 180 INK 7: PRINT PEEK$(add,LEN(string$)); 190 INK 5:
PRINT PEEK$(add+LEN(string$),20) 200 END REPeat searching 210 PRINT
"That's all."

**NOTE**

The search string tofind$ will always be found at least twice in memory
because tofind$ itself needs to be stored somewhere.

**CROSS-REFERENCE**

`PEEK$ <KeywordsP.clean.html#peek>`__, `DEV\_USE <KeywordsD.clean.html#dev-use>`__.
See other implementation of `SEARCH <KeywordsS.clean.html#search>`__. See
`MSEARCH <KeywordsM.clean.html#msearch>`__,
`SEARCH\_MEM <KeywordsS.clean.html#search-mem>`__ and
`TTFINDM <KeywordsT.clean.html#ttfindm>`__ also.

--------------

SEARCH
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SEARCH (array$, tofind$, start, compare [,row] )                 |
+----------+-------------------------------------------------------------------+
| Location |  ARRAY                                                            |
+----------+-------------------------------------------------------------------+

 The function SEARCH searches in a two or three-dimensional string array
array$ for the string tofind$. The search is not case-sensitive but
nevertheless very fast (as the example shows). SEARCH will always look
at one row only - there is just one if the array is two-dimensional but
for three-dimensional string arrays (where there are in fact
two-dimensions of strings because the third dimension is the maximum
string length) the optional row parameter which defaults to the first
row can be used to select a certain row. The start parameter allows you
to tell SEARCH from which element in the row onwards it should look
(remember that the first element is indexed with 0). compare specifies
the number of characters at the start of each entry to ignore, so 0 will
search the whole entry for tofind$. The search stops if tofind$ was
found in an entry but not if the entry and tofind$ are identical. SEARCH
returns the entry index or -1 if no suitable entry was found.

**Example**

Lines 100 to 170 of the following example initialise the name$ array
with n (here 1000) random strings of varying length, from four to 10
characters; this can take a while. After that, the whole array is
scanned for the string QL and all occurrences are listed. If you want to
check out the tremendous speed of SEARCH, amend line 100, set n to 10000
and assure that at least 100K of memory is free for the huge array: you
will be surprised, even the 10000 entries are searched in next to no
time! 100 n = 1000: DIM name$(n,10) 110 FOR i = 1 TO n 120 name$(i) = ""
130 FOR j = 1 TO 10 140 name$(i) = name$(i) & CHR$(RND(65 TO 90)) 150 IF
j > 3 AND NOT RND(5) THEN EXIT j 160 END FOR j 170 END FOR i 180 : 190
first = 1 200 REPeat loop 210 found = SEARCH(name$, "QL", first, 0) 220
IF found < 0 THEN EXIT loop 230 PRINT name$(found) 240 IF found = n THEN
EXIT loop: ELSE first = found + 1 250 END REPeat loop

Minerva and SMS users can use integers for n, i, j, first
 and found to speed up things, so replace them by n%, i%, j%, first% and
found%.

**CROSS-REFERENCE**

Use `INSTR <KeywordsI.clean.html#instr>`__ to locate a sub-string in a string.
`INARRAY% <KeywordsI.clean.html#inarray>`__ is similar. See the other
implementation of `SEARCH <KeywordsS.clean.html#search>`__.

--------------

SEARCH\_MEM
===========

+----------+-------------------------------------------------------------------+
| Syntax   |  SEARCH\_MEM (add1 TO add2, tofind$)                              |
+----------+-------------------------------------------------------------------+
| Location |  MSEARCH (DIY Toolkit - Vol X)                                    |
+----------+-------------------------------------------------------------------+

 This function is very similar to the main MSEARCH function provided by
this toolkit. It is however limited to case- dependent searches and
therefore is even quicker than MSEARCH.

**CROSS-REFERENCE**

See `SEARCH <KeywordsS.clean.html#search>`__ and
`TTFINDM <KeywordsT.clean.html#ttfindm>`__ also.
`MSEARCH <KeywordsM.clean.html#msearch>`__ is a variant on this version.

--------------

SELect
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SELect                                                           |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 This keyword forms an integral part of the SELect ON structure
identifier and has no use on its own. If you try to enter it on its own,
the error 'Bad Name' will be generated.

**CROSS-REFERENCE**

Please see `SELect ON <KeywordsS.clean.html#select20on>`__!

--------------

SELect ON
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SELect ON var                                                    |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 This command is used to mark the start of a SuperBASIC structure which
is an extremely quick means of testing for various values of a variable
and taking a different course of action in a program according to those
values. Unfortunately, the standard form of this command only allows you
to test for different values of a numeric variable (eg. SELect ON a$ is
not allowed). There are actually two forms of the SuperBASIC structure:
SELect ON var=range: statement
:sup:`\*`\ [:statement]\ :sup:`\*\*`\ [:=range:statement
:sup:`\*`\ [:statement]\ :sup:`\*`]\ :sup:`\*
` or SELect ON var
 :sup:`\*`\ [[ON var] = range:statement
:sup:`\*`\ [:statement]\ :sup:`\*` ]\ :sup:`\*
` .. END SELect
 range can be any one, or mixtures of, the following: expression
 expression TO expression
 REMAINDER
 The first of these variants (in this and all SuperBASIC structures) is
known as an in-line structure, as the entire structure appears on the
same program line. This does not need END SELect to mark the end of the
structure. After the main SELect ON var statement, the interpreter looks
for a list of possible values, and then if the value of the given
variable falls within the range of possible values, the program takes
action according to the statements which follow that value in the list.
The interpreter will use the first range of values into which it can fit
the variable and once found, all statements up until (but excluding) the
next range in the list will be treated as applying to that range
(whether they appear on the same line or not). Once all of the
statements applying to that range have been executed, control passes to
the statement following the END SELect
 statement (or if the in-line form of the structure is used, and END
SELect does not appear on that line, then control passes to the next
line). The way in which matches are made when checking whether a value
falls within a range depends on whether range is a single number (eg. ON
var=10) or various values (eg. ON var=10 to 20). If the former, the
value need only be approximately equal to range (ie. to within 1 part in
10\ :sup:`7`, for instance: 100.0000045==100!). However, if the latter
format is used (eg. SELect ON a=90 TO 100), a match will only be found
if the given value is within the absolute range (eg. in the above
example, 100.0000045 would not be matched!). If the long form of the
structure is used, and ON var is used within the body of the structure,
this must be the same variable as that used in the initial SELect ON
statement.

**Example 1**

10 SELect ON x=1,10 TO 100,500:PRINT 'x'

**Example 2**

100 SELect ON test 110 =0,2,4,6,8,10:PRINT 'Even Number' 120
=REMAINDER:PRINT 'Odd Number' 130 END SELect

**Example 3**

A re-write of the example given for ON...GO SUB: 100 no\_of\_locations=3
110 start=0 120 PRINT\_LOC 2 130 DEFine PROCedure PRINT\_LOC(xa) 135
xa=xa+start 140 SELect ON xa 150 =1:PRINT 'This is location 1' 160 =2
165 PRINT 'This is location 2' 170 =3:PRINT 'This is location 3' 180
=REMAINDER:PRINT 'Undefined Location' 185 RETurn 190 END SELect 200
PRINT 'What now?:RETurn 210 END DEFine

**NOTE 1**

Pre JS ROMs and SMS allow you to enter string and integer variables into
the SELect statement, but they will not work unless you used a
SuperBASIC compiler. Later ROMs, report a 'bad line' error unless you
have Minerva.

**NOTE 2**

On JS ROMs, you cannot use a parameter passed to a PROCedure or FuNction
as the variable in a SELect ON statement unless it appears as the last
parameter in the list in the definition line. If you do try to break
this rule, you will end up with a 'bad name' error. The answer is to
copy the parameter to a temporary variable.

**NOTE 3**

As you may have noticed, unlike other SuperBASIC structures which will
expand a command typed into the full structure name if you type just the
capital letters (eg. DEFPROC becomes DEFine PROCedure), SELON will not
be expanded to SELect ON. You will need to type SEL ON instead.

**NOTE 4**

To maximise the speed of the SELect ON command, ensure that the most
common matches appear at the start of the definition block.

**NOTE 5**

Except under SMS, SELect ON can only cope with simple variables, for
example: SELect ON a
 is acceptable. Compare: SELect ON a(2) SELect ON s\*10
 or SELect ON CODE(a$)
 All of these are acceptable on SMS but cannot currently be compiled.
Although lines such as: SELect ON CODE and SELect ON INKEY$
 might be accepted by the interpreter, the lines contained within the
block will be ignored (other than =REMAINDER matches). On SMS both of
these give an 'error in expression' when RUN.

**MINERVA NOTES**

Minerva supports string and variables in SELect ON statements. The check
for characters is normally case independent. For example: SELect ON
a$:='hello'
 will find both a$='HeLLo' and a$='hello'. If however, you want the
match to be exact (case dependent), then something along the lines of:
SELect ON a$:='hello' TO 'hello'
 must be used. Unfortunately, you still cannot SELect ON machine code
functions (for example, INKEY$), which will have no effect, or slice the
string, which will cause a 'bad line' error. A short example of the
additional flexibility is a check for a response to a simple question
{eg. Overwrite (y/n)?}: 100 REPeat loop 110 A$=INKEY$(-1) 120 SELect ON
A$ 130 ='yn'&chr$(27):EXIT loop 140 END SELect 150 END REPeat loop
 is the same as: 100 REPeat loop
 110 A=CODE(INKEY$(-1)) 120 SELect ON A: 130 =89,121,78,110,27:EXIT loop
140 END SELect 150 END REPeat loop
 Minerva also supports integer variables, such as: SELect ON a%. This is
an extremely fast means of testing a condition. However, due to the
nature of integers, tests will only match the integer part of range.

**SMS NOTE**

This has greatly extended the flexibility of SELect ON - see in
particular Note 5 above. It will also allow integer variables as the
SELect, but unfortunately not string SELect variables at present. If you
try to do so, the error 'Incorrectly structured SELect clause' will be
reported. It will however, even support things like: SELect ON
CODE(INKEY$(#1))
 Unfortunately, SMS pre v2.90 had problems in dealing with in-line
SELect ON statements. Prior to v2.89 an error would be generated if an
END SELect statement did not appear in an in-line definition, and v2.89
reported an error if END SELect did appear!!

**CROSS-REFERENCE**

A slower means of testing for values is the structure `IF...END
IF <KeywordsI.clean.html#if...end20if>`__. `END
SELect <KeywordsE.clean.html#end20select>`__ ends a `SELect
ON <KeywordsS.clean.html#select20on>`__ structure.

--------------

SEND\_EVENT
===========

+----------+-------------------------------------------------------------------+
| Syntax   |  SEND\_EVENT {jobname$ \| jobID \| jobnr,tag }, event             |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E v2.71+                                                    |
+----------+-------------------------------------------------------------------+

 With v1.51 of the Window Manager (and v2.71 of SMSQ/E), the possibilty
of Job Events was introduced. This is basically a simple way of making
one program wait until it receives notification from another Job that up
to eight different events has occured. The events are undefined and
simply represented by the eight numbers : 1, 2, 4, 8, 16, 32, 64, 128.
This command allows you to tell a specified job that those events have
occured - several events may be notified by adding together the various
values of event. The job to be notified can be represented by either
its: (1) Jobname (eg. 'SBASIC') (2) Job ID number (returned by OJOB for
example). (3) Job number and Job Tag (returned by JOBS).

**Example**

SEND\_EVENT OJOB(1),2+8
 Notifies the current job's owner that events 2 and 8 have occured.

**CROSS-REFERENCE**

A job can test to see if an event has occured with
`WAIT\_EVENT <KeywordsW.clean.html#wait-event>`__.

--------------

SERMAWS
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SERMAWS acc%, wup%                                               |
+----------+-------------------------------------------------------------------+
| Location |  SERMouse                                                         |
+----------+-------------------------------------------------------------------+

 This command is used to set two parameters which control the effect
that moving the serial mouse has on the on-screen pointer under the
Pointer Environment. The first parameter sets the speed at which the
pointer will accelerate across the screen (this can be any value in the
range 0...9). A standard value is 6. The second parameter sets the
initial speed of the pointer. A standard value is 3. The values can also
be set by configuring the SERMouse file.

**CROSS-REFERENCE**

`SERMPTR <KeywordsS.clean.html#sermptr>`__ makes the mouse driver affect the
Pointer only. Qpac 2 allows you to set the same parameters from the
Sysdef menu. Also refer to\ `SERMSPEED <KeywordsS.clean.html#sermspeed>`__ and
`SERMON <KeywordsS.clean.html#sermon>`__. See the appendix on Mouse Drivers
for more information.

--------------

SERMCUR
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SERMCUR                                                          |
+----------+-------------------------------------------------------------------+
| Location |  SERMouse                                                         |
+----------+-------------------------------------------------------------------+

 The SERMouse driver allows you to use a Mouse to control either the
Pointer (under the Pointer Environment) or the Basic cursor (used in
INPUT commands or similar). This command forces the mouse to control the
Basic cursor provided that the following condition is met: There is a
channel currently open which is awaiting for screen input with a visible
cursor. If you switch to a program which is reading the pointer (ie. a
program which uses the pointer interface) then the command SERMPTR is
automatically called.

**CROSS-REFERENCE**

`SERMPTR <KeywordsS.clean.html#sermptr>`__ switches to Pointer Mode. See also
`SERMSPEED <KeywordsS.clean.html#sermspeed>`__. You can also switch to cursor
mode by hitting the left hand mouse button twice in quick succession.

--------------

SERMOFF
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SERMOFF                                                          |
+----------+-------------------------------------------------------------------+
| Location |  SERMouse                                                         |
+----------+-------------------------------------------------------------------+

 This command removes the Serial Mouse Driver.

**CROSS-REFERENCE**

`SERMON <KeywordsS.clean.html#sermon>`__ will reactivate the Driver. Compare
`SERMWAIT <KeywordsS.clean.html#sermwait>`__

--------------

SERMON
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SERMON                                                           |
+----------+-------------------------------------------------------------------+
| Location |  SERMouse                                                         |
+----------+-------------------------------------------------------------------+

 The serial mouse driver must always be loaded into Resident Procedure
Space (for example with RESPR or LRESPR) before any Jobs are EXECuted.
However, if you have Hermes or SuperHermes fitted, you can configure the
Serial Mouse driver so that it does not automatically start up after
being linked into BASIC. This command can be used to initialise and
startup the driver either following a SERMOFF command or if you have
configured the driver not to automatically start up after being linked
into BASIC. SERMON should also be used to reactivate the driver
following a SERMWAIT command.

**CROSS-REFERENCE**

`SERMOFF <KeywordsS.clean.html#sermoff>`__ and
`SERMWAIT <KeywordsS.clean.html#sermwait>`__ are complementary functions. See
the Appendix on Mouse Drivers for further details.

--------------

SERMPTR
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SERMPTR                                                          |
+----------+-------------------------------------------------------------------+
| Location |  SERMouse                                                         |
+----------+-------------------------------------------------------------------+

 This command switches the Serial Mouse Driver into Pointer Mode, so
that the movements of the Serial Mouse affect the Pointer on screen,
allowing you to control programs which make use of the Pointer
Environment. This is the default mode following loading the driver or a
SERMON command.

**CROSS-REFERENCE**

See also `SERMCUR <KeywordsS.clean.html#sermcur>`__.

--------------

SERMRESET
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SERMRESET                                                        |
+----------+-------------------------------------------------------------------+
| Location |  SERMouse                                                         |
+----------+-------------------------------------------------------------------+

 This command should never really be needed, particularly if you are
using the Serial Mouse with Hermes or SuperHermes. This command resets
the chip which controls the serial ports and should only be necessary if
you notice the Pointer or Cursor moving on screen uncontrollably.

**CROSS-REFERENCE**

Other causes of this problem may be the wrong speed settings - see
`SERMAWS <KeywordsS.clean.html#sermaws>`__,
`SERMSPEED <KeywordsS.clean.html#sermspeed>`__ and
`BAUD <KeywordsB.clean.html#baud>`__.

--------------

SERMSPEED
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SERMSPEED mul%, div%, acc% [,cursormul%, cursordiv%]             |
+----------+-------------------------------------------------------------------+
| Location |                                                                   |
+----------+-------------------------------------------------------------------+

SERMouse
 This command allows you to set various parameters to dictate the speed
and resolution of the mouse. As a mouse moves, it sends a stream of data
to the computer containing details of the direction moved and the
distance moved. These details are sent every few microseconds and
converted by the driver to x,y coordinates on screen. The speed at which
these details are sent is known as the resolution of the mouse. This
command allows you to alter the resolution of the mouse so that you do
not have to move the mouse as far to get the pointer (or cursor) on
screen to move across the whole screen. The mul% and div% parameters can
be in the range 0..127 (with 0 disabling this feature - the default).
The distance sent by the mouse is multiplied by the mul% factor and
divided by the div% factor - with these both set to 0, only two-thirds
of the distance moved by the mouse is passed to the Pointer Interface to
be translated into movements of the Pointer. The acc% parameter can be
in the range (0...8) and defaults to 4 - this is used to calculate an
acceleration factor, so that the faster that the mouse is moved the
quicker the details sent by the mouse are passed on to the Pointer
Interface (thus making the Pointer move in bigger and bigger steps). The
last two parameters are optional and are only relevant when the Mouse
Driver is used in Cursor Mode (see SERMCUR). These two parameters affect
the resolution of the mouse when being used to move the Basic Cursor -
the standard values are both 1.

**CROSS-REFERENCE**

`SERMAWS <KeywordsS.clean.html#sermaws>`__ works in conjunction with this
command. All of these parameters can be configured in the SERMouse file.
See also `SERMCUR <KeywordsS.clean.html#sermcur>`__ and
`SERMPTR <KeywordsS.clean.html#sermptr>`__.

--------------

SERMWAIT
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SERMWAIT                                                         |
+----------+-------------------------------------------------------------------+
| Location |  SERMouse                                                         |
+----------+-------------------------------------------------------------------+

 This command can be used to suspend the Serial Mouse Driver. You may
wish to do this for example, if your system does not support dual BAUD
rates and you need to change the baud rate for a Modem or Printer.

**CROSS-REFERENCE**

`SERMON <KeywordsS.clean.html#sermon>`__ re-activates the Driver. Again, the
Driver can be configured to automatically be suspended when the baudrate
is altered.

--------------

SERNET
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SERNET                                                           |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E, ATARI Emulators                                          |
+----------+-------------------------------------------------------------------+

 A file SERNET\_rext is provided with SMSQ/E, QXL and the Emulators for
the Atari computers which allows you to set up a Network using the
Serial ports provided. Once the Network has been set up with the
necessary leads, and SERNET\_rext been loaded on all computers in the
Network, the command SERNET should be issued to start up the fileserver
Job on each computer. This creates a background Job called 'SERNET'
which is similar to the 'Server' Job created by FSERVE. The two
fileservers are very similar in operation in that they both allow other
computers to access the resources of the Master machine over the
Network. As with MIDINET, SERNET has built-in protection for files which
can prevent other users in a Network accessing sensitive files. Refer to
MIDINET for details.

**CROSS-REFERENCE**

`SNET <KeywordsS.clean.html#snet>`__ is needed to control the Network. See
also `FSERVE <KeywordsF.clean.html#fserve>`__ and
`MIDINET <KeywordsM.clean.html#midinet>`__. See the Appendix on Networks for
further details.

--------------

SER\_ABORT
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SER\_ABORT [port]                                                |
+----------+-------------------------------------------------------------------+
| Location |  ST/QL, SMSQ/E                                                    |
+----------+-------------------------------------------------------------------+

 This command is similar to PAR\_ABORT except that it clears out all of
the closed SER buffers and then sends an 'aborted' message, to the SER
device. If port is specified, on machines which support more than one
serial port, this allows you to specify the port number to be affected
(default SER1).

**CROSS-REFERENCE**

See `PAR\_ABORT <KeywordsP.clean.html#par-abort>`__.

--------------

SER\_BUFF
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SER\_BUFF [port, ] output\_size [,input\_size]                   |
+----------+-------------------------------------------------------------------+
| Location |  ST/QL,                                                           |
+----------+-------------------------------------------------------------------+

SMSQ/E
 Used with one parameter, this is the same as PAR\_BUFF except that it
sets the size of the output buffer attached to each SER channel. The
input buffer is normally a dynamic buffer, unless input\_size is
specified. The output buffer should be a minimum of 5 to avoid confusion
with the port number. You can also use SER\_BUFF to alter the size of
the input buffer, by using the form: SER\_BUFF output\_size,input\_size
 Although you will need to specify the output\_size, you can set this to
0 to enable a dynamic output buffer. You can also specify which serial
port number is to be used to allow this command to work on machines with
more than one serial port (this defaults to SER1).

**Examples**

SER\_BUFF 200
 Set the output buffer size to 200 bytes, with a dynamic input buffer.
SER\_BUFF 200,500
 Have an output buffer of 200 bytes, with an input buffer of 500 bytes.

**NOTE 1**

The actual useable input buffer will be calculated by the value set by
SER\_BUFF less the value set by SER\_ROOM.

**NOTE 2**

In version E-17 of the device drivers for the Atari Emulator (and later
implementations of this command, including SMSQ/E), whenever you use
this command, the value set by SER\_ROOM

is re-calculated so that it is set to one quarter of the input buffer
size. Earlier versions may (after Level B09) would report an error if
the input buffer was not at least twice the size of the value set by
SER\_ROOM.

**CROSS-REFERENCE**

See `PAR\_BUFF <KeywordsP.clean.html#par-buff>`__! You should also refer to
`SER\_ROOM <KeywordsS.clean.html#ser-room>`__.

--------------

SER\_CDEOF
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SER\_CDEOF [port,] time                                          |
+----------+-------------------------------------------------------------------+
| Location |  ST/QL (Level D00 +), SMSQ/E                                      |
+----------+-------------------------------------------------------------------+

 Serial ports are able to both send and receive data. It is therefore
imperative that the System can detect when data is no longer being sent
to a port which is being used to receive the data. Normally, the System
will wait until it receives an End Of File character (CTRL Z or EOF).
However, it can be useful to specify a time limit, whereby if no data is
received during that time, the System assumes End Of File. The command
SER\_CDEOF time allows you to specify the number of frames for which the
System will wait for more data. If time
 equals 0, then the System will wait indefinitely until it receives an
explicit End Of File character. The time should be more than 5 in order
to distinguish it from the port number. For machines with more than one
serial port, you can specify the number of the serial port this command
is to apply to (default SER1).

**NOTE 1**

This command has no effect on a QL, QPC or QXL.

**NOTE 2**

This command would not work properly on SCC ports on the Atari Mega STE
or TT until v2.73+.

**CROSS-REFERENCE**

`EOF <KeywordsE.clean.html#eof>`__ and `EOFW <KeywordsE.clean.html#eofw>`__ allow
you to detect an EOF character.

--------------

SER\_CLEAR
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SER\_CLEAR [port]                                                |
+----------+-------------------------------------------------------------------+
| Location |  ST/QL, SMSQ/E                                                    |
+----------+-------------------------------------------------------------------+

 This is similar to PAR\_CLEAR except that it clears out all current SER
buffers. For machines with more than one serial port, you can specify
the number of the serial port to be affected (default SER1).

**CROSS-REFERENCE**

See `PAR\_CLEAR <KeywordsP.clean.html#par-clear>`__!

--------------

SER\_FLOW
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SER\_FLOW [port,] flow                                           |
+----------+-------------------------------------------------------------------+
| Location |  ST/QL, SMSQ/E                                                    |
+----------+-------------------------------------------------------------------+

 Because of the variety of equipment which can be connected to a QL
system through a serial port, the System has to support several types of
handshaking. Handshaking is basically a means of checking if the data
received through a serial port is the same as the data which has been
sent. Normally, handshaking can be specified when a port is opened (see
the Appendix concerning device drivers). However, it can also be useful
to preset the handshaking by using the command SER\_FLOW. flow can have
one of three values: h Enable handshaking i Ignore handshaking - do not
bother to check data x XON/XOFF detection. To enable flexibility on
machines with more than one serial port, you can also specify the number
of the serial port to be affected by this command (default SER1).

**CROSS-REFERENCE**

Please refer to the Appendix on device drivers for more information.

--------------

SER\_PAUSE
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SER\_PAUSE [port,] time                                          |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E for Gold Card                                             |
+----------+-------------------------------------------------------------------+

 On standard QL serial ports, you may find that some characters which
are sent by the QL through the serial ports get lost or the device to
which they are sent (for example a printer) prints undefined characters.
This problem may be caused by the fact that the stop bit which is sent
by the QL serial ports may be too short for the device at the other end.
The SER\_PAUSE command allows you to set the length of the stop bit in
microseconds - it effectively causes a short pause between each
character sent through the serial ports. If port
 is not specified, this command will affect both serial ports, otherwise
it will only affect the specified serial port. The higher the value of
time, the longer the stop bit will be and hence the slower the serial
transfer rate.

**CROSS-REFERENCE**

If you are using serial ports to receive data, you may need to set
`SER\_ROOM <KeywordsS.clean.html#ser-room>`__. `BAUD <KeywordsB.clean.html#baud>`__
also affects the serial transfer rate. Please also refer to the Appendix
on device drivers for more information.

--------------

SER\_ROOM
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SER\_ROOM [port,] bytes                                          |
+----------+-------------------------------------------------------------------+
| Location |  ST/QL, SMSQ/E                                                    |
+----------+-------------------------------------------------------------------+

 Although handshaking should ensure that serial input is safe,
unfortunately some devices carry on sending data even though they have
been told to stop. This may be caused by a buffer attached between the
sending and receiving equipment, for example. This is known as 'serial
overrun' and can have unfortunate consequences, as the receiving
equipment may not have room to store the additional information. Where
the system is acting as the receiver, you can use the command SER\_ROOM
to specify a minimum amount of memory which must be left in the input
buffer when the System uses handshaking to check on the validity of the
data received. SER\_ROOM sets aside bytes in the input buffer which can
be used to store information received after the System has told the
sending equipment to stop. If you still find that some data is lost due
to serial overrun, try increasing the amount of space. For machines with
more than one serial port, you can specify the number of the serial port
to be affected by this command (default SER1).

**NOTE**

The default room is 32 bytes.

**CROSS-REFERENCE**

`SER\_BUFF <KeywordsS.clean.html#ser-buff>`__ allows you to alter the size of
the input buffer and affects the value set by this command. You should
also look at `SER\_PAUSE <KeywordsS.clean.html#ser-pause>`__.

--------------

SER\_USE
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SER\_USE [device]                                                |
+----------+-------------------------------------------------------------------+
| Location |  ST/QL, SMSQ/E                                                    |
+----------+-------------------------------------------------------------------+

 As with PAR\_USE, this command allows the SER port to emulate the
parallel printer port. Any three letter extension is allowed, you are
not restricted to SER or PAR.

**CROSS-REFERENCE**

See `PAR\_USE <KeywordsP.clean.html#par-use>`__

--------------

SET
===

+----------+-------------------------------------------------------------------+
| Syntax   |  SET x, y, col                                                    |
+----------+-------------------------------------------------------------------+
| Location |  HCO                                                              |
+----------+-------------------------------------------------------------------+

 SET does the same as PLOT with SCRBASE 131072 set, ie. it does not
support virtual screens. x ranges from 0 to 511, y from 0 to 255. The
colour (col) is specified by an integer from 0 to 3, representing the
four colours available in MODE 4: 0 ... black 1 ... red 2 ... green 3

**NOTE**

Although SET is not designed to, it does work in MODE 8 but the colours
appear differently: Colour 1 is not red but magenta for example.

**WARNING 1**

SET writes directly into screen memory and assumes that it starts at
131072, so SET may crash the machine if the screen is located at another
position in memory. SET also assumes a resolution of 512 x 256 pixels.

**WARNING 2**

SET does not check for the existance of the parameters (this means for
example that it will not report 'bad parameter' for SET x, y), it may
crash if any of the parameters is omitted.

**CROSS-REFERENCE**

`PLOT <KeywordsP.clean.html#plot>`__. We highly recommend that you use the
QDOS inbuilt window relative graphic routine,
`POINT <KeywordsP.clean.html#point>`__ in this case.
`COL <KeywordsC.clean.html#col>`__ finds the colour of a screen pixel. See the
other implementation of `SET <KeywordsS.clean.html#set>`__ also.

--------------

SET
===

+----------+-------------------------------------------------------------------+
| Syntax   |  SET [#]variable TO value                                         |
+----------+-------------------------------------------------------------------+
| Location |  SET, ALTER (DIY Toolkit - Vol U)                                 |
+----------+-------------------------------------------------------------------+

 This command allows you to set up various universal constants which
allow programs to read various values which are set by other programs.
This is similar to creating machine code functions which return constant
values. The constants to be set up appear as variable in the command.
They can be string, floating point or integer but must not have
previously been used in the program (otherwise the error 'In Use' will
be reported). They must also not appear in quotes. The constants should
be SET from SuperBASIC Job 0, otherwise they do not seem to work (at
least on Minerva). However, other programs can use ALTER to change the
value of the constants and also read the constants as if they were
predefined variables. As an added bonus, if the variable is prefixed by
a hash sign, then this is taken to a pointer to a system variable, which
will always point to that system variable even if the system variables
move. For example to read the Network number, you could use: SET
#NET\_ID TO HEX('37') PRINT PEEK (NET\_ID)
 instead of: SET NET\_ID TO HEX('37') PRINT PEEK (SYS\_VARS+NET\_ID)

**Example**

Set the following from SuperBASIC: 10 SET FALSE TO 0 : SET TRUE TO 1 20
SET YES$ TO 'Yy' : SET NO$ TO 'Nn' 30 SET DEF\_DRIVE$ TO 'flp1\_'
 Any other program can then just use lines such as: IF INKEY$(1) INSTR
YES$ : PRINT 'Yes has been selected'
 and LBYTES DEF\_DRIVE$&'prog\_data',space

**NOTE 1**

SET does not work on SMS.

**NOTE 2**

SET #value does not appear to work on Minerva v1.97 (at least in
versions up to v1.66 of the toolkit).

**NOTE 3**

Any attempt to use SET from within a multiple BASIC will have no effect.

**CROSS-REFERENCE**

See `ALTER <KeywordsA.clean.html#alter>`__. `TRUE% <KeywordsT.clean.html#true>`__,
`FALSE% <KeywordsF.clean.html#false>`__ and `PI <KeywordsP.clean.html#pi>`__ are
predefined constants.

--------------

SetHEAD
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SetHEAD #ch, adr                                                 |
+----------+-------------------------------------------------------------------+
| Location |  HEADER (DIY Toolkit - Vol F)                                     |
+----------+-------------------------------------------------------------------+

 The command SetHEAD is the counterpart of GetHEAD and is normally used
in conjunction with it. So please refer to GetHEAD for further
information about the syntax and usage. There is just one difference you
must keep in mind: whilst GetHEAD does not care in which mode (read only
or read and write) a file was opened, SetHEAD does. It expects that the
channel was opened with OPEN, FOPEN etc but not with OPEN\_IN or
FOP\_IN.

**CROSS-REFERENCE**

See `GetHEAD <KeywordsG.clean.html#gethead>`__.

--------------

SET\_CLOCK
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SET\_CLOCK                                                       |
+----------+-------------------------------------------------------------------+
| Location |  THOR range                                                       |
+----------+-------------------------------------------------------------------+

 This command sets the THOR's battery backed clock to the current system
time (set with SDATE).

**NOTE**

This is not actually necessary on the THOR XVI as this automatically
alters the battery backed clock when the system clock is altered with
SDATE or ADATE.

**CROSS-REFERENCE**

`SDATE <KeywordsS.clean.html#sdate>`__ and `ADATE <KeywordsA.clean.html#adate>`__
alter the system clock. `A\_SDATE <KeywordsA.clean.html#a-sdate>`__ is similar
on the ST/QL Emulator.

--------------

SET\_FBKDT
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SET\_FBKDT #channel [,time] or SET\_FBKDT \\file [,time]         |
+----------+-------------------------------------------------------------------+
| Location |  Level-2 drivers                                                  |
+----------+-------------------------------------------------------------------+

 The command SET\_FBKDT sets the date when a file was last backed-up.
The time specified, must be in the number of seconds since 1st January
1961, ie. the number returned by DATE. If time is not specified or is 0,
then the current DATE setting is used. If time=1 this has no effect on
the file. Normally the backup date is not set unless you do so using
SET\_FBKDT. This command supports the data default directory (set with
DATA\_USE).

**Example**

 SET\_FBKDT \\BOOT,DATE
 sets the backup date on the file BOOT in the current data default
directory to the current time and date.

**CROSS-REFERENCE**

`FBKDT <KeywordsF.clean.html#fbkdt>`__. See `FGETH$ <KeywordsF.clean.html#fgeth>`__
for the structure of a file header, especially which byte is modified
when the backup date is changed.

--------------

SET\_FUPDT
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SET\_FUPDT #channel [,time] or SET\_FUPDT \\file [,time]         |
+----------+-------------------------------------------------------------------+
| Location |  Level-2 drivers                                                  |
+----------+-------------------------------------------------------------------+

 The command SET\_FUPDT sets the date on which a file was last altered.
This is always set to the current system DATE when a file is SAVEd, or
CLOSEd after having been written to. If time is not specified (or is 0),
then the current DATE is used. If time
 is set to 1, then this command will have no effect on the file. COPY
sets the update time on the file being created to the current DATE. For
a SuperBASIC 'backup' function which gives the newly created file the
same update time as the original and alters the backup time, see FBKDT.
This command supports the current default data directory (see DATAD$).

**NOTE**

If you use SET\_FUPDT to alter the update time of a file OPENed to the
specified channel, closing that channel later in the program will not
affect the update time.

**CROSS-REFERENCE**

`FUPDT <KeywordsF.clean.html#fupdt>`__. See `FGETH$ <KeywordsF.clean.html#fgeth>`__
for the structure of a file header, especially which byte is modified
when the update time is set.

--------------

SET\_FVERS
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SET\_FVERS #channel [,version] or SET\_FVERS \\file [,version]   |
+----------+-------------------------------------------------------------------+
| Location |  Level-2 drivers                                                  |
+----------+-------------------------------------------------------------------+

 The command SET\_FVERS sets the version number of a file - versions
higher than 65535 or smaller than 0 are regarded as version MOD 65536,
version=0 (or if version is omitted) means that the version number will
not be updated when the channel to that file is closed. This command
supports the current default data directory (see DATAD$).

**Example**

SET\_FVERS \\BOOT,13

**CROSS-REFERENCE**

`FVERS <KeywordsF.clean.html#fvers>`__. See `FGETH$ <KeywordsF.clean.html#fgeth>`__
for the structure of a file header, especially which byte is modified
when the version is changed. The version number may be updated by
`SAVE <KeywordsS.clean.html#save>`__ and `QSAVE <KeywordsQ.clean.html#qsave>`__ on
SMS.

--------------

SET\_GREEN
==========

+----------+-------------------------------------------------------------------+
| Syntax   |  SET\_GREEN #channel, operation                                   |
+----------+-------------------------------------------------------------------+
| Location |  Windows (DIY Toolkit - Vol W)                                    |
+----------+-------------------------------------------------------------------+

 This command allows you to change the colours used within a specified
window channel very quickly. In order to use this, you really need a
good understanding of the way in which the QL display works - see the QL
Display Appendix for some details. The effect that this command has on
the specified window depends upon the value of operation:

operationEffect
~~~~~~~~~~~~~~~

0Clear all Green bits (remove any Green from the screen). 1Set all Green
bits. -1If the Red bit for a pixel is set, Set the Green bit, otherwise
clear it.

**NOTE 1**

This command will only work on screen resolutions of 512x256 pixels.

**NOTE 2**

This command should not really be used in MODE 8.

**CROSS-REFERENCE**

`SET\_RED <KeywordsS.clean.html#set-red>`__ is similar. See
`RECOL <KeywordsR.clean.html#recol>`__. `W\_SWAP <KeywordsW.clean.html#w-swap>`__
can also be used to recolour a window. Refer to the QL Display Appendix.

--------------

SET\_RED
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SET\_RED #channel, operation                                     |
+----------+-------------------------------------------------------------------+
| Location |  Windows (DIY Toolkit - Vol W)                                    |
+----------+-------------------------------------------------------------------+

 This command is similar to SET\_GREEN - the only difference is that
instead of affecting green bits, it alters the red bits. The effect that
this command has on the specified window depends upon the value of
operation:

operationEffect
~~~~~~~~~~~~~~~

0Clear all Red bits (remove any Red from the screen). 1Set all Red bits.
-1If the Green bit for a pixel is set, Set the Red bit, otherwise clear
it.

**CROSS-REFERENCE**

See `SET\_GREEN <KeywordsS.clean.html#set-green>`__ !

--------------

SET\_LANGUAGE
=============

+----------+-------------------------------------------------------------------+
| Syntax   |  SET\_LANGUAGE country$  or SET\_LANGUAGE [country$] (THOR XVI v6.41 only)  |
+----------+-------------------------------------------------------------------+
| Location |  THOR range                                                       |
+----------+-------------------------------------------------------------------+

 The command SET\_LANGUAGE takes a string or name parameter and attempts
to change the keyboard layout to the first one with a name of which the
given parameter is an abbreviation (this comparison is
case-independent). If the parameter is an empty string (or not
specified), the next keyboard layout is selected. Ideally, in a program,
the full name of the layout would be used for clarity. The search is
circular which means that for example, if SET\_LANGUAGE d was used, the
Danish (Dansk) keyboard layout would be adopted rather than the German
(Deutsch) layout, unless the Danish layout was already selected. The
current keyboard layouts are supported:

NumberCountry$Language
~~~~~~~~~~~~~~~~~~~~~~

1 InternationalNone specific 2 BritishEnglish 3 Dansk Danish 4 Deutsch
German 5 Espanol Spanish (v4.20+ only) 6 Fran�ais French 7 HELLAS Greek
8 Suisse Swiss 9 Svensk Swedish (v4.20+ only)

**Examples**

SET\_LANGUAGE ""
 jump to next keyboard layout in list. SET\_LANGUAGE 'Esp'
 set layout to Spanish layout.

**NOTE 1**

Connected with each keyboard layout, there is also a national
translation table, which you will need to install by using the command
TRA 1.

**NOTE 2**

On THOR's equipped with a JS ROM, Fran�ais must be enclosed in quotation
marks as it is an invalid variable name.

**NOTE 3**

The second variant of the command should not really be used as it is
only supported on the v6.41 ROM for the THOR XVI. This has the same
effect as SET\_LANGUAGE "".

**CROSS-REFERENCE**

`LANGUAGE$ <KeywordsL.clean.html#language>`__ returns the name of the current
keyboard layout in use. Before v6.41 of the THOR XVI, the keys
<ALT><SYSREQ> had the same effect as `SET\_LANGUAGE
"" <KeywordsS.clean.html#set-language>`__. On v6.41, this keying was altered
to call a Job called Alt\_SysReq (Case dependent).
`LANG\_USE <KeywordsL.clean.html#lang-use>`__ allows SMS to use different
languages for messages and errors. See also
`KBD\_TABLE <KeywordsK.clean.html#kbd-table>`__.

--------------

SEXEC
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SEXEC device\_file,start,length,data  or SEXEC device\_file,start[,length[,data[,extra[,type]]] (Minerva v1.80+)  or SEXEC [device\_]file,start,length,data (Toolkit II)  or SEXEC #channel,start,length,data (SMS only)  |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM, Toolkit II                                               |
+----------+-------------------------------------------------------------------+

 In order for a program to be stored as an executable Job, it is
necessary to store the machine code in a specified format on disk. The
command SEXEC allows you to do this, taking a specified amount of code
from memory and storing it in the specified file in a form which can
later be EXECuted. You will need to specify the start address of the
machine code, the length of the code to be stored and the amount of data
 space to be given to the program when it is loaded back into memory
(the data space represents the amount of working memory which is linked
with the program when it is loaded, either for storing data at the end
of the program or for the user stack - see a good QL machine code book
for more details). The specified file name must include the name of the
device
 to be used, unless Toolkit II is present, in which case the default
program device is supported. If Toolkit II is present and the file
already exists, you will be given the option of overwriting the file.

**Example**

To amend a given executable program, you may need to do the following:
100 length=FLEN(\\example\_exe) 110 datasp=FDAT(\\example\_exe) 120
start=RESPR(length) 130 LBYTES example\_exe,start 140 POKE
start+1024,100 150 SEXEC flp1\_example\_exe,start,length,datasp

**NOTE 1**

On Minerva ROMs (pre v1.80), if SEXEC was aborted for some reason whilst
writing to a file, the file would be deleted. On later versions of
Minerva and all other QL ROMs, the incomplete file is kept. Toolkit II
reports Medium Full if this is the case.

**NOTE 2**

The Minerva variant is overwritten by the Toolkit II version of this
command.

**NOTE 3**

On Minerva pre v1.83, SEXEC set the wrong file type!

**MINERVA NOTE**

On Minerva v1.80 (or later) the command SEXEC is practically the same as
SBYTES. The only difference is the type parameter which defaults to 1 as
opposed to 0 with SBYTES.

**SMS NOTE**

The fourth variant of this command allows you to save the data to an
already existing channel which is OPEN to a file, thus cutting down on
the number of times you need to access the file for error trapping (for
example). See SBYTES for an example.

**WARNING**

Saving part of the QL's memory with SEXEC does not make it into
EXECutable code - you must ensure that the program concerned has a
proper Job header and conforms with the normal QDOS rules for EXECutable
programs.

**CROSS-REFERENCE**

`SEXEC\_O <KeywordsS.clean.html#sexec-o>`__ is very similar.
`EXEC <KeywordsE.clean.html#exec>`__ and `EXEC\_W <KeywordsE.clean.html#exec-w>`__
allow you to load a program saved with `SEXEC <KeywordsS.clean.html#sexec>`__.

--------------

SEXEC\_O
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SEXEC\_O [device\_]file,start,length(Toolkit II)  or SEXEC\_O device\_file,start,length (THOR XVI)  or SEXEC\_O #channel,start,length (SMS only)  |
+----------+-------------------------------------------------------------------+
| Location |  Toolkit II, THOR XVI                                             |
+----------+-------------------------------------------------------------------+

 This command is exactly the same as SEXEC except that it will
automatically overwrite an existing file of the same name.

**NOTE**

The Toolkit II version of SEXEC\_O supports the default data device.

**CROSS-REFERENCE**

See `SEXEC <KeywordsS.clean.html#sexec>`__.

--------------

SGN
~~~

--------------

SGN%
~~~~

+----------+-------------------------------------------------------------------+
| Syntax   |  SGN (x)  and SGN% (x)                                            |
+----------+-------------------------------------------------------------------+
| Location |  Math Package (SGN) and SGN (SGN%)                                |
+----------+-------------------------------------------------------------------+

 Both functions work identically and return the sign of any valid
number. The sign is defined as 1 for positive numbers, -1 for negative
and 0 if the number is zero. Any number is allowed as a parameter.

**CROSS-REFERENCE**

`SIGN <KeywordsS.clean.html#sign>`__ is the same.

--------------

SHOOT
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SHOOT                                                            |
+----------+-------------------------------------------------------------------+
| Location |  ST/QL, QSound                                                    |
+----------+-------------------------------------------------------------------+

 This command produces the sound of single gun shot.

**CROSS-REFERENCE**

`SND\_EXT <KeywordsS.clean.html#snd-ext>`__, `BELL <KeywordsB.clean.html#bell>`__,
`EXPLODE <KeywordsE.clean.html#explode>`__.

--------------

SI
==

+----------+-------------------------------------------------------------------+
| Syntax   |  SI                                                               |
+----------+-------------------------------------------------------------------+
| Location |  Beuletools                                                       |
+----------+-------------------------------------------------------------------+

 This function contains the control codes needed to switch on condensed
print on an EPSON compatible printer: PRINT SI
 is the same as: PRINT CHR$(15)

**CROSS-REFERENCE**

`NORM <KeywordsN.clean.html#norm>`__, `BLD <KeywordsB.clean.html#bld>`__,
`EL <KeywordsE.clean.html#el>`__, `DBL <KeywordsD.clean.html#dbl>`__,
`ENL <KeywordsE.clean.html#enl>`__, `PRO <KeywordsP.clean.html#pro>`__,
`NRM <KeywordsN.clean.html#nrm>`__, `UNL <KeywordsU.clean.html#unl>`__,
`ALT <KeywordsA.clean.html#alt>`__, `ESC <KeywordsE.clean.html#esc>`__,
`FF <KeywordsF.clean.html#ff>`__, `LMAR <KeywordsL.clean.html#lmar>`__,
`RMAR <KeywordsR.clean.html#rmar>`__, `PAGDIS <KeywordsP.clean.html#pagdis>`__,
`PAGLEN <KeywordsP.clean.html#paglen>`__.

--------------

SIGN
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SIGN (x)                                                         |
+----------+-------------------------------------------------------------------+
| Location |  BTool                                                            |
+----------+-------------------------------------------------------------------+

 See SGN!

--------------

SIN
===

+----------+-------------------------------------------------------------------+
| Syntax   |  SIN (angle)                                                      |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 This function returns the sine of the given angle (in radians ranging
from -PI/2 to PI/2). In a right-angled triangle, the sine is the ratio
of the length of the side opposite to the angle, to the length of the
hypotenuse. A negative angle indicates that the hypotenuse appears below
the base line.

**Example**

A procedure to draw a sector of a circle with the centre at x,y and
radius r. a is the angle between the first straight side of the sector
and a vertical line on the screen, b is the angle between the two
straight sides. Both angles have to be given in radians, b should be
between 0 and 2\*PI. ch specifies the window to be used and cannot be
omitted: 100 DEFine PROCedure SECTOR (ch,x,y,r,a,b) 110 LOCal
x1,x2,y1,y2 120 x1=x+r\*SIN(a): x2=x+r\*SIN(a+b) 130 y1=y+r\*COS(a):
y2=y+r\*COS(a+b) 140 LINE#ch,x1,y1 TO x,y TO x2,y2 150 ARC#ch,x2,y2 TO
x1,y1 ,b 160 END DEFine SECTOR
 SECTOR #1,50,50,10,PI/4,PI/2

**NOTE 1**

SIN (PI)==0 on all ROMs. This should in fact equal zero - only the
Lightning maths package and SMS get this right.

**NOTE 2**

On Minerva v1.96+ SIN with very large values for radian return 0. On
other implementations it returns an overflow error. You should therefore
check the range of the angle
 parameter.

**CROSS-REFERENCE**

See `COS <KeywordsC.clean.html#cos>`__, `TAN <KeywordsT.clean.html#tan>`__,
`RAD <KeywordsR.clean.html#rad>`__, `ASIN <KeywordsA.clean.html#asin>`__,
`ACOS <KeywordsA.clean.html#acos>`__, `ATAN <KeywordsA.clean.html#atan>`__,
`DEG <KeywordsD.clean.html#deg>`__. See also `SINH <KeywordsS.clean.html#sinh>`__.
Please also refer to the Mathematics section of the Appendix.

--------------

SINH
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SINH (x)                                                         |
+----------+-------------------------------------------------------------------+
| Location |  Hyper, Hyperbola                                                 |
+----------+-------------------------------------------------------------------+

 This function returns the hyperbolic sine (sinus hyperbolicus). The
function is equivalent to: ( EXP(x) - EXP(-x) ) / 2
 where the angle x (in fact a ratio) is a small floating point value.

**Example**

Draw a hyperbola and its asymptotes: 100 SCALE 10,-7,-5: PAPER 0: CLS:
INK 3 110 LINE -4,-4 TO 4,4, -4,4 TO 4,-4: INK 7 120 FOR t = -2 TO 2
STEP 2E-2 130 x = COSH(t): y = SINH(t) 140 POINT x,y, -x,y 150 END FOR t

**CROSS-REFERENCE**

`COSH <KeywordsC.clean.html#cosh>`__, `TANH <KeywordsT.clean.html#tanh>`__,
`ARSINH <KeywordsA.clean.html#arsinh>`__

--------------

SINT
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SINT (x) x=0..65535                                              |
+----------+-------------------------------------------------------------------+
| Location |  BTool                                                            |
+----------+-------------------------------------------------------------------+

 The range of SuperBASIC integers is -32768 to 32767 - these are called
signed integers because they can be negative. This compares to unsigned
integers which have a different range, from 0 to 65535. The function
SINT converts unsigned integers to signed integers, which is not a very
difficult task apart from the need to check the valid range: signed% =
unsigned - 2^16
 or signed% = SINT(unsigned)

**CROSS-REFERENCE**

`UINT <KeywordsU.clean.html#uint>`__ converts in the other direction.

--------------

SIZE
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SIZE ( array [{% \| $}] )  or SIZE ( variable [{% \| $}] )  or SIZE ( value)  |
+----------+-------------------------------------------------------------------+
| Location |  Math Package                                                     |
+----------+-------------------------------------------------------------------+

 The function SIZE can take any kind of variable, array or constant. The
returned value depends very much on the type of parameter: If a simple
variable was passed, the function returns either 0 or 1, 1 if the
variable points to any value or 0 if it does not, ie. if PRINT variable
would show an asterisk to show that variable is not yet defined. Note
that even though on SMS an unset variable does not show an asterisk when
you use PRINT
 variable, this does not prevent this function from returning the
correct value. The return for a constant parameter such as: PRINT
SIZE(-22.3)
 or PRINT SIZE("QL") is always 1. The return for arrays is entirely
different. Passing an array tells SIZE to count its elements. Note the
existence of a zero element, eg. DIM a(2,2) gives a nine elements in
all: a(0,0), a(0,1), a(0,2) a(1,0), a(1,1), a(1,2) a(2,0), a(2,1),
a(2,2)
 SIZE handles string arrays differently in that it returns the number of
strings, not the number of characters, eg. for DIM a$(2,2), SIZE(a$)
will not give 3\*3=9 but 3. Generally the return value of SIZE does not
depend on the actual contents of the passed object. SIZE recognises if
part of an object (especially strings and arrays) was passed.

**Examples**

DIM numbers(1,2,3,4,5)
 PRINT SIZE(numbers) returns 2\*3\*4\*5\*6=720 yippie$="what a wonderful
world"
 PRINT SIZE(yippie$) returns 1 CLEAR PRINT SIZE(eeek) returns 0 DIM
string$(12,7,10) PRINT SIZE(string$) returns 13\*8=104; and PRINT
SIZE(string$(1 TO)) returns 12\*8=96

**NOTE 1**

String arrays also contain numeric values - the first element (which is
character zero) of a string contains the size of the string. For
instance, take the above string$ and then enter: string$(4,4)
="knocking"
 Now PRINT string$(4,4) and you will see 'knocking' in #1. PRINT
string$(4,4,5) gives the fifth character of knocking, the k, and PRINT
string$(4,4,1) the first one, again a k. And PRINT string$(4,4,0)? There
is no character before the first, instead you will get the integer
number 8 because LEN(string$(4,4))=8. This is tricky and not really
necessary to know about as you can use LEN... just in case you come
across the phenomenon and have wondered about it. See also DIM for a
further explanation of strings.

**NOTE 2**

Before v2.06, this function may refuse to work on some implementations,
giving 'Bad Parameter' error or returning the wrong value for string
arrays.

**NOTE 3**

If the parameter is a single dimension string array, for example: DIM
a$(10) PRINT SIZE (a$)
 the value returned is 0. It is hoped that this will be fixed in a
future version so that the value returned is 1.

**CROSS-REFERENCE**

`DIMN <KeywordsD.clean.html#dimn>`__ and `NDIM <KeywordsN.clean.html#ndim>`__ return
other information about an array, eg: `PRINT SIZE(a$) \* DIMN
(a$,NDIM(a$)) <KeywordsP.clean.html#print20size(a)20*20dimn20(a,ndim(a))>`__
gives the total number of characters which can be stored in a string
array a$. `LEN <KeywordsL.clean.html#len>`__ returns the length of a string.
`FREE\_MEM <KeywordsF.clean.html#free-mem>`__ allows you to check how much
memory an array uses.

--------------

SJOB
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SJOB jobnr,timeout  or SJOB jobname,timeout                      |
+----------+-------------------------------------------------------------------+
| Location |  TinyToolkit                                                      |
+----------+-------------------------------------------------------------------+

 There are three ways in which a job can be made to do nothing: (1)
remove the job, (2) set the job's priority to 0, or (3) suspend the job.
This command suspends the specified job for a specified period of time,
which can be identified either by its jobnr (see JOBS) or by -1 (meaning
the current job) or by its name (which need not be in quotes). Although
suspending a job does not alter its priority, a suspended job will have
no effect upon the speed of the QL. A positive timeout will stop the Job
for timeout/50 seconds, whereas any negative number will suspend the job
forever (ie. it can only be re-activated by an express command such as
REL\_JOB). The highest positive timeout is 32768 frames which is
approximately 9 minutes, 6 seconds.

**Example 1**

SJOB "Quill",-1(suspend Quill indefinitely) SJOB Quill,-1is the same
even if there is a variable called Quill. SJOB -1,100suspend the current
job for approx. 2 seconds SJOB 10,100suspend Job number 10 for approx. 2
seconds

**Example 2**

A background Job which carries out work which is not time consuming,
should not slow the whole system down, otherwise it is a complete waste
of the computer's available time. Unfortunately, a priority of 1 is too
high for a simple action such as checking the clock or updating key
macros (See ALTKEY). SJOB is useful to slow this job down to the desired
speed. SJOB is also useful for setting PAUSEs independently of the
machine's speed. The following program demonstrates both uses of SJOB
and has to be compiled and executed as a multitasking job (ie. EXEC).
The priority of the job does not really matter, because the job only
wakes up once a minute, looks at the clock and then drops off again. 100
REPeat Tower 110 d$=DATE$: minute=d$(16 TO 17) 120 SELect ON minute 130
=30:BEEP 20000,0,100,1000,0 140 =0:hour=d$(13 TO 14) MOD 12:IF
hour=0:hour=12 150 FOR h=1 to hour: BEEP 10000,h,10,100,1: SJOB
Q\_MYJOB,65 160 =15:BEEP 5000,0,10,20,5000 170 END SELect

180 SJOB Q\_MYJOB,3000 190 END REPeat Tower
 This example needs Qliberator's Q\_MYJOB function.

**NOTE**

As from v1.11, jobnr can be -1, so in the above example 2, you could use
SJOB -1,65 and SJOB -1,3000 instead of the similar commands in lines 150
and 180 respectively. Earlier versions would also not accept a variable
as the parameter for the job number.

**CROSS-REFERENCE**

`REL\_JOB <KeywordsR.clean.html#rel-job>`__ releases a suspended job.
`JOBS <KeywordsJ.clean.html#jobs>`__ lists all current jobs.
`SUSJOB <KeywordsS.clean.html#susjob>`__ and `TTSUS <KeywordsT.clean.html#ttsus>`__
are almost the same as `SJOB <KeywordsS.clean.html#sjob>`__.

--------------

SLOAD
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SLOAD adr                                                        |
+----------+-------------------------------------------------------------------+
| Location |  Ecran Manager This command takes part of a screen which has      |
+----------+-------------------------------------------------------------------+

been saved with SSAVE and copies it to the visible screen, removing it
from memory. SLOAD works like SSHOW with the sole difference that it can
only be called once.

**NOTE**

This has the same problems as SSAVE.

**CROSS-REFERENCE**

`SSHOW <KeywordsS.clean.html#sshow>`__

--------------

SLUG
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SLUG msecs                                                       |
+----------+-------------------------------------------------------------------+
| Location |  Gold Card (v2.24+), SMS A disadvantage of the speed              |
+----------+-------------------------------------------------------------------+

improvements by Gold Card (and later expansion boards) is that most
games become simply too fast. The command SLUG can slow down the whole
system by advising the operating system to read the keyboard less often
(other solutions install background interrupts but some games suspend
these). The parameter specifies the delay in milliseconds. The higher
msecs, the slower the general operating speed will be. SLUG 5 to SLUG 10
on a Gold Card gives roughly the speed of a normal QL, but this depends
very much on the software. Programs which do not spend a lot of time
waiting for keyboard input such as interactive games, will not slow down
so much. Only keyboard access is slowed down.

**Example**

100 FOR n=0 to 1000 STEP 10 110 SLUG n 120 PRINT n 130 dummy=KEYROW(0)
140 END FOR n

**NOTE**

Since SLUG only slows down keyboard access (this is especially designed
for arcade games), the above example would not be affected without line
130. All other lines run at maximum speed; the advantage is that screen
output, which is a limiting factor for arcade games, is not affected by
SLUG.

**CROSS-REFERENCE**

`SCR2DIS <KeywordsS.clean.html#scr2dis>`__ and
`CACHE\_ON <KeywordsC.clean.html#cache-on>`__ can be used to speed up the
computer's speed.

--------------

SMOVE
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SMOVE scrno, adr [,xpos, ypos]                                   |
+----------+-------------------------------------------------------------------+
| Location |  Ecran Manager The                                                |
+----------+-------------------------------------------------------------------+

command SMOVE will copy a stored screen (saved with SSAVE, where adr
comes from) to the first (scrno=0) or second screen (scrno=1) - the
latter is only possible if your system supports a dual screen mode.
Optionally, it is possible to specify a location where the screen part's
upper left corner (absolute co-ordinates) should be placed; SMOVE will
correct the xpos and ypos automatically if the restored picture would
exceed the screen borders.

**NOTE**

See SSAVE.

**CROSS-REFERENCE**

`SSHOW <KeywordsS.clean.html#sshow>`__, `SLOAD <KeywordsS.clean.html#sload>`__

--------------

SND\_EXT
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SND\_EXT                                                         |
+----------+-------------------------------------------------------------------+
| Location |  ATARI\_REXT (v1.24 to v2.15) The ST-QL Emulators contain new     |
+----------+-------------------------------------------------------------------+

extensions (based upon the QSound device) to enable programs to use the
ST's sound facilities. Unfortunately, these extensions clash with the
Turbo SuperBASIC compiler from Digital Precision. When the Emulator is
started up, these sound extensions are switched off. SND\_EXT will
switch them back on. This command was replaced in v2.15 by ATARI\_EXT.
You can test if the QSOUND interface (or these commands) are present by
using: PEEK\_L(!! HEX('164'))
 which will be 0 unless the commands are present (Turbo may also alter
this figure whilst it is compiling a program).

**WARNING**

The sound extensions may crash the hardware.

**CROSS-REFERENCE**

Some of the available extensions for sound are
`PLAY <KeywordsP.clean.html#play>`__, `RELEASE <KeywordsR.clean.html#release>`__,
`BELL <KeywordsB.clean.html#bell>`__, `SHOOT <KeywordsS.clean.html#shoot>`__,
`EXPLODE <KeywordsE.clean.html#explode>`__.

--------------

SNET
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SNET no                                                          |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E, ATARI Emulators This command is similar to the NET       |
+----------+-------------------------------------------------------------------+

command in that it sets the Network Station number of the machine on
which it is issued. The only difference is that here it sets the station
number for the SERNET Network (as opposed to the QNet Network).

**CROSS-REFERENCE**

See `SNET% <KeywordsS.clean.html#snet>`__,
`SNET\_USE <KeywordsS.clean.html#snet-use>`__ and
`NET <KeywordsN.clean.html#net>`__. Also please see
`SERNET <KeywordsS.clean.html#sernet>`__, `MIDINET <KeywordsM.clean.html#midinet>`__
and `FSERVE <KeywordsF.clean.html#fserve>`__.

--------------

SNET%
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SNET%                                                            |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E, ATARI Emulators This function returns the current        |
+----------+-------------------------------------------------------------------+

station number of the computer as set with SNET .

**CROSS-REFERENCE**

See `SNET <KeywordsS.clean.html#snet>`__. `NET\_ID <KeywordsN.clean.html#net-id>`__
is similar.

--------------

SNET\_ROPEN
===========

+----------+-------------------------------------------------------------------+
| Syntax   |  SNET\_ROPEN                                                      |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E, ATARI Emulators This command reopens the serial ports    |
+----------+-------------------------------------------------------------------+

for use by the SERNET
 driver in case they have been closed by other programs.

**CROSS-REFERENCE**

See `SERNET <KeywordsS.clean.html#sernet>`__.

--------------

SNET\_S%
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SNET\_S% (station)                                               |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E, ATARI Emulators This function enables you to check       |
+----------+-------------------------------------------------------------------+

whether a machine with the specified station number is connected to the
SERNET . This can be useful to prevent the problem of the Network
re-trying several times before failing when asked to send or read data
from a Network station which does not exist.

**CROSS-REFERENCE**

See `SNET <KeywordsS.clean.html#snet>`__.

--------------

SNET\_USE
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SNET\_USE id                                                     |
+----------+-------------------------------------------------------------------+
| Location |  SMSQ/E, ATARI Emulators Due to the fact that SERNET Networks     |
+----------+-------------------------------------------------------------------+

can be run on computers alongside MIDINET Networks and even QNET
Networks, it may be necessary to alter the identification letter used to
access facilties on other computers in the Network. The default letter
id is s, but this can be set to any other single letter by using this
command. However, you should avoid letters which already appear as the
first letter in another device driver (see DEVLIST).

**Example**

SNET\_USE c DEV\_USE 3,c2\_win1\_
 Redefine DEV3\_ so that it refers to win1\_ on station number 2 in the
SERNET Network. This can be useful to allow some programs to access data
over the Network. However note the file protection implemented in SERNET
and MIDINET.

**NOTE**

Before v2.28 of Toolkit II, the various wildcard commands did not accept
any single letter other than n as representing a Network.

**CROSS-REFERENCE**

See `SNET <KeywordsS.clean.html#snet>`__ and
`SERNET <KeywordsS.clean.html#sernet>`__. Refer also to
`SNET\_S% <KeywordsS.clean.html#snet-s>`__.
`MNET\_USE <KeywordsM.clean.html#mnet-use>`__ is similar. See also
`NFS\_USE <KeywordsN.clean.html#nfs-use>`__.

--------------

SORT
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SORT array$, offset [,row]                                       |
+----------+-------------------------------------------------------------------+
| Location |  ARRAY The SORT command                                           |
+----------+-------------------------------------------------------------------+

takes a two or three-dimensional string array and sorts it in ascending
order. offset is an even number which allows you to apply different sort
criteria by telling SORT to compare the sub-strings to the right of
position offset+1. The third, optional parameter is only necessary for
three-dimensional arrays: it selects the row to be sorted.

**Example**

CAT lists a sorted directory, including deleted files, to window #1.
Sorting the directory in fact requires just one line here (390), the
entries are sorted by file length because the format of each entry is as
follows: 1 10 20 30 37 45
\|--------\|--------\|---------\|-------\|-------\| filename length
Changing the SORT in line 390 to: 390 SORT entry$, 0
 will sort the list alphabetically. The other parts of the example
PROCedure are written to require only Toolkit II, that makes reading the
directory (the j loop from line 240 to 280) quite slow. If you are
wondering why the file header is stored twice, both as a string
(header$) and for direct memory access (header), this is for getting the
best out of basic QL facilities, namely PEEK\_W, PEEK\_L and string
slicing (line 310). 100 DEFine PROCedure CAT (dir$) 110 LOCal ch%,
entries%, header, header$(64) 120 LOCal c%, l%, i 130 PRINT "Directory
of"!dir$;": "; 140 ch% = FOP\_DIR(dir$) 150 IF ch% < 0 THEN 160 PRINT
\\"Cannot open directory,"\\"because "; 170 REPORT#1, ch%: RETurn 180
END IF 190 entries% = FLEN(#ch%) / 64 200 DIM entry$(entries%, 45) 210
header = ALCHP(64) 220 FOR i = 0 TO entries% - 1 230 header$ = "" 240
FOR j = 0 TO 63 250 BGET#ch%, c% 260 POKE header+j, c% 270 header$ =
header$ & CHR$(c%) 280 END FOR j 290 l% = PEEK\_W(header + 14) 300 IF l%
THEN 310 entry$(i) = header$(17 TO 16 + l%) & FILL$(" ", 37 - l%) 320
entry$(i) = entry$(i) & (PEEK\_L(header) - 64) 330 ELSE

340 entry$(i) = "(deleted)" & FILL$(" ", 28) & "n.a." 350 END IF 360
PRINT "."; 370 END FOR i 380 CLOSE#ch%: RECHP header: PRINT 390 SORT
entry$, 36 400 FOR i = 0 TO entries% - 1 410 PRINT entry$(i) 420 END FOR
i 430 END DEFine CAT

**CROSS-REFERENCE**

`SEARCH <KeywordsS.clean.html#search>`__ searches string arrays.

--------------

SOUNDEX
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SOUNDEX (word$)                                                  |
+----------+-------------------------------------------------------------------+
| Location |  �hnlichkeiten This function returns an integer which           |
+----------+-------------------------------------------------------------------+

represents the word contained in the string passed as a parameter, in
such a way that for two English words which sound similar, the same
results are returned. Internally, each character is replaced by a cipher
and then all double (triple etc) ciphers are removed.

**Examples**

SOUNDEX ("user")=26 SOUNDEX ("looser")=426 SOUNDEX ("l'user")=426

**NOTE**

The difference between two SOUNDEX results is not proportional to the
phonetic difference between the parameters.

**CROSS-REFERENCE**

`WLD <KeywordsW.clean.html#wld>`__ calculates such a difference,
`PHONEM <KeywordsP.clean.html#phonem>`__ is similar to
`SOUNDEX <KeywordsS.clean.html#soundex>`__.

--------------

SPJOB
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SPJOB jobname,priority  (Toolkit II, TinyToolkit pre v1.10 and THOR only)  or SPJOB jobnr,tag,priority (Toolkit II and THOR only)  or SPJOB jobID,priority  or SPJOB jobnr,priority(TinyToolkit pre v1.10)  |
+----------+-------------------------------------------------------------------+
| Location |  Toolkit II, THOR XVI, TinyToolkit (pre v1.10), BTool             |
+----------+-------------------------------------------------------------------+

 The specified job (described by either its jobname, its job number and
tag, or its job identification number) is set to the given priority
(which should be in the range 0 to 127 to maintain compatability with
Minerva). A priority of zero will ensure that the job waits until it is
given a higher priority by another job.

**NOTE 1**

It is possible that only the second syntax works. Get an update!

**NOTE 2**

Before v1.10 of TinyToolkit, this toolkit included the same command but
with an incompatible syntax - this version has been renamed SP\_JOB.

**MINERVA NOTES**

Although on other ROMs, a priority higher than 127 can be assigned to a
job, on Minerva, the permitted priority range is actually -128...127 (if
a priority is stated to be higher than 127, you must subtract the
difference between this number and 256 from 0 to get the negative
priority). The idea behind these negative priorities is that they are
for 'background tasks' which will only run when no tasks with a positive
priority are running. However, the effect is slightly more complex
because these negative priorities are split into eight levels, each of
which can have jobs running with priorities equivalent to -1 to -15. A
job in one level will not run whilst a job in a higher level is running,
however within each level each job will get a different amount of
processor time depending on their priorities {a job with a lower
priority (eg. -15) will get more processing time than a job with a
higher priority (eg. -1)}.

LevelPriority RangeOverall value
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

0-1...-15-1...-15 1-1...-15-16...-31 2-1...-15-32...-47
3-1...-15-48...-63 4-1...-15-64...-79 5-1...-15-80...-95
6-1...-15-96...-111 7-1...-15-112...-127

**WARNING**

The supplied parameters are not checked to see what you are trying to
do, which means that you can use this command to set the priority of
SuperBASIC to zero, preventing further command entry.

**CROSS-REFERENCE**

`SJOB <KeywordsS.clean.html#sjob>`__ suspends a job,
`REL\_JOB <KeywordsR.clean.html#rel-job>`__ releases it.
`RJOB <KeywordsR.clean.html#rjob>`__ and `KJOB <KeywordsK.clean.html#kjob>`__ remove
a specific job, `KILL <KeywordsK.clean.html#kill>`__ and
`KJOBS <KeywordsK.clean.html#kjobs>`__ remove all jobs except the main
SuperBASIC interpreter. See also `SP\_JOB <KeywordsS.clean.html#sp-job>`__,
`PRIO <KeywordsP.clean.html#prio>`__,
`PRIORITISE <KeywordsP.clean.html#prioritise>`__.

--------------

SPL
===

+----------+-------------------------------------------------------------------+
| Syntax   |  SPL {input \| #ch} [TO {output \| #ch}]                          |
+----------+-------------------------------------------------------------------+
| Location |  Toolkit II,                                                      |
+----------+-------------------------------------------------------------------+

THOR XVI
 It can sometimes be useful to copy a file in the background. The
command SPL sets up a small Job which runs at a low priority and acts as
a print spooler, reading the whole of the input data from the given
input device as quickly as possible and then just outputting the data
when it can. Although control is returned to the calling program quite
quickly, both the input and output files are left open until SPL
 has completed its job. SPL is mainly for outputting files to a printer
in the background (allowing you to carry on other work in the meantime).
If however, a file is specified as the output, the SPL
 command acts like COPY\_O, except in the background. If output is not
specified, the SPL command uses the default destination device. Existing
channel numbers may also be specified as the input
 and output names, provided that both channels are already open for
input and output respectively.

**Examples**

(1) SPL flp1\_Example\_txt TO SER
 prints the file flp1\_Example\_txt in the background. (2) SPL\_USE
SER:SPL flp1\_Example\_txt
 this is the same as example 1.

**WARNING**

If the default destination device is a directory device and you do not
specify a file for output, the SPL job may never complete its task and
leave files open.

**CROSS-REFERENCE**

See `COPY\_O <KeywordsC.clean.html#copy-o>`__ and
`SPLF <KeywordsS.clean.html#splf>`__. `SPL\_USE <KeywordsS.clean.html#spl-use>`__
and `DEST\_USE <KeywordsD.clean.html#dest-use>`__ allow you to alter the
default destination device.

--------------

SPLF
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SPLF {input \| #ch} [TO {output \| #ch}]                         |
+----------+-------------------------------------------------------------------+
| Location |  Toolkit II,                                                      |
+----------+-------------------------------------------------------------------+

THOR XVI
 This is exactly the same as SPL except that at the end of sending the
output, a form feed symbol, CHR$(12) is sent. SPLF is obviously intended
for use with printers.

**CROSS-REFERENCE**

See `SPL <KeywordsS.clean.html#spl>`__.

--------------

SPL\_USE
========

+----------+-------------------------------------------------------------------+
| Syntax   |  SPL\_USE name                                                    |
+----------+-------------------------------------------------------------------+
| Location |  Toolkit II, THOR XVI                                             |
+----------+-------------------------------------------------------------------+

 This command sets the default destination device and therefore has a
similar effect to DEST\_USE. However, this command is slightly improved,
in that if the supplied name does not end in an underscore, this is
taken to be an external device port (such as SER) and no underscore is
added.

**Examples**

(1) DEST\_USE flp2\_Quill:COPY ram2\_Letter\_doc
 will copy the file ram2\_letter\_doc to flp2\_Quill\_letter\_doc. (2)
SPL\_USE ser:COPY ram2\_Letter\_txt
 will copy the file ram2\_Letter\_txt to the serial port, ser.

**NOTE**

SPL\_USE will overwrite the default destination device set with
DEST\_USE.

**CROSS-REFERENCE**

`DESTD$ <KeywordsD.clean.html#destd>`__ returns the current default
destination device. Also see `PROG\_USE <KeywordsP.clean.html#prog-use>`__,
`DLIST <KeywordsD.clean.html#dlist>`__,
`DATA\_USE <KeywordsD.clean.html#data-use>`__,
`DEST\_USE <KeywordsD.clean.html#dest-use>`__,
`DDOWN <KeywordsD.clean.html#ddown>`__, `DUP <KeywordsD.clean.html#dup>`__, and
`DNEXT <KeywordsD.clean.html#dnext>`__.

--------------

SP\_JOB
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SP\_JOB jobname, priority  or SP\_JOB jobnr, priority            |
+----------+-------------------------------------------------------------------+
| Location |  TinyToolkit (v1.10+)                                             |
+----------+-------------------------------------------------------------------+

 Acts just like SPJOB.

**NOTE**

As from v1.11, the jobnr may be -1 to mean the current job. Earlier
versions would not allow jobnr to be a variable either.

**CROSS-REFERENCE**

See `SPJOB <KeywordsS.clean.html#spjob>`__. `JBASE <KeywordsJ.clean.html#jbase>`__
contains details of the different parameters
`jobname <Keywordsj.clean.html#jobname>`__ and
`jobnr <Keywordsj.clean.html#jobnr>`__.

--------------

SQR
===

+----------+-------------------------------------------------------------------+
| Syntax   |  SQR (x)                                                          |
+----------+-------------------------------------------------------------------+
| Location |  Math Package                                                     |
+----------+-------------------------------------------------------------------+

 See SQRT below!

--------------

SQRT
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SQRT (x)                                                         |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 This function returns the square root of the given parameter. The
opposite of this function is x^2. The given parameter can be zero or any
positive value.

**Example**

PRINT SQRT(32768\*2) will return 256.

**NOTE 1**

The version of SQRT implemented on Minerva v1.90 (or later) is the
fastest version of this command which we have seen anywhere!

**NOTE 2**

On Minerva pre v1.96, SQRT(4^x\*(12^31)) was returning the negative
square root. It now returns the positive square root.

**CROSS-REFERENCE**

`ABS <KeywordsA.clean.html#abs>`__ will return the absolute value of the given
parameter.

--------------

SSAVE
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SSAVE (scrno, xpos, ypos, xsiz, ysiz)                            |
+----------+-------------------------------------------------------------------+
| Location |  Ecran Manager                                                    |
+----------+-------------------------------------------------------------------+

 The function SSAVE reserves memory and saves a part of the screen to
it, the saved block's left upper corner is the point (xpos,ypos) in
absolute co-ordinates, the width is xsiz and the height ysiz. xpos may
range from 0 to 511 and ypos from 0 to 255, so SSAVE
 is not suitable for resolutions other than 512x256 pixels. The reserved
memory can only be released with SLOAD. The first parameter scrno can be
either 0 or 1 - it is used under dual screen mode to select the first or
second screen, scrno=1 is only available under dual screen mode, on
other machines SSAVE will break with the 'not found' (-7) error. The
value returned represents the address where the screen is stored in
memory.

**NOTE**

If you wish to link the Ecran Manager Toolkit to a QLiberated program,
you must not use the ECMAN but the ECMANcp version.

**CROSS-REFERENCE**

Saved pictures can be reloaded with `SSHOW <KeywordsS.clean.html#sshow>`__.

--------------

SSHOW
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SSHOW adr                                                        |
+----------+-------------------------------------------------------------------+
| Location |  Ecran Manager                                                    |
+----------+-------------------------------------------------------------------+

 This command restores a screen part saved with SSAVE, therefore the
parameter adr must be the value returned by the SSAVE function. The
memory area where the picture is saved is unaffected, so SSHOW can be
executed any number of times.

**NOTE**

See SSAVE.

**CROSS-REFERENCE**

`SLOAD <KeywordsS.clean.html#sload>`__ displays a saved screen part and frees
the memory used, `SMOVE <KeywordsS.clean.html#smove>`__ allows you to view
such a saved screen part at a different location or on a different
screen.

--------------

SSTAT
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SSTAT                                                            |
+----------+-------------------------------------------------------------------+
| Location |  Ecran Manager                                                    |
+----------+-------------------------------------------------------------------+

 The function SSTAT returns either 0 or 1, corresponding to the first or
second screen. The function is used to find out which of these screens
is currently the visible screen. Unless you have Minerva or Amiga QDOS
set up in dual screen mode, this is always 0.

**Example**

Force the second screen to be displayed (this only works in Minerva or
Amiga QDOS): IF SSTAT = 0 THEN MODE 80,-1

**NOTE**

See SSAVE.

**CROSS-REFERENCE**

`DEFAULT\_SCR <KeywordsD.clean.html#default-scr>`__,
`SCRON <KeywordsS.clean.html#scron>`__, `SCROFF <KeywordsS.clean.html#scroff>`__,
`MODE <KeywordsM.clean.html#mode>`__

--------------

SSTEP
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  SSTEP [{#ch \| device\_file}] [; [first] [TO [last]]]            |
+----------+-------------------------------------------------------------------+
| Location |                                                                   |
+----------+-------------------------------------------------------------------+

Minerva (TRACE)
 Minerva is supplied with a very simple trace routine on the utility
disk supplied with Minerva, stored in the file trace\_bin. Before using
the trace function, you will need to link in trace\_bin with the line:
LRESPR flp1\_trace\_bin
 or something similar. Having done this, you can turn on the tracing
function with SSTEP which will print to the given channel (default #0)
or file, each line number and statement just before it is performed in
the format: line\_no : statement\_no
 You can also supply the trace function with a line range, so that it
will only report on statements being executed within the given line
range. The line range defaults to: 1 TO 32767
 Whilst the trace function is enabled and the program is running within
the given range, the interpreter will wait for a key to be pressed
between each statement. As each command in each statement is executed, a
single character is shown by the trace routine to represent the type of
the command to be executed. However, the meaning of these symbols has
never been revealed. In single-step mode, you need to press a key
between each command!!

**NOTE**

This trace toolkit will only work on Minerva.

**CROSS-REFERENCE**

See `TRON <KeywordsT.clean.html#tron>`__ and `TROFF <KeywordsT.clean.html#troff>`__.

--------------

STAMP
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  STAMP string$                                                    |
+----------+-------------------------------------------------------------------+
| Location |  STAMP                                                            |
+----------+-------------------------------------------------------------------+

 This command is the same as FORCE\_TYPE !

--------------

STAT
====

+----------+-------------------------------------------------------------------+
| Syntax   |  STAT [#channel,] [device] or STAT \\file [,device]               |
+----------+-------------------------------------------------------------------+
| Location |                                                                   |
+----------+-------------------------------------------------------------------+

Toolkit II, THOR XVI
 This command prints the name of a medium inserted into the given device
and the available sectors to the given channel
 (default #1), or file. The device must be a directory device, such as
FLP1\_ (but not PAR or CON). If no device is stated, then the default
data device is used.

**Examples**

STAT STAT ram1\_ STAT n2\_win1\_ STAT #3,flp2\_ STAT #0 STAT \\mdv2\_
STAT \_dat STAT \\ram5\_TMP,mdv1\_

**CROSS-REFERENCE**

`DLIST <KeywordsD.clean.html#dlist>`__ shows the default devices,
`DATAD$ <KeywordsD.clean.html#datad>`__ holds the default data device. Change
default devices with `DATA\_USE <KeywordsD.clean.html#data-use>`__,
`PROG\_USE <KeywordsP.clean.html#prog-use>`__ and
`SPL\_USE <KeywordsS.clean.html#spl-use>`__. `DIR <KeywordsD.clean.html#dir>`__ and
`WSTAT <KeywordsW.clean.html#wstat>`__ provide other information about
directory devices.

--------------

` <>`__.. STEP
==============

+----------+-------------------------------------------------------------------+
| Syntax   |  .. STEP stepwidth                                                |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 This keyword forms part of the FOR structure and has no meaning on its
own. Any attempt to enter it on its own will result in a 'Bad Line'
error.

**CROSS-REFERENCE**

See `FOR <KeywordsF.clean.html#for>`__!

--------------

STOP
====

+----------+-------------------------------------------------------------------+
| Syntax   |  STOP                                                             |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM, Toolkit II                                               |
+----------+-------------------------------------------------------------------+

 This command forces an interpreted program to be terminated at the
position where STOP appears in the listing. The program can then be
continued (provided that the message 'PROC/FN cleared' has not appeared)
by using the command CONTINUE. Compiled programs terminate and remove
themselves when STOP is encountered.

**Example**

This program will print 1 and 2 to channel #1 and stop at line 120. If
it runs under the interpreter, CONTINUE will restart at line 130 (after
STOP) and print 3 and 4. RETRY does not continue here because it tries
to re-run line 120 and stops again. 100 PRINT 1 110 PRINT 2 120 STOP 130
PRINT 3 140 PRINT 4

**NOTE**

If Toolkit II is installed, STOP clears WHEN ERRor definitions.

**CROSS-REFERENCE**

`RUN <KeywordsR.clean.html#run>`__ starts a program and `GO
TO <KeywordsG.clean.html#go20to>`__ jumps to a specified line. See
`CONTINUE <KeywordsC.clean.html#continue>`__,
`RETRY <KeywordsR.clean.html#retry>`__. Also see
`QUIT <KeywordsQ.clean.html#quit>`__.

--------------

STRIP
=====

+----------+-------------------------------------------------------------------+
| Syntax   |  STRIP [#ch,] colour                                              |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 Whenever a character is printed to the QL screen, it is made up of two
components - the character itself which appears in the current INK
colour, and the rectangular block on which the character has been
formed. The latter is known as the 'strip' of the character and the size
of this strip depends on the current character size and spacing (see
CSIZE). Normally, when you set the PAPER colour of a window, the
character STRIP is set to the same colour. However, you may wish to
print characters on a different background colour in order to make them
stand out. STRIP allows you to alter the colour of the character
background in the specified window (default #1) to a given colour (or
composite colour). However, if you want to print characters in a window
without using this character background (ie. forming a transparent
strip), you will need to use the commands OVER 0 or OVER -1 (see OVER
for more details).

**Example**

A simple routine for printing out a Title on screen: 1 WINDOW
512,256,0,0:PAPER 4 2 MODE 4:CLS 3 TITLE #1,'This is a Title',120,95 100
DEFine PROCedure TITLE(ch,text$,x,y) 110 CSIZE 2,1:OVER 0 120 CURSOR
#ch,x-2,y+1 130 STRIP #ch,0:PRINT #ch,FILL$(' ',LEN(text$)) 140 CURSOR
#ch,x,y 150 STRIP #ch,2:INK #ch,7 160 PRINT #ch,text$ 170 CURSOR
#ch,x-2,y+1 180 OVER 1:INK#ch,0 190 PRINT #ch,text$ 200 END DEFine

**NOTE**

The STRIP colour is automatically reset to the same as the PAPER colour
following a PAPER command.

**CROSS-REFERENCE**

`PAPER <KeywordsP.clean.html#paper>`__ also sets the
`STRIP <KeywordsS.clean.html#strip>`__ colour. Compare
`IO\_TRAP <KeywordsI.clean.html#io-trap>`__. `CSIZE <KeywordsC.clean.html#csize>`__
and `CHAR\_INC <KeywordsC.clean.html#char-inc>`__ allow you to alter the
spacing between characters. `INK <KeywordsI.clean.html#ink>`__ contains
details of standard and composite colours. See also
`INVERSE <KeywordsI.clean.html#inverse>`__ which can also prove useful.

--------------

` <>`__... SUB
==============

+----------+-------------------------------------------------------------------+
| Syntax   |  ... SUB line                                                     |
+----------+-------------------------------------------------------------------+
| Location |  QL ROM                                                           |
+----------+-------------------------------------------------------------------+

 This keyword forms part of the SuperBASIC keyword GO SUB and has no
purpose on its own. Any attempt to use it on its own will cause a 'Bad
Line' error.

**CROSS-REFERENCE**

See `GO SUB <KeywordsG.clean.html#go20sub>`__!

--------------

SUSJOB
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SUSJOB jobId,timeout                                             |
+----------+-------------------------------------------------------------------+
| Location |  BTool                                                            |
+----------+-------------------------------------------------------------------+

 See SJOB.

--------------

SWAP
====

+----------+-------------------------------------------------------------------+
| Syntax   |  SWAP var1,var2  or SWAP var1$,var2$                              |
+----------+-------------------------------------------------------------------+
| Location |  SWAP, Math Package                                               |
+----------+-------------------------------------------------------------------+

 This command exchanges the values of the two variables. The parameters
can be either numeric variables (integer and floating point) or strings.
Arrays are not allowed and both variables have to be the same type: SWAP
a$,b is illegal, even if a$ contained a valid number. Also, constant
expressions such as SWAP a%,3 are not allowed, since this would not make
any sense. Unfortunately, it is not possible to SWAP two elements of an
array, the example shows why this would be practicable. The Math Package
variant also allows you to swap whole arrays.

**Example**

In most kinds of sorting routines, a lot of swapping is necessary and an
assembler routine which takes over this work makes the process quicker.
Here is a Quicksort algorithm as a general subroutine. field$ is sorted
from the left element to the right. 100 DEFine PROCedure QSort
(field$,left,right) 110 LOCal i,j,last$ 120 i=left: j=right:
last$=field$(j) 130 REPeat SortLoop1 140 REPeat SortLoop2:IF
field$(i)<last$:i=i+1:ELSE EXIT SortLoop2 150 REPeat SortLoop2:IF
field$(j)>last$:j=j-1:ELSE EXIT SortLoop2 160 IF i<=j THEN 170
f1$=field$(i): f2$=field$(j): SWAP f1$,f2$ 180 field$(i)=f1$:
field$(j)=f2$ 190 i=i+1: j=j-1 200 END IF 210 IF i>j THEN EXIT SortLoop1
220 END REPeat SortLoop1 230 IF left<j THEN QSort field$,left,j 240 IF
right>i THEN QSort field$,i,right 250 END DEFine QSort
 Compilers have a fixed stack size - you might have to raise this
because this procedure iterates (ie. calls itself), which is something
which eats up the stack very quickly. The SuperBASIC interpreter uses a
flexible stack.

**CROSS-REFERENCE**

`LET <KeywordsL.clean.html#let>`__

--------------

SXTRAS
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SXTRAS [#channel,] [character]                                   |
+----------+-------------------------------------------------------------------+
| Location |  TinyToolkit                                                      |
+----------+-------------------------------------------------------------------+

 This command lists all machine code SuperBASIC extensions in alphabetic
order to the given channel (default #1). If a character is specified,
then only those commands which appear later alphabetically will be
listed - if character is longer than one character, only the first
character is recognised.

**Example**

SXTRAS s

**CROSS-REFERENCE**

`EXTRAS <KeywordsE.clean.html#extras>`__ and
`TXTRAS <KeywordsT.clean.html#txtras>`__ do not sort the keywords. Also look
at `VOCAB <KeywordsV.clean.html#vocab>`__.

--------------

SYNCH%
======

+----------+-------------------------------------------------------------------+
| Syntax   |  SYNCH%                                                           |
+----------+-------------------------------------------------------------------+
| Location |  KMOUSE, MOUSE (DIY Toolkit - Vol I)                              |
+----------+-------------------------------------------------------------------+

 This function is only used to debug the DIY Toolkit mouse drivers. It
returns a value which is in the range 1...3 for a two button mouse and
1...5 for a three button mouse. The value indicates which byte of the
mouse message is due next and therefore when being used, you should see
it circling between the upper and lower limits of the range. However, if
the byte is corrupt or lost, then the value returned by this function
will be zero. This can indicate problems with either your serial port or
the interface to the mouse - if the former, you should consider getting
Hermes for your computer.

**CROSS-REFERENCE**

See `PTR\_ON <KeywordsP.clean.html#ptr-on>`__ and
`PTR\_FN% <KeywordsP.clean.html#ptr-fn>`__.

--------------

SYSBASE
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  SYSBASE                                                          |
+----------+-------------------------------------------------------------------+
| Location |  QBASE (DIY Toolkit - Vol Q)                                      |
+----------+-------------------------------------------------------------------+

 The function SYSBASE is identical to SYS\_BASE, see below. Don't
forget: never assume that the System Variables are located at 163840
($28000). They can move!!

--------------

SYS\_BASE
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SYS\_BASE                                                        |
+----------+-------------------------------------------------------------------+
| Location |  SYSBASE, Fn                                                      |
+----------+-------------------------------------------------------------------+

 The function SYS\_BASE returns the base address of the system
variables.

**Example**

POKE\_W SYS\_BASE+140,8 POKE\_W SYS\_BASE+142,3
 Sets the key repeat delay.

**NOTE 1**

Users peeking and poking in the System Variables should know what they
are doing!

**NOTE 2**

Minerva and SMS offer another technique to read and alter system
variables but these are specific to Minerva and SMS whilst SYS\_BASE
works an every ROM. It is generally not advisable to access fixed
addresses in memory as virtually everything can move around.

**CROSS-REFERENCE**

`SYSBASE <KeywordsS.clean.html#sysbase>`__,
`WIN\_BASE <KeywordsW.clean.html#win-base>`__, `PEEK <KeywordsP.clean.html#peek>`__,
`POKE <KeywordsP.clean.html#poke>`__, `SCREEN <KeywordsS.clean.html#screen>`__,
`SYS\_VARS <KeywordsS.clean.html#sys-vars>`__, `VER$ <KeywordsV.clean.html#ver>`__

--------------

SYS\_VARS
=========

+----------+-------------------------------------------------------------------+
| Syntax   |  SYS\_VARS                                                        |
+----------+-------------------------------------------------------------------+
| Location |  THOR (all models)                                                |
+----------+-------------------------------------------------------------------+

 The function SYS\_VARS returns the base address of the system
variables, which can move around on the THOR range of computers, in much
the same way as they can move on other implementations - it is therefore
imperative that any program which uses the system variables works
relative to the address returned by this function.

**Example**

POKE SYS\_VARS+133,-1
 switches off the THOR XVI's windowing facilities for windows opened
after this command.

**CROSS-REFERENCE**

`VER$(-2) <KeywordsV.clean.html#ver(-2)>`__ on Minerva ROMs and on SMS
returns the base address of the system variables, as do
`SYS\_BASE <KeywordsS.clean.html#sys-base>`__ and
`SYSBASE <KeywordsS.clean.html#sysbase>`__.

--------------

S\_FONT
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  S\_FONT [#channel,] font1, font2                                 |
+----------+-------------------------------------------------------------------+
| Location |  FONTS                                                            |
+----------+-------------------------------------------------------------------+

 This command is exactly the same as CHAR\_USE.

**CROSS-REFERENCE**

See `CHAR\_USE <KeywordsC.clean.html#char-use>`__ and
`CHAR\_DEF <KeywordsC.clean.html#char-def>`__. See also the Appendix on Fonts.

--------------

S\_LOAD
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  S\_LOAD adr                                                      |
+----------+-------------------------------------------------------------------+
| Location |  TinyToolkit                                                      |
+----------+-------------------------------------------------------------------+

 S\_LOAD takes an address (adr) returned by S\_SAVE and displays the
saved screen just like S\_SHOW does. Additionally, the reserved memory
to which adr points is released so that it can be used for other
purposes. S\_LOAD therefore only works once on a given address.

**NOTE 1**

Under odd conditions S\_LOAD will load and show more than had been
stored with S\_SAVE. The Win... set of commands replace the S\_... set
and get around these problems.

**NOTE 2**

S\_LOAD assumes that it needs to copy the stored screen to $20000 and
that will not therefore work on Minerva's second screen. It also assumes
the screen is 512x256 pixels and will not work on higher resolutions or
under dual screen mode.

**WARNING**

A wrong address leads to crashes!

--------------

S\_SAVE
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  S\_SAVE (#wind)                                                  |
+----------+-------------------------------------------------------------------+
| Location |  TinyToolkit                                                      |
+----------+-------------------------------------------------------------------+

 This function causes the contents of the window #wind to be stored in
memory and the address is then returned. Do not forget the return value!
#wind must be a window or a bad parameter error (-15) is reported.

**Example**

100 CLS 110 PRINT PEEK$(0,1000) 120 adr1 = S\_SAVE(#1) 130 CLS 140 PRINT
PEEK$(100,1000) 150 adr2 = S\_SAVE(#1) 160 FOR n=1 TO 20: S\_SHOW adr1:
S\_SHOW adr2 170 S\_LOAD adr1: S\_LOAD adr2

**NOTE**

Although S\_SAVE will save a window stored on the second screen provided
by Minerva and Amiga QDOS, it assumes the screen resolution is 512x256
pixels and cannot work with higher resolutions.

**CROSS-REFERENCE**

`S\_LOAD <KeywordsS.clean.html#s-load>`__ and
`S\_SHOW <KeywordsS.clean.html#s-show>`__ view the saved screen part. Memory
taken by `S\_SAVE <KeywordsS.clean.html#s-save>`__ cannot be freed with
`RECHP <KeywordsR.clean.html#rechp>`__ or `CLCHP <KeywordsC.clean.html#clchp>`__,
only with `S\_LOAD <KeywordsS.clean.html#s-load>`__. See also
`SCR\_STORE <KeywordsS.clean.html#scr-store>`__ and
`SAVEPIC <KeywordsS.clean.html#savepic>`__ for alternatives.

--------------

S\_SHOW
=======

+----------+-------------------------------------------------------------------+
| Syntax   |  S\_SHOW adr                                                      |
+----------+-------------------------------------------------------------------+
| Location |  TinyToolkit                                                      |
+----------+-------------------------------------------------------------------+

 adr must be a value returned by S\_SAVE: the command S\_SHOW
 displays the screen information stored by S\_SAVE. The screen is
however retained in memory for future access.

**NOTE**

This command suffers with the same problems as S\_LOAD.

**WARNING**

A wrong address leads to serious crashes.

**CROSS-REFERENCE**

`S\_SAVE <KeywordsS.clean.html#s-save>`__


