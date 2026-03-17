	UiPath Meditech Expanse Automation
	Overview
	This UiPath automation project aims to streamline and automate tasks to create patients in Expanse by leveraging UiPath's robust automation capabilities, the workflow enhances efficiency, reduces manual errors, and ensures timely completion of repetitive tasks.
	Table of Contents
1. Project Description
2. Prerequisites
3. Setup Instructions
4. Usage
5. Workflows Included
6. Troubleshooting
7. Contributing
8. License
	Project Description
	The Meditech Expanse Automation project includes several UiPath workflows designed to automate test patient creation. These tasks include data entry and report generation. The goal is to reduce the manual workload on staff, thereby allowing them to focus more on critical decision-making and important tasks.
	Prerequisites
	Before you can use the UiPath Meditech Expanse Automation project, ensure you have the following:
· UiPath Studio installed
· A valid UiPath license
· Access to Meditech Expanse environment
· Access to QA Orchestrator environment (acoeTESTING);                                                                       
· Necessary Meditech Expanse credentials
· .NET Framework 4.* or later
· Excel and mail activities packages installed in UiPath Studio
	Setup Instructions
1. Clone the Repository:
	.https://github.com/Hca-Automation/QA_Expanse_Registration_DPx.git (branch name: for_Orchestrator_robots)
	 
2. Open the Project: 
· Launch UiPath Studio.
· Open the cloned project folder.
3. Configure Environment Variables: 
· Update the Nona_Launch_and_Login.xaml workflow; there are 2 major activities: Get Credential & Get 3-4 ID from Asset. These assets can be changed under Expanse_DPx folder in QA Orchestrator (full path: QACOE/Expanse_DPx) OR Clone all assets from public folder to 'My Workspace' to run automation locally.  with the necessary environment-specific details such as Meditech Expanse URLs, credentials, and other settings.
4. Install Dependencies: 
– UiPath.Testing.Activities
– UiPath.Excel.Activities
– UiPath.Mail.Activities
– UiPath.System.Activities
– UiPath.UIAutomation.Activities
· Ensure all required UiPath packages are installed. You can do this by navigating to the 'Manage Packages' section in UiPath Studio and installing any missing dependencies.

Usage
5. Run the Main Workflows to create patients with additional clinical data: 
· Open the (SmokeTest_(visit type)).xaml workflow under (SmokeTest_Facilities_(visit type)) folder in UiPath Studio.

· Put/Change value/s for (in_quantityOfPts; in_ExpanseClinic; in_Facility)
· in_quantityPts - any desired number of quantity patients;
in_ExpanseNetwork - only 3 Networks are accepted now: NHA(New Hampshire), NCFL(North Central Florida) and ORL(Lake Nona). One notice: please, use these values with capital letters as provided in previous sentence.
In_Facility - any facility you want to use (please, put only mnemonic values here).
 
· Click the 'Run' button to execute the automation.
· Monitor the execution via UiPath Orchestrator or the output console in UiPath Studio.

6. Schedule the Automation: 

Use UiPath Orchestrator to schedule the automation based on your requirements (e.g., daily, weekly).

     Workflows Included

•Data Entry: the workflows which are responsible for inputs of patient data placed under these folders: Ancillary; Clinical; EDM; PatientRegistraton(Automates the input of patient data into Meditech Expanse).

•Report Generation: After execution, the output data will be stored in excel file under “Output_Data(Actual Result).xlsx”; full path of location: Utility/ExcelDataTables/Output_Data(Actual Result).xlsx. Excel file with only account numbers of patients in “Created_Patients.xlsx”.

      Troubleshooting


1.There is a lot of failure happens because of performance of Meditech Expanse.

2.There might be missed immunization for particular patient, the reason is missed cart for room (in process of registering a patient you need to select a room which has an associated cart and there is no way to see if the certain room has a cart association with a Room at the beginning of execution).


3.Most of the failures can happen while documenting the selected Care items in Expanse. The current items are scripted:
     1)Admission Health History +
     2)Discharge Instructions +
     3)Plan of Care Prioritized Problems +
     4)Vital Signs/Height/Weight/Measurements +


Usage in Orchestrator (QA Orchestrator (acoeTESTING); Location of team folder: QACOE/Expanse_DPx):

 - There are 2 processes in that folder: Discharge_Patients & QA_Expanse_Registration_Process_All_Visit_types ('Discharge_Patients' process currently is not working, the main process is the second one). 

 - Before running the process, make sure you'll follow these steps:

1) Under the Assests tab user has to edit couple assets:
     1. MeditechExpanse_LoginCredentials - by clicking 'edit' there will be 'Username' & 'Password' input boxes, put your own credentials. Aslo, make sure that you will change the 'Description' and put your 3-4 ID, like Current User: (your 3-4 ID).
     2. Username Expanse - the same steps as in 1. clause, but there is only a 'Text' input box, put your own 3-4 ID as well. 

2) Click 'Edit' in 'QA_Expanse_Registration_Process_All_Visit_types' process to see the 'Entry point' dropdown of main processes related to visit types (SmokeTestingFacilities_(Visit Type)\SmokeTest_(Visit Type).xaml) and arguments for chosen entry point.

3)Here's the arguments which have to be edited before starting a job:

    • in_Facility - put the facility value here (Notice: please, use the mnemonics name, for instance: COCUE, FMH, COCYKO etc.).

    • in_ExpanseNetwork - put the Network where you want to create the patients (Current active Networks: NCFL(North Central Florida); NHA(New Hampshire) and ORL(Orlando). Pleease, put there mnemonic name only). 

    • in_quantityOfPts - sets the total of desired patients which should be created by one run (it can be left empty, then 1 will be default number there).

**NOTICE**: "Just in case, if you see some running processes and you're not sure should you wait until the end of execution or not, you can still trigger it, but under your credentials to prevent interruption of someone's active session."
    






