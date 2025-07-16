# ICSOC 2025
This repository is created for the ICSOC submissions.

# Extended version
You can find <a href="./extended-version.pdf">here</a> extended version. 


# TOOL
BPDML provides a Docker image to run the BPMN modeler as a Container in Docker.
The BPDML Docker image is based on the official NodeJS image (node:16-buster). The container image contains a prebuild appliction and exposes the port 3000. The port 3001 is used flask server that used to connect to the openAI API.


Run the following command after changing the <openai-key> and <bonita-workspace>. The <bonita-workspace> is used to connect our system to the Bonita ecosystem. In this case, we can directly connect to the Business Data Model defined within Bonita to define "Data store" objects. Also, it is important to export the BPDML to be executable within Bonita. Indeed, the <openai-key> is used for the transformation and validation of Gherkin from natural language to Groovy script code.

	$ docker pull anonymous4conferences/bpmn-tool:latest
	$ docker run --name="bpmn-tool" --rm -p 3000:3000 -p 3001:3001  --env OPENAI_KEY=<open-api-key> -it -v <bonita-wokspace>:/usr/src/app/bonita anonymous4conferences/bpmn-tool


The application can be started from a web browser (if you add the Bonita workspace, you should use this workspace). You can run your tool without a Bonita workspace and without an OpenAI key, but it will not be executable for modeling purposes.
    
    http://localhost:3000/#/usr/src/app/workspace


<img
src="./tool/Screenshot (20).png"
width = "250"
raw=true
/>
<img
src="./tool/Screenshot 2023-07-31 120558.png"
width = "250"
raw=true
/>
<img
src="./tool/Screenshot 2023-07-31 120614.png"
width = "250"
raw=true
/>
<img
src="./tool/Screenshot 2023-11-08 150844.png"
width = "250"
raw=true
/>

# Verifying DABs
MCMT is an SMT-based model checker that supports verification of infinite-state transition systems. It can be download here: `http://users.mat.unimi.it/users/ghilardi/mcmt/`. Consult MCMT's user manual for more details on the tool itself. Note that MCMT has to be linked to the SMT solver Yices 1: `https://yices.csl.sri.com/`. To run a file with an MCMT program, use the command line and type this: `./bin/mcmt [options] <filename>`.
