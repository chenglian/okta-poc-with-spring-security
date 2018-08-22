# okta-poc-with-spring-security
OKTA Proof Of Concept with Spring Security framework using ResourceBackedMetadataProvider for OKTA

# README #

This is a POC project for OKTA SAML2 based Single Sign On using Spring Security framework.
It is tested with an OKTA developer sandbox as an IdP and Tomcat 8.5.23 as a web container, in Spring Tool Suite (STS) release 3.9.1.

### What is this repository for? ###

This is created for the Proof of Concept of OKTA SSO.

### How do I get set up? ###

It is assumed that you have basic knowledge of:

(1) SAML2

(2) OKTA

(3) Tomcat and Java

High level setup steps:

(1) Create a OKTA developer sandbox.

(2) Create a new SAML2 application with the following SAML2 configuration (use defaults unless specified here:

Single Sign On URL: https://localhost:9443/spring-security-saml2-sample/saml/SSO

Audience Restriction:https://localhost:9443/spring-security-saml2-sample/saml/metadata

Name ID Format:EmailAddress


SAML Single Logout:Enabled

Single Logout URL:https://localhost:9443/spring-security-saml2-sample/saml/logout

SP Issuer:https://localhost:9443/spring-security-saml2-sample/saml/metadata

Signature Certificate:apollo.cer (CN=apollo) #upload apollo.cer that can be extracted from the keystore provided in this war under "src/main/resources/metadata/".

Honor Force Authentication:Yes

(3) download the IdP metadata file from OKTA and replace the existing okta-idp.xml file under "src/main/resources/metadata/".

(4) Run pom.xml As "Maven build" with targets "clean install" ( I used Maven 3.3.9). If everything goes well, a .war file named "spring-security-saml2-sample.war" should be generated under the "/target" folder.

(5) configure Tomcat with SSL/TLS enabled. A sample server.xml is provided under "src/main/resources/security/".

(6) deploy the new WAR file (as modified in step 3) in Tomcat or equivalent. Alternatively, you may run this application within the IDE.

(7) if everything goes well, you should be able to start the testing by browsing to https://localhost:9443/spring-security-saml2-sample


### Who do I talk to? ###

chenglian*****@gmail.com
