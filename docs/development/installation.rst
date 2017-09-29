.. title:: Installation

Installation
============

For Magento projects there is a base *package theme* that is used as a starting template for all
websites. The code is available in the repo and the initial database configuration is setup in the
Staging server.

This base theme is always evolving and open to changes so it's recommended that it's cloned from the
repo for every new project, then adding a new ``git remote`` pointing to the repository of the
individual project. That way the *package theme* remote can be used to update the project when it
changes without having to manually go through them every time, eg:

.. code-block:: bash

    # Clone *package theme*
    git clone git@bitbucket.org:medialounge_repo/2015ml.git
    cd 2015ml

    # Rename files/folders and setup database...

    # Add new project-specific remote
    git remote add project git@bitbucket.org:medialounge_repo/project.git

    # Update project repo
    git push -u project master

    # If the *package theme* is updated fetch changes from remote
    git pull origin master


Besides having a few extensions pre-installed it is a normal Magento installation, there are a few
things to keep in mind when starting on new projects:

- Use a database prefix, usually a combination of the first few letters of the project name plus an
  underscore character (_).
- Rename the ``ml/2015ml`` theme to a relevant name.
