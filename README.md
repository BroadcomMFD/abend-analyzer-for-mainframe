<div id="header" align="center">

[![GitHub issues](https://img.shields.io/github/issues-raw/BroadcomMFD/abend-analyzer-for-mainframe?style=flat-square)](https://github.com/BroadcomMFD/abend-analyzer-for-mainframe/issues)
[![slack](https://img.shields.io/badge/chat-on%20Slack-blue)](https://join.slack.com/t/che4z/shared_invite/zt-37ewynplx-wCoabaIDxN6Ofm4_XBinZA)
[![Code4z](https://img.shields.io/badge/Code4z-marketplace-cc092f)](https://marketplace.visualstudio.com/search?term=code4z&target=VSCode)

</div>

# Abend Analyzer for Mainframe

Abend Analyzer for Mainframe provides an interface to [SymDump® CICS](https://www.broadcom.com/products/mainframe/testing-and-quality/symdump-cics) and [SymDump® Batch](https://www.broadcom.com/products/mainframe/testing-and-quality/symdump-batch). This extension allows you to browse, manage and view formatted abend reports and symbolic data in a modern IDE environment.

<img align="left" alt="This extension is part of the Code4z experience" width="80" height="82" src="https://raw.githubusercontent.com/BroadcomMFD/code4z/refs/heads/main/icon5.png" />

Abend Analyzer for Mainframe is part of the [Code4z](https://techdocs.broadcom.com/code4z) experience from Broadcom, which offers a modern experience for mainframe application developers. To get started with Code4z, check out our foundational [extension pack](https://marketplace.visualstudio.com/items?itemName=broadcomMFD.code4z-extension-pack).

<br />

<details>
<summary id="address-software-requirements"><span style="font-size: 1.5em"><b>Address Software Requirements</b></span><hr></summary>

Before you use Abend Analyzer for Mainframe, ensure that your site and workstation meet the following requirements:

### Server

Abend Analyzer for Mainframe requires SymDump version 11 to operate.

Before you use Abend Analyzer for Mainframe, complete the following tasks:

- Acquire and install PTFs LU02175, LU03402, LU03403, and LU12023.
- Configure the Testing Tools Server and SymDump REST API. If you already have a Testing Tools Server instance for InterTest and SymDump, redeploy it after you install the PTFs from the previous task.
- To connect through the Zowe API Mediation Layer, integrate the SymDump REST API with Zowe API ML.

For more information, see the [InterTest and SymDump documentation](https://techdocs.broadcom.com/itsd).

### Client

Abend Analyzer for Mainframe is supported on Visual Studio Code and Github Codespaces.
</details>
<details>
<summary id="integrate-with-zowe-explorer"><span style="font-size: 1.5em"><b>Integrate with Zowe Explorer</b></span><hr></summary>

Integrate Abend Analyzer for Mainframe with [Zowe Explorer](https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe) and set up a Zowe profile containing mainframe credentials to enable the Single Sign-On feature of Zowe API ML.

<div align="center">
<a href="https://www.openmainframeproject.org/all-projects/zowe/conformance"><img alt="This extension is Zowe v3 conformant" src="https://artwork.openmainframeproject.org/other/zowe-conformant/zowev3/explorer-vs-code/color/zowe-conformant-zowev3-explorer-vs-code-color.png" width=208 height=156 /></a>
</div>

</details>
<details>
<summary id="add-a-connection-to-the-mainframe"><span style="font-size: 1.5em"><b>Add a Connection to the Mainframe</b></span><hr></summary>

Add a connection to the mainframe to enable communication between Abend Analyzer for Mainframe and SymDump. You can connect directly to your Testing Tools Server or API Mediation Layer gateway using basic authentication (username and password), or by using a Zowe profile. To use a Zowe profile, ensure you have a profile in your team configuration that contains mainframe credentials and either the host address of your Testing Tools Server or Zowe API ML Gateway.

1. Select the Abend Analyzer for Mainframe tab in your IDE.
2. In the sidebar, click **Add Connection**.  
The prompt bar displays at the top of the window.
3. Enter a name for your connection. Ensure that the connection name is unique.
4. Select authentication with **Username and Password** or **Zowe Profile**.
5. If you selected **Username and Password**, do the following:
   1. Enter the URL of your Testing Tools Server instance in the format `http(s)://host:port`, or a Zowe API ML gateway URL in the format `http(s)://host:port/service-id/api/v1`.
   2. (Testing Tools Server only) Select **No** to block self-signed certificates or **Yes** to trust self-signed certificates.
   3. Enter your mainframe username.
   4. (Optional) Enter your mainframe password. If you skip this step, a prompt for your password displays when you open a repository.
6. If you selected **Zowe Profile**, do the following:
   1. Select your Zowe profile from the list.
   2. If the selected profile is authenticated through a Zowe API ML gateway and you are signed into the Zowe Authentication service, enter your Zowe API ML service ID when prompted.
   3. If the selected profile contains credentials to connect to a Testing Tools Server, do the following:
      1. Enter the URL of your Testing Tools Server instance in the format `http(s)://host:port`.
      2. Select **No** to block self-signed certificates or **Yes** to trust self-signed certificates.
  
The connection displays in the sidebar.
 
To edit your connection, right-click the connection in the sidebar and select **Edit connection**, then follow the steps above again.

To delete a connection, right-click the connection in the sidebar and select **Delete connection**.
</details>
<details>
<summary id="load-a-repository"><span style="font-size: 1.5em"><b>Load a Repository</b></span><hr></summary>

Load an abend report repository to view reports.

1. Click the **+** icon next to your connection name.  
The prompt bar displays at the top of the window.
2. Enter the full name of your abend report repository data set.
3. Select either **CICS** or **Batch** from the dropdown list.
4. If prompted, enter your mainframe password.
The abend report repository loads in the sidebar. 

If you specified an incorrect DSN, right-click the repository in the sidebar and select **Edit DSN** to specify the DSN again. 

To remove a repository from the sidebar, right-click the repository and select **Remove dataset**.
</details>
<details>
<summary id="filter-and-sort-reports"><span style="font-size: 1.5em"><b>Filter and Sort Reports</b></span><hr></summary>

To sort reports in the repository by date, right click the repository data set in the tree and select **Sort by date (ascending)** or **Sort by date (descending)**. 

To sort by a different parameter, select **Sort** and select one of the options that display at the top of the window. To change the order from ascending to descending, select **Sort** and choose the same option again.

If you have a large number of reports, you might need to apply a filter to find the reports you need.

1. Right-click the repository data set in the tree and select **Filter**.  
A list of filter options displays at the top of the window.
2. Select one of the options.
3. Enter a filter string and press enter.  
Records containing the filter string are displayed in the sidebar.

Only one filter can be applied at a time. To reset the filter, click the yellow **Cancel filter** icon next to the repository data set.
</details>
<details>
<summary id="lock-unlock-and-delete-reports"><span style="font-size: 1.5em"><b>Lock, Unlock and Delete Reports</b></span><hr></summary>

You can lock abend reports to ensure that they are not edited or deleted by other users. To lock or unlock a report, right-click it and select **Lock report** or **Unlock report**.

To delete a report, click the delete icon next to the report name in the sidebar. The delete icon does not appear if the report is locked.
</details>
<details>
<summary id="load-symbolic-data-from-a-protsym"><span style="font-size: 1.5em"><b>Load Symbolic Data From a PROTSYM</b></span><hr></summary>

If you have symbolic data saved in a PROTSYM, you can load the PROTSYM using Abend Analyzer for Mainframe to display the symbolic data in the report. 

1. Under your connection, click the **+** icon next to **PROTSYMS**.  
The prompt bar displays at the top of the window.
2. Specify the DSN of your PROTSYM and press enter.
3. Open the report linked with the specified PROTSYM. If the report is already open, close and reopen it.
</details>   
<details>
<summary id="display-options"><span style="font-size: 1.5em"><b>Display Options</b></span><hr></summary>

To display global options for your instance of SymDump Batch, right-click your connection and select **Display global options**.

To display an options table for an individual CICS abend report repository (PROTDMP), right-click the data set and select **Display PROTDMP options**.
</details>
<details>
<summary id="customize-the-report-label"><span style="font-size: 1.5em"><b>Customize the Report Label</b></span><hr></summary>

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
</details>
   
<details>
<summary id="technical-assistance-and-support"><span style="font-size: 1.5em"><b>Technical Assistance and Support</b></span><hr></summary>

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
</details>
<details>
<summary id="privacy-notice"><span style="font-size: 1.5em"><b>Privacy Notice</b></span><hr></summary>

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
</details>
