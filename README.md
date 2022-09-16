function sendMails() {
 
  var wrkBk = SpreadsheetApp.getActiveSpreadsheet();
  var wrkShtEmailIds= wrkBk.getSheetByName("Email_Id");
  var wrkShtMessage= wrkBk.getSheetByName("Mail_Details");

  var subject = wrkShtMessage.getRange('A2').getValue();
  var message = wrkShtMessage.getRange('B2').getValue();

  for (var i=2;i<=5;i++) {

    var fname = wrkShtEmailIds.getRange('A' + i).getValue();
    var lname = wrkShtEmailIds.getRange('B' + i).getValue();
    var emailAddress = wrkShtEmailIds.getRange('C' + i).getValue();
    var totalBill = wrkShtEmailIds.getRange('D' + i).getValue();
    var finalmsg = "";
    finalmsg = "Hi " + fname + ", " + "\n" + message;
    finalmsg=finalmsg.replace("Total amount due is:","Total amount due is:" + totalBill);
    MailApp.sendEmail(emailAddress, subject, finalmsg);
    }
    }
