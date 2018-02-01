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
* pm2 >= 2.6.1

You can visit `Nodejs official website <https://nodejs.org/en/>`_ and `MariaDB <https://mariadb.org/>`_ to download.

Follow the `pm2 document <http://pm2.keymetrics.io/docs/usage/quick-start/>`_ to install it after installed nodejs.

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

#.  Setup and setup active directory (AD).

    User authentication will call AD API to verify all users when they are trying to login by mobile or website. 
    So, the backend will connect to AD and get user account and user group. 

    AD API run on internet infomation services (IIS). It is installed as normal website in IIS.

    *   **Configuration in AD API:**

        AD API will check the ``clientId`` when receiving a request, if the ``clientId`` match with the Id in configuration file the request is validate. Otherwise, it will failed.
        
        In Web.config, at ``<appSettings>`` section, change ``clientId`` with whatever ``clientId`` you want.

        .. code-block:: apache

                <add key="clientId" value="here is the cliendId"/>

    *   **Configuration AD in backend:**

        Fill in all AD API infomation in the ``default.json`` of backend.

        .. code-block:: json

                        "ADSettings": {
                                    "isUsing": true,
                                    "url": "the hosting of AD API",
                                    "port": port of the host (it is a number),
                                    "clientId": "here is the cliendId that define in AD API"
                                }

configuration and running backend
---------------------------------

Backend has 2 environment, one for testing environment and the other is production environment. It can enable or disable production in ``index.js``. Just comment out the code ``process.env.NODE_ENV = "production";`` to run it in testing environment.

Configuration consist of default and production. When it is in production environment, some of configuration sections in the production will be used.

It is simply to configuration backend, there many sections in configuration file.

    *   AppSettings: it is basic configuration for application

        restAPIPort: the port of the backend.

        loginExpire**: it is the time out of user. the default is 1 day.. You can select other.

         .. code-block:: json

                    "appSettings": {
                        "secretKey": "you can ignore it if don't want to change",
                        "applicationVersion": "1.0.0",
                        "restAPIPort": "it is the port of the backend will run on",
                        "loginExpire": "1d" // 1d, 10h, 2.5 hrs, 2 days, 1m, 5s, 1y, 100 (time formats to milliseconds)
                    }

        .. tip::

                Keep if as default if you don't want to change.


    *   Database: the configuration for database server (MariaBD)

    *   ADSettings was mentioned above.

    *   AppVersion: When the mobile app has new release, it will be upload to the folder and user can install new version.

        defaultName: the intaller file name.

        uploadFolder: the folder for uploaded intaller file.

        downloadLink: the link user can access and dowload new release.

        .. code-block:: json

                        "AppVersion": {
                            "defaultName": "EmpApp-Install",
                            "uploadFolder": "/your/upload/folder/here",
                            "downloadLink": "https://www.yourhost/download"
                        }








