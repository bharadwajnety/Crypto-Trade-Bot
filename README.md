# Crypto-Trade-Bot
Binance Futures Testnet Trading Bot
A simplified, well-structured Python trading bot for Binance Futures Testnet with comprehensive logging and error handling.
 Features
 Core Requirements

Market orders (instant execution at current price)
Limit orders (execute at specific price or better)
Support for both BUY and SELL sides
Command-line interface with input validation
Comprehensive logging to file and console
Detailed error handling
Real-time order status tracking

  Bonus Features

Stop-Limit orders (advanced order type)
Account balance monitoring
Open orders management
Order cancellation functionality

  Quick Start
1. Install Dependencies
bashpip install python-binance
2. Set Up Binance Testnet Account

Go to Binance Futures Testnet
Register with your email
Navigate to API Management
Create new API key and secret
Save your credentials securely

3. Run the Bot
bashpython trading_bot.py
Enter your API credentials when prompted.
📖 How It Works
Architecture Overview
BasicBot Class
├── __init__()           # Initialize with API credentials
├── _test_connection()   # Verify API connectivity
├── Market Orders        # Instant execution
├── Limit Orders         # Price-specific execution
├── Stop-Limit Orders    # Conditional execution
├── Order Management     # Status, cancel, view
└── Account Info         # Balance and positions
Order Types Explained
1. Market Order

Executes immediately at current market price
Best for: Quick entry/exit, high liquidity scenarios
Example: Buy 0.001 BTC at whatever the current price is

2. Limit Order

Executes only at specified price or better
Best for: Getting better prices, patient trading
Example: Buy 0.001 BTC only if price drops to $60,000

3. Stop-Limit Order (Bonus)

Triggers a limit order when stop price is reached
Best for: Stop-losses, breakout trading
Example: If BTC drops to $59,000 (stop), sell at $58,900 (limit)

 Usage Examples
Example 1: Place a Market Buy Order
Select option: 1
Enter symbol: BTCUSDT
Enter side: BUY
Enter quantity: 0.001
Confirm? yes
Example 2: Place a Limit Sell Order
Select option: 2
Enter symbol: ETHUSDT
Enter side: SELL
Enter quantity: 0.01
Enter limit price: 3500
Confirm? yes
Example 3: Set a Stop-Loss with Stop-Limit
Select option: 3
Enter symbol: BTCUSDT
Enter side: SELL
Enter quantity: 0.001
Enter stop price: 59000    # Triggers when price hits this
Enter limit price: 58900   # Executes at this price
Confirm? yes
 Understanding the Logs
The bot creates timestamped log files: trading_bot_YYYYMMDD_HHMMSS.log
Log levels:

INFO - Normal operations (orders placed, prices checked)
WARNING - Non-critical issues (symbol not found)
ERROR - Failed operations (API errors, invalid orders)

Sample log entry:
2025-10-02 10:30:45 - INFO - Placing MARKET BUY order for 0.001 BTCUSDT
2025-10-02 10:30:46 - INFO - Market order placed successfully!
2025-10-02 10:30:46 - INFO - Order ID: 123456789
2025-10-02 10:30:46 - INFO - Status: FILLED
🔧 Code Structure Explanation
Key Components
1. Initialization & Connection
pythonbot = BasicBot(api_key, api_secret, testnet=True)

Sets up Binance client
Configures testnet URL
Tests connection
Logs account information

2. Order Placement Functions

Each order type has its own method
Validates inputs before submission
Logs all API requests and responses
Returns order details or None on failure

3. Input Validation
pythonvalidate_input(prompt, input_type, validator)

Type checking (string, float, int)
Custom validation rules
Error handling for invalid inputs
Keyboard interrupt support

4. Error Handling

Try-except blocks on all API calls
Specific handling for BinanceAPIException
Detailed error logging
User-friendly error messages

  Best Practices Demonstrated

Separation of Concerns: Each function has one clear purpose
Comprehensive Logging: All actions are logged with timestamps
Input Validation: All user inputs are validated before processing
Error Handling: Graceful failure with informative messages
Code Documentation: Clear docstrings for all functions
User Confirmation: Critical actions require explicit confirmation
Testnet Safety: Defaults to testnet to prevent accidental live trading

   Common Issues & Solutions
Issue 1: "API connection failed"
Solution: Verify your API key and secret are correct, and your IP is whitelisted on Binance Testnet
Issue 2: "Insufficient balance"
Solution: Go to Binance Testnet and request test USDT from the faucet
Issue 3: "Symbol not found"
Solution: Use correct symbol format (e.g., BTCUSDT not BTC-USDT)
Issue 4: "Order would immediately trigger"
Solution: For limit orders, ensure buy price is below current price and sell price is above
 Deliverables Checklist
 Python code with all required features
 Support for Market and Limit orders
 BUY and SELL functionality
 CLI interface with input validation
 Comprehensive logging to file
 Error handling throughout
 Bonus: Stop-Limit orders
 Clean, documented, reusable code
 README with setup instructions
 Testing Checklist
Before submitting, test:

 Bot initializes with your API credentials
 Market buy order executes successfully
 Market sell order executes successfully
 Limit buy order is placed (pending)
 Limit sell order is placed (pending)
 Stop-limit order is placed
 Current price retrieval works
 Open orders are displayed
 Order status check works
 Order cancellation works
 Account balance displays correctly
 Log file is created with all activities
 Error handling works (try invalid symbol)

   Learning Outcomes
This project demonstrates:

API integration with financial services
Object-oriented programming in Python
Error handling and logging best practices
User input validation and CLI design
Working with REST APIs
Understanding trading order types
Production-ready code structure
