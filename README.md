# Connect Poll Solution

## Summary 
This solution provides a way for a firm to diplay a simple multiple-choice question on a page. The user can choose an available answer to that question.  Once they hae answered the question, they will see the firm wide results.  As the page is refreshed they will see updated answers to the current poll. 

## Components 

### SharePoint Lists
There are two SharePoint List that will contain the poll information. 
- Connect Polls 
    - **Title** : The question this poll is asking
    - **Poll Start Date** : When this poll begins
    - **Poll End Date** : When this poll will end
    - **Persona Groups** : Optional, target group for this poll. 
- Connect Poll Items
    - **Title** : One of the available answers for this poll
    - **Connect Poll Lookup** : the Poll this answer belongs to. Lookup Column to "Connect Polls" above 

> Out of the box this solution is meant to have one active poll at a time, per optional persona group.  It's not enforced, but if there is more than one active poll, the skin will display the most recent. 

## Implementation

### Create SharePoint Lists
The Handshake Connect 2.0 Provisining script is used to create the SharePoint Site Columns, Content Types and Lists

```powershell 
..\HCP-Connect.ps1 -credentials current -xmlfile '..\Content-FirmPoll.xml' -CreateSiteColumns -CreateContentTypes  -CreateLists
```

### Handshake Classes / Skins
- Import Schema-ConnectPolls.xml into the toolkit 
- Copy Connect-Polls* skins to HSPartDefinitions\Custom

### Skins
There are 3 skins
-   **Connect-Polls-Current** : displays the current poll and allows the user to respond with their answer
-   **Connect-Polls-Archive** : displays a grid with all polls and current reponses
-   **Connect-Polls-Response** : Used in the archive grid to display the current response for that poll

#### Connect-Poll-Current

Before user response

![connect-poll-current-0](../master/images/connect-poll-current-0.png?raw=TRUE)

After user response

![connect-poll-current-1](images/connect-poll-current-1.png)

#### Connect-Poll-Archive

![connect-poll-archive](images/connect-poll-archive.png)

> Connect-Poll-Response is displayed in the archive grid above 

## Solution History
| Date | Author | Description |
| -------- | ------- | ------------------------ |
| 2019 10/05 | S. McHargue | Initial Development |
