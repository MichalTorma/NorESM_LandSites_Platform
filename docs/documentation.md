[![NorESM](img/NORESM-logo.png "the Norwegian Earth System Model")](https://www.noresm.org/)
[![EMERALD](img/Emerald_darktext_whiteBG_small.png "EMERALD project")](https://www.mn.uio.no/geo/english/research/projects/emerald/)
[![LATICE](img/UiO_LATICE_logo_black_small.png "Land-ATmosphere Interactions in Cold Environments research group")](https://www.mn.uio.no/geo/english/research/groups/latice/)

# Technical documentation for the NorESM Land Sites Platform

This page describes what the platform contains, how the input data were made, the main functionalities, and the model output. See the navigation panel on the left for our [user guide](https://noresmhub.github.io/noresm-land-sites-platform/user_guide), [available sites](https://noresmhub.github.io/noresm-land-sites-platform/land-sites/), [about us](https://noresmhub.github.io/noresm-land-sites-platform/about/), and [contribution guidelines and Code of Conduct](https://noresmhub.github.io/noresm-land-sites-platform/contributing/). 

You can use the platform to run [single-point model simulations](https://en.wikipedia.org/wiki/Climate_model#/media/File:Global_Climate_Model.png "the world is divided into a 3-dimensional grid, where equations can be solved within each gridcell, and information passed between gridcells at certain time points. Single-point model 'runs' only simulate model processes for a single gridcell, which takes a lot less computational power") from a browser on your local computer. We provide [sites](https://noresmhub.github.io/noresm-land-sites-platform/land-sites/) with input data (atmospheric forcing, land surface data), and analysis tools with example python code to plot some input and output data. 

Please let us know if you have questions, suggestions, or trouble using the platform by opening a new [issue](https://github.com/NorESMhub/noresm-land-sites-platform/issues) on GitHub.

*****************************

## Introduction

### Links to NorESM-LSP [GitHub repositories](https://en.wikipedia.org/wiki/Git "a place to store code with version control")

- [NorESMhub/noresm-land-sites-platform](https://github.com/NorESMhub/noresm-land-sites-platform)
- [NorESMhub/noresm-lsp-ui](https://github.com/NorESMhub/noresm-lsp-ui)
- [NorESMhub/noresm-lsp-input](https://github.com/NorESMhub/noresm-lsp-input)
- [NorESMhub/ctsm-api](https://github.com/NorESMhub/ctsm-api)
- [NorESMhub/NorESM](https://github.com/NorESMhub/NorESM)

The main code is stored in the [NorESMhub/noresm-land-sites-platform](https://github.com/NorESMhub/noresm-land-sites-platform) repository. The `main` branch stores the latest functioning version. Older versions can be accessed under [Releases](https://github.com/NorESMhub/noresm-land-sites-platform/releases). This documentation page is made with GitHub pages (`gh-pages` branch) and [Mkdocs](https://www.mkdocs.org/). To contribute to the code or documentation, see our [Contributing](https://noresmhub.github.io/noresm-land-sites-platform/contributing/) instructions. There you will also find our [Code of Conduct](https://noresmhub.github.io/noresm-land-sites-platform/contributing/#code-of-conduct).

### Links to external resources and tutorials

The model framework consists of the Norwegian Earth System Model (NorESM), the Community Land Model (CLM), and the Functionally Assembled Terrestrial Ecosystem Simulator (FATES). Each model has its own documentation and tutorials. Here are some good places to start to get acquainted with the respective models:

#### FATES

- [technical documentation](https://fates-users-guide.readthedocs.io/projects/tech-doc/en/stable/)
- [user guide](https://fates-users-guide.readthedocs.io/en/latest/)
- [GitHub repository](https://github.com/NGEET/fates)

#### CLM

- [technical documentation and user guide](https://escomp.github.io/ctsm-docs/versions/master/html/)
- [GitHub repository](https://github.com/ESCOMP/CTSM)
- [The NCAR-NEON collaboration](https://ncar.github.io/NEON-visualization/) (model-data integration project aimed at beginners)

#### NorESM

- [technical documentation and user guide](https://noresm-docs.readthedocs.io/en/latest/)
- [GitHub repository](https://github.com/NorESMhub/NorESM)

### Glossary of technical terms

#### Software engineering terms

|Term | Definition |
|-----|------------|
| API = Application Programming Interface | An interface for computer programs to communicate with each other. It offers a service to other pieces of software. An API specification is a document or standard that describes how to build or use such a connection or interface. A computer system that meets this standard is said to implement or expose an API. The term API may refer either to the specification or to the implementation. [[Wikipedia]](https://en.wikipedia.org/wiki/API)|
|Container, </br>Container image, </br>Docker | Containers are isolated, virtualized computer environments based on an image, a read-only file with source code, libraries, dependencies, and tools. Docker Inc. provides containers for free personal and educational use. See the [Docker webpage](https://www.docker.com/resources/what-container/) and e.g. the [CLASSIC model's containerisation description](https://doi.org/10.5194/gmd-13-2825-2020)|
|Git, </br>GitHub, </br>repository | Git software enables version control by tracking changes in files. GitHub is an online host of repositories, i.e. data structures of files and their version history.|
|Graphical User Interface (GUI) | An interface between humans and software or hardware, with clickable icons. The NorESM-LSP GUI is accessed after installation and setup at localhost:8080 in a browser, and lets users set up and run model experiments (simulations).|
|Terminal | A computer program where users interact with an operating system by typing in commands (as opposed to clicking and seeing programs in windows). Examples are Windows PowerShell and puTTy. [[Wikipedia]](https://en.wikipedia.org/wiki/Terminal_emulator)|

#### Earth System Modelling terms

| Term | Definition |
|------|------------|
|DGVM, </br>FATES|  |
|LSM,</br>CLM/CTSM| |
|ESM,</br>NorESM| |
|Model coupling, </br>CIME| |
|Stub,</br>Data model| |
|PFT = Plant Functional Type| Plant Functional Types are non-phylogenetic groups of plants, defined by a set of parameters. Parameters include e.g. leaf shape, deciduousness, growth form, allometry equation parameters, maximum specific leaf area, and minimum temperature tolerance.|
|Cohort |A group of individual trees of the same PFT and size.|
|Patch|Tile with a defined age since some disturbance (fire, logging).|
|Forcing data| Data that is not impacted by the model but provided as input, generally from observation data sets. Defines the necessary boundary conditions to the model, e.g. temperature and precipitation, throughout its simulation time.|


### Versions

Platform versions follow standard numbering, and releases below 1 should be considered unstable and preliminary. 

#### List of versions (newest on top):

- [release 1]()
- [archive tag](https://github.com/NorESMhub/noresm-land-sites-platform/releases/tag/archive)
- [tag 0.1.0-dev](https://github.com/NorESMhub/noresm-land-sites-platform/releases/tag/v0.1.0)

#### Model versions

The platform is primarily designed to run the land model (CLM) with the Norwegian Earth System Model. The versions of FATES and CLM therefore have to be in line with stable NorESM versions. NorESM is integrated into the platform via a dedicated `noresm_landsites` branch in the [NorESMhub/NorESM repository](https://github.com/NorESMhub/NorESM/tree/noresm_landsites).


*****************************

## Software architecture

The NorESM-LSP relies on Docker containers and an Application Programming Interface (API). The illustrations below show the relationship between containers and folders for case files, model settings and model files (Figure 1), and between all the NorESM GitHub repositories, Docker images, and containers (Figure 2). 

![Architecture](img/architecture-Page-1.drawio.svg)

*Figure 1: Illustration of the software architecture. The `model` container is expanded to show the two services running in there (i.e. `API` and `Tasks`) in addition to hosting the model and its dependencies. `./resources` contains all the folders that are mounted into the containers by `docker-compose`. The model and the API manage the ones on the left, and the folders on the right are created by the code maintainers -- an asterisk indicates the folder is optional. After [first-time installation and setup](https://noresmhub.github.io/noresm-land-sites-platform/user_guide/#0-prerequisites-first-time-setup), users can access the Web User Interface (UI) and Jupyter server. The UI uses an Application Programming Interface (API) to send commands between the users and containers.*

![Repositories and containers](img/repos_and_containers-MASTER.drawio.svg)

*Figure 2: Illustration of the GitHub repositories and Docker images and containers that make up the NorESM Land Sites Platform. [Dockerfiles](https://doi.org/10.1371/journal.pcbi.1008316) in Github repositories are the basis of static Docker images (read-only files with source code, libraries, dependencies, and tools) that the containers (virtual computer environments where the models can run) can start from. Code in repositories is also sent directly to the containers.*

### Docker containers and model dependencies

CTSM and NorESM depend on many external libraries, which can be challenging to install on a personal computer. The difficulties can be due to a lack of cross-platform support, version conflict with existing libraries, or system architecture.

One solution to this is containerization, which is the process of packaging and distributing software in a way that can be run on various platforms. Containers use Operating System-level virtualization. This allows efficient use of resources while isolating the software from other processes running on the host system. All the requirements for packaged software are included in the container. We used [Docker](https://www.docker.com/) for this purpose. Docker is a widely used and popular containerization tool. 

The packaged software is called an Image. When a Docker Image is run, it is called a Container, i.e., a running instance of the software. The main Image created for the Platform is [ctsm-api](https://github.com/NorESMhub/ctsm-api/pkgs/container/ctsm-api). It contains all the dependencies for the model, the scripts to initialize and configure the model, and the API code that provides access to the model. The Image can be configured via an environment file (`.env`), which gives control to users to adjust some initial properties of the model and the Platform, e.g., what version of the model to use and what drivers should be enabled.

In order to allow easier maintenance and better use of resources, some dependencies are not included in the Image. For example, the message queuing broker (RabbitMQ) required by the API, which is needed to manage asynchronous communications between the model and the API, is not included. This service can be added by using the official [RabbitMQ Docker Image](https://hub.docker.com/_/rabbitmq). Keeping this service out of the Image lets more savvy users pick a different message broker for their use cases.

To address the needs of non-technical users, we have taken care of the extra configurations for the containers by using an orchestration tool called [Docker Compose](https://docs.docker.com/compose/overview/). Docker Compose is a wrapper around Docker, which allows configuring and organizing all the containers in a single `YAML` file.

In addition to the previously mentioned Images, we have included an Image for Jupyter Server and one for our Web User Interface (UI) for `ctsm-api`.

The reason for using a container is that the NorESM model code is not an app but rather a collection of code, and that code needs to be modified in order to run on a new machine. To make the model more like a downloadable app for any machine (e.g. your mac/windows/linux laptop/pc), we put the code in a Docker container that works as a mini-machine within your machine (laptop/pc). A [Docker file](https://docs.docker.com/get-started/overview/ "a text document that contains all the commands a user could call on the command line to assemble an image") is used to enable simulations on any machine, such as a laptop or an HPC cluster. When we release a new version, we have to build a container using this Docker file. Users can then download the container and run simulations there.


**************************************

## Input data preparation

Running the model requires specifying compsets, atmospheric forcing, land surface parameters, and sometimes spin-up to get realistic simulations with stable vegetation. 

Input data is created using the [NorESMhub/noresm-lsp-input](https://github.com/NorESMhub/noresm-lsp-input) repository, and requires access to large amounts of storage to create the necessary input data. This is because the global data files are very large and must be stored somewhere accessible while we subset from them. The scripts in the input repository are therefore run on e.g. Saga or another supercomputer. To add new sites to the LSP or to make new input data, visit the [input repository](https://github.com/NorESMhub/noresm-lsp-input) and read the instructions there. In future releases, we may transition to using NCAR's newly developed [tool for subsetting big input data sets](https://github.com/ESCOMP/CTSM/blob/master/tools/site_and_regional/subset_data) which unfortunately doesn't work with the current version of NorESM (July 2022).

The versioned input data are [in a shared folder on sigma2.no](https://ns2806k.webs.sigma2.no/EMERALD/EMERALD_platform/inputdata_noresm_landsites/). The .tar files are compressed and can be opened as a folder with e.g. 7-zip by right-clicking and choosing 'open archive', and used after extracting (unzipping). The data files are stored in [.nc (NetCDF)](https://www.unidata.ucar.edu/software/netcdf/) format, which can be viewed using [Panoply](https://www.giss.nasa.gov/tools/panoply/), or packages in Python or [R](https://cran.r-project.org/web/packages/ncdf4/index.html). The output data from simulations are stored in the same format but in the specific case folder.

### Component sets (compsets)

Short for component sets, compsets specify which component models are used as well as specific settings for forcing scenarios and physics options. NorESM consists of several sub-models (components) for the atmosphere, land, ocean, etc, plus some common infrastructure code that allows the components to pass information back and forth at certain time steps. Component sets have a short name and a longer name with abbreviations denoting the components included. 

The compset is specified by combining components in this order: atm, lnd, ice, ocn, river, glc, and wave. Each component model version may be "active," "data," "dead," or "stub". Stub components are used instead of active to save computation time and input requirements when that component is not needed for the model configuration. For instance, the active land component forced with atmospheric data does not need ice, ocn, or glc components to be active and can replace them with stubs. The compset long name defines it in the code with the following notation: `TIME_ATM[%phys]\_LND[%phys]\_ICE[%phys]\_OCN[%phys]\_ROF[%phys]\_GLC[%phys]\_WAV[%phys]`. Currently, we only support the following compset using FATES:

>2000_DATM%1PTGSWP3_CLM50%FATES_SICE_SOCN_MOSART_SGLC_SWAV
- TIME: Initialization Time, here for the year 2000 which gives present day conditions (as opposed to pre-industrial or future) of e.g. CO<sub>2</sub> ppm
- ATM: Atmosphere, here DATM%1PTGSWP3 for data-driven (D) atmosphere (ATM) component driven in a point (PT) by [GSWP3](https://www.isimip.org/gettingstarted/input-data-bias-correction/details/4/) forcing data
- LND: Land, here CLM50%FATES/BGC/SP for active Community Land Model version 5.0 and one of the following vegetation modes:
    1. Functionally Assembled Terrestrial Ecosystem Simulator vegetation (FATES)
    2. FATES with BioGeoChemistry (BGC)
    3. FATES simplified mode with Satellite Phenology (SP)
- ICE: Sea-ice, here SICE stub ice
- OCN: Ocean, here SOCN stub ocean
- ROF: River runoff, here MOSART the MOdel for Scale Adaptive River Transport
- GLC: Land Ice, here SGLC stub glacier (land ice) component
- WAV: Wave, here SWAV stub wave component 

More compsets for pre-industrial or future simulations require additional input data and may be included in future versions of the platform. For now, if you need other compsets you need to dig deeper into the CLM technical documentation and provide the necessary input data and code changes yourself. See the [CLM user guide](https://escomp.github.io/ctsm-docs/versions/release-clm5.0/html/users_guide/setting-up-and-running-a-case/choosing-a-compset.html).

### Atmospheric forcing

Atmospheric forcing data drives the modelled climate using a time series of climatic variables. Downloadable data products exist but are often on too coarse scales for realistic single-point simulations. Here is a list of atmospheric forcing variables used in CLM:

- Incident solar radiation (FSDS), 	W/m2
- Temperature at the lowest atmospheric level (TBOT), degrees K (or can be C)
- Precipitation (PRECTmms), mm/s
- Wind speed at the lowest atmospheric level (WIND), m/s

Forcing data for our sites are stored with the rest of the [input data](https://ns2806k.webs.sigma2.no/EMERALD/EMERALD_platform/inputdata_noresm_landsites/). Here are some examples of what the input data .tar contains: 

- CAM/chem/trop_mozart_aero/aero/
    - aerosol deposition: dust, black carbon, organic carbon
- datm7
    - GSWP3v1: monthly atmospheric forcing from the [GSWP3](https://www.isimip.org/gettingstarted/input-data-bias-correction/details/4/) data product. The climatic variables in the above list are stored in these files.
    - NASA_LIS: lightning frequency
    - topo_forcing: topography height

If you have your own data, you can replace the default input files with your own. Make sure the format and units are the exact same, otherwise the model will not be able to use them. For more information on using custom input to CLM, see the [CLM documentation](https://www.cesm.ucar.edu/models/cesm1.0/clm/models/lnd/clm/doc/UsersGuide/x9798.html).

### Surface data

Surface data contains information the model needs about the land surface, such as land use trajectories, soil properties, vegetation parameters, and [albedo](https://en.wikipedia.org/wiki/Albedo). Here are some examples of what the input data .tar contains: 

- 'firedata'
    - population density 
- 'paramdata'
    - CLM5 parameters: many parameters, covering e.g. Plant Functional Types (PFTs), allocation of carbon, photosynthetic pathway
    - FATES parameters: many parameters, covering e.g. Plant Functional Types (PFTs), allometry, carbon pools, nitrogen uptake, mortality, recruitment, fuel load for fire module 
- 'snicardata'
    - snow "growth" parameters
    - snow "optics"
- 'surfdata_map'
    - surface data:  soil depth & other properties, albedo & thermal conductance of different surface types, and fraction of gridcell covered by vegetation, land, & other land cover types
- 'urbandata'
    - urban classes, building interior temperature

Note that when CLM is running without FATES, a simpler 'big-leaf'-version of vegetation is used instead. The CLM5 and FATES parameters thus overlap to some degree, with FATES replacing some and adding other parameters when activated. 

For the integrated field sites, surface data have been created from raw data sets, using [these scripts](https://github.com/NorESMhub/noresm-lsp-input). If you have your own data, you can replace the default input files with your own. Make sure the format and units are the same, otherwise the model will not be able to use them. For more information on using custom input to CLM, see the [CLM documentation](https://www.cesm.ucar.edu/models/cesm1.0/clm/models/lnd/clm/doc/UsersGuide/x9798.html).

**************************************

## Running model experiments

### Graphical User Interface

Users can set up cases, change some model settings, and run simulations via the Web User Interface. Once the platform is correctly up and running, the UI will be available at [localhost:8080](localhost:8080). The web UI is an application that represents some configurable parameters of the model in a user-friendly way. It comes with built-in validations and error handling for the acceptable values of the parameters. Its goal is to streamline the process of editing a case and help users focus on the scientific aspects of their simulations rather than on the technical configuration.

The Web User Interface (UI) code can be found at [https://github.com/NorESMhub/noresm-lsp-ui](https://github.com/NorESMhub/noresm-lsp-ui). The UI is created using [Typescript](https://www.typescriptlang.org/), a superset of JavaScript language, with the [React](https://reactjs.org/) framework.

### API

An Application Programming Interface (API) is a set of tools that enables the end-users to interact with a program. The interaction happens by receiving some commands from the users, performing some actions if necessary, and then sending back some results. We created an HTTP API for the model using FastAPI, a popular high-performance framework for Python. It means the API can be used through any medium that can send and receive HTTP requests, e.g., browsers and libraries like python-requests. FastAPI generates a REST API based on [OpenAPI specifications](https://github.com/OAI/OpenAPI-Specification). It also automatically generates documentation for the API from the docstrings of the python functions, which includes a description of the inputs and outputs and examples. The documentation is interactive and can be accessed through its web-based user interface.

The Platform API is responsible for:

- Getting a copy of the model code (via version control or by downloading the source code).
- Setting up the model's external components.
- Overwriting parts of the model with the specified code in `resources/overwrites` (optional).
- Defining the machine config, i.e., the Docker container, for the model (see `resources/dotcime`).
- Creating, configuring, and running cases.
- Serving inputs and outputs of the created cases.

The API code can be found at [https://github.com/NorESMhub/ctsm-api](https://github.com/NorESMhub/ctsm-api).

### Reaching equilibrium (spin-up phase)

To get realistic simulations, the model needs to run for a while, often hundreds to thousands of years, to reach a state of equilibrium under the applied atmospheric forcing. Starting the model from "bare ground" (= startup run type), the model needs time to grow and kill vegetation - for example, to build up soil carbon storage and to establish stable Plant Functional Type distributions resulting from competitive processes.

**************************************

## Postprocessing

Output is stored in [.nc (NetCDF)](https://www.unidata.ucar.edu/software/netcdf/) format. The model output is stored locally in the noresm-land-sites-platform repository under `resources/cases/<case-id>/archive`, and can optionally be downloaded to another location with the Download Data button in the User Interface. In addition to our notebook and Panoply tools and servers, you can [view NetCDF files](https://en.wikipedia.org/wiki/NetCDF#Applications) using Panoply, or packages in Python or [R](https://cran.r-project.org/web/packages/ncdf4/index.html). 

### Notebooks

Jupyter notebooks combine text and code, and display results directly below the code boxes. When a case has finished successfully you can open the Jupyter server at [localhost:8888](localhost:8888) and work with the model output there, using the provided notebooks. Example and tutorial Jupyter notebooks are stored in  `/notebooks`. Notebooks can easily be copied and changed with whatever changes or additions you make.

The Jupyter server is available as long as the platform containers are up and running. The Jupyter Server Image comes with some commonly used python libraries for data analysis. The list of bundled libraries is available in the [Jupyter Dockerfile](https://github.com/NorESMhub/noresm-land-sites-platform/blob/main/docker/jupyter/Dockerfile).

We can also recommend the NCAR-NEON collaboration tutorials, which also use notebooks and may have additional code inspiration for your analysis: [NCAR-NEON CESM lab](https://ncar.github.io/ncar-neon-books/quick_start_docker.html)

### Panoply

In addition to a Jupyter server, you can open [Panoply](https://www.giss.nasa.gov/tools/panoply/) on [localhost:5800](localhost:5800) while the containers are running. Panoply is useful for exploring the complete set of output variables, and can also generate plots.

**************************************

## Customising the NorESM-LSP

### Adjusting the GUI

#### Model parameters and site configuration

For an overview of the model settings and parameters users can change, see the [user guide](https://noresmhub.github.io/noresm-land-sites-platform/user_guide/). This section describes how the NorESM-LSP code handles the settings that are displayed in the Graphical User Interface.

To be able to set model parameters in the web UI, some configuration files are needed. Both model parameters and site configurations are provided by the maintainers as JSON files in `resources/config/variables_config.json` and `resources/config/sites.json`. They can be modified by users who are familiar with the model. The model parameters file contains a list of JSON objects. Attributes of each object are described in table 1. Note that not all types of variables accepted by the model are supported in the user interface at this point. The tables below describe how these configuration files work and handle the model settings users can change in the UI.

*Table 1: Model parameter attributes, compare to the [variables_config.json](https://github.com/NorESMhub/noresm-land-sites-platform/blob/main/resources/config/variables_config.json) file in `/resources/config`*

| Attribute         | Type                            | default | Required | Scope      | Description                                                                                                                                              |
|-------------------|---------------------------------|---------|----------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| name              | string                          | -       | yes      | Model      | Name of the variable exactly as it should be passed to the model.                                                                                        |
| label             | string                          | -       | no       | UI         | A human-readable label describing the parameter.                                                                                                         |
| category          | string                          | -       | yes      | API        | One of the following: `ctsm_xml`, `user_nl_clm`, `user_nl_clm_history_file`, `fates`, `fates_param`.                                                     |
| type              | string                          | -       | yes      | Model, API | One of the following: `char`, `integer`, `float`, `logical`, `date`.                                                                                     |
| description       | string                          | -       | no       | UI         | Detailed description of the parameter.                                                                                                                   |
| readonly          | boolean                         | false   | no       | UI         | Whether the parameter can be edited by the user.                                                                                                         |
| hidden            | boolean                         | false   | no       | UI         | Whether the parameter should be hidden from the user.                                                                                                    |
| allow_multiple    | boolean                         | false   | no       | API, UI    | Whether the parameter accepts multiple values.                                                                                                           |
| allow_custom      | boolean                         | false   | no       | UI         | Whether users can enter values other than the ones provided as choices (only applies to those parameters with `choices` in their `validation` attribute. |
| validation        | Validation object               | -       | no       | API, UI    | See `Validation` table below ([TODO: X3]).                                                                                                               |
| default           | integer, float, string, boolean | -       | no       | API        | A default value to use. It must match the type specified by the `type` attribute. If `allow_multiple` is set to `true`, it must be a list of values.     |
| placeholder       | string                          | -       | no       | UI         | A placeholder value to show to the user. This value is not actually applied if no value is entered by the user.                                          |
| append_input_path | boolean                         | false   | no       | API        | Whether to adjust a path value based on its relative location in the input folder.                                                                       |


Entered values are checked for correctness with rules defined in the `validation` attribute. Table 2 describes the currently supported validation rules.

*Table 2: validation attributes to define which values are accepted for each model parameter*

| Attribute     | Type                              | Description                                                             |
|---------------|-----------------------------------|-------------------------------------------------------------------------|
| min           | float                             | A minimum value for numeric attributes.                                 |
| max           | float                             | A maximum value for numeric attributes.                                 |
| pattern       | string                            | A regular expression to match the value against.                        |
| pattern_error | string                            | A custom error message for values not matching the `pattern` attribute. |
| choices       | [integer, float, string, boolean] | A list of choices for users to select from.                             |


Sites in `resources/config/sites.json` are described as [GeoJSON points](https://datatracker.ietf.org/doc/html/rfc7946#section-3.1.2). The interactive map in the web UI draws on these site definitions. Their configuration is set in the `properties` attribute of the GeoJSON object, as described in table 3.

*Table 3: Site geoJSON properties, compare with the [sites.json](https://github.com/NorESMhub/noresm-land-sites-platform/blob/main/resources/config/sites.json) file in `/resources/config`*

| Attribute | Type            | Required | Description                                                                                                                                                                                                                                                                       |
|-----------|-----------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| name      | string          | yes      | Name of the site.                                                                                                                                                                                                                                                                 |
| compset   | string          | yes      | The component set to use with the model.                                                                                                                                                                                                                                          |
| res       | string          | yes      | The resolution/grid to use with the model.                                                                                                                                                                                                                                        |
| config    | [Config object] | no       | Config is an object with two keys: `name` and `value`.<br/>The former must point to a parameter in `resources/config/variables_config.json`.<br/>The latter must be a valid value for that parameters.<br/>These are used as default values for the given parameter for the site. |



### Running the NorESM-LSP remotely

Containerisation of software like the NorESM-LSP and models (NorESM, CLM, FATES) makes it possible to publish it on other services, e.g. **cloud computing services** where users can sign up and run model experiments remotely. That way, users don't have to install anything on their own computers. For long or multiple experiments, using remote computing resources may be necessary. An early version of the NorESM-LSP exists on Galaxy, a free and open cloud computing service. It is also possible to run the NorESM-LSP on a remote computer, like a research-infrastructure computer cluster (e.g. NREC, Saga, Fram for University of Oslo users), via an **[ssh tunnel](https://en.wikipedia.org/wiki/Tunneling_protocol#Secure_Shell_tunneling)**. If you need to run many or long simulations, a remote computer may be beneficial because it doesn't take up your local computer's resources and doesn't require your local computer to be turned on throughout the simulation time.

#### Galaxy Tool for FATES
Galaxy is free to use and only requires registering as a user. Note that this tool is to be considered a pilot version, and does not include all the functionalities of the NorESM-LSP. It does, on the other hand, include metadata to make it FAIR (Findable, Accessible, Interoperable, Reusable), and has Research Objects on [ROHub](https://reliance.rohub.org/).

- [Tutorial with the CLM-FATES Galaxy tool](https://training.galaxyproject.org/training-material/topics/climate/tutorials/fates/tutorial.html)

#### SSH tunneling, with example for NREC

These instructions require the remote machine to allow remote access via SSH. If you want to run the NorESM-LSP on a server without this capability, you will need to talk to your local IT department to find a different solution. We describe all required steps from scratch and not all steps might be necessary for all virtual/remote machines (e.g. Docker may already be installed). The instructions are tailored for and tested on [NREC](https://www.nrec.no/) (remote) and Windows with Ubuntu subsystem (local) and might need adaptations on other systems. On NREC, we use a new instance based on the `GOLD Ubuntu 22.04 LTS` base image. The commands to install programs etc. may differ for other distributions and operating systems.

**1 Run the platform remotely**

1. Open a terminal that has the ssh command [installed](https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-20-04/) and access the remote machine (e.g. users at the University of Oslo can run a Virtual Machine on [NREC](https://www.uio.no/studier/emner/matnat/ifi/IN3230/h20/oblig/running-your-vm-on-nrec.html)): 
```
ssh [user]@[ip] # for example:
ssh ubuntu@158.37.65.132
```

2. Install git, clone the [NorESM-LSP repository](https://github.com/NorESMhub/noresm-land-sites-platform): 
```
git clone https://github.com/NorESMhub/noresm-land-sites-platform.git --config core.autocrlf=input
```
and make sure the following lines of code allow users to access its functionalities from the outside. In `/noresm-land-sites-platform/docker/api/.env` (open with an editor or IDE, e.g. `vi .env`), line 2, change to:
```
BACKEND_CORS_ORIGINS=["*"]
```

3. Install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/compose-plugin/#install-using-the-repository). Subsequently, add the current user to the Docker user group if you get an error related to access rights (may require restarting the terminal when finished):
```
[sudo] usermod -a -G docker $USER
newgrp docker
```

4. Start a new named screen session:
```
screen -S lsp
```

May require sudo/admin rights and the installation of `screen`, e.g. on Debian/Ubuntu:
```
[sudo] apt install screen
```

5. Change into the project directory via `cd noresm-land-sites-platform` and install the NorESM-LSP via `docker-compose up` or `docker compose up` (depends on the Docker installation; also described in the user guide).

6. Once everyting is up and running, detach your current screen session by subsequently pressing `CTRL+a` and `CTRL+d`. The session
should now appear when you type `[sudo] screen -list`.

7. Open a new local terminal and enable ssh port listening to the relevant NorESM-LSP ports:
```
ssh -L 8000:localhost:8000 -N -f [user]@[ip] # API
ssh -L 8080:localhost:8080 -N -f [user]@[ip] # GUI
ssh -L 8888:localhost:8888 -N -f [user]@[ip] # JupyterLab
ssh -L 5800:localhost:5800 -N -f [user]@[ip] # Panoply
```
where `[user]@[ip]` must be the same as in step 1. You will probably need to enter your password each time you open a port.

**Attention!** If one or multiple of these ports are already in use, change the number after the second colon or execute step 9 and retry this step.

8. Open your local browser and access the NorESM-LSP tools of your choice. Enter into the address bar (remember to adapt the port numbers if you changed them in step 7.):
```
localhost:8000/api/v1/docs # API dashboard
localhost:8080             # GUI
localhost:8888             # JupyterLab 
localhost:5800             # Panoply
```
You can now build/run model experiments as usual. Once the models are running, you can close the browser and shut off your computer. If you restart your machine, re-execute step 7 to be able to access the programs again.

9. To stop the port listening described above manually:
```
fuser -k 8080/tcp
fuser -k 8000/tcp
fuser -k 8888/tcp
fuser -k 5800/tcp
```
where the port numbers must correspond to the numbers you specified in step 7.

10. Once you are ready to shut off the NorESM-LSP, reattach the screen session via:
```
screen -r lsp
```
and stop the running containers (`CTRL+c`). To kill the screen session, detach (`CTRL+a` and `CTRL+d`) and enter:
```
screen -XS lsp quit
```

**2 Download the results**

To download the results to your local machine, you can either use a dedicated file transfer program such as [WinSCP](https://winscp.net/eng/download.php) or bash commands such as `scp`. To copy a `case` folder from the remote server using `scp`:

```
scp -r [user]@[ip]:[remote_path_to_lsp]/resources/cases/[case_folder_name] [local_save_path]
```
For example:
```
# Note the trailing dot, which denotes copying into the current working directory!
scp -r ubuntu@158.37.65.123:/home/ubuntu/noresm-land-sites-platform/resources/cases/5994e825658b853b95d61feccffd18ad_bor1-1000y .
```
Be aware that model outputs for long simulations can result in large file sizes; make sure you have enough space available on your disk.


**************************************

*This is the end of the technical documentation. Are you missing something? Please let us know by posting an [issue](https://github.com/NorESMhub/noresm-land-sites-platform/issues)*