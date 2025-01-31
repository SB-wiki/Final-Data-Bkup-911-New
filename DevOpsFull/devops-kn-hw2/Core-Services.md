
### PREREQUISITES

### 1. Create a container in azure blob and make it public for content publish. This continer name will be same as the variable  **sunbird_content_azure_storage_container**  which is specified in the common.yml of Core inventory.

### 2. Switch to Build folder and run all jobs. Provide the value for  **github_release_tag**  as per the details mentioned in this page - [Current Release Tags and Jenkins Jobs Reference](https://project-sunbird.atlassian.net/wiki/spaces/DevOps/pages/1025376293/Current+Release+Tags+and+Jenkins+Jobs+Reference)


 **Run the Below Jobs** 
### Below steps needs to be followed as per the order.
 **OpsAdministration** :

1. Bootstrap                                                                                                               # Creates Deployer User

2. SwarmBootstrap                                                                                                    # Creates Swarm with manager and agent nodes

 **Builds** :

1. Adminutils                                                                                                              # Builds Adminutils container

2. API MANAGER                                                                                                      # Builds API Manager Container

3. API MANAGER Echo                                                                                             # Builds API Manager echo Container

4. Badger                                                                                                                  # Builds Badger Container

5. Cassandra                                                                                                            # Creates a jar for migration purpose

6. Content                                                                                                                 # Builds Content Service Container

7. Learner                                                                                                                 # Builds Learner Service Container

8. Player                                                                                                                   # Builds Player Service Container

9. Proxy                                                                                                                    # Builds Proxy container

10. Telemetry                                                                                                           # Builds Telemetry container

 **Artifacts** :

(Make Sure all Artifacts are uploaded)

 **Provision** :

1. (Deploy) ApplicationES                                                                                          # From Deploy Folder Deploy ApplicationES this will Provision Elasticsearch and create indices necessay for Sunbird Core

2. ESMapping (Under OpsAdministarion)                                                                  # Creates ES indexes

2. Postgres                                                                                                                # Provisions Postgres

3. PostgresDbUpdate                                                                                                # Creates the databases, assign roles, create users



 **Deploy** :

1. Adminutil                                                                                                               # Deploy Adminutil Container

2. API Manager                                                                                                         # deploys API Manger Kong and API manager echo

4. OnboardAPIS                                                                                                        # Onboards All API's to sunbird

5. OnboardConsumers (Take the  **jwt token**  from Jenkins Output of  **api-management-test-user**  and update   **core_vault_sunbird_api_auth_token**  if using KP and DP along with core) # Onboards New consumer to sunbird and generates API key specific to Consumer,  **Update this value with correponding api key of ekstep 'core_vault_ekstep_api_key'** 

7. (Provision) Cassandra                                                                                           # Provisions Cassandra and create Keyspaces required for Sunbird Core

8. Cassandra                                                                                                             # Does Migration if required

6. (Provision) Keycloak                                                                                              # Provisions Keycloak by installing prerequisites like java and env vars of learner

9. keycloak                                                                                                                 # Deploys keycloak service to VM

10. Proxy                                                                                                                   # Deploys Proxy, Handles all routing within the swarm

11. KeycloakRealm                                                                                                   # Creates Sunbird Realm, (After Creation of Realm configure keycloak by using Below Steps.)

 **Configuration Steps Required in Keycloak**   a. Login to keycloak using username admin and password as given in private "secrets.yml" file. # Login to keycloak by using <domainname>/auth

  b. Take the sso_public_key by navigating to: sunbird Realm > Realm Settings > keys > click Public Key(copy the key and update core_vault_sso_public_key)

  c. Create Admin Role in Sunbird realm: Roles > Add Role > add details in the form(Role Name: admin) > save > Enable Composite Roles > Under Composite Roles > Select (offline_access, uma_administration) and click add selected,  Permissions(enable Permissions).

  d. Assign permissions to admin-cli client in Sunbird realm: clients > admin-cli > Settings > Implicit Flow Enabled (ON) > Root URL: [https://dev.sunbird.cf](https://dev.sunbird.cf) (your Domain) > Valid Redirect URIs: [https://dev.sunbird.cf/\*](https://dev.sunbird.cf/*) (Add another Link by clicking on "+") > Valid Redirect URIs: [https://dev.sunbird.cf/](https://dev.sunbird.cf/) > Base URL: / > Admin URL: [https://dev.sunbird.cf/\*](https://dev.sunbird.cf/*) > Save

  e. In the Sunbird realm, Clients > admin-cli > Roles > Add Role: Role Name: admin (Save)> composite Roles (ON) > Composite Roles > Realm Roles > add admin,offline_access,uma_authorization > Permissions > Permissions Enabled (ON)

  f. Creating keycloak federation ([[Deployment Steps for Keycloak User Federation|Deployment-Steps-for-Keycloak-User-Federation]])

12. Player                                                                                                                    # Deploys Player service, used to display Frontend of App

 **Note: ** This player deployment job will fail first time and Jenkins will ask for  **In process Approval Script. Click on the approval link in the deploy job page and provide explicit approval for new java.io.File java.lang.String and method java.io.File exists** . Now rerun Player deployment.

13. Learner                                                                                                                 # Deploys Learner Service, handles user management, helps in searching content

14. Content                                                                                                                 # Deploys Content service, Helps in creation of content

15. Telemetry                                                                                                              # Deploys Telemetry Service, Helps in sending telemetry to kafka

16. TelemetryLogstashDataPipeline                                                                                           # Deploys logstash container, which sends telemetry to kafka

17. TelemetryLogstash                                                                                               # Deploys logstash container for sending telemetry to ekstep \[Trigger only when you want to send telemetry to ekstep]

 **Create a mapping for cbatch elasticsearch searchindex index** 
* Follow this documentation and create mappings for cbatch searchindex index. \[[http://402.qa.docs.sunbird.org/master/developer-docs/configuring_sunbird/elasticsearch_static_mapping_course_batch/](http://402.qa.docs.sunbird.org/master/developer-docs/configuring_sunbird/elasticsearch_static_mapping_course_batch/)]



*****

[[category.storage-team]] 
[[category.confluence]] 
