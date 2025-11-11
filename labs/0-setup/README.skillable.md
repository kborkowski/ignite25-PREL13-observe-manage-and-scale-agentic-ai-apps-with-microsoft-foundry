# Lab Setup Instructions - Skillable Environment

> **🎯 For Microsoft Ignite Attendees**: This guide is for participants using the Skillable lab environment at Microsoft Ignite.

---

## 📋 Prerequisites

Before you begin, ensure you have:

- ✅ **Personal GitHub account** - [Sign up here for free](https://github.com/signup)
- ✅ **Basic familiarity** with:
  - Git, Visual Studio Code, Python, and Jupyter notebooks
  - Generative AI concepts and workflows
- ✅ **Skillable lab credentials** - Provided by your lab instructor

---

## 🚀 Step 1: Launch Your Development Environment

### Launch GitHub Codespaces

Click the button below to launch your pre-configured development environment:

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://aka.ms/ignite25/PREL13)

**What to expect:**
1. A new browser tab will open with a VS Code interface
2. Wait for the environment to fully load (1-2 minutes)
3. You'll see the project files in the Explorer panel on the left

> **💡 Tip**: Keep the Skillable lab credentials tab open - you'll need them in the next step!

---

## 🔐 Step 2: Authenticate With Azure

### Connect to your Azure subscription

1. **Open a terminal** in VS Code:
   - Click `Terminal` → `New Terminal` from the top menu
   - Or press `` Ctrl+` `` (backtick key)

2. **Run the Azure login command**:
   ```bash
   az login
   ```

3. **Complete the authentication**:
   - A browser window will open automatically
   - Use the Azure credentials provided in your Skillable lab
   - Return to VS Code once authentication is complete

4. **Verify successful login**:
   - You should see your subscription details in the terminal
   - Look for confirmation that you're logged in

> **✅ Success indicator**: You'll see subscription information displayed in the terminal

---

## ⚙️ Step 3: Configure Your Environment

### Run the automated setup script

Execute the automated configuration script to discover and populate your environment variables:

```bash
./scripts/1-get-env-skillable.sh
```

**What this script does:**
- ✅ Auto-discovers your resource group (rg-Ignite*)
- ✅ Retrieves Azure OpenAI API keys
- ✅ Retrieves Azure AI Search API keys
- ✅ Configures Application Insights connection
- ✅ Sets up all required environment variables
- ✅ Selects `text-embedding-3-large` as the embedding model
- ✅ Configures the agent as `agent-template-assistant`

**Expected output:**

**Expected output:**

```
════════════════════════════════════════════════════════════════
    Azure Environment Setup - Skillable
════════════════════════════════════════════════════════════════

Step 1: Verifying Azure CLI installation...
✓ Azure CLI installed (version: 2.x.x)

Step 2: Checking Azure authentication...
✓ Logged in to Azure

Step 3: Discovering resource groups...
✓ Found resource group: rg-Ignite-XXXXX

Step 5: Discovering Azure OpenAI resources...
✓ Found Azure OpenAI: aoai-XXXXXXX
  Embedding Model: text-embedding-3-large (text-embedding-3-large)

Step 8: Configuring Agent Name...
Using agent name: agent-template-assistant

════════════════════════════════════════════════════════════════
✅ Environment Setup Complete!
════════════════════════════════════════════════════════════════
```

> **💡 Troubleshooting**: If the script fails, ensure you're logged in to Azure (Step 2) and have access to the Skillable resource group.

---

## 📊 Step 4: Populate the Product Catalog

### Load sample products into Azure AI Search

Now that your environment is configured, populate the search index with sample product data:

```bash
python ./scripts/2-add-product-index.py
```

**What this script does:**
- Reads product data from the CSV file
- Creates embeddings for semantic search
- Uploads products to your Azure AI Search index
- Configures the index for vector search

**Expected output:**

```
======================================================================
Add Products to Azure AI Search Index
======================================================================
Using environment variables from system/default locations
✓ Azure CLI authentication verified
Running RBAC update script to ensure proper permissions...

Uploading 49 products to index 'zava-products'...
✓ Successfully uploaded 49 products to the search index!

The product catalog is now ready for semantic search.
======================================================================
```

> **✅ Success indicator**: You should see "Successfully uploaded 49 products" in the output.

---

## 🎓 Step 5: Launch the Lab Instructions

### Start the documentation server

1. **Open a new terminal** in VS Code (or use the existing one)

2. **Start the documentation server**:
   ```bash
   mkdocs serve
   ```

3. **Open the preview**:
   - A pop-up dialog will appear asking to open in browser
   - Click **"Open in Browser"** or **"Open in Editor"**
   - The lab instruction guide will open in a new tab

4. **Navigate the labs**:
   - You'll see a complete navigation menu on the left
   - Labs are organized sequentially from 0-7
   - Start with **Lab 0: Setup Validation**

> **💡 Tip**: Keep the instruction guide open in a separate tab while working through the notebooks.

---

## ✅ Step 6: Validate Your Setup

### Run the validation notebook

Before starting the main labs, verify everything is configured correctly:

1. **Open the validation notebook**:
   - Navigate to `labs/0-setup/00-validate-setup.ipynb`
   - Or use the link in the instruction guide

2. **Run all cells**:
   - Click `Run All` from the toolbar
   - Or run each cell individually with `Shift+Enter`

3. **Check for success**:
   - All cells should execute without errors
   - Environment variables should be properly set
   - Azure connections should be verified

**What gets validated:**
- ✅ All required environment variables are set
- ✅ Azure OpenAI connection is working
- ✅ Azure AI Search index is accessible
- ✅ AI Foundry project is configured
- ✅ Application Insights is connected

> **🎯 Ready to proceed**: If all validations pass, you're ready to start the main labs!

---

## 📚 Step 7: Work Through the Labs

### Recommended lab sequence

Follow the labs in order for the best learning experience:

1. **Lab 0**: Setup & Validation _(You just completed this!)_
2. **Lab 1**: Build AI Agents
3. **Lab 2**: Model Selection & Evaluation
4. **Lab 3**: Model Customization & Fine-tuning
5. **Lab 4**: Evaluation at Scale
6. **Lab 5**: Tracing & Observability
7. **Lab 6**: Deployment
8. **Lab 7**: Teardown

> **💡 Navigation**: Use the instruction guide's sidebar to jump between labs easily.

---

## 🧹 Step 8: Teardown & Cleanup

### When you're done with the labs

**Automatic cleanup:**
- Simply close your Skillable lab session
- All Azure resources will be automatically removed
- No manual cleanup is required

**GitHub Codespaces:**
- Your Codespace will automatically stop after inactivity
- You can manually delete it from: [github.com/codespaces](https://github.com/codespaces)

> **💰 Cost Note**: Skillable labs are pre-configured with resource quotas and automatic cleanup to prevent unexpected costs.

---

## 🆘 Troubleshooting

### Common issues and solutions

| Issue | Solution |
|-------|----------|
| **Script fails with "Not logged in"** | Run `az login` again and complete authentication |
| **Resource group not found** | Ensure you're using the credentials from Skillable lab |
| **MkDocs won't start** | Try `pip install -r requirements-dev.txt` first |
| **Notebook kernel not found** | Select the Python kernel from the top-right kernel picker |

### Additional resources

- 💬 Ask your lab instructor for help
- 🐛 [Report issues on GitHub](https://github.com/Azure-Samples/ignite25-PREL13/issues)
- 💬 Join our community on Discord to interact with other developers:

[![Discord](https://img.shields.io/badge/Discord-Join%20Community-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/3cmBfTFkH7)
---

**🎉 Congratulations!** Your lab environment is ready. Start exploring the power of Azure AI Foundry!