# UI Testing Lab Results

## Part 0: Getting Ready

### Step 0.1: Chrome Version
Google Chrome: 156.0.8078.80
OS: Windows 11 (64-bit)

### Step 0.2: ChromeDriver
ChromeDriver: 156.0.8078.80
Path: C:\drivers\chromedriver-win64\chromedriver.exe
Result: Pass

### Step 0.3: Environment Variable
CHROMEDRIVER: C:\drivers\chromedriver-win64\chromedriver.exe
Result: Pass

### Step 0.4: Locators
- Text input: #my-text-id
- Pizza, Please!: button[name='pizza-please']
- Excluded tools: select
- Must be vegetarian: #default-checkbox
- Custom Pizza Name: input#pizza-name

All locators were tested successfully.

### Step 0.5: Test Case QP-01

Test Case ID: QP-01

Title: A custom pizza reaches the admin list

Pizza Name: Lab Pizza 20261106-190240

| Step | Actual Result | Status |
|------|---------------|--------|
| 1 | QuickPizza home page displayed the expected heading | Pass |
| 2 | Advanced fields appeared | Pass |
| 3 | Entered 600 calories, Knife, vegetarian and pizza name | Pass |
| 4 | Pizza generated with Pizza cutter and 425 calories per slice | Pass |
| 5 | Please log in first. displayed | Pass |
| 6 | Admin login successful; Latest pizza recommendations displayed | Pass |
| 7 | Pizza name found in admin list with Pizza cutter | Pass |

Overall Result: PASS (7/7)

## Step 3.8: Evidence from Two Full Runs

**Tool:** Robot Framework  
**Test Case:** QP-01 A Custom Pizza Reaches The Admin List  
**Browser:** Headless Chrome

### Run 1
- Result: PASS
- Tests: 1 passed, 0 failed
- Elapsed Time: 9.515 seconds
- Pizza Name: [Copy from Run 1 log]
- Evidence: `robot/results/run1/`

### Run 2
- Result: PASS
- Tests: 1 passed, 0 failed
- Elapsed Time: [Copy from Run 2 report]
- Pizza Name: [Copy from Run 2 log]
- Evidence: `robot/results/run2/`

### Conclusion
Both full runs of QP-01 passed successfully using Headless Chrome. The automated test verified the advanced fields, pizza restrictions, login requirement, and the pizza entry in the admin list.