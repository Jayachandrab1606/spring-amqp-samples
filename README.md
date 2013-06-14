This is a sample project that shows how to use RabbitMQ with [Spring AMQP](http://github.com/SpringSource/spring-amqp) and [Cloud Foundry](http://www.cloudfoundry.com/).

The application uses Spring Java configuration and the [cloudfoundry-runtime](https://github.com/cloudfoundry/vcap-java/tree/master/cloudfoundry-runtime) library to get the credentials necessary to connect to a RabbitMQ service. See the [Cloud Foundry documentation](http://docs.cloudfoundry.com/docs/using/services/spring-service-bindings.html) for details on configuring a Spring application for Cloud Foundry using the cloudfoundry-runtime library, and the [connection configuration code](https://github.com/cloudfoundry-samples/spring-amqp-samples/blob/master/stocks/src/main/java/org/springframework/amqp/rabbit/stocks/config/AbstractStockAppRabbitConfiguration.java#L67) to see how this application is configured.

## Building and running locally ##

To build the web application, use the following commands:

    $ cd stocks
    $ mvn package

To run the application locally, you must first download, install, and run a [RabbitMQ](http://www.rabbitmq.com) server.
Once the server is up and running, use the following command to run the web application:

    $ mvn jetty:run

After the application starts, you can browse to `http://localhost:8080/spring-rabbit-stocks/`.

## Deploying to Cloud Foundry ##

After installing in the 'cf' [command-line interface](http://docs.cloudfoundry.com/docs/using/managing-apps/cf/) for Cloud Foundry, targeting a Cloud Foundry instance, and logging in, the application can be pushed using these commands:

    $ cd stocks
    $ mvn package
    $ cf push

The provided `manifest.yml` file will be used to provide the application parameters to Cloud Foundry. You may need to provide a different URL for the application if the `spring-stocks` URL is already being used in your Cloud Foundry domain.
