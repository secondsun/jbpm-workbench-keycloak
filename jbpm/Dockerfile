FROM jboss/jbpm-workbench:latest

#Download and Install Adapter
ENV KEYCLOAK_VERSION 3.1.0.Final

WORKDIR /opt/jboss/wildfly

RUN curl -L https://downloads.jboss.org/keycloak/$KEYCLOAK_VERSION/adapters/keycloak-oidc/keycloak-wildfly-adapter-dist-$KEYCLOAK_VERSION.tar.gz | tar zx

WORKDIR /opt/jboss

# Standalone.xml modifications.
RUN sed -i -e 's/<extensions>/&\n        <extension module="org.keycloak.keycloak-adapter-subsystem"\/>/' /opt/jboss/wildfly/standalone/configuration/standalone-full.xml && \
    sed -i -e 's/<profile>/&\n        <subsystem xmlns="urn:jboss:domain:keycloak:1.1"><secure-deployment name="jbpm-console.war"><realm>jbpm<\/realm><auth-server-url>http:\/\/keycloak.10.1.10.101.nip.io\/auth<\/auth-server-url><ssl-required>EXTERNAL<\/ssl-required><resource>kie<\/resource><credential name="secret">7b191441-6585-4064-affc-3e3165297558<\/credential><\/secure-deployment><\/subsystem>/' /opt/jboss/wildfly/standalone/configuration/standalone-full.xml && \
    sed -i -e 's/<security-domains>/&\n                <security-domain name="keycloak">\n                    <authentication>\n                        <login-module code="org.keycloak.adapters.jboss.KeycloakLoginModule" flag="required"\/>\n                    <\/authentication>\n                <\/security-domain>/' /opt/jboss/wildfly/standalone/configuration/standalone-full.xml

WORKDIR /opt/jboss/wildfly/bin
