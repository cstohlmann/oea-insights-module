# Microsoft Insights Module
Microsoft Insights is a broad service that can provide School Information System (SIS) data through School Data Sync, in combination with Microsoft 365 (M365) and Microsoft Teams data, to holistically collect student interactions with Microsoft products. This module provides a set of assets for the processing of roster and application usage data received from M365 via [Azure Data Share](https://docs.microsoft.com/en-us/azure/data-share/overview#:~:text=%20Azure%20Data%20Share%20enables%20data%20providers%20to%3A,or%20allow%20them%20to%20automatically%20receive...%20See%20More.).

You can use this OEA Microsoft Insights module to incorporate these datasets into your organization's OEA data lakes.

## Problem Statement
 <p align="center">
  <strong><em>[Define the problem you seek to solve using this module]</em></strong>
 </p>
 
## Module Impact
 <p align="center">
  <strong><em>[List out the impact and benefits this module will have on learners, educators and the learning process]</em></strong>
 </p>

## Data Sources and Module Setup
### Data Sources

- As mentioned before, this Microsoft Insights module utilizes usage data from M365 applications to gauge student interaction and involvement from their online activities. 
     * Note the availability of [Insights in Microsoft Teams for Education](https://support.microsoft.com/en-us/office/insights-preview-in-microsoft-teams-for-education-leaders-8738d1b1-4e1c-49bd-9e8d-b5292474c347?ui=en-us&rs=en-us&ad=us) which provides usage analytics available via the Insights app within Teams. Although, the assets provided within this module focus on the processing of M365 usage data.
 - App usage data available via Azure Data Share:
     * In order to begin receiving usage data from M365, the first step is to initiate the Data Share feature within [School Data Sync](https://sds.microsoft.com/). This feature is in Private Preview and is not visible by default - check with your account manager to have the feature enabled for your tenant.
 - The data ingested is formatted as CSV files.

### Module Setup

 - The setup of [School Data Sync](https://sds.microsoft.com/) is a prerequisite for being able to receive this type of usage data from your M365 tenant.
    * You can also find short videos about School Data Sync and the Insights app on the [Microsoft School Data Sync channel](https://www.youtube.com/channel/UCA8ZOC7eTfzLlkcFW3imkHg/featured).
 - In order to install this module:
     1. Connect your Synpase workspace to the Azure Data Share for M365 data.
     2. Import the MSInsights_py.ipynb and process_MSInsights_data.ipynb notebooks into Synapse Studio.
     3. Then, open and run the process_MSInsights_data notebook.
     4. After the Insights data is processed, open up the PowerBI Insights dashboard template provided, and connect to your Synapse workspace serverless SQL endpoint.
 
## Module Components
Sample out-of-the box assets for this OEA module include: 
1. Notebook: Example notebooks on processing the data from stage 1 to stage 2 within Synapse. 
2. PowerBI template: A Power BI sample template making it easy to interact with Microsoft Insights data.
 <p align="center">
  <strong><em>[INSERT POWERBI DASHBOARD TEMPLATE PICTURE HERE]</em></strong>
 </p>

The Microsoft Insights module [welcome contributions](https://github.com/microsoft/OpenEduAnalytics/blob/main/CONTRIBUTING.md).

This module was developed by [name of contributor]. The architecture and reference implementation for all modules is built on [Azure Synapse Analytics](https://azure.microsoft.com/en-us/services/synapse-analytics/) - with [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) as the storage backbone,  and [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/) providing the role-based access control.

#### Additional Information
<p align="center">
  <strong><em>[Provide any additional information and resources]</em></strong>
 </p>

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

# WHAT GENE HAD:

## SignalType data
The current set of signal types coming in the app usage data is:
* UserAtMentioned
* ReactedWithEmoji
* ReplyChannelMessage
* FileAccessed
* VisitTeamChannel
* SubmissionEvent
* ShareNotificationRequested
* ExpandChannelMessage
* PostChannelMessage
* OneNotePageChanged
* FileDownloaded
* CallRecordSummarized
* FileModified
* CommentCreated
* AddedToSharedWithMe
* FileUploaded
* AssignmentEvent

