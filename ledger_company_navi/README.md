Problem description

https://www.geektrust.in/coding-problem/backend/ledger-co

Summary
1. Give Loan
2. Accept Payments
3. Display Balance

INPUT:

LOAN MBI Harry 2000 2 2

BALANCE IDIDI Dale 5

PAYMENT MBI Harry 5000 10


1. We would have LoanManager, BalanceManager, PaymentManager

   LoanManager - It is for capturing & validating loan data. If all fine then it will pass info to LoanProcessor
   
   PaymentManager - It is for capturing & validating payment data. It will get payment list for customer and call PaymentProcessor
   
   BalanceManager - It is for capturing & validating Balance data. It will get payment list for customer and call BalanceProcessor to 
                    display balance.
                    
2. Model 

   Loan -   
        double principal; double interestAmount; double amount; int emiMonths; int emiAmount; List<Payment> paymentList;
   
   Payment -
        double amountPaid, int emiCountLeft, Date dueDate

3. Util - One customer can have Loan from different Banks
   
    Map<String, Map<String, Loan>> customerLoanMap = new HashMap<>();
