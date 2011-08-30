#Slide 1(00:00-00:02)
NULL

没内容
#Slide 2(00:02-00:06)
NULL

没内容

#Slide 3(00:06-01:24)
Throughout 1960's and 1970's, most human interaction with computers was done
through what are called terminals. A terminal device is a piece of hardware
that combines the keyboard with some kind of character display, which in early
days in the 1960's was some kind of printer that print out characters line by
line. Or later in 1970's, it was usually a video console, but video console
was not capable of displaying arbitrary graphics, it can only display text
characters, and these text characters could only be displayed in a fixed grid.
Say, it wouldn't have arbitrarily positioned characters anywhere on the screen,
and also these devices only have one display font and one display color. 

在上个世纪六七十年代的时候，人机交互的主要手段是通过一种叫做“终端”的东西。终端是硬件，一般指的是一个键盘加上某种字符显示设备，最早在六十年代的时候都是打印机，一行一行的把字符打印出来。后来到了七十年代，演进成了“视频工作台“。但那时的”视频工作台”只能显示字符，不能像现在这样显示任意的图形。这些字符显示在固定的格子里，所以大小也是固定的，不像今天这样可以显示在任意的位置。那个时候一般就是：一种字体，一个颜色。

So the idea of terminal is that when they are hooked up to computer, the
computer then can send text characters and sequences to the terminal which get
displayed character by character on the screen and when the user sitting at
the keyboard types anything, a character sent from the terminal to the
computer, so does not need symmetry there. A strict sequence of characters
flows from computer to the terminal and vice versa. As you can probably guess,
the text going in both directions was almost always ASCII text.

所以终端总体上就是这么个东西，你把它连到计算机上，计算机就可以把文本（就是一个一个的字符）和序列（例如转意序列）送到终端，然后一个字符一个字符的显示出来；同样，当用户敲字的时候，这些字就从终端传给了计算机。这里也不需要对称同步，就是一串字符从计算机传到终端，或者反过来从终端传到计算机。可能大家能猜到，这些传来传去的数据基本都是ASCII字符。

#SLIDE 4(01:24-04:21)
In Unix systems, a process may communicate with a terminal through a file
representing that terminal, a terminal character device file. When a process
writes to a terminal character device file, that is putting in data in the
output buffer of the device file which then going to to get sent out by the
operating system to the terminal device associated with that character device
file. Conversely, when the user at the keyboard types something, that data
get sent from the terminal to the computer and the operating system will take
that data and put it in the input buffer of the associated character device
file and then the process may read form the character device file to get that
data. So again, be clear the terminal is a totally dumb device. When you see
text displayed on the terminal that is something that coming from processes
running on the attached computer. 

在Unix系统下，一个进程可以通过一个代表特定终端的文件来和该终端通信，我们把这个文件叫做”终端字符设备文件“。当一个进程向一个终端字符设备文件写数据的时候，这些数据就被放到了设备文件的输出缓冲区里，操作系统继而会把这些数据送给相应的终端。反之，当用户用键盘输入数据时，操作系统会把数据放到相应设备文件的输入缓冲区内，这时相关的进程就可以从设备文件里读到这些数据了。注意，终端是没有什么智能的设备，当你看到终端上显示很多文本时，其实数据是来自与终端连接的那台计算机，数据是计算机上运行着的进程发过来的，终端只是起显示作用而已。

The only exception to this is that with the terminal character device file we
can turn on a mode called echo. When the terminal character device operates
in the echo mode, then any input received from the terminal was immediately
echo back out to the terminal so that is can be displayed on the screen. In
practice what this means when echo is on and the user types on the
keyboard, then whatever key they type, they will immediately see it appear on
their screen. Just be clear that the terminal doesn't have echo mode, it is
the terminal character device file has echo mode, so the data actually has
been sent from the terminal and immediately back to the terminal.

不过这里有个例外：我们可以把设备文件调成echo模式，这样每当终端读到输入数据时，会马上把这些数据发送回终端显示（这就好像“回音”），也就是说，当启用这个模式之后，用户在自己键盘上敲什么，那她就会马上在自己的屏幕上看到什么。注意，是设备文件有echo模式，而不是终端本身有。所以应该说数据已经从终端发出去了（发到了设备文件），只是马上又“弹“回了终端。 

As the years went on, some terminals begin to add more features, like for
example, some terminals feature the ability to change text color, the way this
work is that you would set terminal's mode like, say, what color is printing,
by sending an escape sequence(that is, a sequence of characters beginning with
the ASCII escape character, which is ASCII code 27). By sending escape
sequences to the terminal, we can set its modes, and thereby change its
behaviors, like, say, what color text may be displayed, say, how many lines of
text get displayed on the screen, things like that.

后来，终端逐渐开始增加新功能。比如说显示带颜色的文本。工作原理是这样，我们发一个转意序列（以ASCII转意字符27开头的一串字符）给终端以改变它的工作模式，从而改变字符打印的颜色。当然，也可以改变显示的行数等等。

Now the trouble with this arrangement is that early on escape sequences were
not really standardized. Many manufactures did the wrong thing. So what you
need to do to control one terminal differs from what you do to control
another. In time though, eventually standard did more or less emerge.
Unfortunately, the end result of this process ended up quite messy, so if you
look at the details of terminals and want to know what exactly you can do with
the escape codes, it is all surprisingly complicated. So that's a whole area
we're going to laid over. We will just think of terminals as simply displaying
a sequence of text, and sending back to the computer whatever gets typed at
the keyboard and end of story.

相应的问题是，早期各个厂商对转意序列没有一个统一的标准。所一在一种终端上使用转意序列的方法和另一终端上往往不同。虽然最终大家终于弄出一套标准，但这个标准其实也是乱七八糟。你可以自己学一下转意码，繁琐的很。所以在这里我们干脆就把转意抛开不管。我们就认为终端就是用来显示文本和发送文本到计算机的，这就足够了。

However I do mention these capabilities, because you will likely interact with
some programs that when they do use the terminal, they seem to do things that
are otherwise impossible, like say, changing the color of the text.

当然，我觉的提一提这些功能还是很有必要的，以后你很可能会遇到一些程序，它们会试图改变终端的文本颜色。

#SLIDE 5(04:21-05:18) 
In Unix, we have this convention whereby processes when they are
started expect to inherit from their parent to open file descriptors, 0 and 1.
File descriptor 0, we call it standard in, abbreviated as stdin, and file
descriptor 1, we call it standard out, abbreviated as stdout. 

Unix系统下有这样一个传统，当一个进程开始时，它会从他的父进程继承文件描述符0和1。
我们把文件描述符0称为标准输入，简称stdin;把文件描述符1称为标准输出，简称stdout。

In the usual case, processes expect standard in to be a file descriptor open
for reading a terminal character device file and standard out is expected to
be open for writing that same terminal device file, 

通常，进程会从标准输入（stdin）来读取终端设备文件中的数据，而当进程想要向终端设备文件写数据时就会用到标准输出（stdout）。

In practice, what this means is that when a program wishes to read input from
the terminal, it reads from standard in, its file descriptor 0, and when a
program wish to display text on that same terminal it writes data to its
standard out.

在实际使用中这意味着，当进程想要从终端中读输入时，会读标准输入（文件描述符为0）；
而当进程要在同一个终端上显示文本时，它就会把数据写到标准输出上。

#SLIDE 6(05:18-06:20)
Now be clear, this is what processes expect to inherit from their
parent. We call that when a process forks in Unix, the file descriptors from
the parent will be copied to the child, so has all the same open file
descriptors. So the convention in Unix is that when program wish to interact
with terminal, they usually don't locate a appropriate terminal themselves,
they just expect to inherit these file descriptors already open to a
appropriate terminal. 

注意，如图所示的就是进程要向它的父进程继承什么。一般我们把这个继承过程叫做一个fork.
那么fork进程就意味着父进程的文件描述符会被直接拷贝到子进程，那自然的，子进程就拥有了和父进程相同的那些文件描述符。当程序想要和终端交互时，一般不用自行定位一个终端，因为它们会从父进程继承到文件描述符（其中当然也包括0和1），这些描述符本身就已经指向了特定终端。

Now you maybe wondering why do we have two separate file descriptors, one for
reading, one for writing.  First off something I did not explicitly mention in
the coverage of Unix System calls is that when you open a file you can open in
a mode such that only reading is allowed, or only writing is allowed, that is
possible. Still that doesn't explain why we have two separate file
descriptors, when we could just get away with one for both reading and
writing. This is something we will be explaining a bit later when we talk
about what's called redirection.

你现在可能感觉很奇怪，为什么我们会有两个文件描述符，一个用来读，一个用于写。当初我在讲Unix系统调用的时候没有提到的一点是，文件打开是可以设置模式为只读，或是只写。当然，这样也不足以说明明明我们可以用一个描述符，既读又写，为什么偏偏却非要有两个呢。后续，我们在降到重定向（redirection)的时候，会对此做进一步的说明。

#SLIDE 7(06:20-06:50) 
Something else you maybe wondering at this point is that, hey, my
computer doesn't have a terminal. I have a proper monitor that has full
graphical display, and on that display, I have a graphical user interface
which interact with mouse and keyboard. But these are totally separate
devices, I do not have a keyboard bundled together with a monitor as a single
unit called terminal. So what's the hell is going on here, we do not seem to
have any terminal in modern system. The answer is that well, hardware
terminals are thing of the past. What we do today is that we imitate them. We
emulate them in software. What we have are called terminal emulators.

#SLIDE 8(06:50-07:24)
This window here, for example, is a terminal emulator program. To explain what
is going on here, we actually first have to talk about the graphical user interface in Linux in
general. 

In Microsoft Windows, the graphical user interface is a part of the operating
system itself. It is tangled up with all the other operating system code. In
Unix systems in contrast, including today's Linux, the graphical user
interface runs basically as an ordinary  program, not a component of Linux kernel
at all in fact.

#SLIDE 9(07:24-07:42)
When running a graphical environment in Linux, the program which
controls your screen and which gets the input directly from the mouse and
keyboard is called a X Window System Server. 
#SLIDE 10(07:42-08:21)
When you then run a program which
has graphical interface, like, say, the Firefox web browser or the Gimp image
editing program, these programs send the content of their windows to the
X Window Server and then the X Window Server is responsible for actually
displaying those windows on the screen. 

When the user then, say, click on one of these windows, that mouse data is read by the X
Window Server, which then sends on to the appropriate program. 

Usually in the setup we have a program running responsible for, say, drawing
all the interface elements on the desktop, like,say the desktop wallpaper or
the icons on the desktop, and also whatever interface element you have for
task switching and studying the programs. 
#SLIDE 11(08:21-10:46)
One program commonly for that purpose is the program called Gnome Panel, which is
part of Gnome Desktop, which is whole collection of programs and libraries for
creating a graphical user environment on Linux. 

And then additionally within a Linux window
server, you need what is called a window manager, which is the program which
is
responsible for drawing the borders around windows,and also keeping track of
the positions of the windows on screen and moving them around and resizing them
and such.

The Window Manager included with the Gnome desktop is called Metacity. So notice that Gnome
Panel and the Metacity Window Manager  are both otherwise ordinary processes
that talk to the X Window Server, so they actually talk to the X Window Server
using the same X protocol that all other programs, like Firefox and Gimp use. 

Be clear that the X Window System is defined really by a protocol, the X
protocol. And there are a few different X Window Servers available, the most
widely used one  is called XORG. If you have a Linux system today, most likely
it is using XORG. Also be clear that, although we call it a server, the X Window Server is
usually talking to programs running on the very same machine. So when I run Firefox on the system, and I see it displayed on my screen, that it is 
connecting to the X Window Server running on my same system.

Part of the reason though, for this client-server architecture, is that it is
possible to run a program like Firefox and have it talk to a X Window
server running on a different system. So if we run, say, Firefox on your
system, but have it connected to the X Window Server running on my system,
then I will be seeing that Firefox window displayed on my screen, and I can
interact with it, just like it were a program running locally on my system,
but in fact it's actually running on your system.

This is a example of a feature called Network Transparency. And the idea
going back 30 years ago, when the system was first devised is that  we will have a batch of what are called Thin
Clients, computers which do not have to be very powerful, yet simply just
display programs that are actually been run on other systems. It is the
arrangement that very much like the idea of having a batch of terminals all connecting to one system, when all the
code is really running on a computer system, terminals themselves can be very
thin client, say, they do not have that much smarts in them. 

#SLIDE 12(10:46-11:15)
So now getting back to terminals. A terminal emulator is a program which
sends window content to a X Window Server to display on screen as graphical
window, and it also receives textual input from the keyboard and also perhaps
mouse clicks from the X Window Server.

The question now is how do we get other programs to read and write from the
terminal emulator as if it just like a regular terminal, and actual terminal
character device file. 

#SLIDE 13(11:15-12:25)
The way this is achieved is with another mechanism introduced in Unix systems
called pseduo-terminal device files. These pseduo-terminal files actually
called in pairs, one the slave, one the master. And the program which is
imitating the terminal, it reads and writes from the master, and the program
that actually wishes to use the fake terminal, reads and writes from the
slave.

So for example, I open up my terminal emulator in X windows, and then I click
the window, and, say, start to type something. That text data I type is sent
from the X window server to the terminal emulator which then writes it to the
master pseduo-terminal character device file. The operating system then copies
that data over to the associated slave to be read by a process. 

So be clear that pseduo-terminals are in a sense of fiction, they represents
terminal devices which don't actually exist. And in fact, it is the
responsible of the terminal emulator, when it start, to ask the operating system to
allocate a new pseduo-terminal just for its purposes. You generally want
each terminal to have its own unique pseduo˜-terminal master-slave pair.

#SLIDE 14(12:25-14:15)
In the context of Linux, you will hear talk about a feature called Virtual
Consoles. On a Linux system, if you hold down Ctrl and Alt and hit F1 or
F2..F3 up to F8, it will switch you to another virtual console. 

So the X window system by default actually runs as usually the 6th, 7th or 8th
virtual console. So you switch your X window server by holding down Ctrl-Alt
and hitting F7, or sometimes F8. If you hold down Ctrl-Alt and hit F1, that
switches you to a different virtual console, one without an X window server
but rather just a terminal. 

So a virtual console sort of acts like a terminal
emulator. It is just embedded inside the Linux kernel itself. And though these virtual consoles by
default simply run with terminal command line, you can in a virtual console launch
a X window server, and thereby turning that virtual console into a proper GUI desktop. So
what typically happens in most Linux system upon boot up, it launch an X window server
in one of the virtual consoles and switches to that virtual console.

So the purpose of the system is that the way Linux gives us a terminal even if we
don't have a X window server and also it allows us to in case something goes
wrong with the X window server, we can just switch over to another virtual
console, and use the command line there.

Assuming you have a X window server in which it never goes wrong, you probably
don't ever need virtual consoles, but it's there as a nice fall back feature
basically. 

Just remember though, if you accidently, for whatever reason, switch
away from your X window server, because you hit Ctrl-ALt and say, F3. Just
remember you can get back by hitting Ctrl-Alt-F7, or sometimes F6 or F8,
it depends on your Linux distribution.

#SLIDE 15(14:15-
The Last thing to say about terminal here is where you will find the character
device files. This is something may vary depended upon which Unix you are using
and if you are using Linux, which distribution. But on my Ubuntu system for
example, if I open /dev, I will see a directory called pts, which stands for
"pseduo-terminal slaves", and in this directory, I find all of these
pseduo-terminal slaves that are currently being used. 

And then in the /dev/ directory itself you will find a file called tty, this
is a special kind of special file. It does not represent a character device,
when a program opens the /dev/tty file, what you get back is a file descriptor for the so called
controlling terminal. That is terminal that is associated with their process,
which is a concept we will talk about later on, but the point here is that
when you open this file, there is some special magic going on, where what you get form
file descriptors depends upon which process is opening he file.

And finally also in /dev/ you will see a number of files starting with tty and
then a number. These are character device files representing the virtual
consoles. And again remember virtual consoles are Linux specific feature. But
in any case if say, you open and write to /dev/tty1, what you are doing is you
are writing to the terminal of the first virtual console. 

I believe actually these virtual console are numbered starting from 1 rather than
zero. If you wonder what tty stand for, Let's see historical mechanism, back
in the 
50-60 and 70s, we have this device called teltype machines. That is over a
communication line, you have 2 devices, on either end. You type on one end and the
characters printed out on the other end. So there are actually predecessors to
hardware terminals. 

And for whatever reason that is the name of the creators
of Linux went with, even though it didn't really make sense at that time, it certainly
doesn't make sense as a given name 40 years later, but that's what we are stock
with, when people talk about ttys, they are talking about terminals.