#CF MySQL Broker

CF MySQL Broker provides MySQL databases as a Cloud Foundry service.  This broker demonstrates the v2 services API between cloud controllers and service brokers. This API is not to be confused with the cloud controller API; for more info see [http://docs.cloudfoundry.com/docs/running/architecture/services/].

The broker does not include a MySQL server.  Instead, it is meant to be deployed alongside a MySQL server, which it manages.  These are the MySQL management tasks that the broker performs.

* Provisioning of database instances (create)
* Creation of credentials (bind)
* Removal of credentials (unbind)
* Unprovisioning of database instances (delete)

## Warning

####The new services API is still in progress and may change at any time.  Do not build a broker against this API.

## Running Tests

The CF MySQL Broker integration specs will exercise the catalog fetch, create, bind, unbind, and delete functions against its locally installed database.

1. Run a local install MySQL server.
  * Specs have only been tested with MySQL 5.6
  * Specs assume MySQL root user without a password
  * The anonymous user (User='' and Host='localhost') must be deleted (see [spec/spec_helper])
  * Specific innodb settings are required (see [spec/spec_helper])
    - innodb_stats_on_metadata = ON
    - innodb_stats_persistent = OFF

2. Run the following commands

```
$ cd cf-mysql-broker
$ bundle
$ bundle exec rake db:setup
$ bundle exec rake spec
```
