---
title: Virtual Bank
layout: post
date_range: June 2018 - August 2018
post-image: "https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Virtual%20Bank/Banking%20Menu.PNG"
description: A command-line banking application that allows you to deposit, withdraw, and write checks.

---

# About Project
The final project for my C/C++ programming course was to create a command-line virtual banking application that mimicked a real online bank account. Users should be able to deposit, withdraw, and transfer funds between a Checking and Savings Account; issue checks from their Checking Account for a fee; and print mock statements showing user information, acount balances, account fees, and check-writing fees.

# Prompt
```
Design and implement a hierarchy inheritance system of banking, which includes Savings and Checking Accounts of a customer. Inheritance and virtual funtions must be used and applied, otherwise there is no credit.

The following features must be incorporated:
	1. The account must have an ID and customer's full name and his/her	social security number.
	2. General types of banking transactions for both accounts, Checking and Savings: 
		- withdraw
		- deposit
		- calculate interest (based on the current balance, and if it was not modified, there will be no new interest)
		- figure out the balance
		- transfer funds (between the two accounts, from Checking to Savings and vice versa).
	3. Savings restrictions:
		- Become inactive if balance falls below $25 and, under such situation, no more withdrawals may be allowed.
		- A $1 charge for each transfer fund (to Checking account), with the first transfer being free.
		- The monthly interest rate is 3.75%.
	4. Checking restrictions:
		- A monthly service charge is $5 (automatically charged when Checking account was opened).
		- A $0.10 charge for each written check, with the first check free.
		- A $15 charge for each bounced check (not enough funds).
		- The monthly interest rate is 2.5%.
```

# Code

The application was writting in C++ using object-oriented programming principles, such as class inheritance and virtual functions.

The program collected and stored user information in variables that could be recalled when printing mock account statements. Account fees and check fees were tracked as well.

<table>
  <tr>
	<th>Log In Screen</th>
	<th>Welcome Screen</th>
  </tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Virtual%20Bank/Log%20In.PNG" alt="Log-In"></td>
	<td><img src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Virtual%20Bank/Welcome.PNG" alt="Welcome"></td>
  </tr>
</table>

<table>
  <tr>
	<th>Checking Account Menu</th>
	<th>Savings Account Menu</th>
  </tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Virtual%20Bank/Checking%20Account.PNG" alt="Checking"></td>
	<td><img src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Virtual%20Bank/Savings%20Account.PNG" alt="Savings"></td>
  </tr>
</table>