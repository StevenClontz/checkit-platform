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
funcionality and frequent users of the Dashboard may benefit from creating an account.

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
