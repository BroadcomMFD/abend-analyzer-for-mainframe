<div id="header" align="center">

[![GitHub issues](https://img.shields.io/github/issues-raw/BroadcomMFD/abend-analyzer-for-mainframe?style=flat-square)](https://github.com/BroadcomMFD/abend-analyzer-for-mainframe/issues)
[![slack](https://img.shields.io/badge/chat-on%20Slack-blue?style=flat-square)](https://communityinviter.com/apps/che4z/code4z)
</div>

# Abend Analyzer for Mainframe

Abend Analyzer for Mainframe provides an interface to [SymDump® CICS](https://www.broadcom.com/products/mainframe/testing-and-quality/symdump-cics) and [SymDump® Batch](https://www.broadcom.com/products/mainframe/testing-and-quality/symdump-batch). This extension allows you to browse, manage and view formatted abend reports and symbolic data in a modern IDE environment.

Abend Analyzer for Mainframe is also part of [Code4z](https://marketplace.visualstudio.com/items?itemName=broadcomMFD.code4z-extension-pack), an all-round package that offers a modern experience for mainframe application developers, including extensions for language support, data editing, testing, and source code management.

To find out more about the capabilities of this extension, see this [blog post](https://medium.com/modern-mainframe/abend-analyzer-for-mainframe-97922fbfc340).

## Compatibility

Abend Analyzer for Mainframe is supported on Visual Studio Code and Github Codespaces.

We recommend the use of [Zowe Explorer](https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe) to access mainframe data sets in connection with your test data analysis. Zowe Explorer is available as part of the Code4z package. 

<a href="https://www.openmainframeproject.org/all-projects/zowe/conformance"><img alt="This extension is Zowe v2 conformant" src="https://artwork.openmainframeproject.org/other/zowe-conformant/zowev2/explorer/color/zowe-conformant-zowev2-explorer-color.png" width=20% height=20% /></a>

## Prerequisites

Abend Analyzer for Mainframe requires SymDump version 11 to operate.

Before you use Abend Analyzer for Mainframe, complete the following tasks:

- Acquire and install PTFs LU02175, LU03402 and LU03403. For more information, see [Release Information](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-intertest-and-ca-symdump/11-0/release-information.html).
- [Install the Testing Tools Server and SymDump REST API](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-intertest-and-ca-symdump/11-0/installing/install-testing-tools-server.html). If you already have a Testing Tools Server instance for InterTest and SymDump, redeploy it after you install the PTF from the previous task.

**Note**: To upgrade from version 0.1.0 to a newer version of Abend Analyzer for Mainframe, you must install PTFs LU03402 and LU03403 and then redeploy your Testing Tools Server instance.

## Getting Started

To get started with Abend Analyzer for Mainframe, create a connection to the mainframe and load your SymDump abend report repository. 

### Manage Connections

To add a connection to the mainframe, **follow these steps**:

1. Select the Abend Analyzer for Mainframe tab in your IDE.
2. In the sidebar, click **Add Connection**.  
The prompt bar displays at the top of the window.
3. Enter a name for your connection. Ensure that the connection name is unique.
4. Enter the URL of your Testing Tools Server instance in the format `http(s)://host:port`, or an API Mediation Layer URL in the format `http(s)://host:port/service-id/api/v1`.
5. (Optional) Enter your mainframe username and password. If you skip this step, the credentials prompt displays when you open a repository.  
The connection displays in the sidebar.

To edit your connection, right-click the connection in the sidebar and select **Edit connection**, then follow the steps above again.

To delete a connection, right-click the connection in the sidebar and select **Delete connection**.

### Manage Repositories

To load an abend report repository, **follow these steps**: 
1. Click the **+** icon next to your connection name.  
The prompt bar displays at the top of the window.
2. Enter the full name of your abend report repository data set.
3. Select either **CICS** or **Batch** from the dropdown list.
4. If you are prompted, enter your mainframe username and password.  
The abend report repository loads in the sidebar. 

If you specified an incorrect DSN, right-click the repository in the sidebar and select **Edit DSN** to specify the DSN again. 

To remove a repository from the sidebar, right-click the repository and select **Remove dataset**.

## Using

Abend Analyzer for Mainframe lets you:
- View reports
- Filter and sort reports
- Lock and unlock reports
- Delete reports
- Load symbolic data from a PROTSYM
- Display global options
- Display PROTDMP options for a CICS abend repository

### Filter and Sort Reports

To sort reports in the repository by date, right click the repository data set in the tree and select **Sort by date (ascending)** or **Sort by date (descending)**. 

To sort by a different parameter, select **Sort** and select one of the options that display at the top of the window. To change the order from ascending to descending, select **Sort** and choose the same option again.

If you have a large number of reports, you might need to apply a filter to find the reports you need. To apply a filter, **follow these steps:**

1. Right-click the repository data set in the tree and select **Filter**.  
A list of filter options displays at the top of the window.
2. Select one of the options.
3. Enter a filter string and press enter.  
Records containing the filter string are displayed in the sidebar.

Only one filter can be applied at a time. To reset the filter, click the yellow **Cancel filter** icon next to the repository data set.

### Lock, Unlock and Delete Reports

You can lock abend reports to ensure that they are not edited or deleted by other users. To lock or unlock a report, right-click it and select **Lock report** or **Unlock report**.

To delete a report, click the delete icon next to the report name in the sidebar. The delete icon does not appear if the report is locked.

### Load Symbolic Data from a PROTSYM

If you have symbolic data saved in a PROTSYM, you can load the PROTSYM using Abend Analyzer for Mainframe to display the symbolic data in the report. 

**Follow these steps:**
1. Under your connection, click the **+** icon next to **PROTSYMS**.  
The prompt bar displays at the top of the window.
2. Specify the DSN of your PROTSYM and press enter.
3. Open the report linked with the specified PROTSYM. If the report is already open, close and reopen it.

### Display Options

To display global options for your instance of SymDump Batch, right-click your connection and select **Display global options**.

To display an options table for an individual CICS abend report repository (PROTDMP), right-click the data set and select **Display PROTDMP options**.

## Customize the Report Label

You can customize the format of the report label to choose what data is displayed. 

In the **Extensions** tab, click the cog icon next to **Abend Analyzer for Mainframe** and select **Extension Settings** to open the extension settings. Under **Symdump - View: Label**, specify the text and the variables that you want to include in the report label. Allowed variables are:

- ${ABEND}
- ${DATETIME}
- ${JOB}
- ${KEY}
- ${LOCK}
- ${OFFSET}
- ${PROGRAM}
- ${STEP}
- ${SYSTEM}
- ${USER}

## Technical Assistance and Support for Abend Analyzer for Mainframe

The Abend Analyzer for Mainframe extension is made available to customers on the Visual Studio Code Marketplace in accordance with the terms and conditions contained in the provided End-User License Agreement (EULA).

If you are on active support for SymDump, you get technical assistance and support in accordance with the terms, guidelines, details, and parameters that are located within the Broadcom [Working with Support](https://support.broadcom.com/external/content/release-announcements/CA-Support-Policies/6933) guide.

This support generally includes:

* Telephone and online access to technical support
* Ability to submit new incidents 24x7x365
* 24x7x365 continuous support for Severity 1 incidents
* 24x7x365 access to Broadcom Support
* Interactive remote diagnostic support
* Technical support cases must be submitted to Broadcom in accordance with guidance provided in “Working with Support”.

Note: To receive technical assistance and support, you must remain compliant with “Working with Support”, be current on all applicable licensing and maintenance requirements, and maintain an environment in which all computer hardware, operating systems, and third party software associated with the affected Broadcom software are on the releases and version levels from the manufacturer that Broadcom designates as compatible with the software. Changes you elect to make to your operating environment could detrimentally affect the performance of Broadcom software and Broadcom shall not be responsible for these effects or any resulting degradation in performance of the Broadcom software. Severity 1 cases must be opened via telephone and elevations of lower severity incidents to Severity 1 status must be requested via telephone.

## Privacy Notice
The extensions for Visual Studio Code developed by Broadcom Inc., including its corporate affiliates and subsidiaries, ("Broadcom") are provided free of charge, but in order to better understand and meet its users’ needs, Broadcom may collect, use, analyze and retain anonymous users’ metadata and interaction data, (collectively, “Usage Data”) and aggregate such Usage Data with similar Usage Data of other Broadcom customers. Please find more detailed information in [License and Service Terms & Repository](https://www.broadcom.com/company/legal/licensing).

This data collection uses built-in Microsoft VS Code Telemetry, which can be disabled, at your sole discretion, if you do not want to send Usage Data.

The current release of Abend Analyzer for Mainframe collects anonymous data for the following events:
* Activation of this extension
* Managing connections
* Interaction with data sets, dumps, reports and protsyms
* Sorting
* Filtering
* Display options function

Each such event is logged with the following information:
* Event time
* Operating system and version
* Country or region
* Anonymous user and session ID
* Version numbers of Microsoft VS Code and Abend Analyzer for Mainframe
