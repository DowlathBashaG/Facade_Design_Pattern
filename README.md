# Facade_Design_Pattern

Facade Design Pattern :

		The Facade Design Pattern is a structural pattern that provides a simplified interface to a set of interfaces in a subsystem, making it easier to use. 
		
		This pattern is particularly useful when dealing with complex systems where the intricacies are overwhelming for the client code.

		- Make API easy		
		- Interface not required		
		- Usually a refactoring pattern
		- Simplified
		- Loose coupling
		- Improved readbility and usability
		- Encapsulation
		- Layered Architecture
		
Dis Adv :
--------

		- Over usage		
		- Clean up design pattern
		
		
1.

AccountService :
--------------

		class AccountService {
			public void getAccountDetails(String accountId) {
				System.out.println("Fetching account details for account ID: " + accountId);
			}
		}
		

2. 

TransferService :
----------------

		class TransferService {
			public void transferFunds(String fromAccount, String toAccount, double amount) {
				System.out.println("Transferring " + amount + " from account " + fromAccount + " to account " + toAccount);
			}
		}
		
3.

BillPaymentService :
-----------------

		class BillPaymentService {
			public void payBill(String accountId, String billId, double amount) {
				System.out.println("Paying bill " + billId + " from account " + accountId + " with amount " + amount);
			}
		}

4. Create Facade :
----------------

Bank Facade:
-----------

		class BankingFacade {
			private AccountService accountService;
			private TransferService transferService;
			private BillPaymentService billPaymentService;

			public BankingFacade() {
				this.accountService = new AccountService();
				this.transferService = new TransferService();
				this.billPaymentService = new BillPaymentService();
			}

			public void getAccountDetails(String accountId) {
				accountService.getAccountDetails(accountId);
			}

			public void transferFunds(String fromAccount, String toAccount, double amount) {
				transferService.transferFunds(fromAccount, toAccount, amount);
			}

			public void payBill(String accountId, String billId, double amount) {
				billPaymentService.payBill(accountId, billId, amount);
			}
		}


5. 

Main Class :
----------

		public class Main {
			public static void main(String[] args) {
				BankingFacade bankingFacade = new BankingFacade();
				bankingFacade.getAccountDetails("123456");
				bankingFacade.transferFunds("123456", "654321", 100.0);
				bankingFacade.payBill("123456", "BILL001", 50.0);
			}
		}		
		

Example :

		1. JDBC
		2. AWS
