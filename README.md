# google-forms-to-docs
Help, I am trying to create a document using google forms and docs
I have a google form that has a few categories. 
Main question leads to 7 sections and depending on that section you will answer the questions to that topic. 
      Main topic (has 5 questions that pertain to all) 
 a   b  c  d  e  f  g    (in theses 7 sections you will be given about 12 questions)

My final goal is I want to have a google word document that has only the Main topic answers and one of the 7 sections. 
First section starts with the letter p, second section starts with i, I will add the other 5 sections when I get this figured out. 

1) What is the best way to accomplish this?
2) is there a code that if they select 1 of the 7 options then a different (already composed) google word document will fill and save?
3) or is there a way I can have the QUESTIONS listed and their answers if the person answered the question. If it wasnt answered then no question and answer is listed. 

Thank you so much!!


Here is a sample of what I currently have in the code.gs

function autoFillGoogleDocFromForm(e) {
  var timestamp = e.values[0];
  var date = e.values[1];
  var examiner = e.values[2];
  var overviewexaminer = e.values[3];
  var location = e.values[4];
  var checkride = e.values[5];
  var POverView = e.values[6];
  var pPreflightprep = e.values[7];
  var pPreflightproced = e.values[8];
  var pAirportOps = e.values[9];
  var pTOL = e.values[10];
  var pPGRM = e.values[11];
  var pNav = e.values[12];
  var pSlowflt = e.values[13];
  var pBasicIM = e.values[14];
  var pEmerg = e.values[15];
  var pNight = e.values[16];
  var pPostflt = e.values[17];
  var pMissed = e.values[18];
  
  var IOverView = e.values[19];
  var iPreflightprep = e.values[20];
  var iPreflightproced = e.values[21];
  var iAirportOps = e.values[22];
  var iRefInst =e.values[23];
  var iNav = e.values[24];
  var iapproach = e.values[25];
  var iEmerg = e.values[26];
  var iPostflt = e.values[27];
  var iMissed = e.values[28];
  
  var templateFile = DriveApp.getFileById("This is left blank on purpose");
  var templateResponseFolder = DriveApp.getFolderById("This is left blank on purpose");
  
  var copy = templateFile.makeCopy(checkride + ', ' + examiner + ', ' + timestamp, templateResponseFolder);
  
  var doc = DocumentApp.openById(copy.getId());
  
  var body = doc.getBody();
  
  body.replaceText("{{timestamp}}", timestamp);
  body.replaceText("{{Date}}", date);
  body.replaceText("{{Examiner}}", examiner);
  body.replaceText("{{Overviewexamier}}", overviewexaminer);
  body.replaceText("{{Location}}", location);
  body.replaceText("{{CHECKRIDE}}", checkride);
  body.replaceText("{{Overview}}", POverView);
  body.replaceText("{{Prefltprep}}", pPreflightprep);
  body.replaceText("{{prefltproc}}", pPreflightproced);
  body.replaceText("{{airportops}}", pAirportOps);
  body.replaceText("{{tol}}", pTOL);
  body.replaceText("{{maneuvers}}", pPGRM);
  body.replaceText("{{nav}}", pNav);
  body.replaceText("{{slowstall}}", pSlowflt);
  body.replaceText("{{instrument}}", pBasicIM);
  body.replaceText("{{emerg}}", pEmerg);
  body.replaceText("{{night}}", pNight);
  body.replaceText("{{postflt}}", pPostflt);
  body.replaceText("{{missed}}", pMissed);
  
  body.replaceText("{{Overview}}", IOverView);
  body.replaceText("{{Prefltprep}}", iPreflightprep);
  body.replaceText("{{prefltproc}}", iPreflightproced);
  body.replaceText("{{airportops}}", iAirportOps);
  body.replaceText("{{RefInst}}", iRefInst);
  body.replaceText("{{nav}}", iNav);
  body.replaceText("{{approach}}", iapproach);
  body.replaceText("{{emerg}}", iEmerg);
  body.replaceText("{{night}}", iNight);
  body.replaceText("{{postflt}}", iPostflt);
  body.replaceText("{{missed}}", iMissed);
  
  doc.saveAndClose();
        
 
}
