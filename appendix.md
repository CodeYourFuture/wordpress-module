# WordPress - Appendix

**Further Reading**
- [What do WordPress developers do?](#what-do-wordpress-developers-do)
- [What is Open Source? GPL and MIT Licenses](#what-is-open-source-gpl-and-mit-licenses)
---

## What do WordPress developers do?

As an IT professional, there's several different ways of working with WordPress:

*   You can build and maintain websites for clients using, and adapting, existing WordPress **Themes** ( = collection of templates for the frontend ) and **Plugins** ( = extensions to the default WordPress functionality ).
*   You can create WordPress Themes for clients or to sell them on platforms such as the [Theme Directory](https://en-gb.wordpress.org/themes/) or the [ThemeForest](https://themeforest.net).
*   You can create WordPress Plugins for clients or to sell on the [Plugin Directory](https://en-gb.wordpress.org/plugins/).

Of course, you can also earn a living as a content editor, a blogger or a business owner with a WordPress website. But that topic is outside the scope of this course ;-) .

## What is Open Source? GPL and MIT Licenses

In 1984, Richard Stallman launched the **GNU Project** and created the **General Public License** (GPL) as a response to his increasing unhappiness with proprietary software, vendor lock-in practices and the resulting loss of personal freedom, as he saw it.

> "When users don't control the program, we call it 'nonfree' or 'proprietary' software. The nonfree program controls the users, and the developer controls the program; this makes the program an instrument of unjust power."
> - Richard Stallman, [The Free Software Definition](https://www.gnu.org/philosophy/free-sw.html)

This marked the birth of **Free Software**, by which software is considered free if it respects the 4 fundamental freedoms:

1. Anyone has the freedom to run the software as they wish, for any purpose
2. Anyone has the freedom to study how the program works, and change it as they wish
3. Anyone has the freedom to redistribute the software
4. Anyone has the freedom to distribute copies of their own modified version of the Software

As a consequence, access to the code must be open and all 3rd party software needed to run it must also comply with the 4 fundamental freedoms.

A few years later, in 1997, Eric Raymond wrote an essay called **"The Cathedral and the Bazaar"**, in which he described how the Linux operating system and the Free Software philosophy had created a surprisingly effective and collaborative way of writing software.

This set the stage for the appearance, one year later, of the term **Open Source** software. Open Source software is a close relative of Free Software but with a stronger focus on the methodology rather than the philosophy.

The movement has continued growing since then and nowadays there are many examples of popular Open Source software such as, for example, WordPress, Firefox, React, Python, Node, the Apache and NGINX web servers, just to mention a few.

For example, Node Package Manager is a system for distributing open source code. When someone writes `npm install XXX` they are taking advantage of a vast ecosystem of open source code.

### Copyleft, GPL and MIT

**Copyleft** is a method for making a program compliant with the 4 freedoms of Free Software, and requiring that all modified and extended versions of the program also be compliant.

According to the GNU Project:

> Certain kinds of rules about the manner of distributing free software are acceptable, when they don't conflict with the central freedoms. For example, copyleft (very simply stated) is the rule that when redistributing the program, you cannot add restrictions to deny other people the central freedoms.
>
> Copyleft also provides an incentive for other programmers to add to free software [...] and helps programmers who want to contribute improvements to Free Software get permission to do so.

This Copyleft rule translates into the **General Public License (GPL) Licence** for distribution with the Open Source software in question.

The **MIT License** is another popular Open Source software license that was originally developed at the Massachusetts Institute of Technology. Unlike the GPL, the only requirement an MIT license places on its recipients is that they keep the original copyright notice intact when they repurpose, redistribute, or otherwise reuse the code.

> "Copyright <YEAR> <COPYRIGHT HOLDER>
>
> Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE."
>
> The MIT License, from [The Open Source Initiative website](https://opensource.org/licenses/MIT)

In practical terms, the main difference is that GPL says that if you use my GPL code in your released code, you must also release your code under the GPL or something similar. MIT is very similar to GPL except that if you use my GPL code in your released code, you're allowed to license your part of the code in other non-Open Source ways.

So GPL "coerces" Open Source on anything that uses it whereas MIT is more flexible. There are good reasons for using both and many amongst the WordPress core developers are very committed to the coercive nature of GPL. But many big companies are suspicious of it.

If you wish to find out more about Free Software, Open Source and licensing, please watch the excellent documentary ["Revolution OS"](https://www.youtube.com/watch?v=4vW62KqKJ5A) on YouTube.

These sections have been sourced from:
* [GNU - Free Software Definition](https://www.gnu.org/philosophy/free-sw.html)
* [GNU - What is Copyleft?](https://www.gnu.org/copyleft/copyleft.html)
* [Make WordPress Training - What is Open Source](https://make.wordpress.org/training/handbook/user-lessons/what-is-open-source/)
* [Opensource.com - What's the difference between open source software and free software?](https://opensource.com/article/17/11/open-source-or-free-software)
