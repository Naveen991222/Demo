pipeline {
    agent {
        kubernetes {
            // Pod template specification
            yaml """
                apiVersion: v1
                kind: Pod
                metadata:
                  labels:
                    app: my-app
                spec:
                  containers:
                  - name: maven
                    image: maven:3.8.1-jdk-11
                    command: ["cat"]
                    tty: true
            """
        }
    }
parameters {
    string(defaultValue: "dev20", description: 'Please enter the tenant name', name: 'TENANT')
    choice(choices: 'nonprod-mysql01-a.czuxw3bobnqm.us-east-2.rds.amazonaws.com\ne-prod-mysql0h.us-east-2.rds.amazonaws.com', description: 'Select the RDS/MySQL Host', name: 'DB_HOST')
    string(defaultValue: "dev20_10", description: 'Enter the DB Name for easaas', name: 'ES10_DB_NAME')
    string(defaultValue: "dev20_e20", description: 'Enter the DB Name for easaas', name: 'EA20_DB_NAME')
    string(defaultValue: "dev20_", description: 'Enter the DB Name for connector', name: 'CONNECTOR_DB_NAME')
    string(defaultValue: "ad", description: 'Enter the DB User Name', name: 'DB_USER')
    string(defaultValue: "", description: 'Enter the DB password', name: 'DB_PASSWORD')
    // password(name: 'DB_PASSWORD', defaultValue: 'SECRET', description: 'Enter the DB password')
    choice(choices: 'azure\namazon-prod-new\namazon-nonprod-new', description: 'Which Cloud/ENV ?', name: 'CLOUD')
    // booleanParam(defaultValue: false, description: 'Please select if you want to deploy MySQL', name: 'mysql')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy MemCached', name: 'memcached')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy OpenSearch', name: 'opensearch')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy OpenSearch Dashboard', name: 'opensearch_dashboard')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy SAAS', name: 'saas')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy SAAS React', name: 'saas_react')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy Snowflake Rest API', name: 'snowflake_rest_api_driver')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy Connector Tool', name: 'connector_tool')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy Logstash Connector', name: 'logstash_connector')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy GraphQL Snowflake Service', name: 'graphql')
    booleanParam(defaultValue: false, description: 'Please select if you want to deploy JupyterHub', name: 'jupyterhub')
}
