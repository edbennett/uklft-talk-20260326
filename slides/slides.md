# What is<br>Research Software Engineering?

-

![Diagram of a line labeled "Research" at the left, and "Software engineering" at the right, with "Research software engineering" covering the middle space.](images/rse.svg) <!-- .element width="1300px" -->

Notes:
Research software engineering is the fuzzy space between
pure non-computational research
and pure software engineering.
Put another way,
it's the techniques of software engineering applied to research.

---

# Who are<br>Research Software Engineers?

-

<!-- .element data-background-image="images/rse.jpg" -->

Notes:
A research software engineer
is someone whose job description is
(primarily)
research software engineering.
The term was coined at the Collaborations Workshop 2012,
with a number of aims:
to unite a disparate group of differing job titles at different institutions,
and to highlight the need for more roles specifically focussing on software.
For this reason,
while some use the term "research software engineer"
to refer to anyone who does research software engineering in the course of their job,
my preference is to delineate those who are specifically paid to care about software:
the problem with other roles is that
the incentive structure works against software maintenance,
unless ones KPIs are directly tied to software quality.

-

<!-- .element data-background-image="images/pool-group.jpg" -->

Notes:
One can roughly split RSEs into two groups:
pool RSEs and group (or integrated) RSEs.
Pool RSEs form part of centralised teams,
and frequently work on problems outside of their specialism.
They have to be highly adaptable to new contexts,
but will generally need some startup time
to familiarise themselves with your software and your domain
before they become productive.
The DiRAC RSE team operates on the pool model,
and many institutions also have their own RSE teams.
Group RSEs on the other hand
are integrated with your research group long term;
they frequently handle long-term maintenance of code,
sometimes that they were the original developer of.
As a specialist in the domain and software,
they may sometimes benefit from the support of
pool RSEs specialising in specific topics.

-

<!-- .element data-background-image="images/harp-drums.jpg" -->

Notes:
If you're familiar with performing orchestral music,
think of a pool RSE like a harpist.
You probably don't have one as part of your ensemble usually,
but they're specialist in what they do,
join your group for a specific purpose,
and adapt quickly to working with you.
Once their job is done,
they leave again.
On the other hand,
a group RSE is like a drummer:
while they don't perform the same family of instrument as the rest of the ensemble,
they rehearse with you week in week out,
and are more tightly integrated with everything you do.
Indeed,
much of a band's performance is underpinned by the rhythm section.
Importantly,
both performers are credited for their work,
and the same applies to RSEs;
where work is publishable,
appropriate authorship credit goes to all RSEs involved.

---

# What do RSEs do?

-

![A log-log plot of FLOP/s against node count, showing a roughly straight line](images/benchmark.png) <!-- .element width="1000px" -->

Notes:
One common activity of pool RSEs in particular is
to perform benchmarking and scalability analysis.
This is perhaps one of the easiest tasks for a non-specialist to perform:
if you give them some code to run an example problem,
and instructions on what parameters to adjust to vary the parallelisation,
they can very efficiently produce strong and weak scaling studies.
This is useful if you are applying for HPC time,
for example on DiRAC,
so that you can demonstrate that you will make optimal use of the available resources.

-

![A time series graph, with blue shaded regions above, and red and green spikes underneath.](images/profile-timeseries.png) <!-- .element width="1300px" -->

Notes:
The next step from benchmarking is profiling.
In this case,
example problems are run through tooling to identify
areas where the code makes sub-optimal use of the available hardware.
This is the first step towards optimisation work,
and is simple for a non-domain-specialist RSE to do.

-

![A portion of a pull request focusing on changes to a `Cshift_table` related function](images/optimisation.png) <!-- .element height="700px" -->

Notes:
A very popular activity to give to pool RSEs is performance engineering
(or "optimisation")
of codes,
either for current or for new hardware targets.
Many codes,
even in lattice,
leave a lot of performance on the table,
and RSEs can help to enable codes to make better use of this.
This can however require more onboarding time than benchmarking and profiling,
since a lot more context is needed to understand the data structures and data movement,
as well as how to potentially go beyond technical implementation improvements
to algorithmic ones that can unlock more speedups.

-

![A portion of a pull request focusing on moving from being specific to SU to generic for GaugeGroup](images/feature.png) <!-- .element height="700px" -->

Notes:
Something that's more challenging for a pool RSE to do
is to perform feature addition work.
This is not impossible if a prototype implementation is available,
or a lot of time is available to meet with the RSE and pair program or similar.
An integrated RSE can do this much more quickly,
but an alternative is a team of a student or postdoc and a generalist RSE,
with guidance.

-

![Two diagrams of linear time: one with RSE cleaning up after a student completes; the other with the two working cooperatively for a much quicker finish](images/collaborative-diagram.svg) <!-- .element width="600px" -->

Notes:
Imagine that you have a student working on a new feature for your software.
Assuming that you don't want to let the student push directly into the main branch,
in a pool RSE model,
the most likely setup for merging the code is that
after the student finishes work
(and possibly graduates),
you apply for RSE time to tidy up the code and merge it.
The RSE then has to reverse engineer the student's work,
and potentially reimplement large chunks of it.
With an integrated RSE model,
the RSE can instead work concurrently with the student,
giving regular reviews and feedback,
so that by the time the feature is finished,
only a little effort is required to polish the final corners and merge.
The feature is merged and available for production use much earlier,
and the student learns far more from the experience.

-

![A graph of performance over time for the last two years, showing consistent performance with occasional improvements](images/cicd.png) <!-- .element width="1300px" -->

Notes:
Something that RSEs can and do support with,
but there is space to do more of,
is continuous integration and continuous deployment.
Continuous integration is the idea that your test suite runs
after every commit and on every pull request,
to verify that the tests pass and the code isn't broken before it is merged.
In addition,
performance tests can be used as a continuous benchmark,
to verify that performance regressions aren't introduced into the code,
and that the target hardware is continuing to perform optimally.
Continuous deployment takes this a step further,
with the fresh builds being made available to users of the software,
rather than fixing on a particular version
and needing to manually build newer versions later.

-

![Screenshot of C++ code making assertions](images/tests.png) <!-- .element width="1300px" -->

Notes:
Of course,
a shiny CI setup isn't as valuable as it could be if there are no automated tests.
Writing a good test suite requires both software and domain expertise.

-

![Flowchart of the steps in a typical lattice computation](images/workflow-diagram.svg) <!-- .element height="700px" -->

Notes:
Something I've spent a lot of time on recently is the automation of analysis workflows.
While HPC codes can be relatively stable between different projects,
it's more common for each paper to have its own set of analysis tools.
Arranging these into an automated structure so that the findings are reproducible,
both by the collaboration and by those reading the paper,
requires some work.
This is easiest if it is baked in from the start;
reverse-engineering a completed analysis and re-implementing the automation
is much harder.
An aim of this process is to  make the logic of the analysis clearer to a reader,
as well as ensuring that the results are reproducible
rather than changing on each attempt at the analysis.

-

<!-- .element data-background-image="images/data.png" -->

Notes:
RSEs can also contribute towards open data efforts.
This includes developing middleware and software working with
systems like the International Lattice Data Grid,
as well as taking on basic data stewardship roles.
The former can be done by generalist RSEs;
the latter requires tight integration with collaborations.

---

<!-- .element data-background-image="images/unicorn.jpg" -->

Notes:
For a while,
there was a meme in the RSE community
to use the image of the unicorn to represent ourselves,
the people who could understand both the software and the science.
More recently,
it's increasingly acknowledged that this isn't entirely accurate:
RSEs aren't unicorns,
and that's OK.
There is a low single-digit number of people in the world
who can keep a handle on all developments in lattice field theory
and also on software development practices,
and I'm not one of them.
RSEs,
just like anyone else in academia,
form part of interdisciplinary and multi-skilled teams,
filling gaps that would otherwise exist.

-

<!-- .element data-background-image="images/cash.jpg" -->

Notes:
How do we pay for this?
In the last decade or so we have done a better job at
convincing funders to fund software support alongside large facilities,
in the form of RSE pools or teams.
We still have to push back at every major government procurement
that spending all the money to get a higher headline amount of compute
at the expense of having nobody to get the software to work on it
will not give best value for money,
but that battle has got easier.
Funding RSEs more tightly integrated with research groups is harder.
STFC funded a single RSE fellowship in 2020,
and since EPSRC have moved away from the RSE fellowship model,
to my knowledge have no plans to offer more.
I was lucky enough to be awarded the RSE fellowship,
but surprisingly haven't managed
to single-handedly fix all software in the last five years.

-

![A mortarboard](images/mortarboard.svg) <!-- .element width="600px" -->

Notes:
There is of course a secret third option to being an RSE.
One can become an academic.
Historically this was problematic,
and something the RSE movement sought to escape,
because the pressure was to produce papers rather than spend time on software.
However,
if the academic incentive structure could be changed to include software KPIs,
this would become more viable.
The UK already has a number of academics who have "ascended" from RSE posts;
however,
most institutions don't yet have a structure for this.

---

# What _can_ we do?

-

<!-- .element data-background-image="images/docs.png" -->

Notes:
Given that we have central RSE teams available,
if we can reduce the barrier to entry for them modifying the code,

More complicated software will benefit from a more structured set of documentation.
This can go into more detail on build and run options.
It can include both tutorials and more formal reference material.
One approach you might think about to take things a step further is
"[tutorial-driven development](https://www.youtube.com/watch?v=XjpfgP2SPt8)",
where tutorials are written first,
then the software is written to behave as in the tutorials.

-

<!-- .element data-background-image="images/function.png" -->

Notes:
What about when it becomes necessary to start touching the source code directly?
Documenting each class and function with what it does
makes it much simpler to understand what the code does where,
and find the right place to make edits.
You can use tools like [Doxygen](https://www.doxygen.nl/index.html)
so that specifically-formatted annotations
are automatically turned into formatted developer documentation pages,
but having the comments in place at all is almost as valuable.
(And don't fall into the trap of thinking that
automatically-generated documentation like this
is a substitute for more holistic user-facing documentation!)

-

![Screenshot of the Grid Doxygen for the WilsonGaugeAction template class](images/grid-doxygen.png) <!-- .element height="700px" -->

Notes:
One thing that we worked on at the CCP-TEPP docathon last week
was expanding the Doxygen documentation for the actions in Grid,
as when we asked the DiRAC RSE team to work on optimising them last year,
multiple months were spent tracing through how they worked.

-

<!-- .element data-background-image="images/names.png" -->

Notes:
In general,
good software engineering practice is to use descriptive names for variables.
Since in science we tend to think of problems
in terms of single-letter variable names
for pen and paper definitions,
($l$ for length, $Q$ for charge, ...),
we often think it is intuitive to use the same names for our code.
This is often true,
but it is essential to include or link to definitions.
There are often multiple difference choices of notation
($f$ or $\nu$ for frequency),
and of normalisation
(how many factors of $\sqrt{2}$ are there in $f_{\pi}$?),
without which your collaborators have to reverse-engineer
back to what they think you must have meant.
Also,
single-letter names have very poor search engine optimisation,
so even trying to find a paper or textbook to refer to is hard.)
Adding a single line comment with an arXiv reference and equation number
takes thirty seconds at most
if you already have the paper open to do the implementation,
and immeasurably improves your future collaborators' days.

-

<!-- .element data-background-image="images/test.png" -->

Notes:
Being the conscientious scientists that we are,
we always already perform comprehensive tests on code after we have modified it.
But when your code is more than a few hundred lines long,
then you're not going to be able to,
by hand,
verify that every single path through the code is unbroken.
You'll most likely focus on the areas that got changed,
making certain assumptions about the input data
(perhaps aligned with what you're modifying the code to do at the time),
and other code paths may get overlooked.
Adding automated tests means that future collaborators can automatically make sure that
they aren't breaking any seemingly-unrelated functionality by accident,
as well as verifying that the functionality that you're adding is doing the right thing.
While this takes more time than writing a one-line comment,
it means that the work you've done won't be in vain,
and you won't have to go back and fix it repeatedly later when other people trample it.

Perhaps you've heard of all of these benefits before,
but there's one additional benefit of a suite of unit tests that is less discussed.
Unit tests provide a great entry point for reading the code.
If I want to know how a particular function is called,
and what format to expect from its output,
a unit test for that function will give that to me.
A good test suite will also highlight common errors that won't work,
so I can avoid those.
This can be very helpful when you try and go beyond examples listed in documentation.

-

<div style="width: 30%; float: right;">

[![CoSeC logo](images/cosec.png) <!-- .element height="100px" -->](https://cosec.ac.uk)

</div>

## CCP-TEPP

[ccp-tepp.github.io](https://ccp-tepp.github.io)

- [Roadmap now available](https://ccp-tepp.github.io/files/CCP_TEPP_Roadmap_1.0_2026-03-10.pdf)
- [Docathon: March 18&ndash;20, University of Warwick](https://indico.global/event/16510/) (complete)
- [Hadrons hackathon: April 14&ndash;15, University of Edinburgh](https://indico.ph.ed.ac.uk/event/418/)
- [Summer school: June 29&ndash;July 3, Swansea University](https://indico.global/event/16372/)

Notes:
The project to form a
Collaborative Computational Project in Theoretical and Experimental Particle Physics
aims to address common skills gaps in particle physics software,
and support the community in coming together to share and improve software.
Currently this is funded to the end of 2026 as a scoping project;
time will tell whether this funding will be extended to a full CCP.
In the mean time,
we can engage with its events.
Following a series of workshops last year,
the roadmap of targets for effort in the next few years of particle physics software
is now available.
This will be revised later this year,
so watch out for opportunities to engage.
One gap identified was around documentation;
to try and improve this,
and develop the community's skills in documentation writing,
we organised a docathon last week in Warwick.
We also identified that many groups are interested in using Hadrons,
but lack the time or resources to get started;
we have tried to ease this process by organising a hackathon next month.
Finally,
we identified that many software skills
would be beneficial to be embedded across the community,
but are not typically covered as part of a PhD student's training;
to this end,
we are organising a summer school later this year
to cover as many of the skills gaps as we can.

-

<!-- .element data-background-image="images/codereview.jpg" -->

Notes:
Code review is important for all software developers;
it's a key way to learn from each other,
as well as avoiding introducing bugs or design flaws.
However,
this is especially important when delegating writing code
(including analysis workflows)
to students.
We would do a disservice to students by denying them
this opportunity to develop and get feedback on their programming skills,
and we would do a disservice to the scientific community
by sharing code
(or even the output of code)
in which we haven't developed full confidence.
Looking at the output of the code is not sufficient;
in particular in the age of LLM-based code-writing assistants,
but even where these aren't used,
it is all too easy to produce plausible output
based on an underlying implementation that lacks the necessary scientific rigour.
This is an ideal task for an integrated RSE:
I now hold weekly meetings with each of our PhD students to
review their software work,
understand its reproducibility and rigour,
and offer suggestions for improvement.

-

![Screen shot of the APS Open Science home page](images/aps-open-science.png) <!-- .element height="700px" -->

Notes:
We all do excellent work documenting our scientific findings in papers.
Finding write-ups of technical work,
however,
is harder:
they might be scattered between paper appendices,
PhD thesis,
internal wikis,
and backs of envelops in a paper recycling facility.
Until recently,
this was somewhat justifiable:
there was no appropriate venue for publishing such technical notes;
while Journal of Open Source Software and Communications in Computational Science
could take strictly software contributions,
the more general technical paper didn't have a natural home.
My hope is that the new journal APS Open Science can fill this gap;
it at least claims to welcome a wider scope than the current physics journals
("diverse research outputs including
data and software advances,
replication studies,
and negative and null results"),
which require novel physics to be front and centre.

-


Try working more reproducibly and openly
([arXiv:2504.01876](https://arxiv.org/abs/2504.01876))

Notes:
Four years ago I stood up in front of this group
and promised a set of guidance on how to work openly and reproducibly.
It took longer than expected,
and is still a work in progress,
but I can now at least provide a set of tips on how our collaboration tries to work.

-

<!-- .element data-background-image="images/shareing.png" -->

<br>

<br>

<br>

<br>

<br>

<br>

<br>

[shareing-dri.github.io](https://shareing-dri.github.io)

Notes:
The SHAREing project aims to help
research technical professionals using accelerated compute
develop skills to do this more effectively
This includes researchers and RSEs
doing more effective profiling and performance engineering.
It's worth keeping an eye on.

---

## Conclusions

- Research software _engineering_ is everyone's job
- Central RSE groups are a powerful resource
  - Some small changes in the way you write your code can be a huge force multiplier
- Long-term embedded RSEs are hugely important for long-term maintenance
  - 🦄🚫
- RSE academics are possible
  - But need careful definitions of career pathways and KPIs
