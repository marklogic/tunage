# Tunage

Tunage is a web application that allows you to search, display, and play tracks from your iTunes library in your browser. It runs on MarkLogic Server and uses Information Studio to load content and Application Builder to generate the basic search application. You can [download a free version of MarkLogic Server on the MarkLogic Developer Community](http://developer.marklogic.com/products).

## Information Studio
Information Studio is an easy new way to load information into a MarkLogic database. It includes a web-based UI as well as high-level APIs to collect, transform, and load content. Tunage uses a custom collector to pull song metadata directly from iTunes. To install it, copy (or soft link) the `Information Studio/collector-itunes.xqy` file into `$MARKLOGIC_HOME/
<marklogic-dir>/Assets/plugins/marklogic/appservices`, 
where `$MARKLOGIC_HOME` is where you installed MarkLogic Server. Restart the Server and you should see the “iTunes Metadata Collector” in your list of collectors in the Information Studio UI.

## Application Builder
Application Builder allows you to build search applications without having to write any code. It’s great for prototyping new concepts or exploring content. However, it can also be the foundation for a _real_ application, as is the case with Tunage. 

Application Builder gives you several ways to extend a built application. The most powerful means is to override the contents of the `/application/custom` directory with XQuery, CSS, and/or JavaScript. Once you’ve built your application with Application Builder, the easiest way to edit the generated source code is to create a WebDAV app server. For an Application Builder application named `foobar`, Application Builder generates a `foobar-modules` database upon deployment. This database contains all of the code and assets that power the application. In the MarkLogic admin interface you can create a new WebDAV app server pointing to the `foobar-modules` database with a root of `/`, meaning the “root” database directory. Fire up your favorite WebDAV client and point it to the `http://host:port` that you just set up. Navigate to `/application/custom` and drag in the contents of the `Application Builder/application/custom` directory above.

### License, Disclaimer, and Other Boring Legal Stuff
Tunage is a demonstration to illustrate how to use MarkLogic Information Studio and MarkLogic Application Builder. It has not been thouroughly tested nor optimized as you’d expect in production-quality application. With that, however, you are free to explore it and repurpose it. All code is copyright MarkLogic and is distributed as-is under the [Apache 2.0 license](http://www.apache.org/licenses/LICENSE-2.0.html). 