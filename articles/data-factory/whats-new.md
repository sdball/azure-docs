---
title: What's new in Azure Data Factory 
description: This page highlights new features and recent improvements for Azure Data Factory. Data Factory is a managed cloud service that's built for complex hybrid extract-transform-and-load (ETL), extract-load-and-transform (ELT), and data integration projects.
author: pennyzhou-msft
ms.author: xupzhou
ms.service: data-factory
ms.subservice: concepts
ms.topic: overview
ms.custom: references_regions
ms.date: 10/10/2022
---

# What's new in Azure Data Factory

Azure Data Factory is improved on an ongoing basis. To stay up to date with the most recent developments, this article provides you with information about:

- The latest releases.
- Known issues.
- Bug fixes.
- Deprecated functionality.
- Plans for changes.

This page is updated monthly, so revisit it regularly.  For older months' updates, refer to the [What's new archive](whats-new-archive.md).

Check out our [What's New video archive](https://www.youtube.com/playlist?list=PLt4mCx89QIGS1rQlNt2-7iuHHAKSomVLv) for all of our monthly update videos.

## May 2023

### Data Factory in Microsoft Fabric

[Data factory in Microsoft Fabric](/fabric/data-factory/) provides cloud-scale data movement and data transformation services that allow you to solve the most complex data factory and ETL scenarios. It's intended to make your data factory experience easy to use, powerful, and truly enterprise-grade.

## April 2023

### Data flow

Easily unroll multiple arrays in ADF data flows. ADF updated the **Flatten** transformation that now makes it super easy to unroll multiple arrays from a single **Flatten** transformation step. [Learn more](https://techcommunity.microsoft.com/t5/azure-data-factory-blog/unroll-multiple-arrays-in-a-single-flatten-step-in-adf/ba-p/3802457)

### Continuous integration and continuous deployment

You can customize the commit message in Git mode now. Type in a detailed description about the changes you make, and we will save it to Git repository.

### Connectors

The Azure Blob Storage connector now supports anonymous authentication. [Learn more](connector-azure-blob-storage.md#anonymous-authentication)

## March 2023

### Connectors

Azure Data Lake Storage Gen2 connector now supports shared access signature authentication. [Learn more](connector-azure-data-lake-storage.md#shared-access-signature-authentication)

## February 2023

### Data movement

- Anonymous authentication type supported for Azure Blob storage [Learn more](connector-azure-blob-storage.md?tabs=data-factory#anonymous-authentication)
- Updated SAP template to easily move SAP data to ADLSGen2 in Delta format [Learn more](industry-sap-templates.md)

### Monitoring

Container monitoring view available in default ADF studio [Learn more](how-to-manage-studio-preview-exp.md#container-view)

### Orchestration

- Set pipeline output value (Public preview) [Learn more](tutorial-pipeline-return-value.md)
- Managed Airflow (Public preview) [Learn more](https://techcommunity.microsoft.com/t5/azure-data-factory-blog/introducing-managed-airflow-in-azure-data-factory/ba-p/3730151)

### Developer productivity

Dark theme support added (Public preview) [Learn more](https://techcommunity.microsoft.com/t5/azure-data-factory-blog/introducing-dark-mode-for-adf-studio/ba-p/3757961)

## January 2023

### Data flow

- Flowlets now support schema drift [Learn more](connector-office-365.md?tabs=data-factory)
- SQL CDC incremental extract now supports numeric columns [Learn more](connector-sql-server.md?tabs=data-factory#native-change-data-capture)

### Data movement

New top-level CDC resource - native CDC configuration in 3 simple steps [Learn more](https://techcommunity.microsoft.com/t5/azure-data-factory-blog/announcing-the-public-preview-of-a-new-top-level-cdc-resource-in/ba-p/3720519)

### Orchestration

Orchestrate Synapse notebooks and Synapse spark job definitions natively [Learn more](https://techcommunity.microsoft.com/t5/azure-data-factory-blog/orchestrate-and-operationalize-synapse-notebooks-and-spark-job/ba-p/3724379)

### Region expansion

- Continued region expansion - China North 3 now supported [Learn more](https://azure.microsoft.com/explore/global-infrastructure/products-by-region/?products=data-factory)
- Continued region expansion - Switzerland West now supported [Learn more](https://azure.microsoft.com/explore/global-infrastructure/products-by-region/?products=data-factory)

### SQL Server Integration Services (SSIS)

Express virtual network injection for SSIS now generally available [Learn more](https://techcommunity.microsoft.com/t5/sql-server-integration-services/general-availability-of-express-virtual-network-injection-for/ba-p/3699993)

### Developer productivity

- Added support for favoriting resources on home page
- Save column width for pipeline monitoring
- Monitor filter updates for faster searches
- Directly launch Pipeline Template Gallery through Azure portal [Learn more]()

## December 2022

### Data flow

SQL change data capture (CDC) incremental extract - supports numeric columns in mapping dataflow [Learn more](connector-azure-sql-database.md?tabs=data-factory#source-transformation)

### Data movement

Express virtual network injection for SSIS in Azure Data Factory is generally available [Learn more](https://techcommunity.microsoft.com/t5/sql-server-integration-services/general-availability-of-express-virtual-network-injection-for/ba-p/3699993)

### Region expansion

Continued region expansion - Azure Data Factory is now available in China North 3 [Learn more](https://azure.microsoft.com/explore/global-infrastructure/products-by-region/?products=data-factory)

## November 2022

 
### Data flow

- Incremental only is available in SAP CDC - get changes only from SAP system without initial full load  [Learn more](connector-sap-change-data-capture.md?tabs=data-factory#mapping-data-flow-properties)
- Source partitions in initial full data load of SAP CDC to improve performance  [Learn more](connector-sap-change-data-capture.md?tabs=data-factory#mapping-data-flow-properties)
- A new pipeline template - Load multiple objects with big amounts from SAP via SAP CDC [Learn more](solution-template-replicate-multiple-objects-sap-cdc.md?tabs=data-factory)

### Data Movement
- Support to Azure Databricks through private link from a Data Factory managed virtual network [Learn more](managed-virtual-network-private-endpoint.md?tabs=data-factory#supported-data-sources-and-services)

### User Interface
3 Pipeline designer enhancements added to ADF Studio preview experience 
- Dynamic content flyout - make it easier to set dynamic content in your pipeline activities without using the expression builder  [Learn more](how-to-manage-studio-preview-exp.md?tabs=data-factory#dynamic-content-flyout)
- Error message relocation to status column - make it easier for you to view errors when you see a Failed pipeline run [Learn more](how-to-manage-studio-preview-exp.md?tabs=data-factory#error-message-relocation-to-status-column)
- Container view - in Author Tab, Pipeline can change output view from list to container [Learn more](how-to-manage-studio-preview-exp.md?tabs=data-factory#container-view)


### Continuous integration and continuous deployment

In auto publish config, disable publish button is available to void overwriting the last automated publish deployment [Learn more](source-control.md?tabs=data-factory#editing-repo-settings)

## More information

- [What's new archive](whats-new-archive.md)
- [What's New video archive](https://www.youtube.com/playlist?list=PLt4mCx89QIGS1rQlNt2-7iuHHAKSomVLv)
- [Blog - Azure Data Factory](https://techcommunity.microsoft.com/t5/azure-data-factory/bg-p/AzureDataFactoryBlog)
- [Stack Overflow forum](https://stackoverflow.com/questions/tagged/azure-data-factory)
- [Twitter](https://twitter.com/AzDataFactory?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor)
- [Videos](https://www.youtube.com/channel/UC2S0k7NeLcEm5_IhHUwpN0g/featured)
