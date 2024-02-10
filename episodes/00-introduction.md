---
title: "Course introduction"
teaching: 25
exercises: 0
---

## What is and why do reproducible research?

Scientific transparency and rigor are key factors in research. Scientific methodology and 
results need to be published openly and replicated and confirmed by several independent parties.
However, research papers often lack the full details required for independent replication. 
Many attempts at replicating the results of well-known scientific studies have failed in a variety of disciplines [reference].
This is called [**the reproducibility crisis**](https://en.wikipedia.org/wiki/Replication_crisis) - an ongoing 
methodological crisis in which the results of many scientific studies are difficult or impossible to reproduce.

Reproducible research is a practice that ensures that researchers can repeat the same analysis multiple times with the 
same results. Those who practice reproducible research benefit from it greatly:

* Reproducible research helps researchers remember how and why they performed specific analyses; 
this enables easier explanation of work to collaborators and reviewers. 
* Reproducible research enables researchers to quickly modify analyses and figures - this is often 
required at all stages of research and expediting this process saves substantial amounts of time. 
* Reproducible research enables reusability of previously conducted research tasks so that new projects 
that require the same or similar tasks become much easier and efficient by reusing or reconfiguring previous work. 
* Reproducible research is a strong indicator of rigor, trustworthiness, and 
transparency in scientific research. This can increase the quality and speed of peer review, because reviewers can 
directly access the analytical process described in a manuscript. It increases the probability that errors are caught 
early on - by collaborators or during the peer-review process, helping solve the reproducibility crisis.  

However, increasing rigor often requires that researchers implement new practices and learn new tools.
This course aims to teach some of these practices and tools pertaining to the use of software for reproducible research.

## Software in research
Software is fundamental to modern research - some of it would even be impossible without software [ssi survey reference]. 
From short, thrown-together temporary scripts to
solve a specific problem and help with day-to-day research tasks, 
through an abundance of complex spreadsheets analysing collected
data, to the hundreds of software engineers and millions of lines of code behind international
efforts such as the Large Hadron Collider and the Square Kilometre Array, there are few areas of
research where software does not have a fundamental role.

In the survey conducted by the Software Sustainability Institute in 2014 [ref], 
92% of researchers indicated they used research software [reference]. 
We define "research software" as software or code that is used to generate, process or analyse results of a research 
for publication. 
Even formulas in spreadsheets are considered code - they are a form of computer programming in that allow you to 
create, calculate, and change data sets in a number of different ways. 
So, software is not reserved for [computational science](https://en.wikipedia.org/wiki/Computational_science),
also known as scientific computing, and “traditional” uses of computing capabilities and infrastructures (e.g.
simulations and computational methods) to understand and solve complex physical problems any more.
Nor its use is restricted to the "hard" sciences - the use of research software is ubiquitous and 
fairly even across all disciplines [ssi survey ref].

Research software is also widely developed - researchers do not just use “off the shelf” software,
the majority of researchers develop their own. 
In order to be able to produce quality software that outputs correct and verifiable results and 
that can be reused - this course teaches good practises and reproducible working methods that are agnostic of a 
programming language (although we will use Python as an example language) and hopefully demonstrate 
how programming tasks should be approached, ultimately providing researchers with the tools and knowledge to 
feel confident when writing good quality and FAIR software to support their research.

## FAIR software

FAIR stands for Findable, Accessible, Interoperable, and Reusable and comprises a set of principles designed to 
increase the visibility and usefulness of your research to others. 
The FAIR data principles [ref] are widely known and applied today. 
Similar FAIR principles [ref] have now been defined for software too - in general, they mean: 

* Findable - software and its associated metadata must be easy to discover by humans and machines alike.
* Accessible - in order to reuse software, software and its metadata must be retrievable.
* Interoperable - software must interact other software by exchanging data and/or metadata through 
standardised protocols and application programming interfaces
* Reusable - software should be usable (can be executed) and reusable 
(can be understood, modified, built upon, or incorporated into other software).

Each of the above principles can be achieved by a number of practices listed below. 
This is not exact science, and by all means the list below is not exhaustive, 
but any of the practices that you employ to your research software methodology will bring you 
closer to the gold standard of a fully reproducible research.
(Also check out the following ["10 easy things to make your research software FAIR"](https://librarycarpentry.org/Top-10-FAIR/files/poster_10things_FAIRsoftware.pdf
).)

* Findable
  * Create a description of your software
  * Place your software in a software repository (and ideally register it in a software registry)
  * Use a unique and persist identifier for your software (also useful for citations)
* Accessible
  * Make sure people can download your software
* Interoperable
  * Explain the functionality of your software 
  * Use standard formats for inputs and outputs
  * Communicate with other software via standard protocols
* Reusable
  * Document your software (including its functionality, and how to install and run it) 
  * Follow best practices for software development (including coding conventions, code readability and verifying its correctness)
  * Give a licence to your software clearly stating how it can be reused
  * State how to cite your software

We are going to explore the above practices on an example project we will be working on as part of this 
course. 

## Software and data used in this course
TODO

## References - TODO
[1] [A Beginner's Guide to Conducting Reproducible Research](https://esajournals.onlinelibrary.wiley.com/doi/10.1002/bes2.1801), 
Jesse M. Alston, Jessica A. Rick, https://doi.org/10.1002/bes2.1801

[2] SSI survey
