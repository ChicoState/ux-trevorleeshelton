# Stopping a Process with Htop

### Introduction

On my Linux OS, I've had numerous times where I've needed to stop a process that was no longer desirable and/or easily closed. For many of these, I've used the program Htop, and for some, I found myself *needing* to use it. To walk through a re-enactment of one such time, but from the perspective of a lesser informed user, let's pretend that the arbitrary command below, which does nothing for an extremely long time, was started elsewhere, without my direct input but as my user, and ends up being something I'd want to stop. How would one use Htop to stop it? (Note that I *do* know the name of the application that I want to stop in this instance, by the way.)

![1](/../assets/ux1/1.png)

### Process

First off, knowing that Htop is mainly a terminal-based program, and already knowing at least the basics of how to use a command shell, I'd enter what I remember the program was called into the command line.

![2](/../assets/ux1/2.png)

I'd then press enter to run that program. From there, the following image is what I'm met with.

![3](/../assets/ux1/3.png)

The top fourth has various stats regarding this host's compute, and while this could perhaps have some better labels or may be considered slight clutter in some cases, it is irrelevant for what we currently seek to do. A large list, meanwhile, spans most of the lower 3/4's of the screen. Going into this, I would still know from the outset that Htop is intended to be an application in the vein of Windows Task Manager. That, as well as the visible **information hierarchy**, where similar items are grouped under a greater entity in a space, for each column's part of each entry under their labels, allows me to be fully sure that what is listed here is processes that are currently running.

Looking into the list, it is not *too* difficult to see that one of the processes is highlighted. With the highlight initially being so close to the column labels, that could perhaps be a bit easier, but I'd at least consider the possibility that this is the case. At any rate, the highlight here could be considered to act as an **affordance**, or an aspect of something that suggests a possible usage, of this list as a way to find and select a process from those available in addition to simply seeing whatever is currently shown. To affirm that this is so, knowing that Htop is a terminal user interface program, I press the down key.

![4](/../assets/ux1/4.png)

I then press it some more, seeing that this list can very much scroll down.

![5](/../assets/ux1/5.png)

Perhaps I could find the process I'm seeking to stop by just scrolling or even paging around in this large collection. At the very bottom of the interface, though, a series of **mappings**, which are indicators that each communicate what an input does or what it affects, can be easily spotted by me at this point. In this case, function keys of the keyboard are indirectly being mapped to actions indicated by text labels. Honestly, it probably wouldn't hurt too much to have this bar be somewhat larger.

![6](/../assets/ux1/6.png)

Looking here, I see 10 mappings total. Most would make sense to the user I'm roleplaying as, but a couple, like the mappings for "Nice", probably wouldn't. The mappings of F3 and F4, however, suggest quicker methods of finding a process or processes of interest. Deciding that F3, "Search", would be the more appropriate of the two here, I press that key, and the lower bar changes to what is shown below.

![7](/../assets/ux1/7.png)

Three mappings are visible now. The first two are slightly confusing, as nothing is initially entered in, and I'm not 100% sure whether "S-F3" means Shift-F3 or not. The mapping for Esc to "Cancel" seems useful at first, but does prove either redundant or incomplete soon. What is to the right of these mappings is more important, though: the actual way to enter what you want to search for, afforded by the "Search:" label next to an initially empty field. I promptly begin entering the name of the application I want to stop.

![8](/../assets/ux1/8.png)

As text is entered, an orange bar travels around the list, landing or staying on something that matches what is entered at any point in time. As I type out the name of the process I want to stop, I find myself landing on it, and, satisfied, I press enter to confirm. Such is an example of a **natural mapping**, i.e. one that we, as people, are either primed or inclined to already know/expect without any explicit instruction from the interface. This pressing turns out to exit in the same way as the escape key, which is why I'm now dubious about the "Esc" to "Cancel" mapping that is *shown*. Regardless, I now have the process I want to stop selected. (I'm sure "Next" and "Prev" would come in handy if I was narrowing down amongst similarly named processes, but they were not used in this particular interaction.)

![9](/../assets/ux1/9.png)

Now that I'm back to the main menu of this bottom bar, I look to F9, "Kill", as what I'd assume is the way to stop the process. Pressing that key pops up a new side menu instead, though.

![10](/../assets/ux1/10.png)
![11](/../assets/ux1/11.png)

From the highlight affordance as well as the group label (more information hierarchy), it can be seen that choosing "Kill" doesn't merely stop a process, but rather enters a sub-interface with which to send a single selected "signal" out of many available to said process. This reflects the concept of "kill" in Linux being used to send signals for various things to a given process, with the signal names that can be seen in the above menu very much being what Linux calls them. Nevertheless, a layperson's **mental model**, or conception of how something functions, regarding "killing" a process would likely mismatch with this, at least until they realized what was actually going on after entering the menu. Calling the "Kill" mapping "Send Signal" instead while maybe also having a "Stop" option might help to bridge this gap. The Enter and Escape keys are at least both explicitly mapped here, though, and actually confirm/cancel respectively rather than just redunding off of each other. Unfortunately, though, for some reason, there *is* a redundant option to cancel in the form of a fake signal 0, which seems like it'd be quite unnecessary here unless your Esc key is broken.

The signal that we currently see highlighted is SIGTERM, which does seem like it'd stop the problem process. (This is good, since a lot of the signals' purposes aren't immediately clear from their names. For the developers of Linux, this probably isn't too big of a deal, but for user interfaces, clarifying labels or the partial hiding of less important signals could be helpful here.) If that doesn't work, I could always circle back and choose this more severe (both in look and actual function) signal below to send.

![12](/../assets/ux1/12.png)

With that in mind, I proceed with sending SIGTERM.

![13](/../assets/ux1/13.png)
![14](/../assets/ux1/14.png)
![15](/../assets/ux1/15.png)

The process disappears, and its name is nowhere to be found. I have now stopped the process I've wanted to stop. Now there is just one thing left to do.

![16](/../assets/ux1/16.png)

After that, I'm back at the command line.

![17](/../assets/ux1/17.png)

Looking back at what we *actually* stopped with Htop, which I had running in another terminal, I see this.

![18](/../assets/ux1/18.png)

Success.

### A Couple More Things

There are a couple of things about all of this that I do additionally need to mention. First off, there *is* actually mouse support for Htop (wherever there *is* a mouse present, of course, considering that Htop can be run in both graphical environments and text-only displays), which would have possibly been helpful for my task, but there are hardly any indications (including affordances) of this being a thing when using the interface. It would be good if the mouse being usable in the interface could unobtrusively be communicated from startup as long as a mouse is actually present. Secondly, my graphical terminal *has* been prone to interfering with the usage of the function keys in Htop, which has distorted my usage from the prototypical walk-through covered above whenever I need to work around that inside said graphical terminal (including through usage of the mouse, funnily enough). Whether this is the fault of Htop, me, or the graphical terminal is up to interpretation, though, I believe.

### Conclusion

I successfully managed to stop the undesired process with Htop here. There were a couple of issues, but nothing that I would consider rendered this particular interaction bad on the part of Htop, let alone uncompleteable.
