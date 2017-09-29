.. title:: Scaffolding

Scaffolding
===========

Virtual Machine
---------------

Most of the local development is done under a local Virtual Machine powered by `Vagrant`_, it uses
a basic LAMP stack that mimics the Staging and Live servers so every environment is similar to
minimize cross platform issues.

The VM's configuration can be downloaded from `Github`_ and with instructions on how to use it as
well.

.. _Vagrant: https://www.vagrantup.com/
.. _Github: https://github.com/jahvi/vagrant-vm

Setup
-----

All Magento 1 websites are built on top of a `base package theme`_ that includes multiple plugins
and customizations that are used in every e-commerce store.

.. _base package theme: https://bitbucket.org/medialounge_repo/2015ml

The following checklist can be used as a guideline to setup a new Magento site in all environments:

Local
~~~~~

1. Create a repository for the new site in Bitbucket.
2. Clone the base package theme into the local machine.
3. Add the project repository as a remote branch.
4. Create a new branch pointing to the base package theme, this will help pull changes from it easily.
5. Change the **skin** and **design** theme folder names to match the project's.
6. Commit the changes and make first push to the bitbucket repository.

Staging
~~~~~~~

1. Create new subdomain using the project name, make sure to point it to the projects folder.
2. Create a new database for the new project, usually named **mldemoco_projectname**.
3. Import database from **mldemoco_2015ml** to the new **mldemoco_projectname** database.
4. Change table prefixes to match the new project name.
5. Change site url in **core_config_data** table.
6. Export database and import it on the local version.

Deployment
~~~~~~~~~~

1. Link new repository in deploy bot.
2. Create a new environment and set up pointing to the subdomain folder in the staging server.
3. Make sure to create a new **local.xml** as a static file with the staging database credentials.
4. Deploy first batch of files.

The process to deploy changes is outlined in detail in the :doc:`../deployment` section.

Module Generator
----------------

For Magento projects it's useful to be able to create custom modules quickly, the
`Magento Module Generator`_ powered by `Yeoman`_ is used to create the folder structure for Magento
extensions as well as intial configuration files that might be depended upon.

The geenrator can be installed from `npm`_ using the following commands:

.. code-block:: bash

    npm install -g yo
    npm install -g generator-magento-module

Then generate each extension with:

.. code-block:: bash

    yo magento-module

.. figure:: /_static/terminal.png
    :align: center

    Prompt screen of Magento Module Generator.

.. _Magento Module Generator: https://github.com/jahvi/generator-magento-module
.. _Yeoman: http://yeoman.io/
.. _npm: https://www.npmjs.com/
