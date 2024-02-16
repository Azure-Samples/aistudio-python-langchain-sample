## ✅ | Pre-Requisites

To work through this tutorial you will need:
1. Azure account with active subscription.
2. GitHub account with access to GitHub Codespaces.
3. (Optional) Set of docs that represent "your custom data".
4. Install [Python 3.10](https://www.python.org/) or higher.

The sample comes with a set of "product data" docs as default custom data. 

Make sure you have [access to the Azure AI Studio](https://learn.microsoft.com/en-us/azure/ai-studio/faq#how-can-customers-access-azure-ai-studio--) in your region, and can access related resources in your subscription. Refer to the [Azure AI Studio FAQ](https://learn.microsoft.com/en-us/azure/ai-studio/faq#how-can-customers-access-azure-ai-studio--) for more details on regional availability, pricing and more.

# Getting Started using GitHub Codespaces

To get started quickly, you can use a pre-built development environment. **Click the button below** to open the repo in GitHub Codespaces, and then continue the readme!

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/Azure-Samples/aistudio-python-langchain-sample?quickstart=1)  

This will launch a Codespaces environment with all the dependencies installed.  Once the environment is ready, you can run the following commands to create the Azure resources and run the sample code.

**Note**: You can also access the codespaces by clicking on the green **Code** button in the top right of the repo.  Then selecting the "Codespaces" tab and clicking on the **Create codespace on main** button to launch the Codespaces environement.

![](/img/gh-codespaces.png)

## Set up your development environment

1. Login into your Azure subscription account:

```
az login --use-device-code
```

1. Create and connect to Azure Resources


2. Create and connect to Azure Resources


For best experience choose one of these preview regions for this exercise:
- Canada East
- North Central US
- Sweden
 
Run ai init to create and/or connect to existing Azure resources:
```
ai init
```

- This will will ask you to select or create resources, choose  **New AI Project**.

![](/img/ai-init.png)

- Select your subscription from the pop-up window, then follow the prompts to create an Azure OpenAI resource, model deployments, and Azure AI  search resource


- This will generate a config.json file in the root of the repo, the SDK will use this when authenticating to Azure AI services.



Note: You can open your project in [AI Studio](https://aka.ms/AzureAIStudio) to view your projects configuration and components (generated indexes, evaluation runs, and endpoints)

## Step 3: Build an Azure Search index

Run the following CLI command to create an index that our code can use for data retrieval:
```
ai search index update --files "./data/3-product-info/*.md" --index-name "product-info"
```

Now, generate a .env file that will be used to configure the running code to use the resources we've created in the subsequent steps
```
ai dev new .env
```

## Step 4: Run the co-pilot with Jupiter notebook

To run a single question & answer through the sample co-pilot:

1. Open the `copilot_langchain.ipynb` notebook in the visual studio code (VS code) editor.

![](/img/3-select-kernel.png)

2. In VS code, click on **Select Kernel**. Then under Python Environments, select the **Python 3.10.13** environment you just created

![](/img/3-python-env.png)

3. Click on **Run All** to run the notebook.

![](/img/4-run-all.png)

4. Try asking another question about the products in the dataset. For example:
```
which tent is the most waterproof?
```
![](/img/5-question.png)



### Customize the development container

You can pip install packages into your development environment but they will disappear if you rebuild your container and need to be reinstalled (re-build is not automatic). You may want this, so that you can easily reset back to a clean environment. Or, you may want to install some packages by default into the container so that you don't need to re-install packages after a rebuild.

To add packages into the default container, you can update the Dockerfile in `.devcontainer/Dockerfile`, and then rebuild the development container from the command palette by pressing `Ctrl/Cmd+Shift+P` and selecting the `Rebuild container` command.

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
