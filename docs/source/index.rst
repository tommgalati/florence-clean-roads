Florence Clean Roads Docs
=========================


This API are developed to allow the comunication between the Android App *Florence Clean Roads* and his contextual server-side application hosted on *Heroku*.

.. contents::


User API
--------

Set of API useful for User interaction.


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

Set of API to retrieve data like Street list, Stretch list for a Street and the corresponding cleaning calendar object.


Ciy list
^^^^^^^^

Get the list of Cities managed by this app.

.. http:post:: /getCityList

    **Example request**:

    .. sourcecode:: http

        POST /getCityList HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Cities found",
            "data": {
              "CityList": [
                {
                  "City": {
                    "CityId": 1,
                    "CityName": "CAMPI BISENZIO"
                  }
                },
                ...
              ]
            }
          }
        }

    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem


Street list
^^^^^^^^^^^

Get the Street list for a City.

.. http:post:: /getStreetList

    **Example request**:

    .. sourcecode:: http

        POST /getStreetList HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Streets found",
            "data": {
              "CityName": "CAMPI BISENZIO",
              "StreetList": [
                {
                  "Street": {
                    "StreetId": 1586,
                    "StreetName": "PIAZZA ALDO MORO",
                    "StreetAliaId": 879,
                    "HasStretch": 2
                  }
                },
                ...
                {
                  "Street": {
                    "StreetId": 1836,
                    "StreetName": "VIA YURI GAGARIN",
                    "StreetAliaId": 1122,
                    "HasStretch": 0
                  }
                }
              ]
            }
          }
        }

    :param cityId: city id, received calling the */getCityList* method
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Stretch list
^^^^^^^^^^^^

Get the Stretch list for a Street.
If a Street does not contain any Stretch, an error message is given.

.. http:post:: /getStretchList

    **Example request**:

    .. sourcecode:: http

        POST /getStretchList HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Stretch found",
            "data": {
              "StreetName": "BORGO ALLEGRI",
              "StretchList": [
                {
                  "Stretch": {
                    "StretchId": 1,
                    "StretchName": "DA AGNOLO A PIETRAPIANA"
                  }
                },
                ...
              ]
            }
          }
        }

    :param streetId: street id, received calling the */getStreetList* method
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Find similar Street
^^^^^^^^^^^^^^^^^^^

Find a Street given its name and City. It performs a Levenshtein distance.
Returns Street cleaning schedule if exists, or Stretch list if the Street contains any stretch.

.. http:post:: /findSimilarStreet

    **Example request**:

    .. sourcecode:: http

        POST /findSimilarStreet HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Cleaning found",
            "data": {
              "NextCleaningCalendar": "java.util.GregorianCalendar[time=?,areFieldsSet=false,areAllFieldsSet=true,
                      lenient=true,zone=sun.util.calendar.ZoneInfo[id=\"Europe/Rome\",offset=3600000,dstSavings=3600000,
                      useDaylight=true,transitions=169,lastRule=java.util.SimpleTimeZone[id=Europe/Rome,offset=3600000,
                      dstSavings=3600000,useDaylight=true,startYear=0,startMode=2,startMonth=2,startDay=-1,startDayOfWeek=1,
                      startTime=3600000,startTimeMode=2,endMode=2,endMonth=9,endDay=-1,endDayOfWeek=1,endTime=3600000,
                      endTimeMode=2]],firstDayOfWeek=2,minimalDaysInFirstWeek=4,ERA=1,YEAR=2017,MONTH=8,WEEK_OF_YEAR=39,
                      WEEK_OF_MONTH=3,DAY_OF_MONTH=21,DAY_OF_YEAR=264,DAY_OF_WEEK=5,DAY_OF_WEEK_IN_MONTH=3,AM_PM=0,HOUR=6,
                      HOUR_OF_DAY=6,MINUTE=0,SECOND=13,MILLISECOND=177,ZONE_OFFSET=3600000,DST_OFFSET=3600000]",
              "TextToShow": "Ogni Giovedì pari del mese dalle 00.00 alle 06.00"
            }
          }
        }

    :param cityName: city name, received from Google Maps API
    :param streetName: street name, received from Google Maps API
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Street Cleaning schedule
^^^^^^^^^^^^^^^^^^^^^^^^

Get the cleaning schedule for a Street.
If the Street contains one or more Stretches, the Stretches list is returned.

.. http:post:: /getStreetCleaning

    **Example request**:

    .. sourcecode:: http

        POST /getStreetCleaning HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Cleaning found",
            "data": {
              "NextCleaningCalendar": "java.util.GregorianCalendar[time=?,areFieldsSet=false,areAllFieldsSet=true,
                      lenient=true,zone=sun.util.calendar.ZoneInfo[id=\"Europe/Rome\",offset=3600000,dstSavings=3600000,
                      useDaylight=true,transitions=169,lastRule=java.util.SimpleTimeZone[id=Europe/Rome,offset=3600000,
                      dstSavings=3600000,useDaylight=true,startYear=0,startMode=2,startMonth=2,startDay=-1,startDayOfWeek=1,
                      startTime=3600000,startTimeMode=2,endMode=2,endMonth=9,endDay=-1,endDayOfWeek=1,endTime=3600000,
                      endTimeMode=2]],firstDayOfWeek=2,minimalDaysInFirstWeek=4,ERA=1,YEAR=2017,MONTH=8,WEEK_OF_YEAR=39,
                      WEEK_OF_MONTH=3,DAY_OF_MONTH=21,DAY_OF_YEAR=264,DAY_OF_WEEK=5,DAY_OF_WEEK_IN_MONTH=3,AM_PM=0,HOUR=6,
                      HOUR_OF_DAY=6,MINUTE=0,SECOND=13,MILLISECOND=177,ZONE_OFFSET=3600000,DST_OFFSET=3600000]",
              "TextToShow": "Ogni Giovedì pari del mese dalle 00.00 alle 06.00"
            }
          }
        }

    :param streetId: street id, received calling the */getStreetList* method
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem

Stretch Cleaning schedule
^^^^^^^^^^^^^^^^^^^^^^^^^

Get the cleaning schedule for a Stretch.

.. http:post:: /getStretchCleaning

    **Example request**:

    .. sourcecode:: http

        POST /getStretchCleaning HTTP/1.1
        Host: https://florence-clean-roads.herokuapp.com/
        Accept: application/json, text/javascript

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
          "response": {
            "code": "0",
            "message": "Cleaning found",
            "data": {
              "NextCleaningCalendar": "java.util.GregorianCalendar[time=?,areFieldsSet=false,areAllFieldsSet=true,
                lenient=true,zone=sun.util.calendar.ZoneInfo[id=\"Europe/Rome\",offset=3600000,dstSavings=3600000,
                useDaylight=true,transitions=169,lastRule=java.util.SimpleTimeZone[id=Europe/Rome,offset=3600000,
                dstSavings=3600000,useDaylight=true,startYear=0,startMode=2,startMonth=2,startDay=-1,startDayOfWeek=1,
                startTime=3600000,startTimeMode=2,endMode=2,endMonth=9,endDay=-1,endDayOfWeek=1,endTime=3600000,
                endTimeMode=2]],firstDayOfWeek=2,minimalDaysInFirstWeek=4,ERA=1,YEAR=2017,MONTH=9,WEEK_OF_YEAR=41,
                WEEK_OF_MONTH=1,DAY_OF_MONTH=3,DAY_OF_YEAR=276,DAY_OF_WEEK=3,DAY_OF_WEEK_IN_MONTH=1,AM_PM=0,HOUR=6,
                HOUR_OF_DAY=6,MINUTE=0,SECOND=35,MILLISECOND=415,ZONE_OFFSET=3600000,DST_OFFSET=3600000]",
              "TextToShow": "Ogni Martedì pari del mese dalle 00.00 alle 06.00"
            }
          }
        }

    :param stretchId: stretch id, received calling the */getStretchList* method
    :statuscode 200: Response OK, check json "response.code" value

                        If 0:
                            response ok
                        If 1:
                            there's a problem



