## overview

Feature toggles allow ElPaaso ops to dynamically (de)activate some experimental features

## usage

Feature toogles enable to selectively activate/enable features
They are implemented using [Togglz](http://www.togglz.org/) tool

###Using togglz web console (used dynamically)
Features can be enabled/disabled using the togglz admin console available under http://${elpaaso_webapp_url}/togglz
Only PaaS admin users can access toggles admin console

![Admin console](togglz_features_overview.png)

###Using ElPaaso config service (loaded at startup)
Features state can be initialized using PaaS configuration service by defining following properties:

    FEATURE1=true/false
    FEATURE1.users=user1, user2, ...

If the feature is not defined in config service, it will be disabledby default.
The user list properties is optional, if not defined or empty the feature is available for all users.