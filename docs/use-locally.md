## ✅ | Pre-Requisites

To work through this tutorial you will need:
1. Azure account with active subscription.
2. GitHub account with access to GitHub Codespaces.
3. (Optional) Set of docs that represent "your custom data".
4. Install [Python 3.10](https://www.python.org/) or higher.

The sample comes with a set of "product data" docs as default custom data. 

Make sure you have [access to the Azure AI Studio](https://learn.microsoft.com/en-us/azure/ai-studio/faq#how-can-customers-access-azure-ai-studio--) in your region, and can access related resources in your subscription. Refer to the [Azure AI Studio FAQ](https://learn.microsoft.com/en-us/azure/ai-studio/faq#how-can-customers-access-azure-ai-studio--) for more details on regional availability, pricing and more.

# Getting Started Locally

If you want to get started in your local environment, first install the packages:
```
git clone https://github.com/azure/aistudio-copilot-sample
cd aistudio-copilot-sample
pip install -r requirements.txt
```

Then install the Azure AI CLI, on Ubuntu:
```
curl -sL https://aka.ms/InstallAzureAICLIDeb | sudo bash
```

To install the CLI on Windows and MacOS, follow the instructions [here](https://github.com/Azure/azureai-insiders/blob/main/previews/aistudio/how-to/use_azureai_sdk.md#install-the-cli).

## Step 2: Create and connect to Azure Resources

Run ai init to create and/or connect to existing Azure resources:
```
ai init
```

- This will first prompt to you to login to Azure
- Then it will ask you to select or create resources, choose  **AI Project resource** and follow the prompts to create an Azure OpenAI resource, model deployments, and Azure AI  search resource
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

## Step 4: Run the co-pilot with a sample question

To run a single question & answer through the sample co-pilot:
```bash
python src/run.py --question "which tent is the most waterproof?"
```

To run a sample implementation of LangChain, specify the `--implementation` flag with a `langchain`:

```bash
python src/run.py --implementation langchain --question "what is the waterproof rating of the tent I just ordered?"
```

## Step 5: Delete your Azure resources

To delete the Azure resources created in this tutorial, complete the following steps:

1. [Launch the Azure AI Studio](https://aka.ms/azureaistudio).  Verify that you are in logged in the studio.  If not, click on the **Sign In** button in the top right corner of the page. 

![](/img/5-1-ai-search-sign-up.png)

2. Click on the **Manage** tab.

![](/img/5-1-ai-search-manage.png)

3. Under **Your resource** section, click on the **Azure Portal** link.  This will redirect you to the Azure Portal for your Azure AI Studio resource.

4. Click on your **resource group**.

![](/img/5-3-ai-search-resource-group.png)

5. Click on the **Delete resource group** button.

![](/img/5-4-ai-search-delete-resource-group.png)

5. On the delete a resource group pane, type in the **delete** in the **Enter resource group name to confirm deletion** field.  Then click on the **Delete** button.

6. Wait for the resource group to be deleted.  This may take a few minutes.

### Follow the full tutorial

For a more detailed tutorial using this notebook, you can follow the [Build a co-pilot using the Azure AI SDK](https://github.com/Azure/azureai-insiders/blob/aistudio-preview/previews/aistudio/tutorials/copilot_with_sdk.md) tutorial.

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
