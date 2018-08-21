.. author:: Tobias Stahn <info@tstahn.io>
.. highlight:: console

.. sidebar:: Logo

  .. image:: _static/images/typo3.png
      :align: center

#########
TYPO3 CMS
#########

`TYPO3 CMS`_ is an Open Source Enterprise Content Management System licensed under `GPL v2`_ and provides the basis for
more than 500.000 websites, intranets and other web applications worldwide.

First released in 1997 by Kasper Skårhøj, a Danish developer, when the term "Content Management" was still widely
unknown, it is represented today by the `TYPO3 Association`_ responsible for coordinating and funding the further
development of the platform.

----

.. note:: For this guide you should be familiar with the basic concepts of

  * PHP_
  * MySQL_
  * composer_
  * domains_

Prerequisites
=============

We're using PHP_ in the stable version 7.1:

::

 [isabell@stardust ~]$ uberspace tools version show php
 Using 'PHP' version: '7.1'
 [isabell@stardust ~]$

.. include:: includes/my-print-defaults.rst`

Your website domain needs to be set up:

.. include:: includes/web-domain-list.rst

Installation
============

``cd`` into the directory above your document root ``/var/www/virtual/$USER/`` and create a new project based on the
typo3/cms-base-distribution using composer_.

::

 [isabell@stardust ~]$ cd /var/www/virtual/$USER/
 [isabell@stardust isabell]$ composer create-project typo3/cms-base-distribution typo3-cms 8.7
 Installing typo3/cms-base-distribution (8.7.0)
   - Installing typo3/cms-base-distribution (8.7.0): Downloading (100%)
 Created project in typo3-cms
 Loading composer repositories with package information
 Updating dependencies (including require-dev)
 [...]
 [isabell@stardust isabell]$

Since TYPO3 8.7 provides the subdirectory ``web/`` as document root when installed via composer, we need to
remove the default `document root`_ and create a symlink to the typo3/cms-base-distributions document root instead.

::

 [isabell@stardust ~]$ cd /var/www/virtual/$USER/
 [isabell@stardust isabell]$ rm -rf html
 [isabell@stardust isabell]$ ln -s /var/www/virtual/$USER/typo3-cms/web html
 [isabell@stardust isabell]$

Configuration
=============

Step 1
------

Point your browser to your website URL and append ``/typo3`` (e.g. isabell.uber.space/typo3). You will be greeted with a
"Thank you for downloading" message.

Step 2
------

Create an empty file ``FIRST_INSTALL`` inside your document root and reload the page. You will be redirected to the
TYPO3 Install Tool which will guide you through the remaining steps.

::

 [isabell@stardust ~]$ cd /var/www/virtual/$USER/html
 [isabell@stardust isabell]$ touch FIRST_INSTALL

.. note:: In case you have problems in your environment, you will get warnings or hints in this screen. In this case, you should try to fix them. For the purpose of this guide we assume there are none.

Step 3
------

Enter your database credentials_, keep the other settings unchanged, they are correct as they are.

Step 4
------

Create an additional_ database - for example: `isabell_typo3`.

Step 5
------

Enter a username and password for your first TYPO3 admin user (the password will also be configured for the Install Tool).

.. note:: For security reasons it's best to **not** use the name admin.

Choose a "site name" which will identify this installation (in the page tree and browser title).

Step 5
------

In the last step you may choose whether you want to start with an empty TYPO3 installation (no pages, templates,
configuration) or if you want to have a preconfigured basis to start from.

----

The basic installation procedure is complete, TYPO3 will be working and the most appropriate settings will have been
made for you at this point. You will get redirected to the Backend and can log in with your admin user account.

If you wish to make changes to your installation at a later stage, use the `Install Tool`_.

For further details, please have a look at the official `installation guide`_.

Updates
=======

Subscribe to the `TYPO3 Announce`_ mailing list to get regular updates regarding TYPO3 releases and security bulletins.

.. note:: This is a read-only mailing list, so you can neither reply nor post any messages yourself.

You may also refer to the official Twitter account `@typo3_security`_ to stay up-to-date on security advisories.

If you have any questions or want to contribute join the `TYPO3 Slack`_.


.. _TYPO3 CMS: https://typo3.org/
.. _GPL v2: https://www.gnu.org/licenses/gpl-2.0.html
.. _TYPO3 Association: https://typo3.org/project/association/`
.. _PHP: http://www.php.net/
.. _MySQL: https://manual.uberspace.de/en/database-mysql.html
.. _composer: https://get.composer.org/
.. _domains: https://manual.uberspace.de/en/web-domains.html
.. _document root: https://manual.uberspace.de/en/web-documentroot.html
.. _credentials: https://manual.uberspace.de/en/database-mysql.html#login-credentials
.. _additional: https://manual.uberspace.de/en/database-mysql.html#additional-databases
.. _Install Tool: https://docs.typo3.org/typo3cms/InstallationGuide/In-depth/TheInstallTool/Index.html#the-install-tool-in-depth
.. _installation guide: https://docs.typo3.org/typo3cms/InstallationGuide/Index.html
.. _TYPO3 Announce: http://lists.typo3.org/cgi-bin/mailman/listinfo/typo3-announce
.. _@typo3_security: https://twitter.com/typo3_security
.. _TYPO3 Slack: https://typo3.slack.com/

----

Tested with TYPO3 8.7 LTS and Uberspace 7.1.1

.. authors::
