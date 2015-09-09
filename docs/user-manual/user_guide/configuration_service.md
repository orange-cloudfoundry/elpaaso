## overview

The configuration service is an internal service that provides the ability to declare supported configuration properties that are made available for the application using env variables.

## usage

This section provides informations on how to configure a processing service to use the configuration service.

## programming model

In order to use the **configuration service**, you may use the *PropertySourcesPlaceholderConfigurer* from Spring 3.1 to hide from source of config injection. Here is [more information about this spring feature](http://www.baeldung.com/2012/02/06/properties-with-spring/).

When using *PropertySourcesPlaceholderConfigurer*, properties are looked up:

* first, in java environment (`-Dname=value`)
* then, if not found in the previous case, in system environment variable in El PaaSo config service,
* then, if not found in the previous case, in JNDI,
* then, if not found in the previous case, in the property file of the Spring config.

This allow you to externalize some properties using the config service from El PaaSo. You can also put default values in your Spring config's properties file, and occasionally overwrite properties with system properties.

### Config service restrictions

System environment variables name constraints differ from Java system properties: environment variables should not contain special characters except '_'. So, to be compliant, key name in config service should match this regular expression "[a-zA-Z_]+[a-zA-Z0-9_.]*" (i.e. a letter followed by some letters, some digits, some dot or some underscores).

By using Spring *PropertySourcesPlaceholderConfigurer*, it is transparent for developers. An automatic conversion is done by Spring while reading '_', a java property with '.' is also searched.

El PaaSo service config properties are exposed as system environment variables.

Link between config service and a Spring application:

El Paaso Config Service | Cloud Foundry | Key name (Spring Application)
----------------------- | ------------- | -----------------------------
**user.email**|user_email|**user.email**
userEmail|userEmail|userEmail
user_email|user_email|user_email

Link between config service and a Java application (no spring):

El Paaso Config Service|Cloud Foundry|Key name (Java Application)
-----------------------|-------------|---------------------------
**user.email**|user_email|**user_email**
userEmail|userEmail|userEmail
user_email|user_email|user_email


## application examples

### short example

In order to use the config service, you will need to follow three simple steps:

* first, declare the parameters of your application somewhere among:
    * El PaaSo config service
    * in a property file
    * using Cloud foundry CLI

            cf set-env <APPLICATION_NAME> admin.mail admin@orange.com
            cf set-env <APPLICATION_NAME> DEFAULT_INVOICE_DAY 5

    * using the `-D` parameter on the command line outside El PaaSo / Cloud Foundry

            admin.mail=admin@orange.com
            DEFAULT_INVOICE_DAY=5


* then use the `PropertySourcesPlaceholderConfigurer` from *Spring* with one of the following syntax:

        <context:property-placeholder location="classpath:parameter.properties" />

    or:

        <bean id="propertyConfigurer" class="org.springframework.context.support.PropertySourcesPlaceholderConfigurer">
            <property name="locations">
                <list>
                    <value>classpath:parameter.properties</value>
                </list>
            </property>
        </bean>

* finally, use the newly available parameters where you need it:

        @Value( "${admin.mail}" )
        private String adminMail;

    or:

        @SpringBean(name = "defaultInvoiceDay")
        private Integer INVOICE_DAY;

The spring bean has to be defined in the spring configuration of your application (here: `wicketContext.xml`):

    <bean name="defaultInvoiceDay" class="java.lang.Integer">
        <constructor-arg value="${DEFAULT_INVOICE_DAY}"></constructor-arg>
    </bean>

### full example with a wicket application

To enable `PropertySourcesPlaceholderConfigurer`, check that the spring configuration of the war module (usually `src/main/webapp/WEB-INF/spring-config`) is using the `PropertySourcesPlaceholderConfigurer`.

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

      <!-- load a config properties file at startup. Define page size and database -->
      <bean id="propertyConfigurer"
        class="org.springframework.context.support.PropertySourcesPlaceholderConfigurer">
        <property name="locations">
          <list>
            <value>classpath:parameter.properties</value>
          </list>
        </property>
      </bean>

    </beans>

You now have to change the jave code of your project so that your parameters are no longer set in your code, but are supported by the Spring framework.

The following java parameter defintion:

    private static final int LINES_PER_PAGE = 3;

is now changed to:

    @SpringBean(name = "marketLinesPerPage")
    private Integer LINES_PER_PAGE;

The spring bean has to be defined in the spring configuration of your application (here: `wicketContext.xml`):

    <bean name="marketLinesPerPage" class="java.lang.Integer">
        <constructor-arg value="${marketLinesPerPage}"></constructor-arg>
    </bean>

The spring bean should also be defined in your unit tests:

    mockApplication.getAppctx().putBean("marketLinesPerPage", new Integer(3));

You can now add a **config service** to your logical architecture and set the desired `key=value`:

    marketLinesPerPage=5

This parameter can also be overriden by setting parameters on the command line to the JVM at startup:

    Windows:
        set marketLinesPerPage=2

    Unix:
        export set marketLinesPerPage=2

    Cloud foundry:
        cf set-env <APPLICATION_NAME> marketLinesPerPage 2