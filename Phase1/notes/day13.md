Day 013 Notes: Thinking Like a Programmer				
Why we use this				
Computers do exactly what you tell them, nothing more. You must give clear steps.				
Big problems feel impossible. Small steps feel easy.				
Planning before coding saves time, because fixing a plan is cheaper than fixing code.				
For Playwright: every test is a list of steps (open page, type, click, check). If you can break a problem into steps, you can write a test.				
1. Break a problem into steps				
				
Theory				
				
Take a big problem and split it into small, clear steps				
Each step should be so simple that it has only one action				
Ask: "What must happen first? Then what?"				
				
Example: Withdraw money from an ATM				
				
Insert card				
Enter PIN				
Choose "Withdraw"				
Enter amount				
Check balance is enough				
Give cash				
Return card				
2. Input → Process → Output (IPO)				
				
Theory				
Every program does three things:				
				
Input	Process	Output		
Data given	What we do with it	Result shown		
				
Example: Calculate total bill				
				
Input	Process	Output		
Price, quantity	Multiply price by quantity, add tax	Total amount		
				
Ask three questions: What do I get? What do I do with it? What do I give back?				
				
3. Pseudocode				
				
Theory				
				
Plain-English steps that look like code but aren't a real language				
No strict syntax, so anyone can read it				
Write it first, then convert it to real code				
				
Example: Check if a person can vote				
				
START				
READ age				
IF age >= 18				
PRINT "Eligible to vote"				
ELSE				
PRINT "Not eligible"				
END IF				
END				
				
Common words: READ, PRINT, IF / ELSE, FOR / WHILE (repeat), SET				
				
4. Flowchart				
				
Theory				
A flowchart is a picture of the steps using shapes and arrows.				
				
Shape	Meaning			
Oval	Start / End			
Rectangle	A step or action			
Diamond	A decision (Yes / No)			
Parallelogram	Input / Output			
Arrow	Direction of flow			
				
Example: Voting check				
				
(Start)				
↓				
[Read age]				
↓				
<age >= 18?>				
Yes ↓      ↓ No				
[Eligible] [Not eligible]				
↓        ↓				
(End)				
How the four fit together				
Problem → Break into steps → Identify IPO → Write pseudocode → Draw flowchart → Code				
Real-time problems developers face				
Banking industry				
#	Problem	Input	Process	Output
1	Fund transfer	Sender, receiver, amount	Check balance, deduct, add to receiver	Success or failure message
2	Loan eligibility	Salary, credit score, loan amount	Compare against rules	Approved / Rejected
3	Fraud detection	Transaction details	Flag unusual amount or location	Alert or block
				
Example pseudocode (transfer):				
				
READ amount				
IF balance >= amount				
balance = balance - amount				
PRINT "Transfer successful"				
ELSE				
PRINT "Insufficient funds"				
Gaming industry				
#	Problem	Input	Process	Output
1	Score and level up	Points earned	Add to score, check if threshold reached	New score, next level
2	Player health	Damage taken	Subtract from health, check if zero	Alive or Game Over
3	Matchmaking	Player skill ratings	Group players with similar skill	A balanced match
				
Example pseudocode (health):				
				
health = health - damage				
IF health <= 0				
PRINT "Game Over"				
Manufacturing industry				
#	Problem	Input	Process	Output
1	Inventory tracking	Stock count, items used	Subtract used, compare with minimum	Reorder alert
2	Quality check	Product measurements	Compare to allowed range	Pass or Reject
3	Machine monitoring	Temperature, vibration readings	Check against safe limits	Warning or shutdown
				
Example pseudocode (inventory):				
				
stock = stock - used				
IF stock < minimum				
PRINT "Reorder needed"				
IT industry				
#	Problem	Input	Process	Output
1	Login system	Username, password	Match against stored data, count attempts	Access or error
2	Bug tracking	Bug report	Assign severity and owner, track status	Ticket with status
3	Automated test (Playwright)	Test steps, test data	Run steps in browser, compare actual to expected	Pass or Fail
				
Example pseudocode (login):				
				
READ username, password				
IF username and password match				
PRINT "Welcome"				
ELSE				
PRINT "Invalid login"				
Quick reference				
Term	One line			
Decomposition	Split a big problem into small steps			
IPO	Input, Process, Output			
Pseudocode	Plain-English plan, not real code			
Flowchart	Picture of the steps			
Algorithm	A clear list of steps to solve a problem			
Practice (10 minutes)				
				
Pick one and write the IPO table, pseudocode, and flowchart:				
				
Check if a number is even or odd				
Login with a maximum of 3 attempts				
Calculate a discount: 10% off if the total is above 1000				
				
Send me your answer to one of them, and I'll check it. If you want these notes as an Excel-ready table like Days 5 and 6, tell me.				