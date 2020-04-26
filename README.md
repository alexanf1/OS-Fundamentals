# OS-Fundamentals
A walk through on operating systems with code samples

## Introduction
So what happens when a program runs?
 * It does one very simple thing: it <b>executes instructions</b>
 * Miliions or even Billions per second, the processor <b>fetches</b> an instruction from memory. <b>decodes</b> it, and <b>executes</b> it (e.g. like adding numbers together, checking a condition, or jumping to a function).
 * Once one instruction is complete, the processor goes to the next one, and so forth <b>sequentially</b>.
 * Note: This is a simplified explanation as a processor can actually execute multiple instructions or even out of order!

But there are a lot of other things going on while a program is running with the goal of making the rest of the system easy to use. In fact, its the <b>Operating System (OS)</b> that makes it easy to run programs such as:
* allowing multiple programsn to run at a time
* allowing programs to share memory
* enabling programs to interact with devices, and more

The primary way an OS does the above items is through <b>virtualization</b>.
* Virtualization is the process of taking a <b>physical</b> resource (such as a CPU, Memory, or Disk) and turning it into a <b>virtual form</b>
* This new form is what allows many programs to run (share the CPU), many programs to concurrently access their own instructions and data (share memory), and many programs to access devices (sharing disks). 

In order to allow users to tell the OS what to do (such as running a program or accessing a file), the OS also provides <b>APIs</b> to call 
* There are usually a few hundred <b>system calls</b> available.

## Virtualization
One of the most fundamental abstractions that the OS provides to users is the <b>process</b>.
* The defintion of a process is quite simple: it is a <b>running program</b>.
* A program by itself isn't much, it sits on disk as a bunch of instructions.
* Its the OS that takes these bytes and gets them running.

A typical system may be running tens to hundreds of processes at the same time. It abstracts the concerns from dealing with only having a few physical CPUs. So how does the OS create this illusion of many CPUs to only a few physical? 

The OS creates this illusion by <b>virtualizing the cpu</b>

So how does an OS get a program up and running? How does the process creation actually work?
* Programs initially reside on <b>disk</b> in some <b>executable format</b>
* The OS must read those bytes from disk and load the programs code and any static data into memory, into the <b>address space</b> of a process.
* Note: Modern OSes perform this <b>lazily</b>, meaning loading only pieces of code that are necessary during program execution.
