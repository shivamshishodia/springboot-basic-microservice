# Basic Spring Boot Microservice

A basic Spring Boot microservice. Please read all the comments properly. May start building a boiler-plate on top of this.

## Project Details

- **Specialization** Common exception handler for all controllers `basic.exceptions.CustomResponseExceptionHandler`.

- **Request Validations** Handled inside beans `basic.models.Users` with `@Valid` at the controller level. Refer `basic.exceptions.CustomResponseExceptionHandler.handleMethodArgumentNotValid`. Dependency required `spring-boot-starter-validation`.

- **HATEOAS** Allows you to add reference links with the response without hard-coding URIs. See `basic.resources.fetchOneUser` response having link to `basic.resources.fetchUsers` method. URIs are picked from the mappings automatically. Dependency required `spring-boot-starter-hateoas`.

- **Internationalization** Refer `basic.resources.internationalized` and `basic.resources.internationalizedContext` and all the `messages` property files. Make sure to include `Accept-Language` in request header.

- **Content Negotiation** While making the call ensure to add `Accept: application/xml` and it will return XML instead of JSON. Dependency required `com.fasterxml.jackson.dataformat`.

- **Swagger** Refer [springdoc-openapi](https://springdoc.org/) and include dependency `org.springdoc`. Swagger UI located at [swagger-ui](http://localhost:8080/swagger-ui.html). Swagger docs are located at [api-docs](http://localhost:8080/v3/api-docs). Provides server info, paths, schemas and components.

- **Actuator** Provides production read metrics, heap dumps, jvm, loggers, thread dumps, mapping, etc. Refer properties for wildcard web exposure. [actuator-docs](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html). Dependency added `spring-boot-starter-actuator`. [actuator-endpoint](http://localhost:8080/actuator)

- **HAL Explorer** Bundles features of Swagger UI and visualizes raw JSON such as `/actuator`. Dependency added `spring-data-rest-hal-explorer`. Just go to localhost:8080.

- **Static filtering** To ignore particular data members use @JsonIgnore or @JsonIgnoreProperties. Refer `basic.models.ConfigsStaticFilter` and `basic.models.Configs.FilteredResources`.

- **Dynamic Filtering** Filters are applied when the beans are fetched. Refer `basic.models.ConfigsDynamicFilter` and `basic.models.Configs.FilteredResources`.

- **Versioning** Different companies use different approaches. All are discussed under the `versioning` package.

- **Basic Authentication** Dependency required `spring-boot-starter-security`. Copy of the password displayed in the terminal when the service starts. Currently, the user and password is listed under property file. Make a request using this password and user as `user` under authorization > basic auth.

- **H2 database** Enable h2-console under property file and go to [h2-console](http://localhost:8080/h2-console). Refer `data.sql` under resource file. JDBC url should be set to `jdbc:h2:mem:testdb`.
