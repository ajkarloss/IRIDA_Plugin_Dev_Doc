# IRIDAPlugin Dev Doc
Step by step handson doc for anyone who wants to develop new plugin for IRIDA

# IRIDA architecture 

# Plugin Overview 
<img width="1241" alt="Screenshot 2024-01-07 at 14 51 43" src="https://github.com/ajkarloss/IRIDA_Plugin_Dev_Doc/assets/15940041/6c6ba708-9878-4189-8c0b-ff4bb242965d">

# Prerequisite
IRIDA - Locally Installed
<img width="1043" alt="Screenshot 2024-01-07 at 15 49 40" src="https://github.com/ajkarloss/IRIDA_Plugin_Dev_Doc/assets/15940041/20dd8b26-4497-493d-b139-88cbc2e52a98">

https://phac-nml.github.io/irida-documentation/developer/tools/pipelines/#4-test-in-irida:~:text=is%20as%20follows.-,3.2.1.%20Install%20IRIDA%20to%20local%20Maven%20repository,-In%20order%20to

Also, download the example-plugin
<img width="1037" alt="Screenshot 2024-01-08 at 12 18 50" src="https://github.com/ajkarloss/IRIDA_Plugin_Dev_Doc/assets/15940041/eeec04fd-ac63-4c42-b307-5d5c71b4cafb">

https://phac-nml.github.io/irida-documentation/developer/tools/pipelines/#4-test-in-irida:~:text=publishToMavenLocal%20%2Dxtest-,3.2.2.%20Download%20IRIDA%20plugin%20example,-Once%20you%E2%80%99ve%20installed 



Galaxy - Locally Installed 

1. Install the tool in Galaxy (SeroTypeFinder)
2. Create galaxy workflow for SeroTypeFinder
 <img width="896" alt="Screenshot 2024-01-07 at 20 33 25" src="https://github.com/ajkarloss/IRIDA_Plugin_Dev_Doc/assets/15940041/14f7cf31-b088-4740-877c-4714a84a6ef0">

3. Input box should be "list:paired" and the name should be "sequence_reads_pair"
<img width="282" alt="Screenshot 2024-01-08 at 12 11 32" src="https://github.com/ajkarloss/IRIDA_Plugin_Dev_Doc/assets/15940041/5d11e4ea-2707-4b3c-8358-3b807b717b59">


* Test the workflow to make sure it produces the expected output
* Export the workflow

# Converting Galaxy workflow to IRIDA plugin

* ```cd /home/irida/```
* ```git clone https://github.com/phac-nml/irida-plugin-example```
* change name ```mv irida-plugin-example/ serotypefinder/```
* ```cd serotypefinder/```

IRIDA provides a java file to create the templates (information and XML files) for the plugin development

* https://github.com/phac-nml/irida-wf-ga2xml/releases 
* git clone https://github.com/phac-nml/irida-wf-ga2xml/releases#:~:text=irida%2Dwf%2Dga2xml%2D1.2.1%2Dstandalone.jar

```
java -jar irida-wf-ga2xml-1.2.1-standalone.jar -n SeroTypeFinder -t SeroTypeFinder -W 1.0.0 -o output -i Galaxy-Workflow-SerotyperFinder.ga
```

* Results are stored in ```output/``` folder
* Copy the outputs ```cp output/SeroTypeFinder/1.0.0/* serotyper/src/main/resources/workflows/1.0.0/```
* Directories which are important: ```serotyper/src/main/resources/workflows/``` and ```/src/main/java/ca/corefacility/bioinformatics/irida/plugins/```


 
