.. _example_setup_drupal:

************
Setup Drupal
************

This example will use ``drush`` to install Drupal from within the PHP container.

.. seealso:: `Official Drupal Documentation <https://www.drupal.org/docs/7/install>`_


**Table of Contents**

.. contents:: :local:


Overview
========

The following configuration will be used:

+--------------+--------------------------+-------------+------------+-----------------------+
| Project name | VirtualHost directory    | Database    | TLD_SUFFIX | Project URL           |
+==============+==========================+=============+============+=======================+
| my-drupal    | /shared/httpd/my-drupal  | my_drupal   | loc        | http://my-drupal.loc  |
+--------------+--------------------------+-------------+------------+-----------------------+


Walk through
============

It will be ready in six simple steps:

1. Enter the PHP container
2. Create a new VirtualHost directory
3. Install Drupal via ``drush``
4. Symlink webroot directory
5. Setup DNS record
6. Visit http://my-drupal.loc in your browser


.. seealso:: :ref:`available_tools`


1. Enter the PHP container
--------------------------

.. code-block:: bash

   host> ./shell.sh

.. seealso:: :ref:`tutorial_work_inside_the_php_container`


2. Create new vhost directory
-----------------------------

.. code-block:: bash

   devilbox@php-7.0.20 in /shared/httpd $ mkdir my-drupal


3. Install Drupal
-----------------

.. code-block:: bash

   devilbox@php-7.0.20 in /shared/httpd $ cd my-drupal
   devilbox@php-7.0.20 in /shared/httpd/my-drupal $ drush dl drupal


4. Symlink webroot
------------------

.. code-block:: bash

   devilbox@php-7.0.20 in /shared/httpd/my-drupal $ ln -s drupal-8.3.3/ htdocs


5. DNS record
-------------

If you do not have :ref:`global_configuration_auto_dns` configured, you will need to add the
following line to your host operating systems ``/etc/hosts`` file
(or ``C:\Windows\System32\drivers\etc`` on Windows):

.. code-block:: bash
   :caption: /etc/hosts

   127.0.0.1 my-drupal.loc

.. seealso::
   For in-depth info about adding DNS records on Linux, Windows or MacOS see:
   :ref:`project_configuration_dns_records` or :ref:`global_configuration_auto_dns`.


6. Open your browser
--------------------

Open your browser at http://my-drupal.loc and follow the Drupal installation steps.

.. note::
   When asked about MySQL hostname, choose ``127.0.0.1``.
