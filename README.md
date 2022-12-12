# OpenApiGeneration
A guide for creating an API using the OpenApi generator, using a OpenApi spec yaml file

        Requirements and Instillation guides:
             Apache Maven CLI tool: https://maven.apache.org/install.html
             openapi-generator-cli: https://openapi-generator.tech/docs/installation
             Postman:               https://www.postman.com/downloads/

* Clone this repository or copy the content of the YAML file into your directory of choice.
* Using a CLI in the directory you wish the source code to be generated and where the OpenApi.yaml file is located run the command `openapi-generator-cli generate -i OpenApi.yaml -g spring -o .` 
    * If you wish to use a different application framework other than spring-boot change the type after the -g tag from spring 
    * If you wish to have the code generated somewhere other than the location of the yaml file change the output path that follows the -o tag.
* Some calls to classes in the generated code contain some errors, these are located in the EnumConverterConfiguration.java class, these errors are to do with the importing of Partyinvolvementtypevalues and Partytypevalues, originally, they will be imported with lowercase P at the beginning of each class name, change this to uppercase. Do so to all references to the classes in the EnumConverterConfiguration class.
* In your CMD terminal while in the folder containing the generated code run the command `mvn clean spring-boot:run` 
* Once the application is running open your search engine of choice and search for `localhost:8080`, this will direct you to the swagger user interface, here you will be able to see all the functions provided by the API and the schemas used by the models.
* The current API will respond to all request that are formatted correctly with the expected JSON body and a 501 Not Implemented status.

**Testing**

If you want to test the passing of the Path variables continue, if not skip to step 3.
1. in the `CurrentAccountApi.java` class locate the *retrieve* method, edit the content of the exampleString variable to include the currentaccountid parameter.
- these changes should make the start of the exampleString look like `"{ \"CurrentAccountFacility\" : { \"ProductInstanceReference\" : \"" + currentaccountid + "\",` instead of `"{ \"CurrentAccountFacility\" : { \"ProductInstanceReference\" : \"ProductInstanceReference\",`
2. Test using the Postman collection given in this repository, the expected body contains a JSON text with `CurrentAccountFacility` as the top most object and all the nested objects having matching key pair values except the `ProductInstanceReference` field which should have the `currentAccountID` defined in the Path Variables as its value. 
3. Test using the Postman collection given in this repository, the expected body contains a JSON text with `CurrentAccountFacility` as the top most object and all the nested objects having matching key pair values. 

