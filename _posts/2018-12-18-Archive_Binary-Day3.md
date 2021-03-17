---
title: Archive ~ Old post 3 ~ Binary expolitation Day 3
published: true
---

<h3>Plan</h3>
<p>It&#8217;s 3:51 am and learning about the CPU and memory is a challenging task. I feel that a lot of gaps in my knowledge are starting to be filled. I read about 70 pages of this book, <a href="https://www.amazon.com/Assembly-language-x86-processors-IRVINE-ebook/dp/B079DYP4LM/ref=sr_1_5?s=books&amp;ie=UTF8&amp;qid=1545123219&amp;sr=1-5&amp;keywords=x86">Assembly Language x86.</a> It was pretty good. Most of my notes that I&#8217;m gonna put up are from the book. Learned more about registers and how the CPU takes data from peripheral devices and ram. The other book I had that in my notes I did not read because it focused on a higher level version of the assembly which to me would not be useful in my situation. My prime focus is learning x86 assembly because it can be used on both x86 and x64 CPUs. Tomorrow I shall be reading more on assembly and Reverse Engineering.</p>
<h3>Notes</h3>
<p>Day 3<br />
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;<br />
Book: Assembly Language for x86 processors<br />
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;</p>
<p>CPU PARTS<br />
*The central processor unit (CPU), where calculations and logic operations take place, contains<br />
*a limited number of storage locations named registers, a high-frequency clock, a control unit, and an arithmetic<br />
logic unit.<br />
*The clock synchronizes the internal operations of the CPU with other system components.<br />
* The control unit (CU) coordinates the sequencing of steps involved in executing machine<br />
instructions.<br />
* The arithmetic logic unit (ALU) performs arithmetic operations such as addition and subtract-<br />
tion and logical operations such as AND, OR, and NOT.<br />
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;<br />
*Unsigned means that it&#8217;s a positive number only<br />
*signed means that it can be both negative or positive<br />
*The pins of a CPU are connected to the data, control, and address buss<br />
*A bus is a group of parallel wires that transfer data from one part of the computer to another.<br />
*The 4 buses are: Data, I/O, control, address<br />
*IO &#8211; gets input from peripheral, data &#8211; transfers data from the CPU and memory (the rest you don&#8217;t need to know for now it seems)<br />
*LOOK UP DESCRIPTOR TABLES(MEMORY)<br />
*When a program starts running it becomes a process which then is given a process (ID) that is used for the os to keep track of it<br />
*When the program ends it is removed from memory<br />
*A thread shares it memory area with other threads<br />
*the different areas of memory are called segments for each program<br />
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-<br />
Registers<br />
*Are high-speed storage locations directly inside the CPU, designed to be accessed at a much higher speed than conventional memory<br />
*General purpose registers(just doing operations on them)<br />
EAX is automatically used by multiplication and division instructions. It is often called the<br />
extended accumulator register.<br />
• The CPU automatically uses ECX as a loop counter.<br />
• ESP addresses data on the stack (a system memory structure). It is rarely used for ordinary<br />
arithmetic or data transfer. It is often called the extended stack pointer register.<br />
• ESI and EDI are used by high-speed memory transfer instructions. They are sometimes called<br />
the extended source index and extended destination index register.<br />
• EBP is used by high-level languages to reference function parameters and local variables on<br />
the stack. It should not be used for ordinary arithmetic or data transfer except</p>

<p>Gr3yC1oud ~ Time for another night of no sleep 🙂</p>
