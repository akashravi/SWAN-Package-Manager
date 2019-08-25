# Google Summer of Code 2019 Project Report


<center>
<table>
<tr>
<td><a href="https://summerofcode.withgoogle.com/projects/4999527885438976"><img src="https://user-images.githubusercontent.com/6822941/29750351-e95e7b1c-8b5b-11e7-9f6b-b25b69f7353a.png"/></a></td>
<td><a href="http://hepsoftwarefoundation.org/"><img src="https://user-images.githubusercontent.com/6822941/29750350-e956b512-8b5b-11e7-9e34-4e3a5be9d37f.png"/></a></td>
<td><a href="https://swan.web.cern.ch/"><img src="https://avatars0.githubusercontent.com/u/38285709?s=200&v=4"/></a></td>
</tr>
</table>
</center>


## Introduction

[SWAN](https://swan.web.cern.ch/) (Service for Web based ANalysis) is a platform developed by CERN to perform interactive data analysis in the cloud, without the need to install any software. It is built upon [Jupyter notebooks](http://jupyter.org/) and allows users to code and run their scripts via a web interface.

A Project in SWAN is a special type of folder that you can use as a container for your work on a given topic: notebooks, input/output files, other subfolders, etc. It is also the unit of sharing in SWAN: you can share a project with your colleagues and thus provide them with everything they need to run the notebooks you created.

With this requirement in mind, this GSoC project aims to provide a package manager for SWAN (in the shape of a Jupyter extension), that will allow users to keep track of the packages needed by their “projects”, thus also allowing others to seamless install everything needed.

This extension will allow the users to install python modules (and their respective versions) via a user interface and make them available automatically inside the corresponding project. People who open a shared project would automatically get a prompt to install all the required packages. It thus encourages reproducible results and collaborative analysis.

Each project is internally mapped to a separate conda environment and the project metadata is stored on a hidden file as a part of the project itself. This helps abstract the processing part, while providing an independent environment for each project. 

SWAN allows you to create notebooks in four different languages: Python (2 or 3, depending on the software stack chosen during the session configuration), C++, R and Octave. However, this extension would only work for python projects. For other kernels, it is not certain that the environments guarantee isolated versions of packages.


## Features

- View packages installed for a specific project
- Update / Delete existing packages
- Search for new packages and install them
- Sync your project if any of your packages are missing or misconfigured


## Setup Instructions

- This project assumes a SWAN setup. The APIs require certain actions as prerequisites, which are already fulfilled by SWAN. 

- Please find the install instructions [here](https://github.com/techtocore/Jupyter-Package-Manager/blob/swan-integration/extension/install.md)


## Usage Instructions

- On creating a project, the user will be presented with a cog button on the top right of the view plane.

- Users will be shown a sidebar on clicking the button. The default view would list down the list of packages installed along with their corresponding versions. 

- If in case the project metadata and the underlying environment are not in sync, the sidebar will also list the packages that need to be additionally installed. This would be essential to share projects and collaborate with peers.

- New packages can be installed by searching then and confirming the changes. The list of packages that are selected to be installed can be modified by the user.

- Users can check for updates by clicking the small cog button beside the list of installed packages. A pop-up modal will list the packages that need to be updated.

- Similarly, users can select one or more packages and uninstall them by clicking the bin icon and confirming the changes that would be applied.

- Users will be able to launch notebooks only using the kernel available corresponding to that project. Any external notebook placed under the project will also be using the same kernel.


## Documentation

- Please find the API Specification [here](https://github.com/techtocore/Jupyter-Package-Manager/blob/swan-integration/docs/API_docs.md)
- The code is documented with necessary inline comments and docstrings


## List of completed deliverables

- Server Extension with all the necessary API endpoints
- Frontend Extension that lets users to interact with the package manager
- Dockerfile that automates deployment
- SWAN integration

**Link to extension repository**: [https://github.com/techtocore/Jupyter-Package-Manager](https://github.com/techtocore/Jupyter-Package-Manager)

**Link to modified SWAN setup**: [https://github.com/techtocore/jupyter](https://github.com/techtocore/jupyter)


## List of tasks that is yet to be completed

- Optimisation of kernel display filtering
- Improvising visual cues
- Rigerous end to end testing


## Screenshots

![Alt text](https://github.com/techtocore/Jupyter-Package-Manager/raw/swan-integration/docs/ui.png "Package Management UI")



![Alt text](https://github.com/techtocore/Jupyter-Package-Manager/raw/swan-integration/docs/modal.png "Package Management UI")


## About

This extension is made for the purpose of fulfilment of the GSoC 2019 project at **CERN-HSF** ([Project Summary](https://summerofcode.withgoogle.com/projects/4999527885438976))

### Student

***Akash Ravi***

- **Email ID**: [akashkravi@gmail.com](mailto:akashkravi@gmail.com)
- **Linkedin Profile**: [https://www.linkedin.com/in/akash-ravi/](https://www.linkedin.com/in/akash-ravi/)

### Mentors

- Diogo Castro
- Enrico 
- Enric Tejedor
- Jakub Moscicki
