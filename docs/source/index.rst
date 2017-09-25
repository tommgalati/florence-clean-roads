Florence Clean Roads Docs
=========================


This API are developed to allow the comunication between the Android App *Florence Clean Roads* and his contextual server-side application.

.. contents::


User API
--------

Registration
^^^^^^^^^^^^

Sign up a new user.

.. http:post:: /addUser

    **Example request**:

    .. sourcecode:: http

        POST /addUser HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "User inserted",
            "data": null
          }
        }

    :param email: user email
    :param password: md5 encoded password
    :param name: user nicename
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem


Login
^^^^^

Sign in an existing user.

.. http:post:: /login

    **Example request**:

    .. sourcecode:: http

        POST /addUser HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "User logged",
            "data": {
              "userData": {
                "id": 1,
                "name": "tommgalati",
                "email": "tommasogalati01@gmail.com",
                "carPositionLat": 12.45678,
                "carPositionLong": 34.56884,
                "notification": "{}"
              }
            }
          }
        }

    :param email: user email
    :param password: md5 encoded password
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Favorite Streets
^^^^^^^^^^^^^^^^

Manage User favorite Street list.

Add street to favorites
"""""""""""""""""""""""

Add a Street to User favorite list.

.. http:post:: /addFavStreet

    **Example request**:

    .. sourcecode:: http

        POST /addFavStreet HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Street added to User list",
            "data": null
          }
        }

    :param userId: user id, received during login
    :param streetId: street id, not Alia ID
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Favorite streets list
"""""""""""""""""""""

Get User favorite Street list.

.. http:post:: /getFavStreet

    **Example request**:

    .. sourcecode:: http

        POST /getFavStreet HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Street list",
            "data": {
              "StreetList": [
                {
                  "Street": {
                    "StreetId": 1,
                    "StreetName": "PIAZZA ALDO MORO",
                    "CityId": 1
                  }
                },
                {
                  "Street": {
                    "StreetId": 2,
                    "StreetName": "PIAZZA ANTONIO GRAMSCI",
                    "CityId": 1
                  }
                }
              ]
            }
          }
        }

    :param userId: user id, received during login
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Notifications
^^^^^^^^^^^^^

Manage User notification settings.

Save notification settings
""""""""""""""""""""""""""

Set notification for a User.

.. http:post:: /setNotification

    **Example request**:

    .. sourcecode:: http

        POST /setNotification HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Notification setted",
            "data": null
          }
        }

    :param userId: user id, received during login
    :param notification: JSON containing notification settings
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Get notification settings
"""""""""""""""""""""""""

Get notification JSON for a User.

.. http:post:: /getNotification

    **Example request**:

    .. sourcecode:: http

        POST /getNotification HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Notification found",
            "data": {
              "Notification": "{}"
            }
          }
        }

    :param userId: user id, received during login
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Last Park
^^^^^^^^^

Manage User coordinates about the last place where he left auto.

Set last park
"""""""""""""

Set last park coordinates.

.. http:post:: /setMyCar

    **Example request**:

    .. sourcecode:: http

        POST /setMyCar HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Car position setted",
            "data": null
          }
        }

    :param userId: user id, received during login
    :param carLat: latitude
    :param carLon: longitude
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Get last park
"""""""""""""

Get last park coordinates.

.. http:post:: /getMyCar

    **Example request**:

    .. sourcecode:: http

        POST /getMyCar HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Car found",
            "data": {
              "Position": {
                "Lat": 12.45678,
                "Long": 34.56884
              }
            }
          }
        }

    :param userId: user id, received during login
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem


City API
--------


