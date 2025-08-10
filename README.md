# ReFrameWork_WorkFlow

ReFrameWork has for different state machine
  1. Initialization
  2. Get Transaction Data
  3. Process Transaction
  4. End Process

For Initialization
  steps
    Open InitAllSettings > Add Message Box > "I am from init All Setting XMAL File"

    Open Kill All Process > A dd mséssage Box " "I am from Kill All Process Setting XMAL File"

    Open InitAllApplication > Add message Box > " "I am from initAllApplication Setting XMAL File"



  Step
    For Get Transaction Data
      Open > GetTransaction Data > Add message box > " "I am from Get Transaction data Setting XMAL File"

   Step
    For Process Transaction
      Open > Get Data Process Data > Add message box > " "I am from Get Transaction data Setting XMAL File"

   Step
    For End Process
      Open > CloseAllApplication > Add message box > " "I am from Close All Application XMAL File"



IMPLEMENTATION START
Step
  Open Initializaton
  open config file
      -on setting sheet Name as = StrLogin
      -value = www.rpachallenge.com

Next Manin > 
  -on Invoke IniialiApplication workflow
  -click open Workflow
  -click on Activities panel
      > search for > Use Application/Broswe
      >drag and place below the message box
      > click on indicate Application to Automate
      this help to navigate to browser

  But i dont want to enter url directly. i want to fech it from  congif file. so delete the URL

  Browser URL
  > in_comfig("strLoginURL").ToString
> Add message bos below the first message box = "URL Value fetched from Congfig file:" + in_config("strLoginURL").ToString


Step
In the InitAllApplication
    > create Arguments > in_strLoginURL

NEXT
create a fresh Sequence= name it "RPA_Challenege_Login_Page
search Open Broswer drag inside the sequence
create Argument > In_strLoginURL
on the Open Browser > URL = in_strLoginURL
  Then go back to InitAllApplication delete Use Aplication Browser
  then delete Argument created for it StrLoginUrl > Save

NEXT 
Go to Main
drag newly segence "RPA_Chanlenge_Login_Page" 
place below Invoke InitAllApplication workflow
refresh Argument
Expend 1 item (s) Dictionary on the value enter = Config("strLoginURL").ToString
Save

Add Sequebce on Main >Invoke InitAllApplication Workfloe below this
Inside sequence Add > Read Range WorkBook

NEXT
Go to www.cloud.uipath.com
Go to Config on Document Save on Laptop & Open it
Name Add > strInPutFilePath
Value Add > Paste the rpa excel file download on computer Path

NEXT
Go Back to Studio
Sequence for read range workbook
Path = Config("strInPutFilePath").tostring

click inised Read Range Workbook
  Output DataTable = ctrl + k DtMyData

  search for Bulk Add Queue Item
  Add it below Sequence "Read Range Workbook"


  NEXT
  Go to www.cloud.uipath.com > Orshestractor
  click on Queue > Add Queue > Name it Employee_Data_Queue
  Add

  NEXT
  Go to Studio Save All
  on the Bulk Add Queu Items
    > Orchestrator folder path > anthonyochuba9@gmail.com
    >Queue name > employee.Data_Queue
    >Data Table > DtMyData


NEXT
on RPA challenge_Login:Page:Panel
drag maximin windown > Inside Do > Add Delay
drag click Add Below Maximium window
Click indicate element inside browser


NEXT in Process Transaction
Open Process Transaction
Invoke Process workflow > click Open workflow
drag multiplr Assign > Add below >"Comment (Placeholder")
  -DSave to > Ctrl +k = str_FirstName
  -Value to save > In_TransactionItem.specificContest("firt Name").tostring

drag Anchor Base Below > Multiple Assign
drag find element place inside Anchor Base
click on indicate on screen eg Label First name
click on 3 dot line > open in UiExplorere >Innertext > Validate> Highligt > Save
drag type into > place inside Anchor Base
click indicate on the screen >First name
Text > from dropdown > str_FirstName

REPEAT FOR THE FOLLOWING
Lastname, company name, role in company, Address, Email, Phone Number

Next
drag click > Place below the last Anchor base 
click on indicate on screen
click on Submit.
