DemoApp
=======

Demostrate django app which can integrate with Apache Superset

Settings
--------

Moved to settings_.

.. _settings: http://cookiecutter-django.readthedocs.io/en/latest/settings.html

Getting started
--------------

This application development is done within Docker containers. It should be quick to get up and running with the application.

`docker-compose -f local.yml up`
DB migration is already taken care of., So no need to execute them.

On a different terminal, execute management commands:
````
docker-compose -f local.yml run --rm django python manage.py createsuperuser
#django is the django app container name
````

Setting Up Your Users
---

* To create a **normal user account**, just go to Sign Up and fill out the form. Once you submit it, you'll see a "Verify Your E-mail Address" page. Go to your console to see a simulated email verification message. Copy the link into your browser. Now the user's email should be verified and ready to go.

* To create an **superuser account**, use this command::

    $ python manage.py createsuperuser

For convenience, you can keep your normal user logged in on Chrome and your superuser logged in on Firefox (or similar), so that you can see how the site behaves for both kinds of users.

Superset database initialization
---

On AWS EC2 or linux instance, need to grant write access to superset data directory
`chmod 777 superset-conf/data`

Superset needs to initialize the database and create admin user account. Please execute the following command

`docker exec -it django-demo-project_superset_1 superset-init`

django-demo-project_superset_1 - this is name generated automatically based on our local.yml

If you like to load examples:
`docker exec -it django-demo-project_superset_1 superset load_examples`

#### Connecting superset with external postgres


In datasources, add following SQLAlchemy URI : 
`postgresql://debug:debug@postgres:5432/demoapp`

##### Command line connection to docker postgres 
`psql -h localhost -U debug -d demoapp`


Test coverage
---

To run the tests, check your test coverage, and generate an HTML coverage report::

    $ coverage run manage.py test
    $ coverage html
    $ open htmlcov/index.html

Running tests with py.test
~~~~~~~~~~~~~~~~~~~~~~~~~~

::

  $ py.test

Live reloading and Sass CSS compilation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Moved to `Live reloading and SASS compilation`_.

.. _`Live reloading and SASS compilation`: http://cookiecutter-django.readthedocs.io/en/latest/live-reloading-and-sass-compilation.html




Email Server
^^^^^^^^^^^^

In development, it is often nice to be able to see emails that are being sent from your application. For that reason local SMTP server `MailHog`_ with a web interface is available as docker container.

Container mailhog will start automatically when you will run all docker containers.
Please check `cookiecutter-django Docker documentation`_ for more details how to start all containers.

With MailHog running, to view messages that are sent by your application, open your browser and go to ``http://127.0.0.1:8025``

.. _mailhog: https://github.com/mailhog/MailHog



Deployment
----------

The following details how to deploy this application.



Docker
^^^^^^

See detailed `cookiecutter-django Docker documentation`_.

.. _`cookiecutter-django Docker documentation`: http://cookiecutter-django.readthedocs.io/en/latest/deployment-with-docker.html



