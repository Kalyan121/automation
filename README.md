# automation
 Developed an automation testing framework using Selenium WebDriver, Java, TestNG, and Maven with Page Object Model. Automated registration, login, dashboard validation, and CSV upload. Implemented data-driven testing and Extent Reports for detailed execution results.
# Calley Teams Full Setup - Automation Testing Project
## Project Overview
This is a comprehensive automation testing project for Calley Teams Account Setup using Selenium
WebDriver, TestNG, and Java. The project follows the Page Object Model (POM) design pattern and
implements a data-driven approach.
## Project Structure
```
CalleyTeamsFullSetup/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── calley/
│   │               
├── base/
│   │               
│   │               
│   │               
│   │               
│   │               
│   │               
│   │               
│   │               
│   │                   
│   │                   
│   │                   
│   └── BasePage.java
├── pages/
│   ├── RegistrationPage.java
│   ├── LoginPage.java
│   ├── AgentPage.java
│   ├── CSVUploadPage.java
│   └── DashboardPage.java
└── utils/
├── ConfigReader.java
├── TestDataReader.java
└── ExtentReportManager.java
│   └── test/
│       ├── java/
│       │   └── com/
│       │       └── calley/
│       │           ├── base/
│       │           │   └── BaseTest.java
│       │           └── tests/
│       │               ├── RegistrationTest.java
│       │               ├── LoginTest.java
│       │               ├── AgentTest.java
│       │               ├── CSVUploadTest.java
│       │               └── FullSetupTest.java
│       └── resources/
│           
├── config.properties
│           
│               
└── testdata/
├── data.properties
│               
└── SampleFile.csv
├── test-output/
├── pom.xml
├── testng.xml
└── README.md
```
## Technologies Used- **Java 11** - Programming Language- **Selenium WebDriver 4.15.0** - Browser Automation- **TestNG 7.8.0** - Testing Framework- **Maven** - Build and Dependency Management- **WebDriverManager 5.6.2** - Automatic Driver Management- **ExtentReports 5.1.1** - Test Reporting- **Page Object Model (POM)** - Design Pattern
## Prerequisites
1. Java JDK 11 or higher installed
2. Maven installed
3. Google Chrome browser installed (or Firefox/Edge)
4. IDE (IntelliJ IDEA, Eclipse, or VS Code with Java extensions)
## Setup Instructions
### 1. Clone or Download the Project
```bash
# If using Git
git clone <repository-url>
cd CalleyTeamsFullSetup
# Or download and extract the ZIP file
```
### 2. Import Project into IDE- **IntelliJ IDEA**: File →
 Open →
 Select the project folder- **Eclipse**: File →
 Import →
 Existing Maven Projects →
 Select the project folder
### 3. Install Dependencies
```bash
mvn clean install
```
### 4. Configure Test Data
Update the following files with your test data:
**src/test/resources/testdata/data.properties**
```properties
f
irstName=YourFirstName
lastName=YourLastName
email=your.email@test.com
password=YourPassword@123
# ... other fields
```
**src/test/resources/config.properties**
```properties
browser=chrome
registrationUrl=https://app.getcalley.com/registration.aspx
loginUrl=https://app.getcalley.com/Login.aspx
```
## Running Tests
### Option 1: Run via Maven Command Line
```bash
# Run all tests
mvn clean test
# Run specific test suite
mvn clean test -DsuiteXmlFile=testng.xml
# Run with specific browser
mvn clean test -Dbrowser=chrome
```
### Option 2: Run via TestNG XML
Right-click on `testng.xml` →
 Run As →
 TestNG Suite
### Option 3: Run via IDE- Right-click on individual test class- Select "Run As" →
 "TestNG Test"
### Option 4: Run Specific Tests
```bash
# Run only Full Setup Test
mvn test -Dtest=FullSetupTest
# Run only Registration Tests
mvn test -Dtest=RegistrationTest
# Run only Login Tests
mvn test -Dtest=LoginTest
```
## Test Scenarios
### 1. User Registration Test- **Test Class**: `RegistrationTest.java`- **Objective**: Verify user can register successfully and select Calley Teams plan- **Steps**:
  1. Navigate to registration page
  2. Enter all required details (Name, Email, Phone, Password, Company)
  3. Submit registration form
  4. Select "Calley Teams" plan
  5. Validate successful registration
### 2. User Login Test- **Test Class**: `LoginTest.java`- **Objective**: Verify user can login with valid credentials- **Steps**:
  1. Navigate to login page
  2. Enter email and password
  3. Click login button
  4. Verify successful login and dashboard access
### 3. Add Agent Test- **Test Class**: `AgentTest.java`- **Objective**: Verify user can add new agents- **Steps**:
  1. Login to application
  2. Navigate to agents page
  3. Click "Add Agent" button
  4. Enter agent details (Name, Email, Phone)
  5. Submit form
  6. Validate agent added successfully
### 4. CSV Upload Test- **Test Class**: `CSVUploadTest.java`- **Objective**: Verify user can upload CSV file of contacts
- **Steps**:
  1. Login to application
  2. Navigate to Call List →
 Power Import
  3. Enter list name
  4. Select agents
  5. Upload CSV file
  6. Map fields
  7. Click Import
  8. Validate successful upload
### 5. Complete Setup Test- **Test Class**: `FullSetupTest.java`- **Objective**: End-to-end test covering all steps- **Steps**: Combines all above scenarios in sequence
## Test Reports
### ExtentReports
After test execution, HTML reports are generated in:
```
test-output/Test-Report-<timestamp>.html
```
Open this file in a browser to view detailed test execution reports with:- Test pass/fail status- Step-by-step execution logs- Execution time- System information
### TestNG Reports
Default TestNG reports are available in:
```
test-output/index.html
test-output/emailable-report.html
```
## Configuration Files
### config.properties
Contains application URLs and browser configuration:- `browser`: Browser to use (chrome/firefox/edge)- `registrationUrl`: Registration page URL- `loginUrl`: Login page URL
- `baseUrl`: Application base URL- Wait timeouts
### data.properties
Contains test data:- User registration details- Agent information- Login credentials- List names
### testng.xml
Defines test suite structure:- Test execution order- Test grouping- Browser parameters- Parallel execution settings
## Page Object Model (POM) Structure
### BasePage.java- Common methods for all pages- Wait mechanisms- Element interactions- JavaScript executors
### Page Classes- **RegistrationPage**: Registration form interactions- **LoginPage**: Login functionality- **AgentPage**: Agent management- **CSVUploadPage**: CSV file upload- **DashboardPage**: Dashboard navigation
### BaseTest.java- Test setup and teardown- WebDriver initialization- Browser configuration- Report initialization
## Troubleshooting
### Issue: Tests fail with "Element not found"
**Solution**:- Increase wait times in `config.properties`
- Check if page locators have changed- Verify internet connection
### Issue: Chrome driver not found
**Solution**:- WebDriverManager will automatically download drivers- Ensure internet connection is available- Check firewall settings
### Issue: CSV file not found
**Solution**:- Verify `SampleFile.csv` exists in `src/test/resources/testdata/`- Check file path in test- Ensure file has read permissions
### Issue: Login tests fail
**Solution**:- Update `loginEmail` and `loginPassword` in `data.properties`- Use credentials from a previously registered account- Or run Registration test first to create new account
## Best Practices Implemented
1. **Page Object Model (POM)**: Separation of page objects and tests
2. **Data-Driven Testing**: External test data configuration
3. **Reusable Components**: BasePage and BaseTest classes
4. **Explicit Waits**: Proper synchronization mechanisms
5. **Logging**: Comprehensive extent reports
6. **Error Handling**: Try-catch blocks with meaningful messages
7. **Maintainability**: Clean code structure and comments
8. **Scalability**: Easy to add new pages and tests
## Video Recording Instructions
To create a video demonstration:
1. **Run the test**:
   ```bash
   mvn clean test -Dtest=FullSetupTest
   ```
2. **Use screen recording software**:
   - Windows: Xbox Game Bar (Win + G)
   - Mac: QuickTime Player
   - Linux: SimpleScreenRecorder
   - OBS Studio (All platforms)
3. **Record the entire test execution** showing:
   - Browser opening
   - Registration process
   - Login process
   - Agent addition
   - CSV upload
   - Console output
   - 
Test report
4. **Upload to Google Drive** with public access
## Project Deliverables
1. 
✅
 Complete Maven project with proper structure
2. 
✅
 All test scenarios implemented
3. 
✅
 Page Object Model implementation
4. 
✅
 Data-driven approach with properties files
5. 
✅
 TestNG integration
6. 
✅
 ExtentReports for reporting
7. 
✅
 Sample CSV file
8. 
✅
 Configuration files
9. 
✅
 Comprehensive README documentation
## URLs Reference- **Registration**: https://app.getcalley.com/registration.aspx- **Login**: https://app.getcalley.com/Login.aspx

## License
This project is created for the Automation Testing Internship machine test.--
**Created by**: Kalyan kumar
**Date**: February 2026
**Version**: 1.0
