---
layout: post
title: "GSoC Proposal UCSC Xena"
categories: top_posts
author: "Ayan Banerjee"
tags: blog
permalink: "GSoC19-Proposal"
intro_pic: "https://developers.google.com/open-source/gsoc/resources/downloads/GSoC-icon-192.png"
---

## Table of Contents

- [Project: Update GDC Data on Xena](#project-update-gdc-data-on-xena)
  * [Project Proposal](#project-proposal)
    + [A high-level description of what you plan to work on](#a-high-level-description-of-what-you-plan-to-work-on)
    + [Specific details, key aspects and anticipated challenges](#specific-details-key-aspects-and-anticipated-challenges)
    + [Tell us what research into this project you have done](#tell-us-what-research-into-this-project-you-have-done)
    + [Break the project down into smaller tasks](#break-the-project-down-into-smaller-tasks)
      - [Phase 1 (Week 1-4)](#phase-1-week-1-4)
      - [Phase 2 (Week 5-7)](#phase-2-week-5-7)
      - [Phase 3 (Week 8-11)](#phase-3-week-8-11)
    + [Timeline](#timeline)
  * [Personal Background](#personal-background)
  * [Relevant Skills](#relevant-skills)
    + [What are your languages of choice and how do they relate to the project?](#what-are-your-languages-of-choice-and-how-do-they-relate-to-the-project)
    + [Any prior experience with open source development?](#any-prior-experience-with-open-source-development)
    + [Please point us to a code sample you have written.](#please-point-us-to-a-code-sample-you-have-written)
    + [Any prior experience in bioinformatics or cancer genomics?](#any-prior-experience-in-bioinformatics-or-cancer-genomics)
  * [Your Availability](#your-availability)
    + [Do you have any school-related activities scheduled during the coding period?](#do-you-have-any-school-related-activities-scheduled-during-the-coding-period)
    + [Do you have a full- or part-time job or internship planned for this summer?](#do-you-have-a-full--or-part-time-job-or-internship-planned-for-this-summer)
    + [Any other plans during the coding period that might impact what hours or days you can work?](#any-other-plans-during-the-coding-period-that-might-impact-what-hours-or-days-you-can-work)
    + [How many hours per week do you have for a summer project?](#how-many-hours-per-week-do-you-have-for-a-summer-project)


## Project: Update GDC Data on Xena

### Project Proposal

- #### A high-level description of what you plan to work on

  UCSC Xena is a functional genomics visualization and analysis platform. Forthis (genomics visualization and analysis),
  there are many datasets which are provided by data hubs available with Xenabrowser itself which users can use. The data
  hubs are: _UCSC Public Hub_, _TCGA Hub_, _Pan-Cancer Atlas Hub_, _ICGC Hub_, _UCSC Toil RNAseq Recompute_, _Treehouse Hub_
  and _GDC Hub_. Our discussion of interest lies in the GDC Hub.

   GDC (Genomic Data Commons) Hub fetches data from the GDC repository: 
   [https://portal.gdc.cancer.gov/repository](https://portal.gdc.cancer.gov/repository) via the GDC API. However, the data on
   the Xena is not updated. Current Xena data was updated on _release 10_, roughly 1.5 yrs ago. This project mainly revolves
   around updating data on xena with the current release (_release 15_). This will also simplify the process of adding data
   to Xena removing the XML files as a source.



-  #### Specific details, key aspects and anticipated challenges

   The process involves two high-level goals:

    *   _<span style="text-decoration:underline;">Updating GDC data wrangling pipeline</span>_: The pipeline code (_i.e._ [https://github.com/yunhailuo/xena-GDC-ETL](https://github.com/yunhailuo/xena-GDC-ETL) currently fetches the data from GDC repository via GDC API) is outdated. This part of the goals aims to update with the latest release.
    *   _<span style="text-decoration:underline;">Updating GDC data on Xena</span>_: As the data wrangling pipeline will be updated, this part of the goals will aim to update the GDC data on xena.



- #### Tell us what research into this project you have done

    *   I have analyzed the gdc module of the `xena-GDC-ETL` package and added tests for the same. The module currently has 82% test coverage. In my analysis, I have found that the code and APIs used in the module are updated with the upstream.
    *   During my contributions to the repo, I got sound knowledge on the modules and what task each of them performs.



- #### Break the project down into smaller tasks
	
  ##### Phase 1 (Week 1-4):

  -  Improve the overall project in this phase, _i.e._ adding tests, fixing lint issues, improving CLI and setting up
  doctests for existing ones and release the project to pypi.
  -  Fix broken APIs and code for fetching new data from API.
  -  Start adding code for the new data provided by GDC API. The package should be able to fetch and upload
  FM Simple Somatic Mutation data by the end of this period.

  ##### Phase 2 (Week 5-7):

  -  Add and upload GISTIC - Copy Number Score, DNAcopy data and Star - Counts data into xena and document the process.

  ##### Phase 3 (Week 8-11): 

  -  Finish uploading the data into xena, add docs and doctests.


#### Timeline

This week-by-week timeline provides a rough guideline of how the project will be done.


<table>
  <tr>
   <td>Phase
   </td>
   <td>Date
   </td>
   <td>Tasks
   </td>
  </tr>
  <tr>
   <td>Community Bonding
   </td>
   <td>May 7 - May 26
   </td>
   <td>
<ul>

<li>Familiarising myself with the mentors and the codebase. I will dive deep into the code and learn all the ins and outs of the code with the help of mentors.

<li>Also, check how the data is uploaded into xena cohorts after downloading and transforming.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td rowspan="5" >Phase 1
   </td>
   <td><em>Week 1</em>: May 27 - Jun 2
   </td>
   <td>
<ul>

<li>Fix all the linting issue as reported by <em>flake8.</em>

<li>Also, as the linting issues are fixed, in CI no longer allow lint to fail.

<li>Identify parts of the code which will be incompatible for Python3, especially Python 3.8 and rectify them. This will make the current code future-proof.

<li>Add tests for the existing untested code for the smaller modules, <em>i.e.</em> under scripts <code>panTCGA</code>, <code>merge_xena</code>, <code>make_metadata,</code> and <code>TARGET-CCSK_phenotype_ETL</code> modules.

<li>Setup CI for doctests. Example of one such test can be found inside the docstrings utils module.

<li><code>xena-GDC-ETL 0.2</code> should be released by now in GitHub/pypi. 
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><em>Week 2</em>: Jun 3 - Jun 9
   </td>
   <td>
<ul>

<li>Currently, the package has only ~11% code coverage. Good code coverage is required to enhance the maintainability of the project. I will identify parts of the code base (other than the <code>xena_dataset</code> module) which is out of coverage and add tests for the same.

<li>Investigate the xena_datasets module and add tests for the code which fetches public data from <code>TCGA</code> and <code>TARGET</code> data. In this process, we will get to know which APIs are working and which are not.

<li>Fix the broken APIs and remove them which are obsolete.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><em>Week 3</em>: Jun 10 - Jun 16
   </td>
   <td>
<ul>

<li>Start working on adding missing data.

<li>Add and wrangle the data from <code>FM</code> program by the end of this week.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><em>Week</em> <em>4</em>: Jun 17 - Jun 24 
   </td>
   <td>
<ul>

<li>Modify the <code>gdc2xena</code> script such that it is able to load <code>FM data</code> into xena.

<li>Document the whole process. 
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Jun 24 - Jun 28
   </td>
   <td><em>Phase 1 Evaluation</em>
   </td>
  </tr>
  <tr>
   <td rowspan="4" >Phase 2
   </td>
   <td><em>Week 5</em>: Jul 1 - Jul 7
   </td>
   <td>
<ul>

<li>Add and wrangle <code>GISTIC - Copy Number Score</code> data by the end of this week.

<li>Modify the gdc2xena script such that it is able to load <code>GISTIC - Copy Number Score</code> data into xena. Since in the last week most part of the APIs would be already done, it should not take much longer.

<li>Document the whole process.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><em>Week 6</em>: Jul 8 - Jul 14
   </td>
   <td>
<ul>

<li>Add <code>DNAcopy</code> data by the end of this week.

<li>Modify the <code>gdc2xena</code> script such that it is able to load <code>DNAcopy</code> data into xena.

<li>Document the whole process.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><em>Week 7</em>: Jul 15 - Jul 21
   </td>
   <td>
<ul>

<li>Add gene expression data <code>STAR - Counts</code> data by the end of this week.

<li>Modify the <code>gdc2xena</code> script such that it is able to load <code>STAR - Counts</code> data into xena.

<li>Document the whole process
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Jul 22 - Jul 26
   </td>
   <td><em>Phase 2 Evaluation</em>
   </td>
  </tr>
  <tr>
   <td rowspan="5" >Phase 3
   </td>
   <td><em>Week 8</em>: Jul 29 - Aug 4
   </td>
   <td>
<ul>

<li>Finish uploading data to xena.

<li>Fix any broken codes.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><em>Week 9</em>: Aug 5 - Aug 12
   </td>
   <td>
<ul>

<li>Buffer week for any unfinished task.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><em>Week 10</em>: Aug 13 - Aug 19
   </td>
   <td>
<ul>

<li>Add a cron job using Travis CI which will run the pipeline automatically bi-weekly or monthly and will update the data in xena, in this way it will be never out of sync and even if GDC updates their API, the job will fail and actions can be taken.

<li>Check the robustness of the cron job.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><em>Week 11</em>: Aug 20 - Aug 26
   </td>
   <td>
<ul>

<li>Finish up documentation and tests.

<li>Add tests for the code inside docs. Also setup CI for the same.

<li>Finish setup for writing docs using <strong>Sphinx</strong>.

<li>Release the existing docs in <a href="https://readthedocs.io">https://readthedocs.io</a> as sometimes GitHub wiki does not play well with small screens.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Aug 26 - Sep 2
   </td>
   <td><em>Final Evaluation</em>
   </td>
  </tr>
  <tr>
   <td>Post GSoC
   </td>
   <td><em>-</em>
   </td>
   <td>
<ul>

<li>Keep an eye on the cron job and fix failures if the API structure changes.

<li>Help the newcomers to get started in the UCSCXena organization.
</li>
</ul>
   </td>
  </tr>
</table>




### Personal Background


*   **Name**: Ayan Banerjee
*   **Email**: [ayanbn7@gmail.com](mailto:ayanbn7@gmail.com)
*   **Mobile**: +91 8016399022
*   **Timezone**: Indian Standard Time (UTC +05:30)
*   **Postal Address**: Nutan Mahula, Mahula, Murshidabad, West Bengal, India - 742 134
*   **Links**:
    *   _GitHub_: [https://github.com/ayan-b](https://github.com/ayan-b)
    *   _GitLab_: [https://gitlab.com/ayan-b](https://gitlab.com/ayan-b)
    *   _Gitter_: [https://gitter.im/ayan-b](https://gitter.im/ayan-b) 
    *   _CodeChef_: [https://codechef.com/users/ayan_nitd](https://codechef.com/users/ayan_nitd)
    *   _LinkedIn_: [https://linkedin.com/in/ayanb](https://linkedin.com/in/ayanb) 
*   **Education**
    *   _Bachelor of Technology_
        *   _Department of Electronics and Communication Engineering_
        *   [National Institute of Technology, Durgapur](https://www.nitdgp.ac.in/)
        *   July 2016 - Present
        *   CGPA: 9.30/10 _(till 5th semester)_
    *   _Higher Secondary (10+2)_
        *   February 2016
        *   [Sargachi Ramakrishna Mission High School](http://www.rkmsargachi.org/), West Bengal
        *   Mathematics & Biology
        *   Score: 96%
    <!--*   _Secondary (10th)_
        *   January 2014
        *   [Sargachi Ramakrishna Mission High School,](http://www.rkmsargachi.org/) West Bengal
        *   Mathematics, Biology, History & Geography
        *   Score: 92.43% -->
*   **Work Experience**:
    *   _Student mentor, [Google Code In](https://codein.withgoogle.com/)_

        _Oct - Dec 2018_

        *   Mentored pre-university students to get started in open source
        *   Mentored the students for the organization _coala_
    *   _Summer Intern at [Indian Institute of Technology, Bombay](http://www.iitb.ac.in/)_

        _May - July 2018_

        *   Integrated a plagiarism checker for Python programming language with _Yaksh_, a course-taking application
        written in Django.
        *   Wrote an elaborate test suite for the same.


### Relevant Skills

#### What are your languages of choice and how do they relate to the project?
   **Python**: Since the current data wrangler is completely written in Python, naturally The language of choice for this
   project is **Python**. Some **shell** scripting may be required for automating stuff (tests, linting, etc.).
   Some other technology requirements are **Git** (for version control), **Jinja2**(for templating), **CI**(Continuous Integration) and writing docs using **Sphinx**.


#### Any prior experience with open source development?


*   I have been a core developer at the organization **moremoban** for the last 4 months. I am mainly involved with the
    project **moban**, _a jinja2 CLI command for static text generation_
    ([contributions](https://github.com/moremoban/moban/commits?author=ayan-b)) and
    **pypi-mobans** ([contributions](https://github.com/moremoban/pypi-moban/commits?author=ayan-b)).
    These 2 projects are used as repository management tools, and they are written in **Python** and **Jinja2**.
    I developed 2 plugins for the project: [moban-velocity](https://github.com/moremoban/moban-velocity),
    [moban-haml](https://github.com/moremoban/moban-haml) and released them into [PyPi](https://pypi.org/user/ayanb/).

*   I have also contributed to the `xena-GDC-ETL` repository. My contributions can be
    found [here](https://github.com/yunhailuo/xena-GDC-ETL/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Aayan-b+).
    Also, I have created some [issues](https://github.com/yunhailuo/xena-GDC-ETL/issues?utf8=%E2%9C%93&q=is%3Aissue+author%3Aayan-b+)
    for the overall improvement of the project.

*   I have also developed some personal projects, mostly in Python and Vanilla JavaScript, all of those are open-sourced
    and can be found in my GitHub and GitLab profile.

####  Please point us to a code sample you have written.
My contributions to the project can be taken as code samples as well as the projects I contributed mentioned previously:

-   Commits: [https://github.com/yunhailuo/xena-GDC-ETL/commits?author=ayan-b](https://github.com/yunhailuo/xena-GDC-ETL/commits?author=ayan-b)
-   PRs: [https://github.com/yunhailuo/xena-GDC-ETL/pulls?q=is%3Apr+author%3Aayan-b](https://github.com/yunhailuo/xena-GDC-ETL/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Aayan-b)
-   Reviews: [https://github.com/yunhailuo/xena-GDC-ETL/pulls?q=is%3Apr+reviewed-by%3Aayan-b](https://github.com/yunhailuo/xena-GDC-ETL/pulls?q=is%3Apr+reviewed-by%3Aayan-b) 
  
####   Any prior experience in bioinformatics or cancer genomics?

  I have high-school level knowledge of genomics and am familiar with the basics of it. Also, I am familiar with the commonly
  used terms related to Genomics.


### Your Availability


####   Do you have any school-related activities scheduled during the coding period?

  Summer vacation at my university starts from first week of May and ends on the second week of July. So, from second week of
  July, I will be at my university and will continue coding there.

#### Do you have a full- or part-time job or internship planned for this summer?

  No.

#### Any other plans during the coding period that might impact what hours or days you can work?

  No.

#### How many hours per week do you have for a summer project?

  Since I can do this project full-time, I will be able to devote 50-60 hrs per week for the same.
  Once my university starts in mid-july, I will be able to give 3-4 hrs per day during weekdays
  and 8-10 hrs per day during weekends.

<script src="https://gist.github.com/ayan-b/25c78a26edcfa689be848cd703850652.js"></script>
