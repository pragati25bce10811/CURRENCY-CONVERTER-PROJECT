                                 CURRENCY CONVERTER
                                           
OVERVIEW:
The core idea behind this project was to build a reliable tool that follows the
"Unix philosophy" - do one thing and do it well.

I build this using a static data approach. Instead of fetching data from an API(which
requires keys, limits and internet) , I hardcoded the exchange rates into a Python
Dictionary. This makes the program incredibly fast(O(1) lookup time) and completely
offline-capable.

The logic is split into two parts:
1. The Interface(main): Handles talking to the user,stripping whitespace from inputs,
   and catching errors so the program doesn't crash if you type a word instead of a
   number.
2. The Brain(convert_currency): Pure logic that takes the input,looks up the math,and
   returns the result.   

FEATURES:
Here is what the tool can currently do:
1. Instant Conversions: Supports 9 major currencies (INR,USD,GBP,EUR,JPY,CHF,CAD,AUD
   and KWD).
2. Smart Input Handling:
    1. Case Insensitive: Type usd, USD or uSd- it knows what you mean.
    2. Space Tolerance:  If you accidentally hit space before typing the currency(e.g., inr),
       the tool cleans it up automatically.
3. Crash Protection:
     1. If you enter text (like "fifty") instead of a number , it catches error and asks
        nicely rather than crashing with a Python traceback.
     2. It prevents negative numbers (because negative money doesn't exist in this context).     
4. Identity Checks: If you try to convert USD to USD it just gives you back the original
   amount without wasting a calculation.   
   

TECHNOLOGY ABD TOOL USED :
I wanted to keep the dependencies as minimal as possible to make this easy to run on any machine.
Language: Python 3 (Tested on 3.8+)
Libraries: Standard Python Library only (sys internally, basic I/O). No heavy external packages
like pandas or requests were used.
Data Structure: Hash Map (Dictionary) for rate storage to ensure efficiency.
Editor: Developed using VS Code.
Streamlit: To deploy the code.

STEPS TO INSTALL AND RUN THE PROJECT:
Since I didn't use any external packages (like pip install requests), running this is super simple. You just need Python installed.

Step 1: Get the code
You can download the .py file directly or clone the repository if you are using Git:
git clone [https://github.com/your-username/currency-converter.git](https://github.com/your-username/currency-converter.git) 
cd currency-converter

Step 2: Check your Python version
Make sure you have Python installed. In your terminal/command prompt, type:
python --version
# OR/
python3 --version

Step 3: Run the application
Execute the script using the following command:
python currency_converter.py
# If you are using Mac/Linux and 'Python' doesn't work, try:
python3 currency_converter.py
Once running, the terminal will ask you for the "From" currency. Just follow the prompts!

Instructions for Testing
I’ve put a lot of effort into making sure the inputs are validated. If you want to test the tool yourself to see how robust it is, here are a few scenarios to try:

1. The "Happy Path" (Standard Use)
Try a standard conversion to make sure the math works.
Input: USD -> INR -> 10
Expected: It should show approximately 897.00 INR.

2. The "Messy User" Test (Typos and Case)
Try typing messy inputs to see if the cleaning logic works.
Input:  inr  (with spaces) -> usd (lowercase) -> 100
Expected: The program should accept these without error and perform the conversion.

3. The "Invalid Data" Test (Crash Prevention)
Try to break the math logic.
Input: USD -> EUR -> twenty (Text instead of number)
Expected: The program should print Error: invalid amount so please enter a number. and exit cleanly. It should not show a scary code error.

4. The "Negative Money" Test
Input: USD -> EUR -> -50
Expected: It should warn you that the amount must be a positive number.

5. The "Unknown Currency" Test
Try a currency that isn't on the list.
Input: BTC (Bitcoin) -> USD
Expected: It should tell you Error: Unsupported or invalid input currency "BTC".

es the expected result using the hardcoded rates.

         
