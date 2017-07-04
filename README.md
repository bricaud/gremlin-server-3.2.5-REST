# A Docker container for Gremlin 3.2.5 with REST API and a demo graph

This Docker file creates a container running a Gremlin server, [Gremlin Tinkerpop](https://github.com/apache/tinkerpop) 3.2.5, with a TinkerGraph. The graph database is populated with data from a tree of life (see data section).

To build it, run the following command:
```
docker build -t gremlin-container . 
```
This will create a docker image with name `gremlin-container`.
The graph database is configured using the files in the `files/` folder.
The Gremlin server will serve resquests on port 8182 using the REST API. 

On startup, the server loads the graph from the file `files/treeoflife.graphml`. 
See the [TinkerGraph configuration section](http://tinkerpop.apache.org/docs/current/reference/#_configuration_2) for more details.


You can then start the container using:
```
docker run -p 8182:8182 -it --name gremlin gremlin-container
```
The server can be accessed on port 8182.
Alternatively, you can pull the image from DockerHub [here](https://hub.docker.com/r/bricaud/gremlin-server-REST/)
```
docker pull bricaud/gremlin-server-rest
```
.

## Data
The data provided in the graphml file `files/treeoflife.graphml` is a tree of life.
The original data can be found on the [Tree Of Life Project website](http://tolweb.org/tree/home.pages/downloadtree.html) as a xml file (old xml version of the tree). Details about the data can be found on the same page.


The xml file available on the above website is licenced under the [Attribution Creative Commons 3.0](https://creativecommons.org/licenses/by/3.0/), the copyright is owned by the [Tree Of Life Project](http://tolweb.org/tree/home.pages/tolcopyright.html). It is available at `files/tolskeletaldumpUTF8.xml` (converted to UTF8).


The data has been extracted and saved as a graphml file to be easily loaded by the gremlin server.
The python script performing this task is provided as a Jupyter notebook `files/tree_of_life_xml_tol.ipynb` (APACHE 2.0 licence).
The content of the graphml file `files/treeoflife.graphml` is licenced under the same licence as the original xml file [Attribution Creative Commons 3.0](https://creativecommons.org/licenses/by/3.0/), the copyright is owned by Benjamin Ricaud. Copy, redistributions, modifications are allowed.



