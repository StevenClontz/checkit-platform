# CheckIt Platform

The CheckIt Platform supports authoring randomized exercises for use in
student practice and assessment, and outputs formats that can be used in a
variety of contexts including LaTeX documents and LMS quizzes.

The platform includes the following apps.

## Viewer

The CheckIt Viewer is made available to the public at <https://checkit.clontz.org>.
This fully-Javascript app ingests JSON banks produced by the CheckIt Dashboard
and displays several examples of each learning outcome. When instructor features are enabled,
the source code for each exercise in various formats is made available, and randomized
assessments may be compiled in LaTeX format.

No accounts or subscriptions are necessary to use the full power of the CheckIt Viewer.

- [CheckIt Viewer on GitHub](https://github.com/StevenClontz/checkit-svelte)

## Dashboard

- Quickstart instructions:
    - [Open this CoCalc project in your browser](https://cocalc.com/share/00854508a0fa6e8a193cbc90aff10b9dd7f446b4/checkit/?viewer=share)
    - Click the green "Open with one click!" button and let the project load.
    - Open `dashboard.ipynb` and **▶ Run** the code cell to access the graphical user interface.

The CheckIt Dashboard is a Python application that reads code from CheckIt outcome banks
(see below) and produces files that can be read by the CheckIt Viewer or imported into
a supported LMS.

This dashboard is optimized for use on the [CoCalc](https://cocalc.com) web app and may
be used via the quickstart instructions above without creating an account or purchasing
a subscription to any service. However, the CoCalc free trial is limited in its
functionality and frequent users of the Dashboard may benefit from creating an account.

- [CheckIt Dashboard on GitHub](https://github.com/StevenClontz/checkit)

## Library

The following outcome banks are made available via the CheckIt Viewer and included by default
in the Checkit Dashboard on CoCalc.

- [Differential Equations (Clontz)](https://github.com/StevenClontz/checkit-clontz-diff-eq)
- [Linear Algebra for Team-Based Inquiry Learning](https://github.com/TeamBasedInquiryLearning/checkit-tbil-la)

## Community

Our community of authors and developers is organized in the #checkit-app channel of the
[Mastery Grading Slack workspace](https://bit.ly/join-mastery-grading).
We're also on Twitter [@CheckItProblems](https://twitter.com/CheckItProblems).
Come join the conversation!

### 2021 Summer Authoring Workshop

The community will gather on Zoom this summer between June 7-10 for a free workshop
aimed at getting new CheckIt authors up and running with the platform. Registration is
now closed.

#### Workshop Outline

We will meet using Zoom from 9-12 and 1-4 Central Daylight Time on June 7-9.
Check your email for the Zoom link.

On Monday, we will focus on introducing everyone to the platform and getting everyone set up to use the free CoCalc.com cloud environment to author CheckIt exercises. 

- **Volunteers needed:** I'd like to limit the 9-12 morning block to a small subset of folks to serve as "trainers". Then we can split into breakout rooms to get all participants up to speed in small groups during the 1-4 block. You're likely a good fit for this role as long as you have a basic idea of how to write Python code.

On Tuesday, we will work in groups to develop CheckIt exercises for single-variable calculus and linear algebra. These exercises will be used to support the https://sites.google.com/southalabama.edu/tbil NSF project on Team-Based Inquiry Learning (TBIL) that's funding me this summer. As part of that work, my team will be curating a collection of learning outcomes and sample exercises aligned to those outcomes. So for the workshop, participants will work together in small groups to create CheckIt versions of these exercises. Since these exercises will be well-defined going into the workshop, we'll be able to spend Tuesday focusing on the technical training of how to use the CheckIt Dashboard. These exercises will be available for use by anyone (not just TBIL participants) this fall.

On Wednesday, we will form ad hoc working groups to begin development of CheckIt banks for other courses (and those who are interested can continue work on calculus and linear algebra as needed). Ultimately, my goal is that every participant will at least be enabled by the end of Wednesday to develop CheckIt banks for their personal use, but also connect folks together to develop community-maintained banks that can be made available to the public in addition to the work we'll produce Tuesday.

We will have 50-minute presentations and/or discussions at 9am and 1pm each day. Some of that will be direct training, but other topics will include mastery grading (a common use-case for the CheckIt platform), feature requests for the platform, a vision for our community and the workflow for peer review of public banks, and possible scholarship/funding opportunities related to this work.

- **Volunteer needed:** would anyone like to lead the presentation on mastery grading? This can be a rehash of a presentation you've given for other audiences.

*Email <sclontz@southalabama.edu> if you are participating in the workshop and can volunteer for a role described above.*
