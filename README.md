# How To: Java Servlets

This "How To Guide" dives into Java EE servlets. With Servlet 3.1 you can forego much of the old deployment descriptor (web.xml) hacking, and simply use annotations. In fact, this is what a simple servlet looks like:

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

* Step 1 - Build the WAR
  * Run `gradle` to build the WAR in `build/libs/howto-java-servlet.war`
* Step 2 - Deploy to a server
  * Required feature: `servlet-3.1`


# Import into Eclipse

The following are high-level instructions for importing this project into Eclipse

1. Run `gradle eclipse` to generate the .project and other files needed by Eclipse
2. Import -> Projects from Git


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
4. Update Eclipse source folder to be src/main/java
Project -> Properties -> Java Build Path -> Remove src -> Add src/main/webapp/
5. Create the Servlet
New -> Servlet -> define Package + Name -> Next -> Update URL Mapping to be "/" (if you want to do this) -> Next -> Update template if you want to -> Finish
Creates SimpleServlet.java AND updates the DD (Deployment Descriptor)

