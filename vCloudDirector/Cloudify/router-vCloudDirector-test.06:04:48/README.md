

VNF onboarding with Cloudify
============================

Zip structure:
/types - needed types for Standard TOSCA blueprints
/scripts - scripts used in configuration
vCloud Director-inputs.yaml - inputs needed for Cloudify blueprint deployment, should be copied and filled outside the zip file 
TestRest-vCloud Director.yaml - Cloudify blueprint
TestRest-vCloud Director-TOSCA.yaml - Standard TOSCA blueprint
TestRest-vCloud Director-OSM.yaml - Standard TOSCA blueprint


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
    Fill inputs template with relevant data: vCloud Director-inputs.yaml
    
    At once:
    `cfy install -l TestRest-vCloud Director.zip  -n TestRest-vCloud Director.yaml -b TestRest --include-logs -i vCloud Director-inputs.yaml`
    
    or step by step:
    `cfy blueprints publish-archive -l TestRest-vCloud Director.zip  -n TestRest-vCloud Director.yaml -b TestRest-vCloud Director`
    `cfy deployments create -d TestRest-vCloud Director -b TestRest-vCloud Director`
    `cfy executions -w install -d TestRest-vCloud Director --include-logs`

3. How to operate:

    Using UI or CLI. <information>
   
4. Uninstall 

    At once:
    `cfy uninstall -d TestRest-vCloud Director --include-logs`
    
    or step by step:
    `cfy executions -w uninstall -d TestRest-vCloud Director`
    `cfy deployments delete -d TestRest-vCloud Director`
    `cfy blueprints delete -b TestRest-vCloud Director`

