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

- Before the Workshop
    - [YouTube tutorial on the CheckIt Platform](https://youtu.be/W4_zEmmSDIs)
    - <https://github.com/StevenClontz/checkit-platform/blob/main/generators.md>
    - <https://github.com/StevenClontz/checkit-platform/blob/main/templates.md>
- Monday June 7
    - Check email for a survey with your availablity to attend one of the following
      sessions.
    - 9:00-10:30 Welcome Q&A Session 1
        - Chrissy S
        - Jean-Sebastien T
        - Abby N
        - Neil M
        - Meredith S
        - Jeff F
    - 10:45-11:45 Welcome Q&A Session 2
        - Tien C
        - Katie A
        - Jennifer N
        - Dave R
        - Justin A
        - Briana B
    - 1:00-2:30 Welcome Q&A Session 3
        - Reeve H
        - Kate O
        - Peter K
        - Sarah N
        - Spencer B
        - Sharona K
    - 2:45-3:45 Welcome Q&A Session 4
        - Laura K
        - Hanna B
        - Christine L
        - Theron H
        - Erin K
- Tuesday June 8
    - 9:00-9:50
        - Mastery Grading and the CheckIt Platform
        - Presentation by Sharona Krinsky
    - 10:00-noon
        - Working groups on Calculus bank
    - 1:00-1:50
        - Feature requests for CheckIt Platform
        - Open Discussion
    - 2:00-4:00
        - Working groups on Calculus bank
- Wednesday June 9
    - 9:00-9:50
        - CheckIt Community and Peer Review
        - Open Discussion
    - 10:00-noon
        - Form working groups to collaborate on other CheckIt banks
    - 1:00-1:50
        - Scholarship and Funding related to the CheckIt Platform
        - Open Discussion
    - 2:00-4:00
        - Continue working groups on other CheckIt Banks
