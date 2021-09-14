# FirstBankOfSuncoast

Store History of Transactions
Class Transaction
List<Transaction>

Menu Options

Support Checking & Savings
deposit
withdraw
view balance of

START ATM = inactive

Display Image 1; for 5 seconds
If the user touches screen go to Step 8
Display Image 2; for 5 seconds
If the user touches screen go to Step 8
Display Image 3; for 5 seconds
If the user touches screen go to Step 8
Go to Step 1
ATM = active: Prompt user to insert card "Welcome to SDG Bank. Please insert card."
If no card is inserted after 15 seconds go to Step 1
Once card is inserted, if: a. Card is invalid display an error message "This card is invalid, please visit a teller for more information. Thank you.", eject card and return to Step 1 b. The account doesn't exist, display an error message "No account found, please visit a teller for more information. Thank you.", eject card and return to Step 1 b. Card is valid, prompt user to enter PIN "Please enter your PIN on the keypad, and press Enter."
If PIN is invalid, request PIN again "Incorrect PIN, please try again."
If PIN is invalid, request PIN again "Incorrect PIN, one attempt remaining, account will be locked if incorrect."
If PIN is invalid, alert the user "Incorrect PIN, this account has been locked, please visit a teller for more information. Thank you.", lock the account associated with the card, eject card, return to Step 8
If PIN is valid, prompt the user to select account type, "Please select an account. "Checking" "Savings"" a. If "Checking" or "Savings" go to Step 15 b. Else; "Exit" go to Step 16
Display transaction menu of "Withdraw Cash", "Deposit Cash", "Print Balances", "Exit" for the selected account
If "Exit" is selected, eject card, display "Thank You." for 5 seconds, return to Step 1
If "Withdraw Cash" is selected prompt user to "Enter the amount requested in multiples of $20 with a max daily limit of $2500" a. If the account balance is less than the amount requested, return error message "This account has insufficient funds for the amount requested.", print account balance, and return to Step 14 b. If the ATM has less cash than is requested: return an error message "This ATM has insufficient to complete the transaction. Please visit a teller, thank you.", eject card, return to Step 1 c. Else, if the amount requested is valid: dispense cash, adjust account balance, prompt user to "Complete Another Transaction", "Print New Balance" or "Exit" i. If "Complete Another Transaction" return to Step 14 ii. If "Print New Balance" print receipt with new balances, return to Step 14 iii. If "Exit", eject card, display "Thank you" for 5 seconds, return to Step 1
If "Deposit Cash" is selected prompt user to insert cash "Please insert cash."
Count cash inserted, display value.
Prompt user to verify amount deposited "Confirm Amount." "Yes." "No." a. If "Yes.", go to Step 21. b. If "No.", return cash, return to Step 14
Adjust account balance and prompt user to "Complete Another Transaction", "Print New Balance" or "Exit" a. If "Complete Another Transaction" return to Step 14 b. If "Print New Balance" print receipt with new balances, return to Step 14 c. If "Exit", eject card, display "Thank You" for 5 seconds, return to Step 1
If "Print Balance" is selected, print balance in account
Prompt user to "Complete Another Transaction" or "Exit" a. If "Complete Another Transaction" return to Step 14 b. If "Exit", eject card, display "Thank You for 5 seconds, return to Step 1
If "Exit" is selected, eject card, display "Thank You" for 5 seconds, return to Step 1
END ATM = inactive

Martin:

{

    const string CHECKING_ACCOUNT = "checking.csv"
    const string SAVING_ACCOUNT = "saving.csv"
    static void Main(string[] args)
        {
            Console.WriteLine("Welcome to The First Bank of Suncoast");

             // Write transactions into checking.csv
            var fileWriter = new StreamWriter(CHECKING_ACCOUNT);
            // Create an object that can write CSV to the fileWriter
            var csvWriter = new CsvWriter(fileWriter, Culture.Info.InvariantCulture);



            // Ask our csvWriter to write out our list of transactions
            csvWriter.WriteRecords(transactions);
            // Tell the file we are done

            // Load checking.csv into list of transactions

            static List<Transaction> transactions = new List<Transaction>()
            {
              new Transaction("deposit", 100),
              new Transaction("withdraw", 800)

            };

        }

}
public class Transaction
{
public string Action { get; set; }
public int Amount { get; set; }

    public Transaction(string action, int amount)
    {
      Action = action
      Amount = amount
    }

}
