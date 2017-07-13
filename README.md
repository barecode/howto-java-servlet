# How To: Java Cronjobs

This "How To Guide" dives into Java EE servlets. With Servlet 3.1 you can forego much of the old deployment descriptor (web.xml) hacking, and simply use annotations. In fact, the is what a simple servlet looks like:

```
@WebServlet("/")
public class SimpleServlet extends HttpServlet {
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.getWriter().append("Served at: ").append(request.getContextPath());
	}
}
```

The [@WebServlet](http://docs.oracle.com/javaee/7/api/javax/servlet/annotation/WebServlet.html) annotation keeps things nice and tight.

# Prerequisite

This guide presumes knowledge on install and use of the following:
* Gradle
* Liberty
* WebSphere Developer Tools (WDT)


# Build and Deploy

* Build the WAR
  * Run `gradle` to build the WAR in `build/libs/howto-java-servlet.war`
* Deploy to a the server
  * Required feature: `servlet-3.1`

# Import into Eclipse

The following are high-level instructions for importing this project into Eclipse

1. Import -> Projects from Git
2. Add `howto-java-servlet` to your Servers view
3. You may need to modify your `.classpath` entry to point to your Liberty installation


# Create a new Project

Within Eclipse for JEE Developers

1. Create New ... -> Dynamic Web Project - name it something useful
2. New -> File -> build.gradle
`apply plugin: 'war'`
`defaultTasks 'clean', 'build'`
3. Gradle expects the following directory structure:
```
    src/main/java/
    src/main/webapp/WEB-INF/
```
4. Update Eclipse classpath
- Project -> Properties -> Java Build Path -> Remove src -> Add src/main/webapp/
New -> Servlet -> Package + Name -> Next -> Update URL Mapping to be "/" (if you want to do this) -> Next -> Update template if you want to -> Finish
Creates SimpleServlet.java AND updates the DD (Deployment Descriptor)

# To Build

run `gradle`
Built war is at `build/libs/howto-java-servlet.war`
