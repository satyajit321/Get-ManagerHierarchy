# Get-ManagerHierarchy
This is to quickly find out who a person is, what designation and the manager title etc. It allows understanding the level of escalation, priority it might need.

Date: 8 Aug 2022
Author: Satyajit
Version: 1.1a

This is working, however the view is cluttered, need to work on a better view.

Get-ManagerHierarchy -DepthLevel 10  

Ran tree cmdlet to get the characters and thier views
├ ─ └ │

#Sample:
tree

node_modules
└───ajv
    ├───dist
    ├───lib
    │   ├───compile
    │   ├───dot
    │   ├───dotjs
    │   └───refs
    └───scripts

#Prerequisite
Connect-ExchangeOnline


#Default hieracy is 3, should be good for most cases, but they can put more to cover all.

   
.EXAMPLE
   Works but looks too cluttered view.

   Get-ManagerHierarchy -Identity satyajit.smith -Depth 10

    Satyajit.Smith@Contoso.com, Fabrikam O365 Associate Manager, Third Party, USA, Fabrikam
    │
    └───Jo.Dear@Contoso.com, Manager IT , Employee, USA, Contoso 
        │
        └───John.Smith@Contoso.com, IT Director, Employee, USA, Contoso 
            │
            └───Adam.Smith@Contoso.com, Head IT, Employee, USA, Contoso 
                │
                └───Joe.Smoth@Contoso.com, Chief Enterprise Technology Officer, Employee, USA, Contoso 
                    │
                    └───Tom.Hanks@Contoso.com, Chief Business Operations Officer, Employee, USA, Contoso 
                        │
                        └───Bill.Gates@Contoso.com, Chief Executive Officer, Employee, USA, Contoso PLC
.EXAMPLE
   DOT sourcing the function
   . C:\Script\Get-MailboxDetails\Get-ManagerHierarchy.ps1

   Get-ManagerHierarchy "Sundar, Krishna"

    Krishna.Sundar@Contoso.com
    ├──Project Manager
    ├──Third Party
    ├──India
    ├──Others
    │
    └───Devi.Das@Contoso.com
        ├──IT Manager
        ├──Employee
        ├──India
        ├──Contoso Industries Private Limited
        │
        └───Abhi.Das@Contoso.com
            ├──IT Lead Manager
            ├──Employee
            ├──India
            ├──Contoso Industries Private Limited
            │
            └───Nisha.Das@Contoso.com
                ├──IT Director - R&D
                ├──Employee
                ├──India
                └──Contoso Industries Private Limited
                
                
#Testing
#Get-ManagerHierarchy -Identity satyajit.smith -Depth 3
#Get-ManagerHierarchy -Identity Careers.Info@Contoso.com
#Get-ManagerHierarchy "Sundar, Krishna"
