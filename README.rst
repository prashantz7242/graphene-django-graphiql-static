===============================
graphene-django-graphiql-static
===============================

Graphene-Django-GraphiQL-Static provides an offline-compatible GraphiQL web UI for Graphene-Django projects. It ensures uninterrupted GraphQL query exploration by serving all necessary assets locally, making it reliable even during internet outages.

Documentation
-------------

The full documentation is at https://github.com/prashantz7242/graphene-django-graphiql-static#readme.

Quickstart
----------

Install graphene-django-graphiql-static::

    pip install graphene-django-graphiql-static

Add it to your `INSTALLED_APPS`:

.. code-block:: python

    INSTALLED_APPS = (
        # Other installed apps
        'graphene_django_graphiql_static',
    )

Add ``graphene-django-graphiql-static``'s URL Patterns
======================================================

When using ``graphene-django-graphiql-static``, you should import the ``GraphiQLOfflineView`` provided by this package instead of the regular ``GraphQLView`` from ``graphene-django``.  

**Do Not Import** ``GraphQLView`` from ``graphene_django.views``:

.. code-block:: python

    # Incorrect import
    from graphene_django.views import GraphQLView

Instead, use the ``GraphiQLOfflineView`` provided by ``graphene-django-graphiql-static`` to enable offline-compatible GraphiQL:

.. code-block:: python

    # Correct import
    from graphene_django_graphiql_static.views import GraphiQLOfflineView

Below is an example of how to define your ``urlpatterns`` using ``GraphiQLOfflineView``:

.. code-block:: python

    from django.urls import path
    from django.views.decorators.csrf import csrf_exempt
    from graphene_django_graphiql_static.views import GraphiQLOfflineView

    urlpatterns = [
        # Other installed apps
        path(
            "graphql/",
            csrf_exempt(
                GraphiQLOfflineView.as_view(schema=gq_schema, graphiql=settings.DEBUG)
            ),
            name="graphql",
        ),
    ]

This ensures that your project uses the offline-compatible GraphiQL UI provided by ``graphene-django-graphiql-static`` and serves all necessary assets locally.


Features
--------

1. **Offline-Compatible GraphiQL UI**  
   Provides a fully functional GraphiQL web interface for exploring GraphQL queries and mutations, even when the internet connection is unavailable.

2. **Static Asset Hosting**  
   Serves all required assets (CSS, JavaScript) locally through Django's static files system, ensuring reliability and performance.

3. **Easy Integration with Graphene-Django**  
   Designed to seamlessly integrate with Graphene-Django projects, requiring minimal configuration.

4. **Improved Developer Experience**  
   Offers a consistent and uninterrupted development workflow for working with GraphQL APIs, independent of external asset CDNs.

5. **Customizable and Extendable**  
   Fully customizable to adapt to project-specific requirements while maintaining compatibility with Django’s template and static systems.

.. Running Tests
.. -------------

.. Does the code actually work?

.. ::

..     source <YOURVIRTUALENV>/bin/activate
..     (myenv) $ pip install tox
..     (myenv) $ tox


.. Development commands
.. ---------------------

.. ::

..     pip install -r requirements_dev.txt
..     invoke -l

