# shopify-graphql

Some generated java classes for Shopify's graphql api.

Use at your own risk - we don't guarantee backwards compatibility between versions.

# Tools

We found three possible client libraries to generate this:

* https://github.com/apollographql/apollo-android
  * Gradle build doesn't run out of the box
  * Uses threads and callbacks and might not run on GAE
* https://github.com/graphql-java-generator/graphql-maven-plugin-project
  * Barfs on the input from shopify
* https://github.com/kobylynskyi/graphql-java-codegen-maven-plugin
  * Just generates the models... but that will have to do

# Generating The Schema

Install apollo and the program that will convert json to sdl:
```shell script
$ npm install -g apollo
$ npm install -g graphql-introspection-json-to-sdl
```
Download schema.json:
```shell script
$ apollo service:download --endpoint=https://yourstore.myshopify.com/admin/api/2020-01/graphql.json --header="X-Shopify-Access-Token: <token>" graphql/shopify.json
```
Convert schema.json to sdl:
```shell script
$ graphql-introspection-json-to-sdl graphql/shopify.json > graphql/shopify.graphqls
```
