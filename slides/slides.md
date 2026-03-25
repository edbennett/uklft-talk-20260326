# What is<br>Research Software Engineering?

-

![Diagram of a line labeled "Research" at the left, and "Software engineering" at the right, with "Research software engineering" covering the middle space.](images/rse.svg) <!-- .element width="1300px" -->

Notes:
Research software engineering is the fuzzy space between
pure non-computational research
and pure software engineering.
Put another way,
it's the techniques of software engineering applied to research.

-

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

<!-- .element data-background-image="images/pool-group.jpeg" -->

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

<!-- .element data-background-image="images/harp-drum.jpg" -->

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

-

# What do RSEs do?

-

![A log-log plot of FLOP/s against node count, showing a roughly straight line](images/benchmark.png) <!-- .element width="1000px" -->

Notes:









<!-- .element data-background-image="images/greens.jpg" -->

Notes:
Apologies in advance that this is going to be an "eat your greens" talk.
Many of the topics I'll outline will already be familiar to most of you.
Hopefully by the end of it I'll have convinced you that the greens are tasty,
and you will feel better for having had them.

---

<!-- .element data-background-image="images/write.jpg" -->

Notes:
When we are excited about implementing a new algorithm,
we can go into something of a fugue state,
translating papers into code.
We hold all of the relevant detail in our head,
so the code becomes obvious.
Who could possibly have problems reading such obvious code?
It's time to hurry on and start doing science with the code,
right?

---

<!-- .element data-background-image="images/stop.jpg" -->

Notes:
No!
Now is the time to stop and ask a few very simple questions!

---

# Who

is going to read my code?

-

<!-- .element data-background-image="images/reader.jpg" -->

Notes:
If you're making your code publicly available for reproducibility and openness
(and you should!),
your code is a way you are communicating your intent to those reading your work.
Even if while writing it you don't think you'll be releasing it,
it is still worth writing with this in mind,
in case you change your mind later,
or the code is audited for other reasons.
Things you can think about include
what messages you might unintentionally communicate with,
for example,
hardcoded constants or magic numbers.

-

<!-- .element data-background-image="images/rse.jpg" -->

Notes:
At some point,
you will need to have someone else work on your code.
One such group is Research Software Engineers.
Unless you're lucky enough to have a funded RSE on your project
(and,
depending on their skill set and focus,
possibly even then),
you're likely to need to make use of a pool RSE,
who will not be specialist on your software,
or likely even in your field of research.
They will need to get up to speed with both,
while also trying to make progress towards the project's goals.
The time this takes depends strongly on how the software is written;
there are many things you can do to bring this down,
many of which do not require huge up-front effort on your part!
RSE projects are often as short as 1&ndash;3 months;
for sufficiently difficult-to-approach software,
this can be less than the time taken
to be able to compile and understand how to make meaningful changes to it.

-

<!-- .element data-background-image="images/whiteboard.jpg" -->

Notes:
Even if you never engage with an RSE,
you will most likely at some point have a research student.
Since a typical first-year PhD student is less experienced than a professional RSE,
they will typically take longer to get up to speed with the software.
Similarly to a generalist RSE,
the software is likely to form significant scaffolding
in their developing understanding of the wider research field.
They are also prone to make errors in compilation and usage of the code:
at best,
this wastes valuable months of a 3-year programme of study;
at worst,
the errors are not detected until the work has already entered the literature,
or the student is about to submit and their completion is jeopardised.

-

<!-- .element data-background-image="images/room.jpg" -->

Notes:
Even if you don't have students
(or don't care about their onboarding time),
it's likely that at some point you'll need to revisit your code.
Perhaps to start another project,
or to understand a previous one when you receive questions about it.
Yourself in six months' time is a different person;
you will no longer have the same awareness of all of the moving parts of the code
as you did when you wrote it.

---

# What

do they need to do with it?

-

<!-- .element data-background-image="images/play.jpg" -->

Notes:
They will need to compile, install, or build the code,
and run it.

-

<!-- .element data-background-image="images/read.jpg" -->

Notes:
They will need to read the code,
and understand what it is doing&mdash;either
as a goal unto itself,
or so they will be able to make changes.

-

<!-- .element data-background-image="images/modify.jpg" -->

Notes:
They will most likely need to make changes.
This might include optimising the code for better performance,
porting it to new architectures,
extending it with new functionality,
or interfacing it with other tools.

-

<!-- .element data-background-image="images/verify.jpg" -->

Notes:
They will then need to verify that the program gives correct results.
In particular,
if changes have been made,
they would need to be confident that the changes don't break any existing functionality,
as well as giving the correct results for the feature that has been added.

---

# How

do I help them to do this?

Notes:
Without too much effort from my side?

-

<!-- .element data-background-image="images/books.jpg" -->

Notes:
The first element is documentation.
This is best written while the code is still fresh in your mind;
either at the same time as you're writing it,
or immediately afterwards,
before you move on.
Going back to document things later is much harder.
There's a few kinds of documentation it's worth calling out explicitly.

-

<!-- .element data-background-image="images/readme.png" -->

Notes:
Don't underestimate the power of a good README.
This will probably be the first thing a prospective user sees about your software,
so it's worth taking the extra 30 minutes to polish it. 
Users should come away understanding how to build or install the code,
and perform at least an initial run of it,
and where to find more documentation if they need it.
If your software is small in scope,
a good README might be enough user-facing documentation in itself!

-

<!-- .element data-background-image="images/docs.png" -->

Notes:
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

<!-- .element data-background-image="images/formatting.png" -->

Notes:
Moving to the lowest level,
having a common code format across a repository makes it
much easier to read and reason about.
Having this format be common to most projects makes it
even more approachable to new collaborators.
While it's commonly agreed that a common style is good,
the exact definition of that style can be more contentious.
So rather than defining it by hand
(spending time painting the bike shed rather than building the tools),
it is best to pick a tool and a pre-defined set of rules,
and let the tool enforce the rules automatically.

For the simpler rules where fixes can be applied automatically,
this takes ten minutes to set up for a project,
and results in much more readable code.
For Python,
`ruff format` is very efficient and works to a very common specification.
For C and C++ code,
`clang-format` is a popular choice.

-

<!-- .element data-background-image="images/test.jpg" -->

Notes:
Aside from documentation,
a second element that helps others work with your code is testing.

-

<!-- .element data-background-image="images/test.png" -->

Notes:
Being the conscientious scientists that we are,
we always already perform comprehensive tests on code after we haev modified it.
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

<!-- .element data-background-image="images/ci.png" -->

Notes:
Stepping a little away from software engineering briefly,
once you have a test suite,
a natural next step is to run that test suite automatically after each commit,
and on each merge/pull request to the repository,
so that even if you forget to run it,
or a collaborator isn't aware of it,
you still benefit from it.
This is usually referred to as "continuous integration" (CI).

For small projects,
most code forges offer free CI services.
If you need to test on HPC,
then these won't work,
but many HPC centres work with software communities to facilitate access for CI.
For example,
the DiRAC Extreme Scaling service in Edinburgh
is attached to a TeamCity instance
used to test the Grid particle physics code.

-

<!-- .element data-background-image="images/performance.png" -->

Notes:
Once you have a CI setup,
if your code is at all performance-sensitive
(and in particular if it uses significant amounts of HPC resources),
then it makes sense to monitor the performance of performance-critical routines
as part of your CI.
This lets you know if you've introduced a performance regression,
and conversely demonstrate performance improvement over time if you manage that.

---

## Conclusions

<div width="33%" style="float: left; padding-left: -12px;">

- Write code for:
  - Non-specialist RSEs
  - Future students
  - Your future self
  
</div>

<div width="33%" style="float: left; padding-left: 24px;">

- Help them to:
  - Run
  - Read
  - Modify
  - Test

</div>

<div width="33%" style="float: left; padding-left: 32px;">

- Do this via
  - READMEs
  - Technical documentation
  - Inline documentation
  - Automatic code formatting
  - Automated testing
  - Continuous integration
  - Continuous benchmarking

</div>

<div style="float: left; width: 100%; margin-top: 48px;">
This is less effort than you think!
</div>

-

## Upcoming events

- [CCP-TEPP Docathon: 2026-03-18&ndash;20, University of Warwick](https://indico.global/e/ccp-tepp-docathon-2026)
- [CCP-TEPP Summer School: 2026-06-29&ndash;2026-07-03, Swansea University](https://indico.global/e/ccp-tepp-school-2026)
