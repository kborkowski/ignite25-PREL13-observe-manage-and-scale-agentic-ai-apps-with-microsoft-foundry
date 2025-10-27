# PREL13 Labs

This document lists the various labs in this repository with guidance on dependencies and setup.

---

## 1-Begin-Here

Setup and validation notebooks to configure your Azure environment.

| Notebook | Description | Environment Variables Required |
|----------|-------------|-------------------------------|
| `1-setup/01-create-search-index.ipynb` | Creates Azure AI Search index for Zava product catalog with vector search capabilities. Uploads product data and generates embeddings. | `AZURE_OPENAI_ENDPOINT`, `AZURE_AISEARCH_ENDPOINT`, `AZURE_AISEARCH_INDEX` |
| `2-validate/validate-setup.ipynb` | Validates all required environment variables are properly configured. Checks Azure, OpenAI, AI Foundry, Search, Agent, Embedding, Container, and Monitoring configurations. | **Azure Core:** `AZURE_ENV_NAME`, `AZURE_LOCATION`, `AZURE_RESOURCE_GROUP`, `AZURE_SUBSCRIPTION_ID`, `AZURE_TENANT_ID` <br>**Azure OpenAI:** `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_VERSION`, `AZURE_OPENAI_DEPLOYMENT`, `AZURE_OPENAI_VERSION`, `AZURE_OPENAI_CHAT_DEPLOYMENT` <br>**AI Foundry:** `AZURE_AI_FOUNDRY_NAME`, `AZURE_AI_PROJECT_NAME`, `AZURE_EXISTING_AIPROJECT_ENDPOINT`, `AZURE_EXISTING_AIPROJECT_RESOURCE_ID` <br>**AI Search:** `AZURE_SEARCH_ENDPOINT`, `AZURE_AISEARCH_ENDPOINT`, `AZURE_AI_SEARCH_ENDPOINT`, `AZURE_SEARCH_API_KEY`, `AZURE_SEARCH_INDEX_NAME`, `AZURE_AISEARCH_INDEX`, `AZURE_AI_SEARCH_INDEX_NAME` <br>**Agent Config:** `AZURE_AI_AGENT_DEPLOYMENT_NAME`, `AZURE_AI_AGENT_MODEL_NAME`, `AZURE_AI_AGENT_MODEL_VERSION`, `AZURE_AI_AGENT_DEPLOYMENT_CAPACITY`, `AZURE_AI_AGENT_NAME` <br>**Embedding:** `AZURE_AI_EMBED_DEPLOYMENT_NAME`, `AZURE_AI_EMBED_MODEL_NAME`, `AZURE_AI_EMBED_MODEL_VERSION`, `AZURE_AI_EMBED_DEPLOYMENT_CAPACITY`, `AZURE_AI_EMBED_DEPLOYMENT_SKU`, `AZURE_AI_EMBED_DIMENSIONS`, `AZURE_AI_EMBED_MODEL_FORMAT` <br>**Container Apps:** `AZURE_CONTAINER_ENVIRONMENT_NAME`, `AZURE_CONTAINER_REGISTRY_ENDPOINT`, `SERVICE_API_NAME`, `SERVICE_API_URI`, `SERVICE_API_ENDPOINTS`, `SERVICE_API_IDENTITY_PRINCIPAL_ID`, `SERVICE_API_AND_FRONTEND_IMAGE_NAME` <br>**Monitoring:** `USE_APPLICATION_INSIGHTS`, `ENABLE_AZURE_MONITOR_TRACING`, `AZURE_TRACING_GEN_AI_CONTENT_RECORDING_ENABLED`, `APPLICATIONINSIGHTS_CONNECTION_STRING`, `APPLICATIONINSIGHTS_INSTRUMENTATION_KEY`, `APPLICATION_INSIGHTS_CONNECTION_STRING` <br>**Tracing Labs:** `API_HOST`, `OPENAI_API_KEY` |

---

## 2-Explore-Agent

Explore agent implementations using Azure AI Agent Service and agent frameworks.

| Notebook | Description | Environment Variables Required |
|----------|-------------|-------------------------------|
| `1-agent-service/lab-exercise.ipynb` | Explore Azure AI Agent Service capabilities (TBD - notebook currently empty) | TBD |
| `2-agent-framework/lab-exercise.ipynb` | Explore agent framework implementations (TBD - notebook currently empty) | TBD |

---

## 3-Customize-Model

Model customization techniques including fine-tuning, custom evaluators, and distillation.

| Notebook | Description | Environment Variables Required |
|----------|-------------|-------------------------------|
| `1-Finetuning/basic-fine-tuning.ipynb` | Demonstrates supervised fine-tuning (SFT) to customize model tone and style. Validates training data, uploads to Azure OpenAI, and creates fine-tuned models. | `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_VERSION` |
| `2-Custom-Politeness-Evaluator/creating-grader.ipynb` | Creates a custom politeness evaluator/grader to assess model responses. Defines grading criteria and validates against baseline responses. | `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_VERSION` |
| `3-Distillation/adding-distillation.ipynb` | Demonstrates knowledge distillation from a larger teacher model to a smaller student model for cost-effective deployment while maintaining quality. | `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_VERSION`, `AZURE_SUBSCRIPTION_ID`, `AZURE_RESOURCE_GROUP`, `AZURE_AI_FOUNDRY_NAME` |

---

## 4-Run-Evaluations

Comprehensive evaluation notebooks covering quality, safety, and agent-specific evaluators.

| Notebook | Description | Environment Variables Required |
|----------|-------------|-------------------------------|
| `0-speed-run/lab-exercise.ipynb` | Speed-run through all evaluator types: Quality (Coherence, Fluency), Composite (QA), Agent (Intent Resolution, Tool Call Accuracy, Task Adherence), and Azure OpenAI Graders (Label, String, Similarity, Python). | `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_DEPLOYMENT`, `AZURE_OPENAI_API_VERSION` |
| `1-simulate-data/lab-exercise.ipynb` | Generate synthetic evaluation data (TBD - notebook currently empty) | TBD |
| `2-run-evaluation/1-lab-exercise.ipynb` | Run comprehensive evaluations on agent responses (TBD - notebook currently empty) | TBD |
| `3-explore-evaluators/lab-quality-evaluators.ipynb` | Deep dive into quality evaluators (TBD - notebook currently empty) | TBD |
| `3-explore-evaluators/lab-agent-evaluators.ipynb` | Deep dive into agent-specific evaluators (TBD - notebook currently empty) | TBD |
| `3-explore-evaluators/lab-aoai-graders.ipynb` | Deep dive into Azure OpenAI graders (TBD - notebook currently empty) | TBD |
| `3-explore-evaluators/lab-safety-evaluators.ipynb` | Deep dive into safety and risk evaluators (TBD - notebook currently empty) | TBD |

---

## 5-Observability

Telemetry, tracing, and monitoring for AI agents using OpenTelemetry and Azure Monitor.

| Notebook | Description | Environment Variables Required |
|----------|-------------|-------------------------------|
| `01-trace-agent-session.ipynb` | Demonstrates emitting OpenTelemetry spans for agent workflows using GenAI semantic conventions. Shows agent creation, invocation, and tool execution tracing. | None (uses console exporter) |
| `02-collect-span-snapshots.ipynb` | Shows how to capture and validate agent telemetry locally using in-memory span exporters before sending to production backends. | None (uses in-memory exporter) |
| `1-OpenAIAgents/weekend_planner.ipynb` | Complete example of Azure OpenAI Agents with telemetry instrumentation. Demonstrates weekend planning agent with tool calls and Azure Monitor integration. | `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_VERSION`, `AZURE_OPENAI_MODEL_NAME`, `APPLICATION_INSIGHTS_CONNECTION_STRING` (optional), `AZURE_AI_FOUNDRY_NAME`, `AZURE_AOAI_ACCOUNT`, `AZURE_SUBSCRIPTION_ID`, `AZURE_RESOURCE_GROUP` |
| `2-LangChain/weekend_planner.ipynb` | Weekend planner agent implemented with LangChain framework, demonstrating telemetry integration with LangChain agents. | `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_API_VERSION`, `AZURE_OPENAI_MODEL_NAME`, `APPLICATION_INSIGHTS_CONNECTION_STRING` (optional) |
| `3-LangGraph/music_router.ipynb` | Music recommendation router agent using LangGraph for stateful workflows, with full telemetry instrumentation. | `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_API_VERSION`, `AZURE_OPENAI_MODEL_NAME`, `APPLICATION_INSIGHTS_CONNECTION_STRING` (optional) |

---

## Notes

- All notebooks require environment variables to be set in a `.env` file in the project root
- The `validate-setup.ipynb` notebook in section 1 can be used to verify all required environment variables are properly configured
- Some notebooks are marked as "TBD" where content is still being developed
- Optional environment variables (like `APPLICATION_INSIGHTS_CONNECTION_STRING`) enable additional features but are not required for basic functionality

