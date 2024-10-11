---
title: Ethical & environmental considerations around research software
teaching: 45
exercises: 15
---

:::::::::::::::::::::::::::::::::::::: questions

- What ethical considerations are there when using and writing research software?
- How can our research software impact the rights and well-being of others?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
After completing this episode, participants should be able to:

- Understand some ethical issues around research software development and usage and how they impact others.

::::::::::::::::::::::::::::::::::::::::::::::::

Research software development and its use (along with data it handles) does not happen in a vacuum - 
it can pose a number of ethical concerns and challenges for society and the environment, such as contributing to 
social inequality, compromising privacy and security, increasing environmental impact, and creating social and 
psychological issues. 
While these concerns do not strictly fall under
the FAIR principles, they all contribute to research software quality, reliability and responsibility.

### Software development practices

Ethical software development practices prioritise:

- Transparency: openly sharing source code and methodologies to allow for scrutiny and replication of research.
- Software quality and reliability: rigorous testing to ensure that software performs as documented and
  produces reliable results.
- Accountability: ensuring that developers are accountable for the software they create, particularly in terms of
  accuracy and reliability.
- Responsible use of software & data: 
  - recognising and mitigating the potential for software to be used for harmful 
  purposes (e.g. cybersecurity tools being used for hacking).
  - considering the broader social implications of software applications and data used,
    e.g. the use of data that has been collected without permission from the groups or individuals
    (e.g. historically excluded and exploited groups), or data that contains private or upsetting information.
  - implementing measures to detect and mitigate biases in algorithms and data,
    ensuring that the software treats all users fairly.

:::::: challenge
### Scraping publicly available data responsibly

You have been tasked with writing software to scrape a public forum to collect personal data for your study -
discuss as a group and write down what ethical issues should you consider and how should you act in this case?

::: solution

1. Compliance with Terms of Service (ToS) - most websites, including forums, have ToS that explicitly
   prohibit or restrict web scraping. Violating these terms can lead to legal action and is considered unethical.
2. User privacy concerns - scraping a forum can collect a vast amount of user data, including personal information,
   opinions, and conversations. Avoid collecting personally identifiable information (PII) unless it is absolutely
   necessary and permissible and protecting user privacy (e.g. do not de-anonymize users).
3. Lack of consent: users of the forum likely have not given explicit consent for their posts and data to be scraped
   and used by third parties. It's ethical to inform users and seek consent where possible, or at least be transparent
   about data usage.
4. Impact on website performance - scraping can put significant strain on the forum’s servers, cause Denial of Service
   attacks amd potentially disrupting service for regular users. Ensure your software is designed to be non-disruptive.
5. Data use and sharing - clearly define and limit the purpose of data collection, collect only the data necessary for
   the intended purpose, and be cautious about how the scraped data is shared or sold. Ensure that it is used responsibly
   and does not harm the users from whom the data was collected.
6. Data accuracy and integrity - ensure that the scraped data is used accurately and not misrepresented,
   avoid taking quotes out of context or using data in misleading ways, avoid modifying or altering the data in ways
   that could be deceptive.
7. Legal considerations - forum content is often copyrighted so scraping content without permission can lead to
   copyright infringement so seek permission where necessary.
8. Ethical purpose - consider the intent behind scraping the forum and ensure that the purpose is constructive and
   beneficial (and not harmful and unethical - e.g., for creating, fake profiles, spam, or harassment).
9. Transparency and accountability - where possible, be transparent about your research methodology,
   scraping activities and their purpose, take responsibility for any negative consequences that may arise from scraping
   and be prepared to address and mitigate any issues.

Best Practices for ethical scraping:

- Respect `robots.txt`: Always check and respect the robots.txt file of the forum, which indicates the site's rules regarding web crawling.
- Rate limiting: implement rate limiting to avoid overwhelming the server.
- Data minimization: collect only the data that is necessary for your purpose.
- User-Agent identification: use a User-Agent string that identifies your scraper and include contact information.
- Ethical review: if you are scraping for research, consider submitting your methodology for ethical review.

:::

::::::

:::::: challenge
### Ethical software reuse

Good research software practices apply not only when we develop software ourselves, but also when we reuse other 
people's software. Discuss as group and write down in the shared document your thoughts about what ethical 
considerations should we have in mind and pros and cons we should weigh in when choosing other people's software for 
reuse.

::: solution 

When incorporating other researchers' software into our research workflows we should not do it blindly but should
inspect it critically and look closely at how the software is developed, what reseach methods are used and 
how are results of that software generated. Here are some considerations:

- What is the quality and reliability of software we are reusing? Is it well tested? Some indicators of reliability
  could be a large number of open unresolved issues for bugs. Is it using outdated methods?
- How is software shared? Is it openly available on some code sharing platform or given to us on a memory stick?
- Are developers of the software credited for their work?
- Are software developers respectful to each other, external contributors and their users? 
Does the software project have a code of conduct?
- How is the project funded? Are there any concerns about who is financing the work?
- Are we are users respecting licenses and giving proper attribution to the developers of the code we are reusing?

Note: tools such as [Snyk](https://snyk.io/) are available to help you check software projects that you intend to reuse 
in your work - they are designed to help you identify find weaknesses, violations, vulnerabilities and security issues 
in open-source software libraries and can help you make a decision whether or not you should use some software.

:::

::::::

### Intellectual property and licensing

Ethical considerations in intellectual property (IP) and licensing in software development involve 
respecting creators' rights, promoting fair use and ensuring that the use and distribution of software align 
with legal and ethical standards. Here are some ethical practices to consider in this space:

- Clarity and accessibility: make the licensing terms clear and accessible to users, provide documentation that 
explains the license and how others can comply with it. 
Conversely, take time to understand and comply with the terms of any licenses associated with the software or code 
you are using.
- License compliance: ensuring that software use complies with licensing agreements and avoiding unlicensed
(and illegal) use of software and data. 
Regularly review the licenses of all dependencies of your code and ensure that their terms are 
compatible with your project's licensing and distribution model.
- Permission: ask for explicit permission when using code or resources that do not have a clear license or when your 
intended use is outside the scope of the given license.
- Avoiding exploitative practices: do not exploit open source software for profit without giving back to the 
community or complying with the license terms.
- Contributing back to the community: when using open source software, contribute back to the community by 
reporting bugs, contributing code improvements, or helping with documentation. 
Share your own improvements or extensions to open source projects under the same or compatible licenses.


:::  challenge
### Intellectual property and licensing of AI-generated code

The licensing and intellectual property (IP) of code generated by large language models (LLMs) and 
[AI pair programmers][ai-pair-programmers] (such as [CodeGen][codegen] or [Google Copilot][google-copilot]
which operate with an AI system as one of the code developers) raise complex legal and ethical questions that are not 
clear cut. 
Discuss as group and write down in the shared document some considerations and pros and cons of using AI-generated code.

::: solution

Here are some considerations:

- Intellectual Property (IP) ownership of the AI-generated code - typically, IP laws assign authorship to humans, 
not machines. However, the authorship of AI-generated code is ambiguous - it could belong to the developer who directs 
the AI, the developer's employer or the entity owning the AI. Furthermore, AI pair programmers can generate results 
that match or closely match code that is publicly available and potentially already licensed. As a result, you might 
end up incorporating someone else's (licensed) code into your code base without attribution or considering license 
implications. Some tools like GitHub Copilot have taken steps to reduce the risk of this by filtering out code 
completions that match publicly available code.
- Intellectual Property (IP) ownership of the training data: if the AI model was trained on copyrighted code, 
the output could potentially be seen as a derivative work, raising IP issues regarding the training data's licenses.
- Licensing terms of the AI-generated code - under what terms is the generated code to be used, for example, if the 
AI model is trained on open-source code, the generated code might need to comply with the open-source licenses 
(e.g., GPL, MIT). How can we attribute the original authors of the code used to train the AI model on? In addition, 
ethically, it is good practice to acknowledge the use of AI tools in generating code, even if not legally required.
- Security and bias concerns of AI-generated code - AI tools can generate code that is insecure, potentially 
destructive (e.g. deleting files) or use biased algorithms and data (see the section below) - 
so we should always try to understand and check any generated code before running it. 

:::

::::::


### Environmental impact of research software

The environmental impact of research software is an increasingly important consideration as the demand for 
computational resources grows. 
This impact is driven by the energy consumption and carbon footprint of the hardware infrastructure that supports 
software development, execution, and data storage.

- Energy consumption: research software often relies on large-scale data centers for storage and computation,
  or the use of HPC systems and supercomputers for complex simulations and data analysis, which can significantly
  increase energy usage (much of which may come from non-renewable sources).
- Carbon footprint: the electricity used to power data centers and HPC systems contributes to CO2 emissions,
  particularly if the energy comes from fossil fuels.

Here are some strategies to mitigate the environmental impact of computational research:

- Using data centers and cloud providers that use renewable energy sources (e.g., wind, solar) can reduce the
  carbon footprint of research software.
- Regular maintenance and upgrades can extend the life of existing hardware, reducing the need 
for new equipment and the environmental impact of manufacturing and disposal.
- Using virtualisation and containerisation technologies can reduce the number of physical servers needed to run our 
code, thereby saving energy.
- Optimisation of algorithms and code to run more efficiently can reduce the computational load and energy consumption.


:::::: challenge

### Using HPC systems in a more environmentally responsible manner

Often our research software is written for use on HPC systems. 
Discuss as a group and write down in which way can we improve our practices when writing, testing and running code 
on HPC system to support more responsible and less wasteful use of resources.

::: solution

Here are some thing to consider:

- Code efficiency: writing efficient code and choosing more efficient algorithms and data structures 
that minimises unnecessary computations can significantly reduce computational load and 
energy consumption. For example, avoid including an expensive data processing step in every job when it could be run 
once and set as a dependency for other jobs. Or using many nodes for a job that is not designed to run in parallel - 
consider refactoring your code.
- Profiling and optimisation: using profiling tools to identify and optimize resource-intensive parts of the code can 
enhance performance and reduce energy usage. To make best use of resources, part of our workflow should include 
identifying the most appropriate job configurations, e.g. [job scaling](https://ri.itservices.manchester.ac.uk/csf3/batch/scaling/) or using workflow management tools like 
Snakemake to ensure that we do not repeat expensive steps unless some upstream step in our workflow has changed.
- Code testing: avoid running untested code on a HPC system - test and debug locally first. Run a test job on one case 
study or a small data set before running on full data (consider setting up many jobs and finding 100s of jobs crashed 
after a few hours).

Technical topics:

- Work-flow management
- Profiling jobs on HPC
- Profiling Python code

:::

::::::

## Further reading

We recommend the following resources for some additional reading on the topic of this episode:

- [Ethics Issues in Custom Software and App-Based Research Experiments and Data Collection][ethics-ucl]
- [Ethical Considerations in Software Development][ethics-software]


Also check the [full reference set](learners/reference.md#litref) for the course.


:::::::::::::::::::::::::::::::::::::::: keypoints

- To act ethically, we have to be both responsible producers and consumers of research software.
- Free and open source research software and data, along with FAIR, ethical and environmental considerations, 
offer viable ways to make more transparent, reliable and accountable science that not only advances
scientific knowledge but also respects and protects the rights and well-being of all users.

::::::::::::::::::::::::::::::::::::::::::::::::::

