## protocol_eg
This project demonstrates the use of prototool which provides useful iteration around the protoc  
tool. Simply enter in all the code that needs generating in prototool.yaml and prototool  
loops through all .proto files it can find and puts generated code in the cpp, python dirs.

### How to generate code
Here we use prototool in a docker container:
In this directory execute this:  


prototool_eg> docker run -v "$(pwd):/work" uber/prototool:latest prototool --debug generate  
To generate gprc files

### NOTE : 

Prototool is a frustrating tool because it fails silently.
When it runs successfully it executes protoc as follows but frustratingly when there are errors it 
executes with "-o /dev/null" rather than "--cpp_out"

api> docker run -v "$(pwd):/work" uber/prototool:latest protoc -I /usr/include -I /work --cpp_out /work /work/sql_vdi_api.proto

### TIP1:
Good idea to generate a dummy prototool file consistent with the tool 
To do this:  
In bash shell in this container generate dummy prototool.yaml file as follows  
api> docker run -i -t -v "$(pwd):/work" uber/prototool:latest /bin/bash  
bash> prototool config init  

### TIP2:
Need to set the appropriate version of protoc at the top of the prototool.yaml file

### Reference:
See docker image at: https://github.com/uber/prototool/blob/dev/docs/docker.md  

