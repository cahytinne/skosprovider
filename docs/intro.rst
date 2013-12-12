.. _introduction:

Introduction
============

Skosprovider provides an interface that can be included in an application to 
allow it to talk to different :term:`SKOS` vocabularies. These vocabularies could be
defined locally or accessed remotely through webservices.

Adhering to this interface in you application decouples your application and the
actuals thesaurus. This makes unit testing easy because it allows you to swap
a remote and a local implementation. It also makes it easy to switch from a 
simple, static implementation based on a csv file to a more complete implementation
using you relation database.

One of the main goals of this project is to be able to build an application that
can use thesauri or vocabularies without knowing upfront what these might be
or where they might come from. This could be for an application that allows
cataloguing things, but where it can be expected that different instances will
require different thesauri or would need to be able to talk to existing vocabulary
systems.

Some sample providers are present in this package. The :class:`skosprovider.providers.DictionaryProvider` 
uses a simple python dict as the datastore. It can be considered the reference
implementation for the :class:`skosprovider.providers.VocabularyProvider` interface. 
Most likely you will want to implement a provider for your own SKOS, vocabulary or 
thesaurus system.

Currently the following other providers exist:
 
* `Skosprovider_oe <https://github.com/koenedaele/skosprovider_oe>`_: This 
  provider implements the :class:`skosprovider.providers.VocabularyProvider` 
  interface for the thesauri attached to the 
  `Inventaris Onroerend Erfgoed <https://inventaris.onroerenderfgoed.be/thesaurus>`_.
  This provider also demonstrates making the switch from a term based thesaurus
  to a concept based one.
* `Skosprovider_sqlalchemy <http://skosprovider-sqlalchemy.readthedocs.org/en/latest/>`_: 
  An implementation of the 
  :class:`VocabularyProvider <skosprovider.providers.VocabularyProvider>` 
  interface with a `SQLAlchemy <http://www.sqlalchemy.org>`_ backend. This allows
  using a RDBMS for for reading but also writing :term:`SKOS` concepts.

Currently there also exists a library to integrate Skosprovider with
`Pyramid <http://www.pylonsproject.org/>`_ at 
`pyramid_skosprovider <https://github.com/koenedaele/pyramid_skosprovider>`_.