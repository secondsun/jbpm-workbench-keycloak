# jbpm-workbench-keycloak
Docker and OpenShift scripts to run JBPM Workbench in OpenShift with Keycloak

# Setup
 * Run the template in OpenShift  
 * Login into KeyCloak
 * Import [realm](keycloak/kie-realm.json) and users(keycloak/kie-users-0.json)
 * Update the kie client's redirect URI to match the JBPM_URI you setup when you imported your template
 * Log into your jbpm as admin/admin