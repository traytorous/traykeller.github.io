---
title: Archive ~ Old post 2 ~ Binary expolitation Day 2
published: true
---
<h1>Plans</h1>

<h3>This post is from a blog series that I did 3 years ago. I am storing it here because it was part of my my cybersecurity journey and it is still dear to me. Please enjoy.<h3/>

<h3><span style="text-decoration:underline;">PLAN</span></h3>
<p>It&#8217;s day two of my break. After reading a ton of books yesterday I decided to test my knowledge by going through ctfs that mainly focused on binary exploitation. I found that my skills are still insufficient enough to solve most binary exploitation challenges because of the fact that most require dynamic reverse engineering. I can read the source code just fine of most programming languages, but I am at a disadvantage when it comes to reading assembly and the concepts of low-level systems excluding kernel and virtual memory subjects. Tomorrow I need to focus on learning x86  assembly because my main targets will be desktop and servers in the future and because x86_64 is backward compatible, so what I learn in x86 can be used in x64. I also need to learn how to use radare2 and gdb to a degree in which I can beat easier challenges. I found that microcorruption is too hard for me as well because of the faults that I just stated. Another fact that I realized is how much my skills in python have increased since I&#8217;ve taken that programming class. I can now think more outside the box and come up with solutions to problems faster in any programming language that I feel confortable with.</p>
<h3><span style="text-decoration:underline;">Notes</span></h3>
<p>Day 2<br />
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;<br />
CTFS I FOUND AND THERE REVIEWS<br />
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-<br />
<a href="https://ringzer0ctf.com/challenges" rel="nofollow">https://ringzer0ctf.com/challenges</a> # Good<br />
<a href="https://io.netgarage.org/##" rel="nofollow">https://io.netgarage.org/##</a> Overthewire but for actually writing exploits<br />
<a href="https://w3challs.com/" rel="nofollow">https://w3challs.com/</a> # Had probles logging into this one -&gt; will try later<br />
<a href="http://hax.tor.hu/welcome/##very" rel="nofollow">http://hax.tor.hu/welcome/##very</a> old site&#8230;maybe wonkey would like this one<br />
<a href="https://pwnable.tw/" rel="nofollow">https://pwnable.tw/</a> ## It seems these are just binary exploitation challenges<br />
<a href="https://ctflearn.com/problems" rel="nofollow">https://ctflearn.com/problems</a> # This ones a good one for security in general</p>
<hr />
<p><strong>General Purpose Registers (GPR)</strong><br />
In the x86 family, the registers have roughly stayed the same, although some registers have been added later on. The 16-bit Intel 8086 used 8 General Purpose Registers:</p>
<p><em>The Accumulator Register</em><em> (AX)</em>: used in arithmetic and is often used to store the return value (if the value does not exceed the register size)<br />
<em>The Base Register (BX)</em>: contains a pointer to data (the <em>DS</em> register is used when in segmented mode)<br />
<em>The Counter Register (CX)</em>: used during loops (to keep track of the loop count) and shifts/rotations of data<br />
<em>The Data Register (DX)</em>: used for I/O and arithmetic<br />
<em>The Stack Pointer Register (SP)</em>: points to the top of the stack<br />
<em>The Stack Base Pointer Register (BP)</em>: used to point to the base of the stack<br />
<em>The Source Index Register (SI)</em>: used during stream operations and points to the source location<br />
<em>The Destination Index Register (DI)</em>: used during stream operations and points to the destination location<br />
<em>The Instruction Pointer Register (IP)</em>: used to point to the next instruction, also known as the <em>program counter</em> (<em>PC</em>)</p>
<p>The <em>Accumulator Register (AX)</em>, <em>Base Register (BX)</em>, <em>Counter Register (CX)</em> and <em>Data Register (DX)</em> are divided in two 8-bit registers. The lower half is accessible by replacing the <em>X</em> with the <em>L</em> (for <em>Lower</em>) and the higher half is accessible by replacing the <em>X</em> with an <em>H</em> (for <em>Higher</em>). This results in:</p>
<pre><em>AX = AH and AL
BX = BH and BL
CX = CH and CL
DX = DH and DL
</em></pre>
<p>The 32-bit architecture uses the same registers as the 16-bit variant, but each register has twice the size. The naming scheme is therefore different: each register has the prefix <em>E</em>, which stands for <em>Extended</em>:</p>
<pre>EAX, EBX, ECX, EDX, ESP, EBP, ESI, EDI and EIP</pre>
<p>The 64-bit architecture uses the same registers as the 32-bit variant and has registers twice the size of the 32-bit architecture. The 64-bit registers have the prefix <em>R</em> (which stands for <em>Register</em>), resulting in a different naming scheme:</p>
<pre>RAX, RBX, RCX, RDX, RSP, RBP, RSI, RDI and RIP</pre>
<hr />
<p>&nbsp;</p>
<h3><span style="text-decoration:underline;">Articles I found Useful</span></h3>
<ul>
<li><a href="https://maxkersten.nl/binary-analysis-course/introduction/basic-cpu-architecture/" rel="nofollow">https://maxkersten.nl/binary-analysis-course/introduction/basic-cpu-architecture/</a> (The Register notes from above are from here. Great source !)</li>
</ul>
<p>&nbsp;</p>
<p>Gr3yC1oud ~ Another night of no sleep</p>
<p>Comment below if you want to discuss anything 🙂</p>
