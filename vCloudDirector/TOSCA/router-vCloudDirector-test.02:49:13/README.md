

Standard TOSCA blueprint
------------------------

1. Setup environment
   `virtualenv env`
   `. env/bin/activate`
   `pip install git+http://git-wip-us.apache.org/repos/asf/incubator-ariatosca.git`

2. Unzip blueprints package
   `unzip TestRest-vCloud Director`

3. Parse blueprint to generate model
   `aria parse TestRest-vCloud Director/TestRest-vCloud Director-TOSCA.yaml instance`


