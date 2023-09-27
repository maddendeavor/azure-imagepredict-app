[![testcoverage](/doc/testcoverage_badge.svg)](/doc/testcoverage.txt)
[![maintainability](/doc/maintainability_badge.svg)](/doc/maintainability.txt)
[![docstring_coverage](/doc/docstringcoverage_badge.svg)](/doc/docstringcoverage.txt)
[![doc_style](https://img.shields.io/badge/%20style-numpy-459db9.svg)](https://numpydoc.readthedocs.io/en/latest/format.html)

# Azure Image Prediction Application
This project is an example application using Azure Functions to provide a REST interface 
for interacting with an Image Prediction Model from torchvision.


## Installation/Build Instructions
First you must create an azure account with the correct credentials.

And install [Azure Core function tools](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=linux%2Cisolated-process%2Cnode-v4%2Cpython-v2%2Chttp-trigger%2Ccontainer-apps&pivots=programming-language-csharp#install-the-azure-functions-core-tools)


## Running the Application Locally
Install the project into the virtual environment as listed in the Contributing section below.
```commandline
python3 -m venv .venv
source .venv/bin/activate (linux) or source .venv/Scripts/activate (windows)
pip install --no-cache-dir -r requirements.txt
```

Once in the venv you can run the application locally within the project folder:
```commandline
func start --verbose
```
or within VS Studio:
Start the emulator by pressing `F1` and selection `Azurite: Start`
Run locally by going to Run & Debug panel and pushing `F5` and then sending a request


## Testing the App Locally
Test the app by opening a browser and running the following request:
<http://localhost:7071/api/predict?img=https://raw.githubusercontent.com/gvashishtha/functions-pytorch/master/resources/assets/Bernese-Mountain-Dog-Temperament-long.jpg>

This project also provides a frontend splash page that you can run locally to interface with the application.
Open the file in `frontend/index.html` which will open a place for you to submit to an image URL for classification.
Try this one to see a bald eagle classified: <https://i.natgeofe.com/k/afe51970-80c6-46c3-b047-4c407c72d874/bald-eagle-closeup_4x3.jpg>

## Deploying the App

To deploy the project see the publish-to-azure project below.  
The `deploy_app` bash file to setup the Azure application structure.
Note that names will need to be changed to make them unique.

To deploy the latest code, run the following within the virutal environement:
```commandline
func azure functionapp publish azImagePredictor --build local
func azure functionapp publish azImagePredictor --build-native-deps
```
Use the remote version of the statement above if there is issue with the build

## Testing the App after Deployment

If you deploy to Azure you can replace the http://localhost:7071 in the statements above with 
the deployed application URL: <https://azimagepredictor.azurewebsites.net>

Similarly there is a file `frontend/index_deployed.html` which points to the deployed URL above.


## References
* https://learn.microsoft.com/en-us/azure/azure-functions/machine-learning-pytorch?tabs=bash
* https://learn.microsoft.com/en-us/azure/azure-functions/create-first-function-vs-code-python?pivots=python-mode-decorators#publish-the-project-to-azure
* https://learn.microsoft.com/en-us/azure/azure-functions/functions-bindings-http-webhook-trigger?tabs=python-v1%2Cin-process%2Cnodejs-v4%2Cfunctionsv2&pivots=programming-language-python#example
* https://learn.microsoft.com/en-us/azure/azure-functions/functions-reference-python?tabs=asgi%2Capplication-level&pivots=python-mode-decorators#development-options

## Contributing
* To contribute to the repository use the following:
```commandline
git clone <ENTER SSH HERE>
cd reponame
git lfs install
git checkout -b feature/feature_name
git add <files>
git commit -m "Add my feature"
git push origin feature/feature_name
```

