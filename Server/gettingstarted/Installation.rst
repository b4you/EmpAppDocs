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

#.  Setup and config active directory (AD).

    User authentication will call AD API to verify all users when they are trying to login by mobile or website and users have a role base on AD Group. 
    So, the backend will connect to AD and get user account and user group. 

    AD API run on internet infomation services (IIS). It is installed as normal website in IIS.

    * Configuration in AD API:

        AD API will check the ``clientId`` when receiving a request, if the ``clientId`` match with the Id in config file the request is validate. Otherwise, it will failed.
        
        In Web.config, at ``<appSettings>`` section, change ``clientId`` with whatever ``clientId`` you want.

        .. code-block:: apache
        
                <add key="clientId" value="here is the key"/>

    * Configuration AD in backend:

        Fill in all AD API infomation in the ``default.json`` of backend.

        .. code-block:: json

                        "ADSettings": {
                        "isUsing": true,
                        "url": "the hosting of AD API",
                        "port": port of the host (it is a number),
                        "clientId": "here is the key that config in AD API"
                    }









