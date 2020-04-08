---
layout: post
title: Automating Email with Google Apps Scripts
date: 2019-03-11 19:00:20 -0800
description: Using GMail, Sheets, and Drive to send emails
img: emailer.jpg
tags: [GCP, Google Apps Scripts, GMail, SpreadsheetApp, GSuite]
---
<!-- <img src='{{site.baseurl}}/assets/img/emailer.jpg' alt='file desc'> -->

### Email automation is a way to create emails that reach the right people with the right message at the right moment—without doing the work every time. 

---

In this journal entry on Email Automation I'll be covering:

- Google Gmail, Drive, & Spreadsheet Services
1. Getting a list from a spreadsheet
2. Creating a HTML & Plain Text Email Message
3. Adding a custom send email menu button
4. Attaching files from Google Drive

Google offers an amazing tool to work with along side their GSuite products and that's [Google Apps Scripts](https://developers.google.com/apps-script/) 'GAS'.

Quick shout out to [www.benlcollins.com](https://www.benlcollins.com/). Without his articles and recipes on GAS, at times I would have been lost.

---

Here's our sitation.<br>
>Recently you had an event and provided a sign-up list for people who wanted information about your product or service. It will be the same templated message being sent to everyone. Sitting down to email everyone you look into third party options for sending mass email blasts, but you really dont need all the extra features that you'd be paying for. Due to privacy concerns you don't want to just CC everyone on the same email, and BCC feels really unprofessional. In addition, you want add a personal touch and decide to add the recipient name in the email. This time only 12 people signed up on your list, so it's a pretty easy task. You sit down, type your tempalted email, then copy paste the first person's name and email into your message and press send. You edit and send your email for the second, third, and everyone else down the list.<br><br>At the next event things go crazy. Hundreds of people show up and sign up on your list. Now trying to manually complete your personalized email task just got exponetially more time consuming. What are you to do? No fear, Google Apps Scripts are here!

---

## 1. Getting a list from a spreadsheet

First, let's look at how we get our event sign up list from a Spreadsheet into something we can use in our Apps Script.

Once you have contacts populated on a spreadsheet, navigate to the menu, click **Tools>Script Editor**.

~~~SQL
# Example Spreadsheet Data
      | Column A                | Column B   |
- - - | - - - - - - - - -  - -  | - - - - -  |
Row 1 | Email Address           | First Name |
- - - | - - - - - - - - -  - -  | - - - - -  |
Row 2 | john.p.romano@gmail.com | Johnny     |
~~~

From here we have to get a list of recipients and their first name and email Address.

~~~javascript
function run(){
  // SET sheet id
  // Your spreadsheet ID is a unique string at the end of your URL
  // https://docs.google.com/spreadsheets/d/ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789/
  // var id = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789'
  var id = 'REPLACE-WITH-YOUR-SPREADSHEET-ID';  

  // GET sheet by id
  var ss = SpreadsheetApp.openById(id);

  // GET sheet by name 'Sheet1'
  var sheet = ss.getSheetByName('Sheet1')

  // SET first row of data to process
  // Row #1 is the title row
  var startRow = 2;

  // GET number of rows to process
  // Row number offset because of title row
  var numRows = ss.getLastRow()-1;

  // GET the range of cells A2:B2
  // getRange(row, column, numRows, numColumns)
  var dataRange = sheet.getRange(startRow, 1, numRows, 2);

  // GET values for each row in the Range.
  var data = dataRange.getValues();

  Log.logger(data)
}
~~~

Now we can test our work by inserting a logging statement as our last line and running the script. To show the logging console output, from the menu click **View > Show Logs**.

> OUTPUT <BR>
> [19-03-11 11:37:33:358 PDT] [[john.p.romano@gmail.com, Johnny]]

---

## 2. Creating a HTML & Plain Text Email Message

Gmail supports both plain-text and HTML email. When you compose an email in Gmail is creates these for you, but since we're scripting it we'll have to handle both of those ourselves. Here is where it's helpful to have a basic understanding of HTML, but I'll try and break it down. 

To start we'll put together a hard coded email template. With any email correspondence we need to add common elements like subject, salutation, recipient, our main message, valediction, and sender name. 

~~~javascript

// Email Subject
var recipientAddress = 'john.p.romano@gmail.com'
var subject = 'It was great to meet you at our conference in Los Angeles!';

// Email Greeting
var salutation = "Dear";
var recipient = "Valued Customer";

// Email Body
var msg = 'Hello World, and thank you!';

// Email Signature
var valediction = 'Respectfully';
var senderName = 'Johnny Romano';
var senderTitle = 'CEO';

// Default Plain-text Message
var message = salutation + ' ' + recipient + ',\n';
message += msg + ' \n';  
message += valediction + ', \n';
message += senderName + ' \n';
message += senderTitle;

// Send HTML Email
MailApp.sendEmail(recipientAddress, subject, message, {
  name: senderName,
  htmlBody: "<div>" + salutation + " " + recipient + ",</div><br>" +
  "<div>" + msg + "</div><br>"+
  "<div style='font-size:12px'>" + valediction + ",<br></div>" + 
  "<div style='font-size:12.8px'><b>" + senderName + "</b></div><br>" +
  "<div style='font-size:12.8px'>" + senderTitle + "</div>",
}); 

~~~

---

# Putting it all together

Perfect, so now we have all of our components to sending an email. We have our email template, and a Google Sheet with two columns, one for first name, and one for email address. Now we need to build a loop that iterates through our list personalizing the recipient information.

~~~javascript
function run(){

    // Email Subject
    var subject = 'Great Seeing You in our Virtual Los Angeles!';
    
    // Email Greeting
    var fontsize = "12.8px";
    var salutation = "Hi";
    var msg = "Thanks so much for stopping by our booth at CONFERENCE 2020!"
    
    // Email Signature
    var signatureColor = "#073763";
    var valediction = "Best Regards"
    var senderName = "Johnny Romano";
    var senderTitle = "Automation Engineer";
    
    // SET how many recipients
    var sheet = SpreadsheetApp.getActiveSheet();
    var startRow = 2;
    var numRows = sheet.getLastRow()-1;
    var dataRange = sheet.getRange(startRow, 1, numRows, 3);
    
    // Fetch values for each row in the Range.
    var data = dataRange.getValues();
    var num = 0;
    
    // LOOP through all the contacts
    for (i in data) {
        var row = data[i];
        var recipientAddress = row[0]; // First column
        var recipientName = row[1]; // Second column
    
        // Default Plain-text Message
        var message = salutation + " " + recipientName + ',\n\n';
        message += msg + '\n\n'; 
        message += valediction + ', \n';
        message += senderName + '\n';
        message += senderTitle + '\n\n';
                
        // SEND HTML EMAIL
        MailApp.sendEmail(recipientAddress, subject, message, {
        name: senderName,
        htmlBody: "<div style=font-size:12.8px'>" + salutation + " " + recipientName + 
                ",</div>"+
                // HTML Email Body        
                "<br>" + "<div style=font-size:" + fontsize + "'>" + msg + "<br><br>" +
                // Signature
                "<div style='font-size:" + fontsize + "'>" + 
                "<font color='"+ signatureColor + "'>" + valediction + ",</font><br></div>" + 
                "<div style='font-size:" + fontsize + "'>" + 
                "<font color='" + signatureColor + "'> <b>" + senderName + "</b></font></div>" +
                "<div style='font-size:" + fontsize + "'>" + 
                "<font color='" + signatureColor + "'>" + senderTitle + "</font></div><br>"        
        }); 
        num++;
    }
    SpreadsheetApp.getActiveSpreadsheet().toast(num, "Emails sent");
}
~~~

---

## A couple last things...

### 3. Adding a custom send email menu button

The script has to be run from the Script Editor and thats ok it's just not always so user friendly. But Google allows you to create custom menus that will show up as a new menu item. It's easy to add, simply create the following function. This will run our primary script named 'run'.
~~~javascript
// Create custom menu when Spreadsheet opens
function onOpen() {
    SpreadsheetApp.getUi()
    .createMenu('Send Emails')
    .addItem('Send!', 'run')
    .addToUi();
};
~~~

### 4. Attaching files from Google Drive

Sometimes you need to attach a file to your email. Here is a modified example of our send mail template with two pdf's from Google Drive attached.

~~~javascript
// Adding Google Drive Files as attachments                                  
// i.e. https://drive.google.com/open?id=file1ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvw
// PDF File 1
var file1 = DriveApp.getFileById('file1ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghjklmnopqrstuvw'); 

// PDF File 2
var file2 = DriveApp.getFileById('file2ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvw');    

// SEND HTML EMAIL as Active Sheet User
MailApp.sendEmail(recipientAddress, subject, message, {
  name: senderName,
  htmlBody: "<div style=font-size:12.8px'>" + salutation + " " + recipientName + 
          ",</div>"+
          // HTML Email Body        
          "<br>" + "<div style=font-size:" + fontsize + "'>" + msg + "<br><br>" +
          // Signature
          "<div style='font-size:" + fontsize + "'>" + 
          "<font color='"+ signatureColor + "'>" + valediction + ",</font><br></div>" + 
          "<div style='font-size:" + fontsize + "'>" + 
          "<font color='" + signatureColor + "'> <b>" + senderName + "</b></font></div>" +
          "<div style='font-size:" + fontsize + "'>" + 
          "<font color='" + signatureColor + "'>" + senderTitle + "</font></div><br>"        
  
  attachments: [file1.getAs(MimeType.PDF), file2.getAs(MimeType.PDF)]
}); 
~~~

---

### Google API Documentation:<br>

**[Spreadsheet Service](https://developers.google.com/apps-script/reference/spreadsheet)** -
This service allows scripts to create, acces, and modify Google Sheets Files.

**[Gmail Service](https://developers.google.com/apps-script/reference/gmail)** - This Service lets you send email, compose drafts, manage labels, mark messages and threads, and conduct a variety of other Gmail account management tasks.

**[Drive Service](https://developers.google.com/apps-script/reference/drive)** - This service allows scripts to create, find, and modify files and folders in Google Drive.

[Custom Menus in GSuite - onOpen()](https://developers.google.com/apps-script/guides/menus)

[Class DriveApp - getFileById()](https://developers.google.com/apps-script/reference/drive/drive-app#getfilebyidid)

[Class Logger - log()](https://developers.google.com/apps-script/reference/base/logger#log(Object))

[Class MailApp - sendEmail()](https://developers.google.com/apps-script/reference/mail/mail-app#sendEmail(Object))

[Class Sheet - getLastRow()](https://developers.google.com/apps-script/reference/spreadsheet/sheet#getLastRow())

[Class Sheet - getRange()](https://developers.google.com/apps-script/reference/spreadsheet/sheet#getRange(Integer,Integer))

[Class Spreadsheet - toast()](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet#toast(String))

[Class SpreadsheetApp - getSheetByName()](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet#getSheetByName(String))

[Class SpreadsheetApp - openById()](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet-app#openbyidid)

[Class Range - getValues()](https://developers.google.com/apps-script/reference/spreadsheet/range#getvalues)