# springboot-react-multimodule

This is an example of how bundling separate maven modules with spring backend and react frontend into single executable jar can be achieved.  

Many thanks to Justin Calleja and Olivier Gérardin for their excellent blogposts on which this demo is based.

- [Justin Calleja - Serving a Webpack bundle in Spring Boot](http://justincalleja.com/2016/04/17/serving-a-webpack-bundle-in-spring-boot/)
- [Olivier Gérardin - Spring Boot backend and web frontend in separate Maven modules](http://blog.gerardin.info/archives/824)


Both modules can be run separately during development to achieve hot-reloading and other development features, or they
can be both packaged into single executable jar.

There are two ways to create the jar:

- Either you can run `mvn package` on the root pom.xml, which builds backend, then frontend, then the bundle.
- Or you can run `mvn install` on both, the `backend/pom.xml`, and `frontend/pom.xml` - which builds them and stores the result, then
run `mvn package` on `bundle/pom.xml`. This eliminates the need for extra pom and makes it possible to store all of this
in three independent repositories, then assembling the whole thing in your CI pipeline.


The resulting uber jar is stored in bundle/target and you can run it with `java -jar bundle-0.0.1-SNAPSHOT.jar`.

Then you can access the running app on `localhost:8080`.

