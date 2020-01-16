## protocol_eg
This project demonstrates the use of prototool which provides useful iteration around the protoc  
tool. Simply enter in all the language types that need generating in prototool.yaml and on execution prototool  
reads this file and loops through all .proto files it can find and puts generated code in the cpp and python dirs.

### Prerequisites
1.) Recent version of Docker. Follow these instruction for fedora 29,30,31
https://docs.docker.com/install/linux/docker-ce/fedora/

### How to generate code
Here we use prototool in a docker container:
In this directory execute this:  
  
prototool_eg> docker run -v "$(pwd):/work" uber/prototool:latest prototool --debug generate  
  
to generate gprc files

### NOTE : 

Prototool is a frustrating tool because it fails silently.
When it runs successfully it executes protoc as follows but frustratingly when there are errors it 
executes with "-o /dev/null" rather than "--cpp_out"

api> docker run -v "$(pwd):/work" uber/prototool:latest protoc -I /usr/include -I /work --cpp_out /work /work/sql_vdi_api.proto


### TIP1:
Need to set the appropriate version of protoc at the top of the prototool.yaml file
  
### TIP2:
Good idea to generate a dummy prototool file consistent with the tool. 
To do this:  
In bash shell in this container generate dummy prototool.yaml file as follows  
api> docker run -i -t -v "$(pwd):/work" uber/prototool:latest /bin/bash  
bash> prototool config init  
  
### Reference:
See docker image at: https://github.com/uber/prototool/blob/dev/docs/docker.md  

