# Microsoft Education Insights Module
Microsoft [Education Insights Premium](https://education.microsoft.com/en-us/resource/3978f2d8) is a new service in Microsoft Teams for Education that provides data on learners digital activity in O365 applications like Teams, OneNote, OneDrive and Sharepoint. It includes data on education-specific apps like Assignments, Reading Progress, and Reflect. 

Using this module, data from Education Insights Premium can be exported into your organization's OEA data lakes to combine it with other datasets for a variety of use cases. 

There are several important prerequisites for using this module:

1. Education Insights Premium requires a license fee.
2. Education Insights Premium requires the implementation of School Data Sync on O365, which provides school and class roster data, to enable its reports in Teams.
3. At present, the feature of Education Insights Premium that allows data to be exported to an OEA data environment is in private preview, so a special agreement must be signed to accept the terms of this feature that is not yet in General Availability. To request the private preview agreement and have the Education Insights Premium data export feature enabled, please email the request to Alex Freemon (Alex.Freemon@microsoft.com) with the subject line "Inquiry on Education Insights Premium ADS feature for OEA". 

<p align="center">
  <img src="https://github.com/cstohlmann/oea-ms_insights-module/blob/main/docs/images/insights%20visual.png?raw=true" alt="Microsoft Insights Visual"/>
</p>

 (Microsoft documentation on Education Insights Premium: [Education Insights Premium in Microsoft Teams - Microsoft Education Center](https://education.microsoft.com/en-us/resource/3978f2d8)) 
 
## Problem Statement: Digital Learning Insights
As education systems shift to digital applications and platforms to support learning, it is important for education systems and educators to be able to see patterns of student digital activity across those applications and platforms. Most students use many different applications and platforms. This module provides data from education-specific applications in O365. This data can be combined with other digital activity data from other applications and platforms used in learning to develop "digital learning insights" across the ecosystem of applications and platforms a student uses.

Microsoft Insights Premium data can be used for a variety of analytics purposes, including:
 - School and district dashboards for education leaders to identify variability in student activity in learning applications and platforms. 
 - Combining Insights data with other data sources to show the relationship between digital activity and other metrics such as attendance and assessments. 
 - Combining Insights data with student demographics, school information, or geographic data to show patterns of digital activity in relation to the whole education system. This can reveal patterns of inequality in access to digital tools and applications for learning.

Ingesting data using this Insights Premium module provides data to fulfill these types of use cases. Data from this module can be combined with data from other OEA modules to provide richer picture of digital learning in an education system:
 - [Microsoft Graph Reports API Module](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/Microsoft_Graph) (includes data from other O365 applications)
 - [Intune for Education Module](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/Intune) (includes data on devices managed by Intune)
 - Other Digital Learning Insights modules will be added to OEA modules here. 

This Education Insights Premium module will leverage the OEA Azure Synapse environment to help education systems to export their Education Insights data into their own Azure data lake for further analytics. 

## Data Sources and Module Setup 
### Data Sources

- O365 and Microsoft Teams applications from the education system's O365 tenant (single subscription).
- [School Data Sync](https://sds.microsoft.com/) class and school roster data.
- The data ingested is formatted as a CSV file.

### Module Setup

 - Education Insights Premium is available for purchase. Contact your Microsoft account manager or fill out this form for more information. \[THIS FORM LINK NEEDS TO BE ADDED\]
 - The setup of [School Data Sync](https://sds.microsoft.com/) is a prerequisite for Education Insights Premium.
    * In order to begin receiving usage data from M365, the first step is to initiate the Data Share feature within [School Data Sync](https://sds.microsoft.com/). This feature is in Private Preview and is not visible by default - check with your account manager to have the feature enabled for your tenant.
    * You can find short videos about School Data Sync and Education Insights Premium on the [Microsoft School Data Sync channel](https://www.youtube.com/channel/UCA8ZOC7eTfzLlkcFW3imkHg/featured).
 - In order to install this module:
     1. Connect your Synpase workspace to the Azure Data Share for M365 data.
     2. Import the MSInsights_py.ipynb and process_MSInsights_data.ipynb notebooks into Synapse Studio.
     3. Then, open and run the process_MSInsights_data notebook.
     4. After the Insights data is processed, open up the PowerBI Insights dashboard template provided, and connect to your Synapse workspace serverless SQL endpoint.

 
## Module Components
Sample out-of-the box assets for this OEA module include: 
1. [Tutorial](https://github.com/cstohlmann/oea-ms_insights-module/tree/main/docs): A tutorial on how to use this module within your own Synapse workspace.
2. [Test data](https://github.com/cstohlmann/oea-ms_insights-module/tree/main/test_data): Ingest sample data to understand the utility and functionality of the notebooks.
3. Pipeline: 
4. [Notebook](https://github.com/cstohlmann/oea-ms_insights-module/tree/main/notebook): Example notebooks on processing the data from stage 1 to stage 2 within Synapse. 
5. [PowerBI template](https://github.com/cstohlmann/oea-ms_insights-module/tree/main/powerbi): A Power BI sample template making it easy to interact with Microsoft Insights data.
 <p align="center">
  <strong><em>[INSERT POWERBI DASHBOARD TEMPLATE PICTURE HERE]</em></strong>
 </p>
 
 <p align="center">
  <em>(This dashboard example represents only data from Microsoft Insights Premium.)</em>
 </p>
 
The Microsoft Insights module [welcomes contributions](https://github.com/microsoft/OpenEduAnalytics/blob/main/CONTRIBUTING.md).

This module was developed by [Kwantum Analytics](https://www.kwantumanalytics.com/). The architecture and reference implementation for all modules is built on [Azure Synapse Analytics](https://azure.microsoft.com/en-us/services/synapse-analytics/) - with [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) as the storage backbone,  and [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/) providing the role-based access control.

#### Additional Information
| Resource | Description |
| --- | --- |
| [Overview of Microsoft Education Insights](https://docs.microsoft.com/en-us/microsoftteams/class-insights) | Intro to Education Insights, what it can do, and what it can provide. |
| [Syncing SIS Data with Education Insights](https://docs.microsoft.com/en-us/microsoftteams/education-insights-sis-data-sync) | Reference to how to sync SIS data with Education Insights, and includes information on how to integrate SIS data through SDS. |


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
