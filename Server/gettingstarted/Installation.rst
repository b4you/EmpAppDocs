============
Installation
============

.. tip::

        The backend develop on nodejs, so it can be deployed on multi platform.

Requirements
------------

The most important requirements are:

* Nodejs >= 7.10.1
* MariaDB >= 5.5.56

You can visit `Nodejs official website <https://nodejs.org/en/>`_ and `MariaDB <https://mariadb.org/>`_ to download.


Fundamental Installation
------------------------
.. note::

        The backend requires ffmpeg and sharp plugin for videos and image processing.

#.  First you need to install ffmpeg to settle all videos before store it in server. You can download it in `official website <https://ffmpeg.org/>`_

    Please follow the `link <https://github.com/fluent-ffmpeg/node-fluent-ffmpeg>`_ to install ffmpeg can run with nodejs.

#.  Backend need to process uploading image and save it. So, it use sharp plugin to do image processing.

    Please follow the `link <http://sharp.dimens.io/en/stable/install/>`_ to install environment for it.

.. tip::

        Just follow the `Prerequisites <http://sharp.dimens.io/en/stable/install/#prerequisites>`_ in the `link <http://sharp.dimens.io/en/stable/install/>`_

#.  Push notification processing

    The mobile part will have push notification. 
    The backend use `OneSignal <https://onesignal.com/>`_ to handle it. Just come to the `OneSignal website <https://onesignal.com/>`_. Register an account and reconfig in the configuaraion file in backend

.. tip::

        OneSignal is a free push notification service designed for multiple platform. 





