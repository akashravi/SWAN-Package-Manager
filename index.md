# Google Summer of Code 2019 Project Report

## Introduction

SWAN (Service for Web based ANalysis) is a platform developed by CERN to perform interactive data analysis in the cloud, without the need to install any software. It lets users create catalogs of their analyses. 

This Jupyter notebook extension will allow the users to specify python modules (and their respective versions) via a user interface and make them available automatically inside the corresponding project. People who open a shared project would automatically get a prompt to install all the required packages. It thus encourages reproducible studies and collaborative experimentation.

Each project is internally mapped to a separate conda environment and the project metadata is stored on a hidden file as a part of the project itself. This helps abstract the processing part, while providing an independent environment for each project. 


## Features

- View packages installed for a specific project
- Update / Delete existing packages
- Search for new packages and install them
- Sync your project if any of your packages are missing or misconfigured


## Setup Instructions

- This project assumes a [SWAN](https://gitlab.cern.ch/swan) setup. The APIs require certain actions as prerequisites, which are already fulfilled by SWAN. 
- Please find the install instructions [here](https://github.com/techtocore/Jupyter-Package-Manager/extension/install.md)


## Usage Instructions

- On creating a project, the user will be presented with a cog button on the top right of the view plane.

- Users will be shown a sidebar on clicking the button. The default view would list down the list of packages installed along with their corresponding versions. 

- If in case the project metadata and the underlying environment are not in sync, the sidebar will also list the packages that need to be additionally installed. This would be essential to share projects and collaborate with peers.

- New packages can be installed by searching then and confirming the changes. The list of packages that are selected to be installed can be modified by the user.

- Users can check for updates by clicking the small cog button beside the list of installed packages. A pop-up modal will list the packages that need to be updated.

- Similarly, users can select one or more packages and uninstall them by clicking the bin icon and confirming the changes that would be applied.

- Users will be able to launch notebooks only using the kernel available corresponding to that project. Any external notebook placed under the project will also be using the same kernel.


## Documentation

- Please find the API Specification [here](https://github.com/techtocore/Jupyter-Package-Manager/docs/API_docs.md)
- The code is documented with necessary inline comments and docstrings


## List of completed deliverables

- Server Extension with all the necessary API endpoints
- Frontend Extension that lets users to interact with the package manager
- Dockerfile that automates deployment
- SWAN integration

Link to extension repository: https://github.com/techtocore/Jupyter-Package-Manager
Link to modified SWAN setup: https://github.com/techtocore/jupyter


## List of tasks that is yet to be completed

- Optimisation of kernel display filtering
- Improvising visual cues
- Rigerous end to end testing


## Screenshot

![Alt text](https://github.com/techtocore/Jupyter-Package-Manager/docs/ui.png?raw=true "Package Management UI")


## About

This extension is made for the purpose of fulfilment of the GSoC 2019 project at CERN ([Project Summary](https://summerofcode.withgoogle.com/projects/4999527885438976))

- Developer: Akash Ravi
- Email ID: akashkravi@gmail.com
- Linkedin Profile: https://www.linkedin.com/in/akash-ravi/