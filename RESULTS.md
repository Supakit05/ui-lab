# UI Testing Lab Results

**Selected Parts:** Part 3 – Robot Framework และ Part 4 – Cypress

## Part 0: Getting Ready

### Step 0.1: Chrome Version
- Google Chrome: 156.0.8078.80
- OS: Windows 11 (64-bit)

### Step 0.2: ChromeDriver
- ChromeDriver: 156.0.8078.80
- Path: `C:\drivers\chromedriver-win64\chromedriver.exe`
- Result: PASS

### Step 0.3: Environment Variable
- `CHROMEDRIVER`: `C:\drivers\chromedriver-win64\chromedriver.exe`
- Result: PASS

### Step 0.4: Locators

| Element | Locator |
|---|---|
| Text input | `#my-text-id` |
| Pizza, Please! | `button[name='pizza-please']` |
| Excluded tools | `select` |
| Must be vegetarian | `#default-checkbox` |
| Custom Pizza Name | `input#pizza-name` |

**Result:** PASS – ทดสอบ Locators ทั้งหมดแล้ว สามารถค้นหา Elements ได้ถูกต้อง

### Step 0.5: Test Case QP-01

- Test Case ID: QP-01
- Title: A custom pizza reaches the admin list
- Pizza Name: Lab Pizza 20261106-190240

| Step | Actual Result | Status |
|---|---|---|
| 1 | เปิดหน้า QuickPizza และแสดง Heading ถูกต้อง | PASS |
| 2 | กด Advanced แล้วแสดงช่องกรอกข้อมูลเพิ่มเติม | PASS |
| 3 | กำหนด Calories 600, Excluded tools เป็น Knife, เลือก Vegetarian และตั้งชื่อพิซซ่า | PASS |
| 4 | ระบบสร้างพิซซ่าที่ใช้ Pizza cutter และมี 425 Calories per slice | PASS |
| 5 | กด Love it! แล้วแสดง `Please log in first.` | PASS |
| 6 | Login Admin สำเร็จ และแสดง Latest pizza recommendations | PASS |
| 7 | พบชื่อพิซซ่าใน Admin list และ Tool ตรงกับหน้า Recommendation | PASS |

**Overall Result: PASS (7/7 Steps)**

## Part 3: Robot Framework

### Robot Framework Version
- Version: ไม่ได้บันทึกไว้

### Step 3.2: Wrong Title Test
- Error Message: ไม่ได้บันทึกไว้

### Step 3.8: Evidence from Two Full Runs

- Tool: Robot Framework
- Test Case: QP-01 A Custom Pizza Reaches The Admin List
- Browser: Headless Chrome

**Run 1**
- Result: PASS
- Tests: 1 passed, 0 failed
- Elapsed Time: 9.515 seconds
- Pizza Name: ไม่ได้บันทึกไว้
- Evidence: `robot/results/run1/`

**Run 2**
- Result: PASS
- Tests: 1 passed, 0 failed
- Elapsed Time: ไม่ได้บันทึกไว้
- Pizza Name: ไม่ได้บันทึกไว้
- Evidence: `robot/results/run2/`

### Conclusion
Robot Framework ทดสอบ QP-01 ผ่านทั้ง 2 รอบ โดยตรวจสอบการกรอกข้อมูล การสร้างพิซซ่าตามเงื่อนไข การแจ้งเตือนให้ Login และการแสดงพิซซ่าใน Admin list พร้อมบันทึก Reports, Logs และ Screenshots เป็นหลักฐาน

## Part 4: Cypress

### Step 4.1: Versions
- Node.js: v24.11.0
- npm: ไม่ได้บันทึกไว้
- Cypress: 16.2.1
- Browser: Google Chrome 156 (Headless)

### Step 4.3: Wrong Title Test
- Error Message: ไม่ได้บันทึกไว้

### Step 4.6: Pizza Scenario and API Verification
- Result: PASS
- Tests: 1 passed, 0 failed
- Duration: 10 seconds
- Screenshots: 6
- API: `POST /api/pizza`
- Response Status: 200 OK

ระบบสร้างพิซซ่าตามเงื่อนไขที่กำหนด โดยตรวจสอบชื่อพิซซ่า Tool และ Calories ว่าไม่เกิน 600

### Step 4.7: Admin Login
- Result: PASS
- Tests: 1 passed, 0 failed
- Duration: 11 seconds

ใช้ Custom Command `cy.adminLogin('admin', 'admin')` สำหรับ Login Admin และตรวจสอบว่าพิซซ่าที่สร้างปรากฏใน Admin list โดยมี Tool ตรงกับหน้า Recommendation

### Step 4.8: Evidence from Two Full Runs

- Browser: Google Chrome 156 (Headless)
- Command: `npx cypress run --browser chrome`

**Run 1**
- Result: PASS
- Tests: 2 passed, 0 failed
- Total Duration: 15 seconds
- Pizza Scenario: PASS
- Web Form: PASS
- Pizza Name: ไม่ได้บันทึกไว้
- Screenshots: 6
- Videos: 2

**Run 2**
- Result: PASS
- Tests: 2 passed, 0 failed
- Total Duration: 14 seconds
- Pizza Scenario: PASS
- Web Form: PASS
- Pizza Name: ไม่ได้บันทึกไว้
- Screenshots: 6
- Videos: 2

**Evidence:**
- `cypress/cypress/screenshots/`
- `cypress/cypress/videos/`

### Step 4.9: Second Browser (Optional)
- Result: Not performed

### Conclusion
Cypress ทดสอบผ่านทั้ง 2 รอบ โดย Pizza Scenario และ Web Form ผ่านทั้งหมด พร้อมเก็บ Screenshots และ Videos เป็นหลักฐานการทดสอบ

## Part B: Reflection

### 1. Why locate Max Calories per Slice through its label instead of its id?

เพราะช่อง Max Calories per Slice ไม่มี ID เฉพาะที่เหมาะสำหรับใช้ค้นหา จึงใช้ Label เพื่อค้นหาช่อง Input ที่เกี่ยวข้อง หากเพิ่ม ID เช่น `max-calories` จะสามารถใช้ `#max-calories` ได้โดยตรง ทำให้ Locator สั้นและดูแลรักษาง่ายขึ้น

### 2. What kind of test oracle is used in Step 7?

เป็น **Consistency-based Test Oracle** เพราะนำค่า Tool จากหน้า Recommendation มาเปรียบเทียบกับ Admin list ว่าตรงกันหรือไม่ ช่วยตรวจจับกรณีที่ระบบแสดง Tool อย่างหนึ่ง แต่บันทึกข้อมูลเป็นอีกอย่างหนึ่ง

### 3. How could QP-01 verify that the pizza is vegetarian?

ควรเพิ่มการตรวจสอบ Ingredients ของพิซซ่าที่ระบบสร้าง ว่าไม่มีเนื้อสัตว์หรือส่วนผสมที่ไม่ใช่ Vegetarian เพราะการตรวจสอบแค่ Checkbox ยังยืนยันไม่ได้ว่าพิซซ่าที่ได้เป็น Vegetarian จริง

### 4. Compare Robot Framework and Cypress.

Robot Framework ใช้ Keywords ทำให้โค้ดอ่านง่ายและมี Reports ที่ละเอียด ส่วน Cypress เขียนด้วย JavaScript มี Automatic Retry และสามารถตรวจสอบ API ได้สะดวกผ่าน `cy.intercept()` ทั้งสองเครื่องมือทดสอบผ่าน แต่ Cypress มี Screenshots และ Videos ช่วยให้ตรวจสอบการทำงานย้อนหลังได้ง่าย

### 5. Which tool would you choose for Project 2?

เลือก **Cypress** เพราะมี Automatic Retry ช่วยจัดการกับ Elements ที่โหลดช้า และสามารถทดสอบ UI พร้อมตรวจสอบ API ได้ในเครื่องมือเดียว นอกจากนี้ยังมี Screenshots และ Videos สำหรับใช้ตรวจสอบข้อผิดพลาด

### 6. Part 3: How does the Resource File help when a locator changes?

หาก Locator ของช่อง Calories เปลี่ยน สามารถแก้ไขที่ `robot/resources/quickpizza.resource` ได้โดยไม่ต้องแก้ทุก Test Case เพราะ Resource File ใช้เก็บ Keywords และรายละเอียดการค้นหา Elements ทำให้แก้ไขและดูแลโค้ดได้ง่ายขึ้น

### 7. Part 4: Why must QP-01 remain a single Cypress test?

เพราะ Cypress แยก Browser State ระหว่าง Tests หากแยก Step 6–7 เป็นอีก Test อาจทำให้ Cookie ที่เชื่อมกับ Server เดิมหายไป ส่งผลให้ Admin list ไม่พบพิซซ่าที่สร้างไว้ จึงควรทำทั้ง 7 Steps ภายใน Test เดียวกันเพื่อรักษา Session ให้ต่อเนื่อง