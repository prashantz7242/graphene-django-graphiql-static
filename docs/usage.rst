=====
Usage
=====

To use graphene-django-graphiql-static in a project, add it to your `INSTALLED_APPS`:

.. code-block:: python

    INSTALLED_APPS = (
        ...
        'graphene_django_graphiql_static.apps.GrapheneDjangoGraphiqlStaticConfig',
        ...
    )

Add graphene-django-graphiql-static's URL patterns:

.. code-block:: python

    from graphene_django_graphiql_static import urls as graphene_django_graphiql_static_urls


    urlpatterns = [
        ...
        url(r'^', include(graphene_django_graphiql_static_urls)),
        ...
    ]
