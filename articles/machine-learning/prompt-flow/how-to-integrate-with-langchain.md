---
title: Integrate with LangChain in Prompt flow (preview)
titleSuffix: Azure Machine Learning
description: Learn how to integrate with LangChain in Prompt flow with Azure Machine Learning studio.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: how-to
author: jiaochenlu
ms.author: chenlujiao
ms.reviewer: lagayhar
ms.date: 06/30/2023
---

# Integrate with LangChain (preview)

Prompt Flow can also be used together with the [LangChain](https://python.langchain.com) python library, which is the framework for developing applications powered by LLMs, agents and dependency tools. In this document, we'll show you how to supercharge your LangChain development on our Prompt Flow.

:::image type="content" source="./media/how-to-integrate-with-langchain/flow.png" alt-text="Screenshot of flows with the LangChain python library. " lightbox = "./media/how-to-integrate-with-langchain/flow.png":::

> [!IMPORTANT]
> Prompt flow is currently in public preview. This preview is provided without a service-level agreement, and is not recommended for production workloads. Certain features might not be supported or might have constrained capabilities.
> For more information, see [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

## Benefits of LangChain integration

We consider the integration of LangChain and Prompt flow as a powerful combination that can help you to build and test your custom language models with ease, especially in the case where you may want to use LangChain modules to initially build your flow and then use our Prompt Flow to easily scale the experiments for bulk testing, evaluating then eventually deploying.

- For larger scale experiments - **Convert existed LangChain development in seconds.**
    If you have already developed demo prompt flow based on LangChain code locally, with the streamlined integration in Prompt Flow, you can easily convert it into a flow for further experimentation, for example you can conduct larger scale experiments based on larger data sets.
- For more familiar flow engineering - **Build prompt flow with ease based on your familiar Python SDK**.
    If you're already familiar with the LangChain SDK and prefer to use its classes and functions directly, the intuitive flow building python node enables you to easily build flows based on your custom python code.

## How to convert LangChain code into flow

Assume that you already have your own LangChain code available locally, which is properly tested and ready for deployment. To convert it to a runnable flow on our platform, you need to follow the steps below.

### Prerequisites for environment and runtime

> [!NOTE]
> Our base image has langchain v0.0.149 installed. To use another specific version, you need to create a customized environment.

#### Create a customized environment

For more libraries import, you need to customize environment based on our base image, which should contain all the dependency packages you need for your LangChain code. You can follow this guidance to use **docker context** to build your image, and [create the custom environment](how-to-customize-environment-runtime.md#customize-environment-with-docker-context-for-runtime) based on it in Azure Machine Learning workspace.

Then you can create a [Prompt flow runtime](./how-to-create-manage-runtime.md) based on this custom environment.

:::image type="content" source="./media/how-to-integrate-with-langchain/runtime-custom-env.png" alt-text="Screenshot of flows on the runtime tab with the add compute instance runtime popup. " lightbox = "./media/how-to-integrate-with-langchain/runtime-custom-env.png":::

### Convert credentials to custom connection

Custom connection helps you to securely store and manage secret keys or other sensitive credentials required for interacting with LLM, rather than exposing them in environment variables hard code in your code and running on the cloud, protecting them from potential security breaches.

#### Create a custom connection

Create a custom connection that stores all your LLM API KEY or other required credentials.

1. Go to Prompt flow in your workspace, then go to **connections** tab.
2. Select **Create** and select **Custom**.
    :::image type="content" source="./media/how-to-integrate-with-langchain/custom-connection-1.png" alt-text="Screenshot of flows on the connections tab highlighting the custom button in the create drop-down menu. " lightbox = "./media/how-to-integrate-with-langchain/custom-connection-1.png":::
1. In the right panel, you can define your connection name, and you can add multiple *Key-value pairs* to store your credentials and keys by selecting **Add key-value pairs**.
    :::image type="content" source="./media/how-to-integrate-with-langchain/custom-connection-2.png" alt-text="Screenshot of add custom connection point to the add key-value pairs button. " lightbox = "./media/how-to-integrate-with-langchain/custom-connection-2.png":::

> [!NOTE]
> - You can set one Key-Value pair as **secret** by **is secret** checked, which will be encrypted and stored in your key value.
> - You can also set the whole connection as **workspace level key**, which will be shared to all members in the workspace. If not set as workspace level key, it can only be accessed by the creator.

Then this custom connection is used to replace the key and credential you explicitly defined in LangChain code, if you already have a LangChain integration Prompt flow, you can jump to​​​​​​​ [Configure connection, input and output](#configure-connection-input-and-output).

### LangChain code conversion to a runnable flow

All LangChain code can directly run in the Python tools in your flow as long as your runtime environment contains the dependency packages, you can easily convert your LangChain code into a flow by following the steps below.

#### Create a flow with Prompt tools and Python tools

> [!NOTE]
> There are two ways to convert your LangChain code into a flow.

- To simplify the conversion process, you can directly initialize the LLM model for invocation in a Python node by utilizing the LangChain integrated LLM library.
- Another approach is converting your LLM consuming from LangChain code to our LLM tools in the flow, for better further experimental management.

:::image type="content" source="./media/how-to-integrate-with-langchain/code-consume-llm.png" alt-text="Screenshot of LangChain code in Prompt flow. " lightbox = "./media/how-to-integrate-with-langchain/code-consume-llm.png":::

For quick conversion of LangChain code into a flow, we recommend two types of flow structures, based on the use case:

|| Types | Desc | Case |
|-------| -------- | -------- | -------- |
|**Type A**| A flow that includes both **prompt tools** and **python tools**| You can extract your prompt template from your code into a prompt node, then combine the remaining code in a single Python node or multiple Python tools. | This structure is ideal for who want to easily **tune the prompt** by running flow variants and then choose the optimal one based on evaluation results.|
|**Type B**| A flow that includes **python tools** only| You can create a new flow with python tools only, all code including prompt definition will run in python tools.| This structure is suitable for who don't need to explicit tune the prompt in workspace, but require faster batch testing based on larger scale datasets. |

For example the type A flow from the chart is like:

:::image type="content" source="./media/how-to-integrate-with-langchain/flow-node-a-1.png" alt-text="Screenshot of flows highlighting the prompt button and system template. " lightbox = "./media/how-to-integrate-with-langchain/flow-node-a-1.png":::

:::image type="content" source="./media/how-to-integrate-with-langchain/flow-node-a-2.png" alt-text="Screenshot of system template showing variant one and zero with the finish tuning button highlighted. " lightbox = "./media/how-to-integrate-with-langchain/flow-node-a-2.png":::

While the type B flow would look like:

:::image type="content" source="./media/how-to-integrate-with-langchain/flow-node-b.png" alt-text="Screenshot of flows showing the LangChain code node and graph. " lightbox = "./media/how-to-integrate-with-langchain/flow-node-b.png":::


To create a flow in Azure Machine Learning, you can go to your workspace, then select **Prompt flow** in the left navigation, then select **Create** to create a new flow. More detailed guidance on how to create a flow is introduced in [Create a Flow](how-to-develop-a-standard-flow.md).

#### Configure connection, input and output

After you have a properly structured flow and are done moving the code to specific tools, you need to configure the input, output, and connection settings in your flow and code to replace your original definitions.

To utilize a [custom connection](#create-a-custom-connection) that stores all the required keys and credentials, follow these steps:

1. In the python tools, need to access LLM Key and other credentials, import custom connection library `from promptflow.connections import CustomConnection`.
    :::image type="content" source="./media/how-to-integrate-with-langchain/custom-connection-python-node-1.png" alt-text="Screenshot of doc search chain node highlighting the custom connection. " lightbox = "./media/how-to-integrate-with-langchain/custom-connection-python-node-1.png":::
1. Add an input parameter of type `connection` to the tool function.
    :::image type="content" source="./media/how-to-integrate-with-langchain/custom-connection-python-node-2.png" alt-text="Screenshot of the chain node highlighting the connection. " lightbox = "./media/how-to-integrate-with-langchain/custom-connection-python-node-2.png":::
1. Replace the environment variables that originally defined the key and credential with the corresponding key added in the connection.
1. Save and return to authoring page, and configure the connection parameter in the node input.

Before running the flow, configure the **node input and output**, as well as the overall **flow input and output**. This step is crucial to ensure that all the required data is properly passed through the flow and that the desired results are obtained.

## Next steps

- [Langchain](https://langchain.com)
- [Create a Custom Environment](./how-to-customize-environment-runtime.md#customize-environment-with-docker-context-for-runtime)
- [Create a Runtime](./how-to-create-manage-runtime.md)