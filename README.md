# OpenApiGeneration
A guide for creating an API using the OpenApi generator, using a OpenApi spec yaml file

        Requirements and Instillation guides:
             Apache Maven CLI tool: https://maven.apache.org/install.html
             openapi-generator-cli: https://openapi-generator.tech/docs/installation

* Clone this repository or copy the content of the YAML file into your directory of choice.
* Using a CLI in the directory you wish the source code to be generated and where the OpenApi.yaml file is located run the command 'openapi-generator-cli generate -i OpenApi.yaml -g spring -o .' 
    * If you wish to use a different application framework other than spring-boot change the type after the -g tag from spring 
    * If you wish to have the code generated somewhere other than the location of teh yaml file change the output path that follows the -o tag.
* Some calls to classes in the generated code contain some errors, these are located in the EnumConverterConfiguration.java class, these errors are to do with the importing of Partyinvolvementtypevalues and Partytypevalues, originally they will be imported with lowercase P at the begining of each class name, change this to uppercase. Do so to all references to the classes in the EnumConverterConfiguration class.
* In your CMD terminal run the command 'mvn clean spring-boot:run' 