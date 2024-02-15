---
title: Open project collaboration & management
teaching: 60
exercises: 30
---

::::::::::::::::::::::::::::::::::::: objectives

- Explain why adding licensing information to a repository is important.
- Understand that some licenses are intended for code and others for data. 
- Understand your rights and obligations under the GPL, MIT, BSD, Apache 2 and Creative Commons licenses.
- Recall that open source software can be sold and used in commercial products but that license declaration will need to be included and any other terms of the license adhered to.
- Apply an appropriate open source license to a code repository that is shared on Github.
- Understand how to write a citation file that can be included with code shared on Github.

::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::: questions 

-  What licensing information should I include with my code and data?
-  How do I share my code on Github?
-  How do I ensure my code is citable?

::::::::::::::::::::::::::::::::::::::::::::::::


## What is licensing and why is it important?

### Copyright Licenses

The authors of any creative work such as written text, photographs,
films, music and computer code are protected by Copyright law.  This
allows them to set the terms under which their work can be copied or
reproduced. This often takes the form of the creator of the work selling
copies of it and receiving a fee from each person who obtains a copy.
Those receiving the copies are typically forbidden from making additional
copies without the permission of the creator. For example if an author
writes a book they will receive some money for each copy of that book
that's sold and anybody who makes and sells a copy of that book would
need their permission to do so.

Copyright licenses don't necessarily require any money to be charged for
copies and the creator might choose to let anybody copy their work,
providing they don't change it and keep their name on it.

Copyright is automatically implied, any creative work which doesn't
specify a license should be assumed to be copyrighted. If it were ever to
come to a court case then the author might have a problem proving this
and enforcing their copyright. Technically the work is copyrighted the
moment it is created, even without any kind of copyright statement,
registration or license agreement.

### Copyright and Open Source

An Open Source license is a form of copyright license that gives anybody
who receives a copy of a work to make additional copies and distribute
them to anybody they like. It also allows anybody who receives a copy to
make changes to the original work and to redistribute those. When applied
to software this requires that the source code of the program is
distributed alongside the executable program. 

### Free Software

In the early history of computing there were often informal agreements
where programmers would share source code with each other, but this was
rarely backed up with any formal copyright license. As the field grew
this was first formalised in the 1980s by Richard Stallman who formed the
Free Software Foundation and defined "Free Software" as software which
stated the Free Software was defined by software which respected users
freedoms by giving users:

1. The freedom to run the program as you wish, for any purpose.
2. The freedom to study how the program works, and change it so it does your computing as you wish. Access to the source code is a precondition for this.
3. The freedom to redistribute copies so you can help your neighbor.
4. The freedom to distribute copies of your modified versions to others. By doing this you can give the whole community a chance to benefit from your changes. Access to the source code is a precondition for this.

The term "Free" in English often causes some confusion here as it can
mean both "free as in freedom" and "free as in beer" (no charge). The
term "Libre" software is sometimes used instead of "Free" to help clarify
this.

### Open Source Definition

In the 1990s the "Open Source" movement wanted to make a more business
friendly term and thought using the term "Free" might lead to confusion
when people wanted to charge for software. Despite "Free Software" often
being given away for no charge (or just a small charge/suggested donation
to cover media or distribution costs), nothing in the four freedoms and
the software licenses that were designed around it prohibits charging for
software. 

In 1998 the Open Source Defintion was created in 1998 and says that
software which is open source must be distributed under the a license
which allows the following:

1. Free Redistribution must be allowed
2. Source Code must be included
3. Derived Works must be allowed
4. Integrity of The Author’s Source Code - Restrict distribution of modifications if patches can be distributed instead. Must explicitly permit distribution of software built from modified source code. The license may require derived works to carry a different name or version number from the original software.
5. No Discrimination Against Persons or Groups
6. No Discrimination Against Fields of Endeavor
7. Distribution of License - License applies to anyone the software is distributed to
8. License Must Not Be Specific to a Product - the program can be extracted from other software it is distributed with
9. License Must Not Restrict Other Software, e.g. can't insist it is only distribted alongside other open source software.
10. License Must Be Technology-Neutral

### Free and Open Source Software

Because of these two terms many people use the term "Free and Open Source
Sofware" (FOSS), while other's simple say "Open Source Software" and some
will say "Free Software". In reality these all have very similar meanings
that will respect the four freedoms and the open source definition. For
the rest of this chapter we will refer to "Open Source", but could have
equally said "Free and Open Source Software" or "Free Software". 

## Types of licenses

A number licenses have been written that conform to the Four Freedoms
and/or the Open Source definition. Each of these set out the rights of
anybody receiving software that is distributed under that license. We
will look at a few of the most popular ones. 

### Public Domain  

Before we look at any licenses in detail, one other thing to consider is
Public Domain. This is a concept in some countries (but not all) where a
work is not protected by copyright. These works have no license from
their creators and typically anybody can do anything they like with them.
Copyrights are usually time limited to between 50 and 100 years and in
many jurisidictions when Copyrights expire the works enter the public
domain. It is for this reason that the works of Charles Dickens are no
longer subject to Copyright and anybody can make a copy of them. In some
jursidicitons works can be placed straight into the public domain simply
with a declaration within the work. In the USA works produced by the
federal government are automatically public domain. But in other
countries works need to be registered as public domain. For this reason
it isn't recommended to simply make work public domain if you want to
release it for anybody in the world to freely use.

If you really want to release code under something very similar to public domain then the [unlicense](https://unlicense.org/) could be for you. 
It states that anybody is free to use the software in any way they like. In jursidictions with public domain, it "dedicates" the software into the public domain.


### Permissive Licenses

Some of the simplest open source licenses are known as the "permissive
licenses". Broadly speaking these require anybody redistributing the code
to include the license text and a copyright statement crediting the
authors. But they do not require any modifications to release their
source code alongside the executable program. This allows software
released under these licenses to be made into part of a closed source
program and all the creator of the closed source program needs to do is
dsitribute the license text and perhaps some crediting statement to the
original author, but they don't need to redistribute the source code with
their closed source program.

#### MIT License 

The MIT License is very simple and a very popular choice of license, it is only three paragraphs long. It
states that:
* Anybody receiving the software can copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software to anybody they like.
* That they must include the license text and copyright statement when they redistribute it.
* That there's no warranty included and you can't hold the authors liable for any problems or damages that might arise.

#### BSD 

The BSD license is very similar to the MIT license, but it has several
variants. The oldest is the 4 clause version which requires:

* Source code redistributions must include the copyright statement and license text.
* Binary redistributions must include the copyright notice and license text in their documentation.
* Any advertising for the software incorporating this software must include a statement saying that it includes software written by the author.
* That the author doesn't endorse any derived products.
* That the author doesn't provide a warranty.

The acknowledgement clause caused some controversey and some people
thought that it didn't meet the open source definition or comply with the
four freedoms. To address this a new version of the license known as the
3 clause BSD license was created. This removed the acknowledgement
clause. An even simpler 2 clause version was launched that simply
required the copyright notices to be included in both source and binary
forms and still included the text about there being no warranty. 

#### Apache 2.0

Another popular permissive license is the Apache 2.0 license. It is very
similar to the MIT and BSD licenses, but also includes some clauses about
patent licensing. These require any contributor to a program which is
licensed under Apache 2.0 to allow their patents to be used free of
charge by any user of the software. This was done to head off some
concerns about software patent legislation at the time the license was
developed.

### Copyleft Licenses

The other common form of open source licenses are the "Copyleft"
licenses. These require that any modifications to the program are also
released under a compatible copyleft license. This can cause
complications when combining code that's under copyleft with other
licenses as now the entire codebase must be released under the copyleft
license. If there are any incompatible terms in the other license then
this can prevent the two codebases from being combined. 

The main advantage of copyleft licenses is that anybody else who
incorpoates the code into another product must also keep that product
open and this makes it harder for it to be subsumed into a commercial
product that doesn't contribute improvements to the code back to the
community which created it.

#### GPL version 2

The mostly commonly known copyleft license is the GNU Public License or
GPL. There are several versions of the GPL available, the oldest GPL
version 1.0, but this version was quickly replaced with version 2.0 and
was rarely used. Version 2 is much more common and is used by a lot of
popular software including the Linux Kernel and much of the GNU operating
system that is key to many Linux systems. Compared with the permissive
license the GPL is quite a long license agreement and many of its clauses
can be quite difficult for non-lawyers to fully understand.

#### GPL version 3

The GPL version 3 was introduced to try and prevent patenting of software
under the license and to require that people distributing GPL code on
embedded systems must also give users the ability to rebuild that
software and use it in their device. It is an even longer document than
GPL version 2 and has proved controversial with some and hasn't been as
widely adopted as version 2. 

#### LGPL

In order to allow library software to be combined with ("linked" in
technical terms) other software that's no GPLed, a special version of the
GPL called the LGPL (L for "Lesser" or "Library") was created. This is
used by many popular libraries including the GNU C library that is linked
to every C program compiled on a Linux system.  


#### AGPL

One problem for the GPL is that a lot of modern software doesn't run on
user's own computers, but on remote web servers that they connect to
through their web browser. When a user run's one of these web
applications they aren't receiving a copy of the software's executable
binaries, but are interacting with them over a computer network such as
the internet. This doesn't meet the GPL's definition of dsitributing the
binaries, so even if the web applicaiton is under the GPL, the person
running the server has no obligation to supply users with the source
code. The Affero GPL or AGPL requires that people running web
applications licensed under the AGPL make the source code available to
the users of those web applicaitons. 

### Choosing a License

When choosing a license for your code there's a number of things you might want to consider:

* Do you want to ensure that anybody modifying and redistributing your code will release the source code of their changes?
* Or would you prefer to ensure the least number of restrictions and that your code will be used as widely as possible? Even if that means it might end up in commercial products that don't release their source code.
* Are you reusing code which is already under an open source license? What obligations do you have under those licenses? 
* Is there a preferred license in your research community?

Don't be tempted to write you're own license (or modify an existing one)
unless you are a copyright lawyer. The common open source licenses have
been carefully written by copyright lawyers, many of them have undergone
multiple iterations in response to cases that have arisen and the
implications of many different legal jurisidcitons has been considered.
The common licenses are also well known, meaning that potential users and
contributors have a better understanding of what their rights and
responsibilities are leaving less room for misunderstanding.

#### Tools to help you choose

The website [choosealicense.com](choosealicense.com) has some great
resources to help you choose a license that's appropriate for your needs.

::::::::::::::::::::::::::::::::::::: challenge

## License selection exercise

Q: You have created a library of functions that are commonly used by
researchers in your field. You would like to share this code with your
research community and ensure that the code remains as open as possible
to benefit the community. But you would also like to see it being
integrated into as many different research codes and even commercial
products as possible. What would be a good choice of license?

:::::::::::::::: solution

A: The LGPL license could be a good choice for library code. It can be
linked to software that isn't GPL licensed but any modifications to the
library itself must be released under a GPL compatible license.

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::


### Creative Commons Licenses

All of the licenses we've discussed so far are really only intended for
source code. They are not suitable for documentation, datasets, drawings,
logos, music, maps etc. To solve this problem there are the Creative
Commons licenses, which are expressly built for anything other than
source code. Creative commons has now gone through four versions with the
latest being version 4.0, generally you should use version 4.0 as this is
more suited for use around the world 

There are several different types of Creative Commons licenses:

#### CC0

Creative Commons Zero or CC0 is the simplest license and is effectively a
public domain license, but is suitable for use world wide.

####  Attribution (BY)

All the Creative Commons licenses apart from CC0 require you to give
credit to the original creator. This is very similar to what is required
by all of the permissive code licenses.

#### Share-a-like (SA)

Share-a-Like Creative Commons licenses requires any derivative works to
be released under a compatible creative commons license. This is very
similar to the way that Copyleft licenses work.

#### Non-Commercial (NC)

Non-commercial creative commons licenses only allow for non-commercial
use of the work.


#### No Derivatives (ND)

No derivatives creative commons licenses require that users of the work
can't redistribute modified versions of it.

#### Combinations of Creative Commons Licenses

Under these rules the following combinations are possible:

 * CC-BY - Creative Commons Attribution    * CC-BY-SA - Creative Commons
Attribution Share Alike     * CC-BY-NC - Creative Commons Non Commercial 
*  CC-BY-NC-SA - Creative Commons Non Commercial Share Alike
* CC BY-ND - Creative Commons No Derivatives
* CC BY-ND-NC - Creative Commons No Derivatives Non Commercial

::::::::::::::::::::::::::::::::::::: challenge

## License selection exercise 2

Q: choose a license for a scenario involving code and data

:::::::::::::::: solution

A: 

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::



## Adding a license to your code/data

* Add a license file
* Add license statement to the top of every file


::::::::::::::::::::::::::::::::::::: challenge

## License file exercise
Q: add a license file to your git repo

:::::::::::::::: solution

A: 

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::



## Relicensing 

* License compatibility
* CC0/PD to anything
* Permissive to Copyleft

## Going commercial 
* Dual licensing
* Contributor license agreements
* Don't try to write your own

::::::::::::::::::::::::::::::::::::: challenge

## Relicensing exercise

Q: somebody has code under license X, can they relicense under Y?

:::::::::::::::: solution

A: 

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::

## Sharing your code 
* Make code public
* Transferring to an organisation
* Archive to Zenodo
* Add a DOI
* Add a citation file
* Add a codemeta file, FAIR principles

## Pull Requests
 * show pull request workflow
 * get a helper to pull reuqest a change into a file
 * demonstrate review process

::::::::::::::::::::::::::::::::::::: challenge

## Pull Request Exercise

Q: add yourself to the authors or citation file and submit a pull request

:::::::::::::::: solution

A: 

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::

## Acknowledgements

The content of this episode was inspired / heavily borrowed from the following resources:

- Software carpentry git lesson licensing and citation sections - https://swcarpentry.github.io/git-novice/11-licensing.html and https://swcarpentry.github.io/git-novice/12-citation.html
- ...

## Further reading

We recommend the following resources for some additional reading on the topic of this episode:

- Open source definition - https://opensource.org/osd/
- What is free software - https://www.gnu.org/philosophy/free-sw.en.html




:::::::::::::::::::::::::::::::::::::::: keypoints

- Open source applies Copyright licenses permitting others to reuse and adapt your code or data.
- Permissive licenses
- Copyleft licenses
- Creative commons
- Open source software can be sold
- Add license file to your repo, add a license to each file in case it gets detached
- Unless you are a lawyer don't try to create your own license.

::::::::::::::::::::::::::::::::::::::::::::::::::

