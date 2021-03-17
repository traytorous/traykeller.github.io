---
title: Archive ~ Old post 4 ~ Binary expolitation Day 4
published: true
---

<h1>Plans</h1>

<h3>This post is from a blog series that I did 3 years ago. I am storing it here because it was part of my my cybersecurity journey and it is still dear to me. Please enjoy.</h3>

<p>Very tired right now and Assembly is such a hard language to learn. Through learning it I&#8217;m learning so much background information about memory and how the CPU works, but I realize how much background information you have to have just to make something useful in it. I&#8217;m used to creating small programs to solidify my knowledge in a programming language, but it&#8217;s so tedious. I made a small program in assembly using the NASM assembler. I also just found out that I have to learn more about syscalls than I already know because there are some registers in the x86 architecture that uses them to interrupt a program. Tomorrow keeps reading more on assembly and learns about stack frames.</p>
<p>Also cool site I just found. Might be useful later on 🙂</p>
<p><a href="http://howto.hackallthethings.com/2016/08/" rel="nofollow">http://howto.hackallthethings.com/2016/08/</a></p>
<hr />
<p>First program in assembly</p>
<p>global _start<br />
section .data<br />
msg db &#8220;hello world!&#8221; , 0x0a<br />
len equ $ &#8211; msg<br />
section .text<br />
_start:<br />
mov eax,4<br />
mov ebx, 1<br />
mov ecx, msg<br />
mov edx, len<br />
int 0x08 // system call I was talking about<br />
mov eax, 1<br />
mov ebx, 0<br />
int 0x80</p>
<hr />
<p>Videos I used today</p>
<div class="jetpack-video-wrapper"><span class="embed-youtube" style="text-align:center; display: block;"><iframe class='youtube-player' width='775' height='436' src='https://www.youtube.com/embed/75gBFiFtAb8?version=3&#038;rel=1&#038;showsearch=0&#038;showinfo=1&#038;iv_load_policy=1&#038;fs=1&#038;hl=en&#038;autohide=2&#038;wmode=transparent' allowfullscreen='true' style='border:0;' sandbox='allow-scripts allow-same-origin allow-popups allow-presentation'></iframe></span></div>
<div class="jetpack-video-wrapper"><span class="embed-youtube" style="text-align:center; display: block;"><iframe class='youtube-player' width='775' height='436' src='https://www.youtube.com/embed/wLXIWKUWpSs?version=3&#038;rel=1&#038;showsearch=0&#038;showinfo=1&#038;iv_load_policy=1&#038;fs=1&#038;hl=en&#038;autohide=2&#038;wmode=transparent' allowfullscreen='true' style='border:0;' sandbox='allow-scripts allow-same-origin allow-popups allow-presentation'></iframe></span></div>
<div class="jetpack-video-wrapper"><span class="embed-youtube" style="text-align:center; display: block;"><iframe class='youtube-player' width='775' height='436' src='https://www.youtube.com/embed/H4Z0S9ZbC0g?version=3&#038;rel=1&#038;showsearch=0&#038;showinfo=1&#038;iv_load_policy=1&#038;fs=1&#038;hl=en&#038;autohide=2&#038;wmode=transparent&#038;listType=playlist&#038;list=PL038BE01D3BAEFDB0' allowfullscreen='true' style='border:0;' sandbox='allow-scripts allow-same-origin allow-popups allow-presentation'></iframe></span></div>
<p>&nbsp;</p>
