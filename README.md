# CLOUDBANK VERSION 9-22-2017

The purpose is to allow software to pown coins.

To do this, four services are available:
1. Print Welcome
2. Echo
3. Show Coins
4. Import One Stack
5. Export One Stack
6. Get Receipt

------------------------------------------------------------------
Config file:
The following will be needed in app configurations:

bank_server =  https://CloudCoin.co/ (Use the name of the local host)
timezone = UTC-7 (use the customer's  timezone)

For security, the system admin must setup SSL and limit the servers that can connect to this web server. 
----------------------------------------------------------------
# Services
------------------------
## Print Welcome Service 
Get's the bank's welcome information

Sample request
```
https://cloudcoin.global/bank/print_welcome.php
```
Response if success:
```
{
	"bank_server": "www.myBank.com",
	"status": "welcome",
	"version":"4.07.17",
	"message": "CloudCoin Bank. Used to Authenticate, Store and Payout CloudCoins. 
	This Software is provided as is with all faults, defects and errors, and without warranty of any kind.  
	Free from the CloudCoin Consortium.",
	"time": "2016-40-21 10:40:PM"
}
```

## Echo RAIDA Service
Sample GET Request:
```
https://CloudCoin.co/bank/echo.aspx
```

Echo Response for good
```
{
    "bank_server":"CloudCoin.co",
    "status":"ready",
    "message":"The RAIDA is ready for counterfeit detection.",
    "time":"2016-49-21 7:49:PM"
}
```

Echo Response for bad
```
{
    "bank_server":"CloudCoin.co",
    "status":"fail",
    "message":"Not enough RAIDA servers can be contacted to import new coins.",
    "time":"2016-49-21 7:49:PM"
}
```
Not enough RAIDA servers can be contacted to import new coins.


### IMPORT ONE STACK 

The program must put a stack file in a folder that is accessible via the web to cors on the CloudBank Server. 


Sample POST Request:
```
https://CloudCoin.co/bank/import_one_stack.aspx?
stack=
{
	"cloudcoin": [
		{ 
		"nn":"1", 
		"sn":"1112240", 
		"an": ["f5a52ee881daaae548c24a8eaff7176c", "415c2375a6fa48c4661f5af8d7c95541", "73e067b7b47c1556deebdca33f9a09fb", "9b90d265d102a565a702813fa2211f54", "e3e191ca987c8010a3adc49c6fc18417",
			"baa7578e207b7cfaa0b8336d7ed4a4f8", "6d8a5c66a589532fe9e5dc3932650cfa", "1170b354e097f2d90132869631409bd3", "b7bc83e8ee7529ff9f874866b901cf15", "a37f6c4af8fbcfbc4d77880fc29ddfbc",
			"277668208e9bafd9393aebd36945a2c3", "ef50088c8218afe53ce2ecd655c2c786", "b7bbb01fbe6c3a830a17bd9a842b46c0", "737360e18596d74d784f563ca729aaea", "e054a34f2790fd3353ea26e5d92d9d2f",
			"7051afef36dc388e65e982bc853be417", "ea22cbae0394f6c6918691f2e2f2e267", "95d1278f54b5daca5898c62f267b6364", "b98560e11b7142d1addf5b9cf32898da", "e325f615f93ed682c7aadf6b2d77c17a",
			"3e8f9d74290fe31d416b90db3a0d2ab1", "c92d1656ded0a4f68e5171c8331e0aea", "7a9cee66544934965bca0c0cb582ba73", "7a55437fa98c1b10d7f47d84f9accdf0", "c3577cced2d428f205355522bc1119b6"],
		"ed":"7-2019",
		"pown":"ppppppppppppppppppppppppp",
		"aoid": []
		}

	]
}
```


Sample Response if good:
```
{
 "bank_server":"CloudCoin.co",
 "status":"importing",
 "message":"The stack file has been imported and detection will begin automatically so long as they are not already in bank. Please check your reciept.",
 "reciept":"640322f6d30c45328914b441ac0f4e5b",
 "time":"2016-49-21 7:49:PM"
}
```

Sample Response if bad file bad:
```
{
 "bank_server":"CloudCoin.co",
 "status":"Error",
 "message":"JSON: Your stack file was corrupted. Please check JSON validation.",
 "reciept":"640322f6d30c45328914b441ac0f4e5b",
 "time":"2016-49-21 7:49:PM"
}
```
Sample Response if nothing attached :
```
{
 "bank_server":"CloudCoin.co",
 "status":"Error",
 "message":"LoadFile: The stack file was empty.",
 "reciept":"640322f6d30c45328914b441ac0f4e5b",
 "time":"2016-49-21 7:49:PM"
}
```

# Sample Reciepts
If powning process has not been started
```
{
	"reciept_id": "e054a34f2790fd3353ea26e5d92d9d2f",
	"time": "2016-49-21 7:49:PM",
	"timezone": "UTC-7",
	"bank_server": "bank.CloudCoin.Global",
	"total_authentic": 5,
	"total_fracked": 7,
	"total_counterfeit": 1,
	"total_lost": 0,
	"reciept_detail": [{
			"nn.sn": "1.16777216",
			"status": "suspect",
			"pown": "uuuuuuuuuuuuuuuuuuuuuuuuu",
			"note": "Waiting"
		},
		{
			"nn.sn": "1:1425632",
			"status": "suspect",
			"pown": "uuuuuuuuuuuuuuuuuuuuuuuuu",
			"note": "Waiting"
		},
		{
			"nn.sn": "1.956258",
			"status": "suspect",
			"pown": "uuuuuuuuuuuuuuuuuuuuuuuuu",
			"note": "Waiting"
		},
		{
			"nn.sn": "1.15666214",
			"status": "suspect",
			"pown": "uuuuuuuuuuuuuuuuuuuuuuuuu",
			"note": "Waiting"
		},
		{
			"nn.sn": "1.15265894",
			"status": "suspect",
			"pown": "uuuuuuuuuuuuuuuuuuuuuuuuu",
			"note": "Waiting"
		}

	]

}
```

If powning process is complete:
```
{
        "reciept_id":"e054a34f2790fd3353ea26e5d92d9d2f",
	"time": "2016-49-21 7:49:PM",
	"timezone": "UTC-7",
	"bank_server": "bank.CloudCoin.Global",
	"total_authentic": 5,
	"total_fracked": 7,
	"total_counterfeit": 1,
	"total_lost": 0,
	"reciept_detail": [{
			"nn.sn": "1.16777216",
			"status": "authentic",
			"pown": "ppppppppepppppppppppeppp",
			"note": "Moved to Bank"
		},
		{
			"nn.sn": "1:1425632",
			"status": "counterfeit",
			"pown": "fffffffffpfffffffffffffff",
			"note": "Sent to trash"
		},
		{
			"nn.sn": "1.956258",
			"status": "authentic",
			"pown": "ppppppppppppppppppppppppf",
			"note": "Moved to Fracked"
		},
		{
			"nn.sn": "1.15666214",
			"status": "lost",
			"pown": "pfpfpfpfpfpfpfpfpfpfpfpfp",
			"note": "Moved to Lost"
		},
		{
			"nn.sn": "1.15265894",
			"status": "lost",
			"pown": "ppppffpeepfpppfpfffpfffpf",
			"note": "STRINGS ATTACHED!"
		}

	]

}
```
## Service show_coins

Sample GET Request:

```
https://CloudCoin.co/bank/show_coins.aspx
```
Sample Response:
```
{
 "bank_server":"CloudCoin.co",
 "status":"coins_shown",
 "ones":205,
 "fives":10,
 "twentyfives":105,
 "hundreds":1050,
 "twohundredfifties":98,
 "time":"2016-49-21 7:49:PM"
}
```

## Service export

Sample GET Request:

```
https://CloudCoin.co/bank/export_one_stack.aspx
```
sample response if good

```
{
	"cloudcoin": [
		{ 
		"nn":"1", 
		"sn":"1112240", 
		"an": ["f5a52ee881daaae548c24a8eaff7176c", "415c2375a6fa48c4661f5af8d7c95541", "73e067b7b47c1556deebdca33f9a09fb", "9b90d265d102a565a702813fa2211f54", "e3e191ca987c8010a3adc49c6fc18417",
			"baa7578e207b7cfaa0b8336d7ed4a4f8", "6d8a5c66a589532fe9e5dc3932650cfa", "1170b354e097f2d90132869631409bd3", "b7bc83e8ee7529ff9f874866b901cf15", "a37f6c4af8fbcfbc4d77880fc29ddfbc",
			"277668208e9bafd9393aebd36945a2c3", "ef50088c8218afe53ce2ecd655c2c786", "b7bbb01fbe6c3a830a17bd9a842b46c0", "737360e18596d74d784f563ca729aaea", "e054a34f2790fd3353ea26e5d92d9d2f",
			"7051afef36dc388e65e982bc853be417", "ea22cbae0394f6c6918691f2e2f2e267", "95d1278f54b5daca5898c62f267b6364", "b98560e11b7142d1addf5b9cf32898da", "e325f615f93ed682c7aadf6b2d77c17a",
			"3e8f9d74290fe31d416b90db3a0d2ab1", "c92d1656ded0a4f68e5171c8331e0aea", "7a9cee66544934965bca0c0cb582ba73", "7a55437fa98c1b10d7f47d84f9accdf0", "c3577cced2d428f205355522bc1119b6"],
		"ed":"7-2019",
		"pown":"ppppppppppppppppppppppppp",
		"aoid": []
		}

	]
}
```

# END OF CLOUDBANK VERSION 1










# Server Side CloudCoin Banking Software
*WORK in Progress CLOUDCOIN BANK API 9/19/2017*

This code allows your server or application to pown (password own) CloudCoins and track those CloudCoins owned by your users.
You can also issue "checks" that refer to your CloudCoins so that users/customers who use your bank can trade amoung themselves
without needing to detect counterfeits everytime with the RAIDA. 

NOTE: To Stop Replay attacks and other sercurity concenrs, HTTPS is required. 


Folder Structure
<pre>
UserAccounID
-Bank
-Broke
-Counterfeit
-Export
-Fracked
-Import
-Imported
-Logs
-Lost
-Suspect
-Templates
-Trash
-Waiting
</pre>
# ###################
## Create Account Service
# ##################

*CREATE ACCOUNT REQUEST STRING*

Create an account for a new user. This will create a folder names after the account and populate it with the following subfolders:

* Bank
* Broke
* Counterfeit
* Export
* Fracked
* Import
* Imported
* Logs
* Lost
* Suspect
* Templates
* Trash
* Waiting

**rules for user account names**
Your users must have a unique identifier that allows your system to identify the accounts within the CloudBank. We call this unique identifer the "Account ID." This number will become the name of folders within the CloudBank. This folder could be a number (like a customer number) or a GUID or any thing that you use to uniquly identify your users in your system. 
However, there are some rules: 
Your Account ID must work as folder names for both Windows and Linux Operating sytems.
Account IDs cannot contain any of the following characters:
```
    \ / : * ? " ' < > | 
```
Your CloudBank may treat your Account identifiers as either case sensitive or case insensitive. This depends on if your CloudBank is hosted on a Linux (PHP) or Windows (C#) System. 

POST:
https://cloudcoin.global/bank/add_account.php?
uid=e24b3a755916472f8768e4e9992827a0

uid = Unique Identifier


Note: If the account has already been created the API just says success. 
Response if success:
```
{
	"server": "www.myBank.com",
	"status": "added",
	"message": "Account was created for user e24b3a755916472f8768e4e9992827a0.",
	"time": "2016-40-21 10:40:PM"
}
```

Response if fail:
```
{
	"server": "www.myBank.com",
	"status": "notadded",
	"message": "Account was not created for user e24b3a755916472f8768e4e9992827a0.",
	"time": "2016-40-21 10:40:PM"
}
```

# ###################
## Print Welcome Service 
# ##################

*PRINT_WELECOME REQUEST STRING*

Get's the bank's welcome information

https://cloudcoin.global/bank/print_welcome.php


*PRINT_WELECOME RESPONSE STRING*

Response if success:
```
{
	"server": "www.myBank.com",
	"status": "welcome",
	"version":"4.07.17",
	"message": "CloudCoin Bank. Used to Authenticate, Store and Payout CloudCoins. 
	This Software is provided as is with all faults, defects and errors, and without warranty of any kind.  
	Free from the CloudCoin Consortium.",
	"time": "2016-40-21 10:40:PM"
}
```

# ###################
## Echo RAIDA Service 
# ##################

*ECHO REQUEST STRING*

Ask the bank to echo the RAIDA to make sure it is there. 

https://cloudcoin.global/bank/echo_raida.php


*ECHO RESPONSE STRING*

Response if success:
```javascript
{
	"server": "www.myBank.com",
	"status": "echo",
	"raida_status": ["ready", "notready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", 
	"ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready", "ready"],
	"raida_ms": [226, 526, 510, 326, 1226, 526, 526, 526, 526, 526, 526, 526, 526, 526, 526, 526, 526, 526, 526, 
	526, 526, 526, 526, 526, 526],
	"message": "Echo Completed",
	"time": "2016-40-21 10:40:PM"
}
```


# ##################
## Service ShowCoins
# ##################
Lets the program know how many coins the user has in the bank. Or how many coins are in the bank total.

*SHOWCOINS REQUEST STRING*

https://cloudcoin.global/bank/showcoins.php?id=273C9DFA8061407AB8102C0A4E872CA3

(Shows all the coins that belong to account id 273C9DFA8061407AB8102C0A4E872CA3)

https://cloudcoin.global/bank/showcoins.php?id=all

(Shows all the coins in the bank and fracked)

*SHOWCOINS RESPONSE STRING*
There are two arrays with six indexes each. The first index (zero) is a sum of the coins the account has. Then:
+ 0 Sum of all coins in that catagory. 
+ 1 1s
+ 2 5s
+ 3 25s
+ 4 100s
+ 5 250s

if good:
```javascript
{
	"server": "www.myBank.com",
	"status": "showcoins",
	"bank_totals":["13180","5","15","0","3","50"],
	"fracked_totals":["285","0","1","1","0","1"],
	"aoid":"273C9DFA8061407AB8102C0A4E872CA3",
	"total":"13465",
	"message": "273C9DFA8061407AB8102C0A4E872CA3 has 13465 CloudCoins",
	"time": "2016-40-21 10:40:PM"
}
```

if good all:
```javascript
{
	"server": "www.myBank.com",
	"status": "showcoins",
	"bank_totals":["13180","5","15","0","3","50"],
	"fracked_totals":["285","0","1","1","0","1"],
	"aoid":"all",
	"total":"13465",
	"message": "Total in bank is 13465 CloudCoins",
	"time": "2016-40-21 10:40:PM"
}
```

if bad:
```javascript
{
	"server": "www.myBank.com",
	"status": "fail",
	"bank_totals":["0","0","0","0","0","0"],
	"fracked_totals":["0","0","0","0","0","0"],
	"aoid":"273C9DFA8061407AB8102C0A4E872CA3",
	"total":"0",
	"message": "Account did not exist",
	"time": "2016-40-21 10:40:PM"
}

```

*SHOWCOINS REQUEST STRING*


https://cloudcoin.global/bank/showcoins.php?id=all

(Count all the coins in the bank for the ID)


*SHOWCOINS RESPONSE STRING*

if good:
```javascript
{
	"server": "www.myBank.com",
	"status": "showcoins",
	"nn":["1","1","1"],
	"sn":["5111558","9665542","1569855"],
	"aoid":"273C9DFA8061407AB8102C0A4E872CA3",
	"total":"1242",
	"message": "273C9DFA8061407AB8102C0A4E872CA3 has 1242 CloudCoins",
	"time": "2016-40-21 10:40:PM"
}
```
if bad:
```javascript
{
	"server": "www.myBank.com",
	"status": "fail",
	"nn":["1","1","1"],
	"sn":["5111558","9665542","1569855"],
	"aoid":"273C9DFA8061407AB8102C0A4E872CA3",
	"total":"0",
	"message": "Account did not exist",
	"time": "2016-40-21 10:40:PM"
}

```

if All:
```javascript
{
	"server": "www.myBank.com",
	"status": "totals",
	"nn":["1","1","1"],
	"sn":["5111558","9665542","1569855"],
	"aoid":"273C9DFA8061407AB8102C0A4E872CA3",
	"total":"0",
	"message": "Account did not exist",
	"time": "2016-40-21 10:40:PM"
}

```





# ###################
## Import Service 
# ##################
To send CloudCoins to the bank, your program must first put the CloudCoin stack and jpeg files in the import folder. All files that are placed in the import folder must have a .stack or .jpg extention. The program will first need to create a subfolder that has the same name as the account number that the CloudCoin is to be imported to. Then it must call the Bank's import service to import. The import service places the coins in the suspect folder in the owners subfolder. Then it creates report files for each coin to be imported in the ImportReports folder, and automatically starts the detect their authenticity. 

There is a naming convention for programs to use to put the coins in the import folder:
File Name Format:
```
import/273C9DFA8061407AB8102C0A4E872CA3/700.CloudCoins.ForSean.stack
```
Where 273C9DFA8061407AB8102C0A4E872CA3 = Account ID of the user or entity that the CloudCoins belong to. 


*IMPORT REQUEST STRING*

To pown all the files in the mort folder

https://cloudcoin.global/bank/import.php?id=all

To pown all the files in the import folder that belong to one account:

https://cloudcoin.global/bank/import.php?id=273C9DFA8061407AB8102C0A4E872CA3



*IMPORT RESPONSE STRING*

Response if success:
```javascript
{
	"server": "www.myBank.com",
	"status": "imported",
	"nn": [ 1, 1, 1, 1, 1],
	"sn":[ 16777212, 16777213, 16777214, 16777215, 16777216, ],
	"report_id":"20170614243654524",
	"report":["suspect","suspect","suspect","suspect","suspect"]
	"message": "Coins have been moved to the suspect folder and detection will begin.",
	"time": "2016-40-21 10:40:PM"
}
```
Or Response if Failed
```javascript
{
	"server": "www.myBank.com",
	"status": "fail",
	"cloudcoins": [],
	"message": "The Import folder was empty of the coins from that ID.",
	"time": "2016-40-21 10:40:PM"
}
```

Algorith:

Program seperates all CloudCoins into individual files and puts them in the suspect folder. Then creats a report file in the
DetectionReports Folder. The detction report may look like this to begin with



# ###################
## Detection Report Service
# ##################

*DETECTION_REPORT REQUEST STRING*

To find out how a detection attempt went. 

https://cloudcoin.global/bank/detection_report.php?report_id=20170614243654524


*DETECTION_REPORT RESPONSE STRING*

Response if success:
```javascript
{
	"server": "www.myBank.com",
	"status": "detected",
	"cloudcoins": [{
		"sn": "152485046",
		"nn": "1",
		"results": "counterfeit"
	}, {
		"sn": "152485045",
		"nn": "1",
		"results": "duplicate already exists"
	}, {
		"sn": "152485045",
		"nn": "1",
		"results": "NonJSON file moved to trash"
	}, {
		"sn": "152485045",
		"nn": "1",
		"results": "authentic"
	}],
	"totals":[25,1,56,24],
	"message": "Import Complete",
	"time": "2016-40-21 10:40:PM"
}
```
Totals:

+ 0 Total imported to bank
+ 1 Total Counterfeit
+ 2 Total imported to fracked
+ 3 Total kept in suspect folder

Or Response if Failed
```javascript
{
	"server": "www.myBank.com",
	"status": "empty",
	"cloudcoins": [],
	"message": "The Import Report folder did not have that report",
	"time": "2016-40-21 10:40:PM"
}
```


# ##################
## Change_Owner Account Service :
# ##################
Requests that a CloudCoin note change ownership from one account to another.

*CHANGE REQUEST STRING*

https://cloudcoin.global/bank/change_owner.php?nn=1&sn=15489521&newid=273C9DFA8061407AB8102C0A4E872CA3


*CHANGE RESPONSE STRING*

if success
```javascript
{
    "server": "www.myBank.com",
	"status": "change",
	"message": "Change Complete",
	"time": "2016-40-21 10:40:PM"
}
```
if fail
```javascript
{
    "server": "www.myBank.com",
	"status": "fail",
	"message": "Change Failed, No such account",
	"time": "2016-40-21 10:40:PM"
}
```
# ##################
# Export Service
# ##################
Exports the coins from the bank folder to the export folder/email so they can be downloaded or emailed.

*EXPORT REQUEST STRING*

https://cloudcoin.global/bank/export.php?sn=15489521&tag=273C9DFA8061407AB8102C0A4E872CA3&action=email&destination=Sean@Wortington.net

action will be either email, download or some other transfer method. 

*EXPORT RESPONSE STRING*

Response if good:
```javascript
{
	"server": "www.myBank.com",
	"status": "exported",
	"url":"www.myBank.com/export/2017-05-12-15-45-0f74aa51",
	"message": "Export Complete",
	"time": "2016-40-21 10:40:PM"
}
```
Response if bad:
```javascript
{
	"server": "www.myBank.com",
	"status": "fail",
	"url":"",
	"message": "Coin did not exist",
	"time": "2016-40-21 10:40:PM"
}
```


# ##################
## Change_Maker Service 
# ##################
Tells the Bank to break a CloudCoin note into several smaller notes.
Note that there are many (but a finte) way of making chage for each denomination. Each denomination will have a list (or matrix) of possible breaks with an id for Method for each possible method. 
 
*CHANGE_MAKER REQUEST STRING*

https://cloudcoin.global/bank/make_change.php?nn=1sn=88772322&method=100D

if good:

*CHANGE_MAKER RESPONSE STRING*
```javascript
{
	"server": "www.myBank.com",
	"status": "success",
	"nn":["1","1","1"],
	"sn":["5111558","9665542","1569855"],
	"message": "CloudCoin note was broken into smaller units.",
	"time": "2016-40-21 10:40:PM"
}
```
if bad:
```javascript
{
	"server": "www.myBank.com",
	"status": "fail",
	"nn":["1","1","1"],
	"sn":["5111558","9665542","1569855"],
	"message": "CloudCoin note was broken into smaller units.",
	"time": "2016-40-21 10:40:PM"
}

```

Make Change
*CHANGE_MAKER METHODS:*

Denominaton 1
+ 1 (Cannot break)

Denaomination 5
+ Method 5A: 1,1,1,1,1

Denomination 25
+ Method 25A: 5,5,5,5,5 (Min)
+ Method 25B: 5,5,5,5,5A
+ Method 25C: 5,5,5A,5A,5A
+ Method 25D: 5A,5A,5A,5A  (Max)

Denomination 100
+ Method 100A: 25,25,25,25 (min)
+ Method 100B: 25,25,25,25A
+ Method 100C: 25,25,25A,25B
+ Method 100D: 25D,25D,25D,25D (Max)


Denomination 250
+ Method 250A: 100,100,25,25 (Min)
+ Method 250B: 100A,100A,25A,25B
+ Method 250C: 100B,100B,25B,25C
+ Method 250D: 100D,100D,25D,25D (Max)



# ##################
## Issue Reference Service 
# ##################
The Issue Reference service issues a "check" that refers to a real cloudcoin in the bank. 
The purpose is to allow CloudCoins to circulate amoung the bank customers without having 
to authenticate with the RAIDA everytime they change hands instead they will authenticate 
with the bank.

CloudCoin check format:

Any file can store a CloudCoin check because the CloudCoin check is stored in the file name.
However, it is best to have a txt (text) file with a .check extension. The text file keep
he size of the file small.

Example of a CloudCoin check embedded in a file name:

```
250.CloudCoin.1.16777216.cb5e46ce270545b39b5efa9d9e199d93.www.myBank.com.2017.05.17.13.45.Any user memo here less 
than 155 characters.check
```

Denomination: For human reading.
CloudCoin: Litteral string for human reading
SN: Serial Number
NN: Network Number
AN: Single authenticity number (GUID with no hyphens) 
Bank Server URL: A DNS name or IP address of an application that can can turn the check into a 
real CloudCoin
Year:Year
Month
Day
Hour
Minute
Memo: 
Inside you can place a memo too. 


*ISSUE_REFERENCE REQUEST STRING*

https://cloudcoin.global/bank/issue_reference.php?nn=1&sn=88772322&method=1

*ISSUE_REFERENCE RESPONSE STRING*
```javascript
{
	"server": "www.myBank.com",
	"status": "success",
	"name":"250.CloudCoin.1.16777216.cb5e46ce270545b39b5efa9d9e199d93.www.myBank.com",
	"message": "CloudCoin note issued as reference.",
	"time": "2016-40-21 10:40:PM"
}
```
if bad:
```javascript
{
	"server": "www.myBank.com",
	"status": "fail",
	"name":"",
	"message": "CloudCoin not found. No reference can be made.",
	"time": "2016-40-21 10:40:PM"
}
```

# ##################
## Deposit Reference Service 
# ##################

*DEPOSIT_REFERENCE REQUEST STRING*

https://cloudcoin.global/bank/deposit_reference.php?an=cb5e46ce270545b39b5efa9d9e199d93

*DEPOSIT_REFERENCE RESPONSE STRING*
```javascript
{
	"server": "www.myBank.com",
	"status": "success",
	"name":"250.CloudCoin.1.16777216.cb5e46ce270545b39b5efa9d9e199d93.www.myBank.com",
	"message": "CloudCoin note issued as reference.",
	"time": "2016-40-21 10:40:PM"
}
```
if bad:
```javascript
{
	"server": "www.myBank.com",
	"status": "fail",
	"name":"",
	"message": "CloudCoin not found. No reference can be made.",
	"time": "2016-40-21 10:40:PM"
}
```

# ##################
## Service Detect Reference
# ##################

https://RAIDA20.cloudcoin.global/bank/detect_reference?nn=1&sn=16777216&an=1836843d928347fb22c2142b49d772b5&pan=1836843d928347fb22c2142b49d772b5

*Detection Response Example If Passed:*
```javascript
{
  "server":"www.myBank.com",
  "status":"pass",
  "sn":"16777216",
  "nn":"1",
  "message":"Authentic:16777216 is an authentic 1-unit. Your Proposed Authenticity Number is now the new Authenticate Number. Update your file.",
  "time":"2016-44-19 7:44:PM"
}
```
Note that the 1 after the word Authentic: is the serial number of the unit that was tested.
 
*Detection Response Example If failed to authenticate:*
```javascript
{
  "server":"www.myBank.com",
  "status":"fail",
  "sn":"16777216",
  "nn":"1",
  "message":"Counterfeit: The unit failed to authenticate on this server. You may need to fix it on other servers.",
  "time":"20"
}
```






END OF API





