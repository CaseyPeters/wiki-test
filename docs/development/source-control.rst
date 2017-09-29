.. title:: Source Control

Source Control
==============

GIT is used to keep track of source files changes across all projects, the main
repo is setup in `Bitbucket`_ but some non-client work is hosted on `Github`_ as
well.

As a general rule commits should be made often and in smaller chunks this way it
becomes easier to revert a single piece of functionality by rolling back a single
commit.

Most of the time a single ``master`` branch is used for development unless working
on a very complex or *error prone* feature where a feature branch can be used instead
to keep the main branch clean.

Commit messages should be kept short and must contain a summary of the changes
included in that commit, if a longer description is needed it can be added to the
body of the commit message. A rule of **50/72** is used where the main summary
line should have no more than 50 characters and 72 characters for the body
if needed, for reference a good commit message should:

- Separate subject from body with a blank line
- Limit the subject line to 50 characters
- Capitalize the subject line
- Do not end the subject line with a period
- Use the imperative mood in the subject line
- Wrap the body at 72 characters
- Use the body to explain what and why vs. how

.. _Bitbucket: https://bitbucket.org/
.. _Github: https://github.com/
