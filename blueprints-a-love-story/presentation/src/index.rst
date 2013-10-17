:skip-help: true
:css: hovercraft.css

.. title:: Blueprints: A Love Story

Blueprints
==========

A Love Story

----

What's a Blueprint?
===================

    Blueprints are the recommended way to implement larger or more pluggable applications in Flask 0.7 and later.

    -- Flask source code

----

What's a Blueprint?
===================

    A Blueprint object works similarly to a Flask application object, but it is not actually an application. Rather it is a blueprint of how to construct or extend an application.

    -- Flask docs

----

What's a Blueprint?
===================

    Blueprints are "subapplications" that encapsulate related logic and the only way to sanely grow an application.

    -- Me

----

An Analogy to Django
====================

Flask Application ≅ Django Project

Blueprint ≅ Django Application

----

Why Use Blueprints?
===================

- Portable and reusable code
- Encourages manageable project structure
- Makes your code DRYer

----

How Flask Applications Grow
===========================

A single file containing most of your application code

----

How Flask Applications Grow
===========================

A few files representing your MVC structure

----

How Flask Applications Grow
===========================

Blueprints!
    - Models, views, and templates for each Blueprint
    - Blueprints get reused between applications

----

Examples
========

- The official `large app how to <https://github.com/mitsuhiko/flask/wiki/Large-app-how-to#first-view>`_

- Matt Wright's `notes <http://mattupstate.com/python/2013/06/26/how-i-structure-my-flask-applications.html#s2b>`_ and `examples <https://github.com/mattupstate/overholt/tree/master/overholt/api>`_ on the subject

----

Converting Your Code
====================

Change this:

.. code:: python

    from ..core import app

    ...

    @app.route('/users/')
    def user_list():
        ...

----

Converting Your Code
====================

To this:

.. code:: python

    from flask import Blueprint
    
    bp = Blueprint('users', __name__, template_folder='templates')

    ...

    @bp.route('/')
    def user_list():
        ...

----

Converting Your Code
====================

And add this:

.. code:: python

    from .users.views import bp as user_bp

    ...

    app.register_blueprint(user_bp, url_prefix='/users')

----

Considerations
==============

- What about my DB?

- My code depends on other blueprints!

----

Blueprints All The Way Down
===========================

- `Issue 593 <https://github.com/mitsuhiko/flask/issues/593>`_

- `Pull Request 750 <https://github.com/mitsuhiko/flask/pull/750>`_

----

:id: lastpage

FIN.
====

(Questions?)
