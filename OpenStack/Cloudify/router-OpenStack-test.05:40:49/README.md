

VNF onboarding with Cloudify
============================

Zip structure:
/types - needed types for Standard TOSCA blueprints
/scripts - scripts used in configuration
OpenStack-inputs.yaml - inputs needed for Cloudify blueprint deployment, should be copied and filled outside the zip file 
TestRest-OpenStack.yaml - Cloudify blueprint
TestRest-OpenStack-TOSCA.yaml - Standard TOSCA blueprint
TestRest-OpenStack-OSM.yaml - Standard TOSCA blueprint


Run your VNF with Cloudify and follow steps below.

1. Setup Cloudify virtualenv.
   
    You can skip this step if your virtualenv is already created and just activate it or use Cloudify UI instead.
    
    Using virtualenv:
    `virtualenv cloudify`
    `source cloudify/bin/activate`
    
    or using virtualenv wrapper:
    `mkvirtualenv cloudify`
    
    install cloudify cli:
    `pip install cloudify==3.4.1`
    
    Use cloudify manager:
    `cfy use -t <cfy manager ip>`

2. Install
    Fill inputs template with relevant data: OpenStack-inputs.yaml
    
    At once:
    `cfy install -l TestRest-OpenStack.zip  -n TestRest-OpenStack.yaml -b TestRest --include-logs -i OpenStack-inputs.yaml`
    
    or step by step:
    `cfy blueprints publish-archive -l TestRest-OpenStack.zip  -n TestRest-OpenStack.yaml -b TestRest-OpenStack`
    `cfy deployments create -d TestRest-OpenStack -b TestRest-OpenStack`
    `cfy executions -w install -d TestRest-OpenStack --include-logs`

3. How to operate:

    Using UI or CLI. <information>
   
4. Uninstall 

    At once:
    `cfy uninstall -d TestRest-OpenStack --include-logs`
    
    or step by step:
    `cfy executions -w uninstall -d TestRest-OpenStack`
    `cfy deployments delete -d TestRest-OpenStack`
    `cfy blueprints delete -b TestRest-OpenStack`

