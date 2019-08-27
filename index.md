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

In SWAN, users can create projects and store their notebooks, input/output files, etc. Internally, a project is a special type of folder that can be used as a container for your work. It is also the unit of sharing in SWAN: you can share a project with your colleagues and thus provide them with everything they need to run the notebooks you created.

Software packages in SWAN are retrieved on the fly from an HTTP-based file system called [CVMFS](https://cernvm.cern.ch/portal/filesystem) (CernVM File System) allowing users to forget about installation, configuration, and compatibility of packages. Due to the [centrally managed software](http://lcginfo.cern.ch/), provided by CVMFS, a user trying to open the shared notebook doesn’t have to worry about compatibility with its software stack, since they are the same. However, SWAN is also used by users who need to install their own packages, breaking this seamless sharing experience.

The objective of this GSoC project is to create a package manager for SWAN (in the shape of a Jupyter extension), that will allow users to keep track of the packages needed by their “projects”. This lets users manage their projects and dependencies.

The extension allows users to install python modules (and their respective versions) via a user interface, making them available inside the corresponding project. People who open a shared project would automatically get a prompt to install all the required missing packages. It thus encourages reproducible results and collaborative analysis.

Each project is internally mapped to a separate conda environment and the project metadata is stored on a hidden file as a part of the project itself. This helps abstract the configuration while mapping an independent environment for each project. 

SWAN allows the creation of notebooks in four different languages: Python (2 or 3, depending on the software stack chosen during the session configuration), C++, R, and Octave. However, this extension would only work for python projects. For other kernels, it is not certain that the environments guarantee isolated versions of packages.


## Features

- View packages installed for a specific project
- Update / Delete existing packages
- Search for new packages and install them
- Sync your project if any of your packages are missing or misconfigured


## Setup Instructions

- This project assumes a SWAN setup. The APIs require certain actions as prerequisites, which are already fulfilled by SWAN. 

- Please find the install instructions [here](https://github.com/techtocore/Jupyter-Package-Manager/blob/swan-integration/extension/install.md)


## Usage Instructions

- From the Projects tab, you can create a folder by clicking on the  **`+`** button. Internally, this will create a new conda environment for all the notebooks inside it.

- To configure the project, click the cog button. This would reveal a side panel listing down the installed packages, along with their corresponding versions. 

- If in case the project metadata and the underlying environment are not in sync, the sidebar will also list the packages that need to be additionally installed. This is fundamental to share projects and collaborate with peers. By default, when a user clones a shared project, the required packages are not installed. This extension will let users install them.

- To install a new package, the user can search for them (an autocomplete feature is available). The selected packages are installed only when the user clicks the 'install' button. This allows the selection of other packages before issuing the 'install' command, which might take a while.

- Users can check for updates, for all or only the selected packages, by clicking the small cog button beside the list of installed packages. A pop-up modal will list the packages that need to be updated, along with their versions. Similarly, users can select one or more packages and uninstall them by clicking the bin icon.

- In order to create a notebook, click on the **`+`** button from inside a project or a regular folder. A list will then appear with the available languages. Users will be able to launch notebooks only using the kernel corresponding to that project. Any external notebook placed under the project will also be using the same kernel.


## Documentation

- Please find the API Specification [here](https://github.com/techtocore/Jupyter-Package-Manager/blob/swan-integration/docs/API_docs.md)
- The code is documented with necessary inline comments and docstrings


## List of completed deliverables

- Server Extension with all the necessary API endpoints
- Frontend Extension that lets users interact with the package manager
- Dockerfile that automates deployment
- SWAN integration (Partially done)

**Link to extension repository**: [https://github.com/techtocore/Jupyter-Package-Manager](https://github.com/techtocore/Jupyter-Package-Manager)

**Link to modified SWAN setup**: [https://github.com/techtocore/jupyter](https://github.com/techtocore/jupyter)


## List of tasks that is yet to be completed

- Optimization of kernel display filtering
- Integration with [EOS](http://information-technology.web.cern.ch/services/eos-service)
- Improvising visual cues
- Rigorous end to end testing


## Screenshots

![Alt text](https://github.com/techtocore/Jupyter-Package-Manager/raw/swan-integration/docs/ui.png "Package Management UI")



![Alt text](https://github.com/techtocore/Jupyter-Package-Manager/raw/swan-integration/docs/modal.png "Package Management UI")


## About

This extension is made for the purpose of fulfillment of the GSoC 2019 project at **CERN-HSF** ([Project Summary](https://summerofcode.withgoogle.com/projects/4999527885438976))

### Student

***Akash Ravi***

- **Email ID**: [akashkravi@gmail.com](mailto:akashkravi@gmail.com)
- **Profile**: [https://akashravi.github.io/](https://akashravi.github.io/)

### Mentors

- Diogo Castro
- Enrico Bocchi
- Enric Tejedor
- Jakub Moscicki


<script>
//open external links in a new window
function external_new_window() {
    for(var c = document.getElementsByTagName("a"), a = 0;a < c.length;a++) {
        var b = c[a];
        if(b.getAttribute("href") && b.hostname !== location.hostname) {
            b.target = "_blank";
            b.rel = "noopener";
        }
    }
}
//open PDF links in a new window
function pdf_new_window ()
{
    if (!document.getElementsByTagName) return false;
    var links = document.getElementsByTagName("a");
    for (var eleLink=0; eleLink < links.length; eleLink ++) {
    if ((links[eleLink].href.indexOf('.pdf') !== -1)||(links[eleLink].href.indexOf('.doc') !== -1)||(links[eleLink].href.indexOf('.docx') !== -1)) {
        links[eleLink].onclick =
        function() {
            window.open(this.href);
            return false;
        }
    }
    }
} 
pdf_new_window();
external_new_window();
</script>
