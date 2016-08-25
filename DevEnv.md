# Development environment
- JRE
- JDK
	JAVAHOME=C:\Program Files\Java\jdk1.8.0_77
- Create c:\dev
	Eclipse
		Help -> Check Updates...
		Help -> Eclipse Marketplace... -> Spring IDE
		Help -> Eclipse Marketplace... -> Oracle Database Tools
		Help -> Eclipse Marketplace... -> Oracle WebLogic Server Tools
	Maven
		M2=C:\dev\Apache Software Foundation\apache-maven-3.3.9\bin
		M2_HOME=C:\dev\Apache Software Foundation\apache-maven-3.3.9
		MAVEN_OPTS=-Djavax.net.ssl.trustStore=C:\dev\certs\<file>.jks -Djavax.net.ssl.trustStorePassword=<password>
	Spring
		SPRING_HOME=C:\dev\spring-1.3.5.RELEASE
		PATH=%PATH%;%SPRING_HOME%\bin;
