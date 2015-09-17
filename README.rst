==============
Zinnia-twitter
==============

Zinnia-twitter is a package putting your entries on `Twitter`_.

Installation
============

* Install the package on your system: ::

  $ pip install zinnia-twitter

  `Tweepy`_ will also be installed as a dependency.

* Register the ``'zinnia_twitter'`` in your ``INSTALLED_APPS`` after the
  ``'zinnia'`` application.

* Define these following settings with your credentials:

  * ``TWITTER_CONSUMER_KEY``
  * ``TWITTER_CONSUMER_SECRET``
  * ``TWITTER_ACCESS_KEY``
  * ``TWITTER_ACCESS_SECRET``

* If you have enabled one of the ``zinnia-wysiwyg-xxx`` plugin widget, you
  need to reconstruct the ``EntryAdmin`` class manually with the provided
  mixins: ::

    from zinnia.admin.entry import EntryAdmin
    from zinnia_twitter.admin import EntryAdminTwitterMixin
    from zinnia_ckeditor.admin import EntryAdminCKEditorMixin

    class FinalEntryAdmin(EntryAdminCKEditorMixin,
                          EntryAdminTwitterMixin,
                          EntryAdmin):
        pass

    admin.site.unregister(Entry)
    admin.site.register(Entry, FinalEntryAdmin)

Note that the authentification for Twitter has changed since
September 2010. The actual authentification system is based on
oAuth. That’s why now you need to set these 4 settings. If you don’t know
how to get these information, go to:

https://apps.twitter.com/
https://apps.twitter.com/app/(app_number)/keys

Now in the admin, you can post an update containing your entry’s title and
the shortened URL of your entry.

.. _Twitter: https://twitter.com
.. _Tweepy: http://www.tweepy.org/
