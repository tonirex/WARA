#Well Architected Framework Reliability Powershell script
The script wara-arg-runner.ps1 was developed to automate the process of evaluating the workloads and automatically create the Excel file for the Action Plan. 

Requirements
To run the script there are 4 prerequisites:

<u>**1.1 The script must be run in Powershell, not Windows Powershell:**<u>

Powershell

<u>**1.2 Git must be installed on the computer: Git**<u>

<u>**1.3 Powershell modules:**<u>

The following Powershell modules must the installed, the script will validate and try to install the required modules. However, we recommend you install the modules manually before running the script.

Install-Module -Name ImportExcel -Force -SkipPublisherCheck
Install-Module -Name Az.ResourceGraph -SkipPublisherCheck
Install-Module -Name Az.Accounts -SkipPublisherCheck

After installing modules, you must open a new Powershell session

<u>**1.4. Unblock the script:**<u>

The script is digitally signed, but the PowerShell module ImportExcel is not. So at this moment, you need to allow the execution of scripts not signed locally:

Set-ExecutionPolicy -ExecutionPolicy Unrestricted

If there is any error regarding "but setting is overriden by a policy defined at a more specific scope"

Use these commands to override the setting:

Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser
 
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope LocalMachine

NOTE
Feedback we have received is that sometimes this command will throw an error message but successfully execute.

Use the command below to manually verify that the execution policy is set to unrestricted.

Get-ExecutionPolicy -list

We recommend you change that setting back after you run the script.

<u>**1.5. Reader permissions in the target Azure tenant/subscription.**<u>

Running the script
Make sure to change your directory to the location that you saved the script to.

Once directory has been changed run:

.\wara-arg-runner.ps1 -TenantID <replace with tenant ID> -Subscription IDs <replace with subscription IDs>