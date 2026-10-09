# Bank Account Simulator

A command-line bank account simulator written in Python. It was built as a beginner-friendly project to practice **conditional statements** (`if` / `elif` / `else`), **functions**, **return values**, and basic **object-oriented programming** with a class.

## Features

- Deposit money with input validation
- Withdraw money with insufficient-funds checks
- Optional minimum balance rule
- Check the current balance
- View a transaction history
- Interactive menu in the terminal
- Handles invalid input (non-numeric amounts, bad menu choices) without crashing
- Built-in tests that need no extra libraries

## Requirements

- Python 3.6 or newer (uses f-strings)
- No third-party packages

## Getting Started

Clone the repository and run the program:

```bash
git clone https://github.com/<your-username>/bank-account-simulator.git
cd bank-account-simulator
python bank_account.py
```

## Usage

When you start the program you'll see a menu:

```
Welcome, Student!

1) Deposit  2) Withdraw  3) Balance  4) History  5) Quit
Choose an option:
```

Example session:

```
Choose an option: 1
Amount to deposit: 500
Deposited 500.0. New balance: 500.0

Choose an option: 2
Amount to withdraw: 1000
Insufficient funds.

Choose an option: 4
Deposit        500.0   balance: 500.0
```

## Using the BankAccount class in your own code

```python
from bank_account import BankAccount

account = BankAccount('Alice', balance=500, min_balance=100)

success, message = account.withdraw(450)
print(message)                  # Insufficient funds.

success, message = account.withdraw(400)
print(message)                  # Withdrew 400. New balance: 100

print(account.check_balance())  # 100
print(account.show_history())
```

`deposit()` and `withdraw()` both return a tuple of `(success, message)`, so the calling code decides what to do with the result instead of the method printing directly.

## Running the Tests

```bash
python bank_account.py --test
```

Expected output:

```
PASS  test_deposit_valid
PASS  test_deposit_invalid
PASS  test_withdraw_valid
PASS  test_withdraw_insufficient_funds
PASS  test_withdraw_invalid_amount
PASS  test_withdraw_exact_balance
PASS  test_minimum_balance
PASS  test_history

8/8 tests passed
```

The test functions follow the `test_` naming convention, so they also work with pytest:

```bash
pip install pytest
pytest bank_account.py
```

## Project Structure

```
bank-account-simulator/
├── bank_account.py   # BankAccount class, menu, and tests
└── README.md
```

## Concepts Demonstrated

| Concept | Where it appears |
|---|---|
| `if` / `elif` / `else` | Validation in `deposit()` and `withdraw()`, menu handling in `main()` |
| Comparison and logical operators | Minimum balance check, amount validation |
| Functions with parameters and defaults | `get_amount()`, `BankAccount.__init__()` |
| `return` vs `print()` | Methods return results; only `main()` prints |
| Classes and methods | `BankAccount` |
| Exception handling | `try` / `except ValueError` in `get_amount()` |
| Loops | Menu loop with `while True` |
| Testing with `assert` | Test functions and `run_tests()` |

## Ideas for Extending the Project

- Support multiple accounts stored in a dictionary
- Add a `transfer()` method between two accounts
- Save and load account data from a JSON file
- Add interest calculation
- Add a PIN check before transactions
- Rewrite the tests with `unittest` or `pytest` fixtures

## License

This project is licensed under the MIT License. Feel free to use it for learning.
