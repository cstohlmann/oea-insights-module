> **Note:** This module is currently released as v0.1, and is dependent on the OEA framework v0.7

<img align="right" height="75" src="https://github.com/microsoft/OpenEduAnalytics/blob/main/docs/pics/oea-logo-nobg.png">

# Microsoft Education Insights Module

[Microsoft Education Insights](https://docs.microsoft.com/en-us/microsoftteams/class-insights) is an analytics service in Microsoft Teams for Education that provides data on learners' digital activity in O365 applications like Teams, OneNote, OneDrive and Sharepoint. It includes data on education-specific apps like Assignments, Reading Progress, and Reflect. 

Using this module, data from Education Insights can be exported into your organization's OEA data lakes to combine it with other datasets for a variety of use cases, including Digital Learning Analytics. 

Education Insights requires the implementation of [Microsoft School Data Sync](https://sds.microsoft.com/) on O365, which provides school and class roster data, to enable its reports in Teams. For production data, you will need an O365 education tenant as Microsoft Education Insights is only enabled for education tenants.


<p align="center">
  <img src="https://github.com/cstohlmann/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/docs/images/insights_module_overview_visual.png" alt="Microsoft Insights Module Overview"/>
</p>

 (Microsoft documentation on Education Insights: [Education Insights in Microsoft Teams - Microsoft Education Center](https://docs.microsoft.com/en-us/schooldatasync/enabling-insights-premium-export)) 
 
## Problem Statement and Module Impact

As education systems shift to digital applications and platforms to support learning, it is important for them to be able to see patterns of student digital activity across those applications and platforms. Most students use many different applications and platforms. This module provides data from education-specific applications in O365. This data can be combined with other digital activity data from other applications and platforms used in learning to develop "digital learning insights" across the ecosystem of applications and platforms a student uses.

Microsoft Insights data can be used for a variety of analytics purposes, including:
 - School and district dashboards for education leaders to identify variability in student activity in learning applications and platforms. 
 - Combining Insights data with other data sources to show the relationship between digital activity and other metrics such as attendance and assessments. 
 - Combining Insights data with student demographics, school information, or geographic data to show patterns of digital activity in relation to the whole education system. This can reveal patterns of inequality in access to digital tools and applications for learning.

## Module Setup Instructions

<p align="center">
  <img src="https://github.com/microsoft/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/docs/images/insights_module_setup_visual.png" alt="Microsoft Insights Setup Instructions"/>
</p>

<ins><strong>Preparation:</ins></strong> This module currently leans on v0.7 of the OEA framework. Ensure you have proper [Azure subscription and credentials](https://github.com/microsoft/OpenEduAnalytics/tree/main/framework) and setup of the [OEA framework](https://github.com/microsoft/OpenEduAnalytics/tree/main/framework#setup-of-framework-assets). This will include v0.7 of the [OEA python class](https://github.com/microsoft/OpenEduAnalytics/blob/main/framework/synapse/notebook/OEA_py.ipynb). 

<ins><strong>Note:</ins></strong> 
All the steps outlined below are applicable to deployment of this module with production data. However, if you are doing a test deployment using the [test data sets](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data) we provide as part of this module, skip to step 3.

1. Setup [School Data Sync](https://sds.microsoft.com/) to begin receiving usage data from M365. You can find videos about School Data Sync and Education Insights on the [Microsoft School Data Sync Youtube channel](https://www.youtube.com/channel/UCA8ZOC7eTfzLlkcFW3imkHg/featured) [for production data only].
2. Within School Data Sync, [enable the education data lake export](https://docs.microsoft.com/en-us/schooldatasync/enable-education-data-lake-export) to land data in Stage 1 of your data lake [for production data only].
3. Import the [Insights module class notebook](https://github.com/microsoft/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/notebook/Insights_py.ipynb) into your Synapse workspace. This notebook contains data schema information and data writing functions needed to support module pipelines. 
4. Import the [Insights module pipeline template](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/pipeline) into your Synapse workspace and execute the pipeline. See the [module pipeline page](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/pipeline) for detailed instructions.
5. Verify that the module pipeline landed data into stage 1 and 2 and SQL databases were created. See the [module pipeline page](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/pipeline) for detailed instructions.
6. Download the [module Power BI template file](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/powerbi). Module test data is already imported into the Power BI. See the [module Power BI page](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/powerbi) page for instructions for switching the Power BI template data source to import from your Synapse workspace data source.

#### OEA Digital Engagement Schema:

After completing the setup of this module, the MS Education Insights activity schema can be transformed into the [OEA schema standard for digital engagement](https://github.com/microsoft/OpenEduAnalytics/tree/main/schemas/schema_catalog/Digital_Engagement_Schema). Refer to the documentation and assets to see how this module can be extended and standardized for OEA package-use.

## Data Sources

This module imports digital activity and roster data for an education system via [School Data Sync](https://sds.microsoft.com/).
- [Digital Activity Data](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-activity) provides a log of M365 signal activity from apps including Sharepoint, Teams Channel, Teams Meetings, Assignment Services, OneNote, Reading Progress, and Reflect.
- [Rostering Data](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-rostering) is concerned with students, teachers, courses, and schools relationships.
- [Azure Active Directory Data](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-azure-ad) provides people details and group memberships.

See the [module test data page](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data) for details on data format and contents.

## Module Components
Out-of-the box assets for this OEA module include: 
1. [Test Data](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data): Two artificially generated test data sets, which supports the module pipeline and Power BI template. Test data matches the [School Data Sync](https://sds.microsoft.com/) format exactly.
    - [K-12 Test Data](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data/k12_test_data): Test data formatted as a k-12 education system.
    - [Higher Education Test Data](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data/hed_test_data): Test data formatted as a higher education system.
2. [Pipeline Template](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/pipeline): One main pipeline template which lands data into the data lake in Stage 1 (for raw data) and processes into the Stage 2 data lake (for structured, queryable data). Stage 2 data is then made available via a serverless SQL endpoint.
3. [Notebooks](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/notebook): 
    - [Insights_example.ipynb](https://github.com/microsoft/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/notebook/Insights_example.ipynb): A module example notebook that demonstrates the basic functions of landing raw test data to Stage 1, ingestion from Stage 1 to Stage 2/Ingested, and refinement from Stage2/Ingested to Stage2/Refined.
    - [Insights_schema_correction.ipynb](https://github.com/microsoft/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/notebook/Insights_schema_correction.ipynb): Insights-module-specific notebook that corrects each table's schema. The updated table schemas overwrite the pre-existing schemas in Stage2/Ingested. The pipeline template automatically uploads this notebook. 
4. [PowerBI Template](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/powerbi): A Power BI template which explores data in a basic way. The Power BI file is pre-loaded with test data making it easy to quickly interact with data. See instructions on the [module PowerBI page](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/powerbi) to switch the dashboard data source to direct query from your Synapse workspace. Screenshots of the Power BI template are below.

Dashboard Explanation | Digital Engagement in Teams Summary
:-------------------------:|:-------------------------:
![](https://github.com/cstohlmann/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/docs/images/insights_module_k12_explanation_page.png) |  ![](https://github.com/cstohlmann/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/docs/images/insights_module_sample_k12_dashboard.png)   
## Additional Information

| Resource | Description |
| --- | --- |
| [Overview of Microsoft Education Insights](https://docs.microsoft.com/en-us/microsoftteams/class-insights) | Intro to Education Insights, what it can do, and what it can provide. |
| [School Data Sync (SDS) Overview](https://docs.microsoft.com/en-us/schooldatasync/) | Overview of SDS and reference to full documentation. |
| [Enable SDS Data Export](https://docs.microsoft.com/en-us/schooldatasync/enable-education-data-lake-export) | Instructions for landing SDS data in your data lake. |
| [Demo Tenant for Microsoft Education Insights](https://learn.microsoft.com/en-us/partner-center/mpn-demos) | Get access to a demo tenant provisioning that comes with demo data and demo scripts. |
| [Activity Data Information](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-activity) | Reference to learn about the schema details for activity data ingested into stage 1. |
| [Azure Active Directory (AD) Data Information](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-azure-ad) | Reference to learn about the schema details for AD data ingested into stage 1. |
| [Roster Data Information](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-rostering) | Reference to learn about the schema details for roster data ingested into stage 1. |


## Contributions from the Community
 
The Microsoft Insights module [welcomes contributions](https://github.com/microsoft/OpenEduAnalytics/blob/main/docs/license/CONTRIBUTING.md).

This module was developed by [Kwantum Analytics](https://www.kwantumedu.com/). The architecture and reference implementation for all modules is built on [Azure Synapse Analytics](https://azure.microsoft.com/en-us/services/synapse-analytics/) - with [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) as the storage backbone,  and [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/) providing the role-based access control.

# Legal Notices
Microsoft and any contributors grant you a license to the Microsoft documentation and other content
in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.

Privacy information can be found at https://privacy.microsoft.com/en-us/

Microsoft and any contributors reserve all other rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.
