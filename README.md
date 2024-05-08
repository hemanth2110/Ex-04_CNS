# Ex-04
# DEMONSTRATION OF INTRUSION DETECTION SYSTEM(IDS) 
 
# AIM: 
         To demonstrate Intrusion Detection System (IDS) using Snort software tool. 
 
 
# STEPS ON CONFIGURING AND INTRUSION DETECTION: 
 
1. Download Snort from the Snort.org website. (http://www.snort.org/snort-downloads) 
2. Download Rules(https://www.snort.org/snort-rules). You must register to get the rules.
(You should download these often) 
3. Double click on the .exe to install snort.  This will install snort in the “C:\Snort” folder.It is 
important to have WinPcap (https://www.winpcap.org/install/) installed 
4. Extract the Rules file. You will need WinRAR for the .gz file. 
5. Copy all files from the “rules” folder of the extracted folder.  Now paste the rules into 
“C:\Snort\rules” folder. 
6. Copy “snort.conf” file from the “etc” folder of the extracted folder.  You must paste it into 
“C:\Snort\etc” folder. Overwrite any      existing file.  Remember if you modify your 
snort.conf file and download a new file, you must modify it for Snort to work. 
7. Open a command prompt (cmd.exe) and navigate to folder “C:\Snort\bin” folder. ( at the 
Prompt, type cd\snort\bin) 
8. To start (execute) snort in sniffer mode use following command: 
snort -dev -i 3 -i indicates the interface number.  You must pick the correct interface number.  In my case, it 
is 3. 
 -dev is used to run snort to capture packets on your network. 
 
To check the interface list,  use following command: 
 snort   -W 
 
 ![image](https://github.com/IsaacAIML2023/Ex-04_CNS/assets/158465339/83d7de69-ebad-45e4-a444-3b5fdce21db9)


# Finding an interface 
 
You can tell which interface to use by looking at the Index number and finding Microsoft.  
As you can see in the above example, the other interfaces are for VMWare.  My interface is 
3. 
9. To run snort in IDS mode, you will need to configure the file “snort.conf” according to 
your network environment. 
10. To specify the network address that you want to protect in snort.conf file, look for the 
following line. 
var HOME_NET 192.168.1.0/24  (You will normally see any here) 
11. You may also want to set the addresses of DNS_SERVERS, if you have some on your 
network. 
 
Example: 
example snort 
12. Change the RULE_PATH variable to the path of rules folder. 
 var RULE_PATH c:\snort\rules 
 
path to rules 
13. Change the path of all library files with the name and path on your system. and you must 
change the path    of snort_dynamicpreprocessorvariable. 
C:\Snort\lib\snort_dynamiccpreprocessor 
You need to do this to all library files in the “C:\Snort\lib” folder. The old path might be: 
“/usr/local/lib/…”. you will need to    replace that path with your system path.  Using 
C:\Snort\lib 
14. Change the path of the “dynamicengine” variable value in the “snort.conf” file.. 
Example: 
 dynamicengine C:\Snort\lib\snort_dynamicengine\sf_engine.dll  
 
15 Add the paths for “include classification.config” and “include reference.config” files. 
  include c:\snort\etc\classification.config 
include c:\snort\etc\reference.config 
16. Remove the comment (#) on the line to allow ICMP rules, if it is  commented with a #. 
 include $RULE_PATH/icmp.rules 
17. You can also remove the comment of ICMP-info rules comment, if it is commented. 
 include $RULE_PATH/icmp-info.rules 
18. To add log files to store alerts generated by snort,  search for the “output log” test in 
snort.conf and add the following line: 
output alert_fast: snort-alerts.ids 
19.  Comment (add a #) the  whitelist $WHITE_LIST_PATH/white_list.rules and the 
blacklist 
 
Change the nested_ip inner , \  to nested_ip inner #, \ 
20. Comment out (#) following lines: 
#preprocessor normalize_ip4 
#preprocessor normalize_tcp: ips ecn stream 
#preprocessor normalize_icmp4 
#preprocessor normalize_ip6 
#preprocessor normalize_icmp6 
 
21. Save the “snort.conf” file. 
 
 
22. To start snort in IDS mode, run the following command: 
 
snort -c c:\snort\etc\snort.conf -l c:\snort\log -i 3 
(Note: 3 is used for my interface card) 
 
If a log is created, select the appropriate program to open it.  You can use WordPard or 
NotePad++ to read the file. 
 
To generate Log files in ASCII mode, you can use following command while running snort 
in IDS mode: 
snort -A console -i3 -c c:\Snort\etc\snort.conf -l c:\Snort\log -K ascii 
 
23. Scan the computer that is  running snort from another computer by using PING or NMap 
(ZenMap). 
After scanning or during the scan you can check the snort-alerts.ids file in the log folder to 
insure it is logging properly.  You will see IP address folders appear. 
 
Snort monitoring traffic – 
 
 ![image](https://github.com/IsaacAIML2023/Ex-04_CNS/assets/158465339/95bdedbe-90ce-41d1-a19f-c50ba02394c1)

 
# RESULT: 
  Thus  demonstration of Intrusion Detection System (IDS) using Snort software tool was implemented successfully. 







  # EXPLORING N-STALKER, A VULNERABILITY ASSESSMENT TOOL 
  
 # AIM: 
 To download the N-Stalker Vulnerability Assessment Tool and exploring the features. 
 
# EXPLORING N-STALKER: 
 N-Stalker Web Application Security Scanner is a Web security assessment tool. 
 It incorporates with a well-known N-Stealth HTTP Security Scanner and 35,000 Web 
attack signature database. 
 This tool also comes in both free and paid version. 
 Before scanning the target, go to “License Manager” tab, perform the update. 
 Once update, you will note the status as up to date. 
 You need to download and install N-Stalker from www.nstalker.com. 
 
1. Start N-Stalker from a Windows computer. The program is installed under Start ➪ 
Programs ➪ N-Stalker ➪ N-Stalker Free Edition.  
2. Enter a host address or a range of addresses to scan. 
3. Click Start Scan. 
4. After the scan completes, the N-Stalker Report Manager will prompt 
5. you to select a format for the resulting report as choose Generate HTML. 
6. Review the HTML report for vulnerabilities. 
 
 ![image](https://github.com/IsaacAIML2023/Ex-04_CNS/assets/158465339/f83917c1-ed89-4125-a6fa-a060fe755cb2)

 
Now goto “Scan Session”, enter the target URL. 
 
In scan policy, you can select from the four options, 
 Manual test which will crawl the website and will be waiting for manual attacks. 
 full xss assessment 
 owasp policy 
 Web server infrastructure analysis. 
 
Once, the option has been selected, next step is “Optimize settings” which will crawl the 
whole website for further analysis. 
 
In review option, you can get all the information like host information, technologies used, 
policy name, etc. 
 
![image](https://github.com/IsaacAIML2023/Ex-04_CNS/assets/158465339/5b783b6d-347a-4bd4-a8f9-64cbcd13b75b)
![image](https://github.com/IsaacAIML2023/Ex-04_CNS/assets/158465339/d6fa80c9-7025-4a28-b02b-796decebd7c9)

Once done, start the session and start the scan.  
 
The scanner will crawl the whole website and will show the scripts, broken pages, hidden 
fields, information leakage, web forms related information which helps to analyze further. 
 
 ![image](https://github.com/IsaacAIML2023/Ex-04_CNS/assets/158465339/3d6104f7-f217-45a8-9faa-ee117a4c6d3b)

Once the scan is completed, the NStalker scanner will show details like severity level, 
vulnerability class, why is it an issue, the fix for the issue and the URL which is vulnerable to 
the particular vulnerability? 
 
 ![image](https://github.com/IsaacAIML2023/Ex-04_CNS/assets/158465339/7bff201b-2d00-43aa-9bc0-fa7681ade360)

 
# RESULT:
  Thus the N-Stalker Vulnerability Assessment Tool was downloaded and  the features were explored successfully... 

