# Microsoft_URI_SCHEME_RCE

Summary:

The binary "protocolhandler.exe" which handles the logic of URI Scheme-based Microsoft Office files, fails to filter two different default Windows Environment Variables (%appdata% and %localappdata%), allowing an attacker to trick a user into automatically downloading and executing an Excel file from the browser to the default Downloads folder and opening a malicious file.
This can be useful for an attacker to use other known and unkown CVEs in the same program in order to execute arbitrary code within the application context.

Description:

By leveraging the Office 365 Excel URI scheme in a malicious HTML document that includes an <\a> HTML element, either one pre-defined "href" value can be placed as follows:

ms-excel:%appdata%/../../Downloads/malicious_excel_file.xls
ms-excel:%localappdata%/../../Downloads/malicious_excel_file.xls

With a little help of a JavaScript function that automatically clicks the <\a> element, the browser will automatically download the potential malicious excel file, prompting a pop-up window to open the malicious_excel_file.xls.

Steps to Reproduce:

Open the PoC.html file with a browser of your choice - preferably one listed on the tested environments below.
As soon as the PoC.html file is loaded, the browser will automatically download the attacker's malicious excel file to your browser's default Downloads folder.
Click on the prompt that will appear to open the downloaded attacker's malicious excel file.

Supporting materials/ references:

PoC.html - used to reproduce the vulnerability.
PoC.gif - demonstrating visually the vulnerability.

Tested Environment: 

Scope: Microsoft Excel (Microsoft®️ Excel®️ for Microsoft 365 MSO (Version 2110 Build 16.0.14527.20234))

Testing Browsers (Last build version of all of them): Google Chrome, Mozilla Firefox, Microsoft Edge, Microsoft IE.
*Only a URL click is required with Mozilla Firefox and Internet Explorer browsers, others required to confirm a browser prompt to open Excel application.

Operating System: Windows 10 version 21H1 (OS Build 19043.1348) (64-bit)

Credits: Sahar Shlichove - Security Researcher
