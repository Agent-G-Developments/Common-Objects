# Agent G Common Objects Library

## Introduction

The Agent G Common Objects Library is a collection of Power Platform Components developed to support citizen and pro developers within local and central government. All of the components are built using out of the box Microsoft Power Platform objects, meaning you do not need to enable the component framework for canvas apps feature. The repository holds Power Platform solution for Agent G Common Objects Library and a Sample app. This readme file explains how to import solutions and what components are available and how to use them. 


## Importing Solution

Navigate to the latest *Release* within github and download the desired solution zip file. 
- Navigate to either your Power Apps or Power Automate home page.
- Select your desired Power Platform *Environment*
- Click on *Solutions*
- Press *Import Solutions* and then *browse* and select the downloaded zip file *"Agent-G-Common-Objects-Solution.zip"*
- Review the details of the solution and press *Import*

Note this is the same process if you are upgrading the solution.

## Global Configuration Variable (Prerequisite For the Component Library)

To save time developing Power Apps I have created this pfx which I save into all of my Apps. It allows me to easily reference common information anywhere from my apps but also passes information to all of my Common Objects such as the colour theme to use or the font size to be used. 
To use this code in a PowerApp simply navigate to ***App*** option the ***Screens*** menu and paste the below code in the ***OnStart*** property. The first four values should be updated as appropriately for your app however the others should remain as they are.  

```
Set(gblConfiguration, {
// Update the below, they can be then used within your app and in Agent G Component Libraries objects
        AppName: "Agent G Sample App",                                
        AppSummary: "This app showcases the Common Objects Component Library.", // Note you can add regular text or html text to enhance the styling
        AppSupportEmail: "support@AgentG-Developments.com", // To add more than one email address delimit with a semicolon
        AppFontSize: "Medium",
// The below do not need to be amended as the will automatiucally capture this information for use in the app and Component Libraries objects
        UserName: User().FullName,
        UserMail: User().Email,
        UserEntraObjID: User().EntraObjectId,
        UserPhoto: User().Image,
        OS: Host.OSType,
        HostVersion: Host.Version,
        SessionID: Host.SessionID,
        BrowserUserAgent: Host.BrowserUserAgent});
```
  
Once this is added this code you can access the information anywhere in your app. To reference these values type the Gblobal Variable name then a full stop followed by the configuration value you want e.g. ***gblConfiguration.UserPhoto***.

## Common Objects Component Library Introduction

| Component | Description | Sample |
|:---------------:|---------------|:---------------:|
| About This App | This control will display key information from the gblConfiguration script to all end users to clear see details about the app and who supports it. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/About.jpg "ABout This App")
| Action Controls | This small control is designed to perform the common steps of a **_Edit_**, **_Save_** and **_Cancel_** within an app. Save and Cancel options are hidden until the Edit button has been pressed. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/ActionControl.jpg "Action Controls")
| Calendar Interactive | This calender control is designed to display events and allows a user to edit delete and create events. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/CalendarInteractive.jpg "Calendar Interactive")
| Data Validation | This component is made up of seven functions which enable data validation to be performed easily within your app such as check for a valid Email address or UK Postcode. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/DataValidation.jpg "Data Validation")
| Error Banner | This control allows you to display errors / warnings in a uniform way to users; whilst also giving users the option to dismiss or easily report the error. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/ErrorBanner.jpg "Error Banner")
| Font Adjustment | This control works with all components to enable users of your apps to adjust the font size. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/FontAdjustment.jpeg "Font Adjustment")
| Screen Header | This control will cover the width of your visible screen and allow you to optionally have a search input box. This will also display the currently logged in users picture. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/Header.jpeg "Header")
| Loading - Spinner | This is based onn the native spinner control but is enhanced by automatically covering the full screen when its visible. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/LoadingSpinner.jpg "Loading Spinner")
| Loading - Bar Style 1 | This is a left to right style progress bar. It automatically covers the visible screen. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/LoadingBarS1.jpg "Loading Bar Style 1")
| Loading - Bar Style 2 | This is a left to right style loading bar which moves back and forth like kit. It automatically covers the visible screen. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/LoadingBarS2.jpg "Loading Bar Style 2")
| Progression Bar | This progression bar enables you to have a tube map style progression through any number of stages. This is similar in design to the Model Driven Business Process Flow design. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/ProgressionBar.jpeg "Progression Bar.jpeg")
| User Prompt Small | This simple control displays a 2 button dialog box with a small area for text. Buttons, Text, OnSelect are all customisable. This dialog will automatically cover the visible screen. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/PromptSmall.jpeg "User Prompt Small")
| User Prompt Large | This simple control displays a 2 button dialog box with a large area for text and a heading. Buttons, Text, OnSelect are all customisable. This dialog will automatically cover the visible screen. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/PromptLarge.jpeg "User Prompt Large")
| Menu - Side | This control allows you to have a pop out side bar which icons and text for navigating around your app. It can display up to 9 buttons excluding a dedicated settings icon. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/SideBar.jpeg "Side Bar")
| Menu - Waffle | This menu control will appear like a waffle icon and when pressed will present the user with up to 9 icons for navigation excluding a dedicated settings button. This control works best when used with the screen header control. | ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/Waffle.jpeg "Waffle")

## Agent G Component Library User Guide

### <u>About This App</u>

 ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/About.jpg "About This App")

### Description
The About this app component is used to display information such as who supports the app, what its intended purpose is and session data relating to the currently logged in use which can be used to assist in support tickets. The control takes over the full screen by default to ensure user interaction.  All data displayed is fully customisable.

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Background Colour| This input property allows you to adjust the background colour of the object, by default it will use the 80% lighter colour of the app theme bia value **App.Theme.Colors.Lighter80**. 
| About Message| This input property allows you to add the detail displayed on the ABout message. This property accepts HTML for easier formatting and has a predefined message which pulls data about the app from the gblConfiguration variable. 
| Close OnSelect| This event property allows you to add the OnSelect command for the Close button within the component. 


### <u>Action Controls</u>
 ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/ActionControl.jpg "Action Control")
### Description
This control quickly gives the developer a 3 button control to perform Edit, Save and Cancel actions. The Save and Cancel buttons are not visible until Edit is pressed which at this point the Edit button becomes disabled. The input properties allow the developer to easily add the OnSelect actions for each button press. You can also hide the labels so the control just shows icons (Edit Pencil, Save Disk and Cancel Dismiss Circle). You can also disable the Edit button dynamically for scenarios where records may be read only using the Disable Edit property. 

### Custom Properties
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Show Labels| This input property can be set to **true** or **false** and allows the developer to hide the text Edit, Save and Cancel to just leave Icons on the control.  
| Disable Edit| This property allows you to disable the Edit button so users cannot access the Save / Cancel buttons. This property accepts **true** or **false** values. 
| Edit OnSelect| This event property allows you to add the OnSelect command for the Edit button within the component
| Save OnSelect| This event property allows you to add the OnSelect command for the Save button within the component
| Cancel OnSelect| This event property allows you to add the OnSelect command for the Cancel button within the component

### <u>Calendar - Interactive</u>
 ![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/CalendarInteractive.jpg "Calendar - Interactive")
### Description
This control is a responsive and interactive Month view calendar. This control allows you to display, create, edit and delete events all in the single control. Its based on a complex calendar created by Matthew Devaney.com with some additional features like additional fields and event types. 


### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Calendar Content| This input property expects a Table of data to display the Events, the fields all of which are strings expected are:  <br> <br>**EventID** - This can be any unique ID which would be required when performing Updates to events. <br>**Title** - This is the title of the event. <br>**Description** - This is the description or details of the event. <br>**Type** - If you are wanting to indicate different event types such as Meetings and Appointments or Repairs and Visits you can use this field to display. If you only have one event type to display its recommend to hard code "Event" for this field. <br>**StartDate** - This should the start date and time of the event in UK format (DD/MM/YYYY hh:mm). <br>**EndDate** - This should the end date and time of the event in UK format (DD/MM/YYYY hh:mm). <br>**Colour** - This field is optional and allows you to dynamically colour the event based on your logic e.g. the Type or its Start date etc.. If this field is not provided the Accent Colour property is used. 
| Show Delete Option | This input property defaults to true, if set to false the delete event button visible on the edit event screen will not display. 
| Show Add Option | This input property defaults to true, if set to false the + button displayed on the top right of each day will not be displayed stopping users from creating events. 
| Event Types | This input property expects a csv of the event types you will display in the calendar. If you only have a single event type set this value to "Event", alternatively add as many comma separated event types as you which such as "Event, Appointment, Meeting, Visit, Catch up" etc.. 
| Allow Editing| This input property defaults to true, if set to false the Save button within the edit event screen will not be displayed and fields will not be editable.
| Edit Save OnSelect| This event property allows you to add the OnSelect command for the Save button within the Edit Event screen. For your command to save the correct updated values to your data source you will most likely require the event ID and the data fields in their updated for, this is accessible via the Output Property **Selected Event Data**. 
| Add Save OnSelect| This event property allows you to add the OnSelect command for the Save button within the Add Event screen. For your command to save the correct values to your data source you will require the data from the event, this is accessible via the Output Property **New Event Data**. 
| Delete Event OnSelect | This event property allows you to add the OnSelect command for the Delete button within the Edit Event screen. For your command to delete the correct event in your data source you will most likely require the event ID, this is accessible via the Output Property **Selected Event Data**. 
| Selected Event Data | This output property will display a record of the event which has been selected. It will display all data fields in the same format as the Calendar Content table. This can be used to perform Updates and deletes on the selected event as required. 
| New Event Data | This output property will display a record of the event has added on the Add new event screen. It will display all data fields in the same format as the Calendar Content table minus the EventID which would not be available until a record as been created from your data source. This can be used to perform Patch commands for the created event as required. 

Sample Code of the Calendar Content:
```
Table(
    {
        EventID: "0001",
        Title: "Major Repairs Site 180",
        Description: "Major Repairs to site 123 expected duration 5 weeks.",
        Type: "Repair",
        StartDate: "26/06/2025 10:00",
        EndDate: "31/07/2025 14:00"
    },
    {
        EventID: "0002",
        Title: "Site 51 Visit",
        Description: "Site 51 visit, evaluate security. ",
        Type: "Visit",
        StartDate: "27/06/2025 10:00",
        EndDate: "27/06/2025 16:00",
        Colour: Color.SpringGreen
    },
    {
        EventID: "0003",
        Title: "Maintenance of Site 9",
        Description: "Review and maintaine inside Site Number 9. ",
        Type: "Repair",
        StartDate: "06/06/2025 10:00",
        EndDate: "27/06/2025 22:00",
        Colour: Color.LightYellow
    }
)
)
```

### <u>Data Validation</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/DataValidation.jpg "Data Validation")
### Description
This component acts as method of accessing predefined functions for data validation where an output property will provide a true or false depending on the validation. This can be used to validate data in text input boxes via ValidationState properties or whilst saving sata to ensure data quality. This component needs to be placed in the app, but does not have to be on a visible screen, you can set both **X** and **Y** values to **-75** to have it appear off screen or can be placed on an "Admin" screen not accessible to end users.

### Custom Properties 
| Property | Description 
|:--------:|-------------
| IsFinancial| Used to check if a value is a valid UK financial value. Accepted formats are with or without a £ symbol, and with or without 2 decimal places. ```Example pfx: 'Data Validation_1'.IsFinancial(txtInputCost.Value)``` 
| IsInteger| Used to check if a value is a valid integer. This will ensure the value is a numeric value without any decimal places. ```Example pfx: 'Data Validation_1'.IsInteger(txtInputStock.Value)``` 
| IsValidUKPostalCode| This validates if a string is a valid UK formatted postcode. Note this does not check if its a real UK postcode only that it is in a valid format.  ```Example pfx: 'Data Validation_1'.IsValidUKPostalCode(txtInputPostcode.Value)``` 
| IsValidEmailAddress| This validates if a string is a valid email address. ```Example pfx: 'Data Validation_1'.IsValidEmailAddress(txtInputEmail.Value)``` 
| IsBetween| This property uses 3 parameters to validate if a a Value is between an range of numbers. This property only accepts numeric values. ```Example pfx: 'Data Validation_1'.IsBetween(txtInputAge.Value, 0,18)``` 
| IsDateInPast| This property requires a data value and will check if the date is in the past. ```Example pfx: 'Data Validation_1'.IsDateInPast(DatePickerPlannedDelivery.SelectedDate)``` 
| IsDateInFuture| This property requires a data value and will check if the date is in the future. ```Example pfx: 'Data Validation_1'.IsDateInFuture(DatePickerPlannedDelivery.SelectedDate)``` 

### <u>Error Banner</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/ErrorBanner.jpg "Error Banner")
### Description
The Error Banner Control can be used when catching errors to display them consistently to users and give them the option to report an error to Admins directly from the notification. When pressing the Report button it will by default launch a new outlook with session information and the error message ready to send to the App Support email. This could be customised to send an email automatically via a Cloud Flow if desired. Note on the input parameters are code samples which can uncommented to use. 

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Error Message| This field is used to display the error message in the banner. When you catch or raise an error this is the input property to display the text to the user. By default it uses a local variable called locErrorMessage. 
| Background Colour| This input property allows you to adjust the background colour of the object, by default it will use the 80% lighter colour of the app theme bia value **App.Theme.Colors.Lighter80**. 
| Hide Report Button| This property allows you to disable the Report button so users cannot report errors. This property accepts **true** or **false** values. You may want to enable the report button for errors which are unexpected but hide it for expected errors (e.g. when form validation has not been met). 
| Dismiss OnSelect| This event property allows you to add the OnSelect command for the Dismiss button within the component. Usually this would be hiding the banner and clearing the error message value. Default pfx is commented out on this property ready for you to use. 
| Report OnSelect| This event property allows you to add the OnSelect command for the Report button within the component. Default pfx is commented out on this property ready for you to use.

Example of how this error banner can be raised when performing a action:
```
IfError(submitForm(frmRequest),
UpdateContext({locErrorMessage: Concatenate(
        "Error: ",
        FirstError.Message,
        "Kind: ",
        FirstError.Kind,
        ", Observed: ",
        FirstError.Observed,
        ", Source: ",
        FirstError.Source
    ),locShowErrorBanner:true}))
```
Note the above locErrorMessage would store the error messages and the locShowErrorBanner would be used to use on the Visible property of the error banner. 

### <u>Font Adjustment</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/FontAdjustment.jpeg "Font Adjustment")
### Description
This component when used in conjunction with the gblConfiguration script allows end users to adjust the font sizes used with components from Small to XLarge. The component also contains an output property which contains the below pfx which is the default font sizing formula used in the components for adjusting font sizes. 
```
Switch(gblConfiguration.AppFontSize, ""Small"", 16, ""Medium"", 20, ""Large"", 24,""XLarge"", 26, 20)
````


### Custom Properties 
| Property | Description 
|:--------:|-------------
| Increase OnSelect| This input property is used run the formula which increases the font size listed in the **gblConfiguration.AppFontSize**. The default value for this should not be adjusted to ensure it works with the gblConfiguration variable. 
| Decrease OnSelect| This input property is used run the formula which decreases the font size listed in the **gblConfiguration.AppFontSize**. The default value for this should not be adjusted to ensure it works with the gblConfiguration variable. 
| FontSize pfx OnSelect| This output property simply contains the pfx which is used to adjust the font sizes in the controls. This pfx can be used any Font Size property in your app to ensure they are dynamically adjusted with this controls usage. 

### <u>Screen Header</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/Header.jpeg "Header")
### Description
This Screen Header by default will cover the full width of the screen and has an optional search box and customisable text to display. This control as designed to sit under the Waffle menu for a complete navigation user interface. 

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Background Colour| This input property allows you to adjust the background colour of the object, by default it will use the 80% lighter colour of the app theme bia value **App.Theme.Colors.Lighter80**. 
| Title| This input property will display text at the centre of screen header. By Default it will display the screen name via App.ActiveScreen.Name. 
| ShowSearchBox| This input property can be used to show or hide the Search box on the screen header. By default this is set to visible via true, to hide the box set to false. 
| Search Text| This output property is used in conjunction with the search box to allow you to get the text value of what a user has typed into the search box. e.g. 'Screen Header'.SearchText will display whatever text has been typed into the search box. 

### <u>Loading - Spinner</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/LoadingSpinner.jpg "Loading Spinner")
### Description
This Loading Spinner will by default cover the full screen and display a customisable loading message. This control should be used during CRUD (Create, Read, Update and Delete) actions where its visible only until interactions with data sources have completed. This control is simply the native spinner control with a shape to cover the full visible screen. This message text can be set to be a local variable which will allow you to adjust the message from Loading to Saving or Creating messages to allow this control to be used more than one withing your screens without duplicating.  

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Background Colour| This input property allows you to adjust the background colour of the object, by default it will use the 80% lighter colour of the app theme bia value **App.Theme.Colors.Lighter80**. 
| Loading Message| This input property allows you to change the text from Loading by default to any required message. Usually best make this dynamic by using a local variable to be set at run time.

### <u>Loading - Bar Style 1</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/LoadingBarS1.jpg "Loading Bar Style 1")
### Description
This Loading Spinner will by default cover the full screen and display a customisable loading message. This control should be used during CRUD (Create, Read, Update and Delete) actions where its visible only until interactions with data sources have completed. This control is simply the native spinner control with a shape to cover the full visible screen. This message text can be set to be a local variable which will allow you to adjust the message from Loading to Saving or Creating messages to allow this control to be used more than one withing your screens without duplicating.  

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Background Colour| This input property allows you to adjust the background colour of the object, by default it will use the 80% lighter colour of the app theme bia value **App.Theme.Colors.Lighter80**. 
| Loading Message| This input property allows you to change the text from Loading by default to any required message. Usually best make this dynamic by using a local variable to be set at run time.
| Bar Size| This Input property accepts, Small, medium, Large and XLarge values and can be used to adjust the width of the Progress Bar. Default is set to Medium. 
| MessageAboveBar| This input property by default is set to True which means the Loading Message will appear above the progress bar, however setting this value to false will move the message underneath it. 

### <u>Loading - Bar Style 2</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/LoadingBarS2.jpg "Loading Bar Style 2")

### Description
This Loading Spinner will by default cover the full screen and display a customisable loading message. This control should be used during CRUD (Create, Read, Update and Delete) actions where its visible only until interactions with data sources have completed. This control is formed of a HTML progress bar so appears differently to the native options. This message text can be set to be a local variable which will allow you to adjust the message from Loading to Saving or Creating messages to allow this control to be used more than one withing your screens without duplicating.

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Background Colour| This input property allows you to adjust the background colour of the object, by default it will use the 80% lighter colour of the app theme bia value **App.Theme.Colors.Lighter80**. 
| Loading Message| This input property allows you to change the text from Loading by default to any required message. Usually best make this dynamic by using a local variable to be set at run time.
| Bar Size| This Input property accepts, Small, medium, Large and XLarge values and can be used to adjust the width of the Progress Bar. Default is set to Medium. 
| MessageAboveBar| This input property by default is set to True which means the Loading Message will appear above the progress bar, however setting this value to false will move the message underneath it. 

### <u>Progression Bar</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/ProgressionBar.jpeg "Progression Bar")
### Description
The Progression Bar is a dynamic and flexible control to easily display to a user the progress made in a workflow or process. You can indicate All stages along with the Completed, Future Stages to the user. This has been designed to dynamically adjust to however many stages you a the developer configure and is in line with the design of the model driven business process flow design. 
To use this control you simple need to define the Stages in Order and then tell the control which is the last Completed Stage you which to display (This could be the current status of your record). 


### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Stages| This input property expects a table of stages from first to last. The default text provides a simple example of 4 Stages: <br> ``` [{Stage:"Contact Details"},{Stage:"Request"},{Stage:"Finance"},{Stage:"Submit"}]```
| Last Completed Stage| This input property will be used to inform the control which stages are completed and which are pending based the values location in the table of Stages. You just need to use a String for this value e.g. "Finance" to set the control to display Finance as Completed and the stage Submit to be the next stage.  


### <u>User Prompt Small</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/PromptSmall.jpeg "Prompt Small")
### Description
This component is designed to easily display message prompts to users and force interaction such as confirming or canceling. This prompt is designed for smaller confirmation messages such as "Are you sure you want to delete this record" etc.. You can customise both the Cancel and Confirm buttons display text as well as the actions each of them perform via an OnSelect property. This control will cover the full visible screen to ensure user interaction. 

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Background Colour| This input property allows you to adjust the background colour of the object, by default it will use the 80% lighter colour of the app theme bia value **App.Theme.Colors.Lighter80**. 
|Prompt Message| This input property accepts a text string which will display on the message prompt e.g. Are you sure you want to exit without saving? 
|Confirm Button text| This input property when empty will default to "Confirm", however if you type in any text string e.g. "Save" the Confirm button text will amend accordingly. 
|Cancel Button text|This input property when empty will default to "Cancel", however if you type in any text string e.g. "Back" the Confirm button text will amend accordingly. 
|Cancel OnSelect| This event property will should store the commands you want run when the Cancel button is pressed, e.g. updating a variable to hide the prompt. 
|Confirm OnSelect|This event property will should store the commands you want run when the Confirm button is pressed, e.g. deleting a record from your data source and updating a variable to hide the prompt. 


### <u>User Prompt Large</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/PromptLarge.jpeg "Prompt Large")
### Description
This component is designed to easily display message prompts to users and force interaction such as confirming or canceling. This prompt is designed for larger confirmation messages such as "Are you sure you want to create this request along with a summary of the new request. " etc.. You can customise both the Cancel and Confirm buttons display text as well as the actions each of them perform via an OnSelect property. This control will cover the full visible screen to ensure user interaction. 

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Background Colour| This input property allows you to adjust the background colour of the object, by default it will use the 80% lighter colour of the app theme bia value **App.Theme.Colors.Lighter80**. 
|Prompt Heading| This input property accepts a text string which will display at the top of the message prompt above the prompt message. This will appear in bold. This often can be used to display a question for the user and the prompt message can display details to aid in answering the decision e.g. "Are you sure you want to complete this application?"  
|Prompt Message| This input property accepts a text string which will display on the message prompt. THis accepts more text than the small prompt and should be used to display more detail for the user to confirm e.g. <br><br>Application Name: XXXXXXX <br>Application Date: XX/XX/XXXX <br> Description: <br>XXXXXXXXXXXXXXXXXXXXXX<br>XXXXXXXXXXXXXXXXXXXXXX<br>XXXXXXXXXXXXXXXXXXXXXX

|Confirm Button text| This input property when empty will default to "Confirm", however if you type in any text string e.g. "Save" the Confirm button text will amend accordingly. 
|Cancel Button text|This input property when empty will default to "Cancel", however if you type in any text string e.g. "Back" the Confirm button text will amend accordingly. 
|Cancel OnSelect| This event property will should store the commands you want run when the Cancel button is pressed, e.g. updating a variable to hide the prompt. 
|Confirm OnSelect|This event property will should store the commands you want run when the Confirm button is pressed, e.g. deleting a record from your data source and updating a variable to hide the prompt. 


### <u>Menu - Side</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/SideBar.jpeg "Side Bar")
### Description
This component can be used as a navigation menu, by default it collapses to just displaying icons on the left and when pressed will expand to display navigation labels. The menu has a maximum 9 customisable menu items and can be reduced via the property TotalMenuButtons. 

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Menu Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Menu Item Colour| This input property is used to set the colour of the component text and Icons. By default this will match the existing app theme used with the value **App.Theme.Colors.Lighter80**. 
|Menu Items| This input property expects a table of the menu items which contains the Menu Text and Menu Icon. You can record the values in any order and use the MenuItem property which is used to order the menu items. Note the MenuIcon text value should match the text used within the modern Button Icon value. The Table should look similar to this: <br><br> Table(<br>{MenuText: "**Home**", MenuIcon: "**Home**", MenuItem: **1**},<br> {MenuText: "**Menu 2**", MenuIcon: "**ChevronRight**", MenuItem: **2**},<br>{MenuText: "**Menu 3**", MenuIcon: "**ChevronRight**", MenuItem: **3**},<br>{MenuText: "**Menu 4**", MenuIcon: "**ChevronRight**", MenuItem: **4**},<br>{MenuText: "**Menu 5**", MenuIcon: "**ChevronRight**", MenuItem: **5**}<br>)
| Total Menu Buttons| This input property should be used to indicate how many menu items you want to display, by default its set to 9 which is the maximum. 
| Menu Title| This input property will display text at the top of the menu when expanded. By Default it will display the App name from the gblConfiguration variable. 
| Menu Item 1 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 2 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 3 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 4 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 5 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 6 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 7 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 8 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 9 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Setting OnSelect| This Event property allows you to define the OnSelect action when a Setting  Icon or Text is pressed. E.g. a Navigate command. 

### <u>Menu - Waffle</u>
![Alt text](https://github.com/Agent-G-Developments/Common-Objects/blob/main/Screenshots/Waffle.jpeg "Waffle")
### Description
This component can be used as a navigation menu, by default it collapses to just displaying the Waffle icon and when pressed will expand to display navigation buttons. The menu has a maximum 9 customisable menu items + Settings. This Waffle button will expand in size when pressed and this usually works well when placed above the Screen header component to mimic the M365 styling user interface. 

### Custom Properties 
| Property | Description 
|:--------:|-------------
| Font Size| This input property is used to set the Font size of the component. It expects one of the following strings; **Small, Medium, Large and XLarge**. The default value for this property is **gblConfiguration.AppFontSize** so when using the provided APP OnStart global variable gblConfiguration this will automatically work without manually having to set a value. 
| Accent Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
| Background Colour| This input property is used to set the colour of the component. By default this will match the existing app theme used with the value **App.Theme.Colors.Primary**. 
|Menu Items| This input property expects a table of the menu items which contains the Menu Text and Menu Icon. You can record the values in any order and use the MenuItem property which is used to order the menu items. Note the MenuIcon text value should match the text used within the modern Button Icon value. The Table should look similar to this: <br><br> Table(<br>{MenuText: "**Home**", MenuIcon: "**Home**", MenuItem: **1**},<br> {MenuText: "**Menu 2**", MenuIcon: "**ChevronRight**", MenuItem: **2**},<br>{MenuText: "**Menu 3**", MenuIcon: "**ChevronRight**", MenuItem: **3**},<br>{MenuText: "**Menu 4**", MenuIcon: "**ChevronRight**", MenuItem: **4**},<br>{MenuText: "**Menu 5**", MenuIcon: "**ChevronRight**", MenuItem: **5**}<br>)
| Menu Item 1 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 2 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 3 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 4 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 5 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 6 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 7 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 8 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Menu Item 9 OnSelect| This Event property allows you to define the OnSelect action when a Menu Item Icon or Text is pressed. E.g. a Navigate command. 
| Setting OnSelect| This Event property allows you to define the OnSelect action when a Setting  Icon or Text is pressed. E.g. a Navigate command. 

