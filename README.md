# Abend Analyzer for Mainframe

Abend Analyzer for Mainframe provides an interface to [CA SymDump® Batch](https://www.broadcom.com/products/mainframe/testing-and-quality/symdump-batch). This extension allows you to browse, manage and view formatted abend reports and symbolic data in a modern IDE environment.

## Prerequisites
Abend Analyzer for mainframe requires CA SymDump Batch version 11 to operate.

Before you use Abend Analyzer for Mainframe, complete the following tasks:

- Acquire and install PTF LU02175. For more information, see [Release Information](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-intertest-and-ca-symdump/11-0/release-information.html).
- [Install the Testing Tools Server and CA SymDump REST API](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-intertest-and-ca-symdump/11-0/installing/install-testing-tools-server.html). If you already have a Testing Tools Server instance for CA InterTest and CA SymDump, redeploy it after you install the PTF from the previous task.

## Getting Started

To get started with Abend Analyzer for Mainframe, create a connection to the mainframe and load your CA SymDump abend report repository. 

### Manage Connections

To add a connection to the mainframe, **follow these steps**:

1. Select the Abend Analyzer for Mainframe tab in your IDE.
2. In the sidebar, click **Add Connection**.  
The prompt bar displays at the top of the window.
3. Enter a name for your connection. Ensure that the connection name is unique.
4. Enter the URL of your Testing Tools Server instance in the format `http(s)://host:port`.
5. (Optional) Enter your mainframe username and password. If you skip this step, the credentials prompt displays when you open a repository.  
The connection displays in the sidebar.

To edit your connection, right-click the connection in the sidebar and select **Edit connection**, then follow the steps above again.

To delete a connection, right-click the connection in the sidebar and select **Delete connection**.

### Manage Repositories

To load an abend report repository, **follow these steps**: 
1. Click the **+** icon next to your connection name.  
The prompt bar displays at the top of the window.
2. Enter the full name of your abend report repository data set.
3. If you are prompted, enter your mainframe username and password.  
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
