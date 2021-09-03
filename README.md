# gap-docker-deepnote
GAP Docker container for Deepnote
- Latest official GAP release (GAP 4.11.1) [<img src="https://deepnote.com/buttons/launch-in-deepnote-white-small.svg">](https://deepnote.com/project/GAP-Kernel-6I_gbA2oTJeS-h3UCNbvRQ)

## Deepnote
[Deepnote](https://deepnote.com/) is a web-based data science notebook that is Jupyter-compatible. It allows for real-time collaboration helping to bring teams and projects together. No installation is required, and can be used on any OS that has a browser. All notebooks on Deepnote are run on machines in the cloud, which can be customised to the needs of each project (with some features gated behind a subscription). To find out more, access the [docs](https://docs.deepnote.com).

## GAP in Deepnote
This repository attempts to integrate the GAP kernel with Deepnote as a Jupyter Notebook. It does not require a local GAP installation, and can be accessed through the browser. To start a new GAP session, do the following:
1. Click on the "Launch in Deepnote" badge at the top of this read-me, which will take you to an existing project setup for you in Deepnote.
2. To execute your own code, you can click the "Duplicate" button which will setup a new project for you to work with.
3. To make sure that everything is setup correctly, you can click the "Environment" tab on the left-hand side, and ensure it is set to "GAP".
4. If not, you may need to add the Deepnote docker image as a new environment if it is not present in the dropdown. To do this, follow the steps in [Setting up the GAP Docker Image in Deepnote](#setting-up-the-gap-docker-image-in-deepnote).

To test the GAP kernel, simply create a new notebook in Deepnote by clicking on the "Notebooks & Files" tab on the left toolbar, and then the "+" button at the top right of the opened panel. Now, GAP commands can be directly written into the cells in the newly created notebook.

For further information about Jupyter, see Jupyter's [documentation](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/index.html).

## Setting up the GAP Docker Image in Deepnote
To get started with your own GAP projects in a new Deepnote project without duplicating the already set-up project, setup is rather simple:
1. After creating a Deepnote account, create a new project from the dashboard, by clicking the blue "New Project" button.
2. Under the "Environment" tab on the left toolbar, there is a dropdown under the subsection "Environment". This is where all of the Docker images are stored for Deepnote.
3. Since GAP is not pre-bundled with deepnote, it needs to be artificially added by clicking the "Set up a new Docker image" link, and then using the Docker image `ghcr.io/gap-system/gap-docker-deepnote:main`, with the name set to whatever you want.
4. Now, there should be a new option in the dropdown menu under "Your Environments" with the name you set. This environment can then be selected to make use of GAP within Deepnote.

## Limitations
Due to the max 5GB Docker image size limit imposed by Deepnote, the provided Docker image only compiles a select number of GAP packages which are required by the JupyterKernel package. These packages are `io`,`crypting`, `json` & `ZeroMQInterface`. In order to install any other packages, you will need to do so manually. This can be done from the GAP installation directory:

    cd /usr/lib/gap-4.11.1
    
And then running the installation commands as you would on a normal GAP installation. It is likely also possibly to run the `BuildPackages.sh` script to compile all the GAP packages, but this will take an incredibly long time and may lead to a reduced efficiency for your Deepnote notebooks.
