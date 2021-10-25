# Smart-Contract-
For this project, I've taken on the role of the founder of a new startup which has created its own Ethereum-compatible blockchain to help connect financial institutions. My startup wants to build smart contracts to automate some company finances to make everyone's lives easier, increase transparency, and to make accounting and auditing practically automatic.I have created what is called a ProfitSplitter contract, where the contract will pay my Associate-level employees quickly and easily. In additiona, this contract will accept Ether into the contract and divide the Ether evenly among the associate level employees of the startup. This will allow the Human Resources department to pay employees quickly and efficiently.

## Contract Creation: 

At the top of my contract, I defined the following public variables (as seen in ../Solidity.sol)

employee_one -- The address of the first employee. Make sure to set this to payable.
employee_two -- Another address payable that represents the second employee.
employee_three -- The third address payable that represents the third employee.


Next, I created a constructor function that accepts:


address payable _one
address payable _two
address payable _three


Within the constructor, I set the employee addresses to equal the parameter values. This will the contract to avoid hardcoding the employee addresses.
Next, create the following functions:

- balance -- This function is set to public view returns(uint), and returns the contract's current balance. Since we will always be sending Ether to the   beneficiaries, this function will always return 0. 

- deposit -- This function will set to public payable check, ensuring that only the owner can call the function.
   In this function, I performed the following steps:
   
   - Set a uint amount to equal msg.value / 3; in order to calculate the split value of the Ether.
   - Transfered the amount to employee_one.
   - Repeated the steps for employee_two and employee_three.

Next, I created a fallback function using function() external payable, and called the deposit function from within it. This ensures that the logic in deposit executes if Ether is sent directly to the contract. This is important to prevent Ether from being locked in the contract since we don't have a withdraw function in this use-case.
