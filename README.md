> IMPORTANT NOTE: This fork implements a workaround to avoid the 10,000 entry limit in the PubMed API (For details see [PubMed documentation](https://www.ncbi.nlm.nih.gov/books/NBK25499/)).
In order to work, the Unix command line tool [EDirect](https://www.ncbi.nlm.nih.gov/books/NBK179288/) needs to be installed (see installation details). 
 
# PyMed - PubMed Access through Python
PyMed is a Python library that provides access to PubMed through the PubMed API.

## Why this library?
The PubMed API is not very well documented and querying it in a performant way is too complicated and time consuming for researchers. This wrapper provides access to the API in a consistent, readable and performant way.

## Installation
### EDirect installation
EDirect can only be installed in Unix and Mac with the following commands on the terminal:
``sh -c "$(wget -q https://ftp.ncbi.nlm.nih.gov/entrez/entrezdirect/install-edirect.sh -O -)"``
As a convenience, the installation process ends by offering to run the PATH update command for you. Answer "y" and press the Return key if you want it run. If the PATH is already set correctly, or if you prefer to make any editing changes manually, just press Return.
Once installation is complete, run:
``export PATH=${HOME}/edirect:${PATH}``
to set the PATH for the current terminal session.

### Package installation
To install the patch in this fork, clone this repository and install it from its local location by running:
``python -m pip install -e.``
> NOTE: if you will use pymed as a dependency of another package (e.g. paperscraper), make sure that the right implementation of pymed was installed. 

## Features
This library takes care of the following for you:

- Querying the PubMed database (with the standard PubMed query language)
- Batching of requests for better performance
- Parsing and cleaning of the retrieved articles

## Examples
For full (working) examples have a look at the `examples/` folder in this repository. In essence you only need to import the `PubMed` class, instantiate it, and use it to query:

```python
from pymed import PubMed
pubmed = PubMed(tool="MyTool", email="my@email.address")
results = pubmed.query("Some query", max_results=500)
```

## Notes on the API
The original documentation of the PubMed API can be found here: [PubMed Central](https://www.ncbi.nlm.nih.gov/pmc/tools/developers/). PubMed Central kindly requests you to:

> - Do not make concurrent requests, even at off-peak times; and
> - Include two parameters that help to identify your service or application to our servers
>   * _tool_ should be the name of the application, as a string value with no internal spaces, and
>   * _email_ should be the e-mail address of the maintainer of the tool, and should be a valid e-mail address.

## Notice of Non-Affiliation and Disclaimer 
The author of this library is not affiliated, associated, authorized, endorsed by, or in any way officially connected with PubMed, or any of its subsidiaries or its affiliates. The official PubMed website can be found at https://www.ncbi.nlm.nih.gov/pubmed/.
