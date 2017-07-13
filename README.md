# howto-java-servlet
How-To Guide for creating a simple Java Servlet


Eclipse - Create New ... -> Dynamic Web Project/

New -> File -> build.gradle
`apply plugin: 'war'`
`defaultTasks 'clean', 'build'`

Since using Gradle, expects source here: `src/main/webapp`
Create dir: `mkdir -p src/main/webapp`
Update Eclipse classpath
- Project -> Properties -> Java Build Path -> Remove src -> Add src/main/webapp/
New -> Servlet -> Package + Name -> Next -> Update URL Mapping to be "/" (if you want to do this) -> Next -> Update template if you want to -> Finish
Creates SimpleServlet.java AND updates the DD (Deployment Descriptor)

# To Build

run `gradle`
Built war is at `build/libs/howto-java-servlet.war`
