# TestingWebApp
Installation:
1.	Chrome browser
2.	IntelliJ IDEA
3.	Java 8
4.	Selenium 3.141.59
5.	Junit 5
6.	Maven 3.0

Folder Structure: 

Under test package we have main package. In our main package – 4 different packages: pages, runners, step_defenitions and utilities. Pages package has the page object classes, runners package has our runner classes this is where we trigger our framework, step_definitions has implementation of our code for running the driver, and utilities package is used for general utility classes.
Also under test package, there is a resources file, and under it we have our features directory for our feature files.
Finally, we have a configuration.properties file right under our root file.

Feature files:

In feature file we write our test scenario using Gherkin language.

Step Definitions: 

Step Definitions is the package where we write our java code to implement selenium logic. We have to implement all scenarios from our feature files otherwise it will give an error. 

Hooks class:

Hooks class takes place under step_definitions package. In hooks class we store some cucumber annotations like @Before @BeforeStep and @After @AfterStep annotations for providing these conditions. @Before and @After runs before and after each scenario . @BeforeStep and @AfterStep runs before and after each step in our feature files.In this layout, the most important part in this class is @After annotation since with the cod implemented there, the framework takes a screenshot and attach it to scenario whenever our test cases fail.

Pages:

The framework implements page object model to locate elements, and implement some useful methods about elements. Page object model is a design pattern that helps to organize located web elements and avoid code repetition. It uses PageFactory.initElements() method to initialize web elements with the driver. Base Page class is used to avoid initializing elements in each page class, and locate common elements that exist all pages of an application in one place. 

Runners:

We trigger framework using runners class. We can run different testing suits using tags, which we store in feature file under resources.
To run our scenarios we need cucumber-junit dependency in our pom.xml. We need to add @RunWith(Cucumber.class) annotation. Then we can add our configurations inside @CucumberOptions tag. In this framework, we have html, json, and rerun for our plugin configuration. Html is provided to create built-in html report, json is used for maven cucumber reporting to generate a detailed report, rerun plugin is used to save failed test cases in a txt file so later we can run these tests separately. Path of the step definitions is provided through glue keyword. Path of the feature files is provided by features keyword. We can check if our step definitions implemented all the scenarios from feature files using dryRun keyword, if it is true, it only makes a check, does not run the actual cod. Finally, tags are used to choose which test suites to run.

Driver:

The framework implements singleton design pattern to create and call the driver. Singleton allows framework to only have one instance for one session.
For parallel execution we use ThreadLocal together with singleton design pattern. Normally, singleton allows creation of only one instance, but with ThreadLocal, it is allowed to create one instance for each thread we are running.

Configuration Properties:

Configuration properties is a file where we store some important information that can change the flow of the whole framework. Such as browser type, environment, username and password. It also helps us to avoid hard-coding, to change these values are easier as we only have to change them in one place. 

Configuration Reader:

Is a utility class that we use to read the data from configuration.propeties file. It has a private Properties object we load all the data from configuration.properties file, and we can get this data using public getProperty method.

Dependencies:
1.	Selenium
2.	WebDriver Manager
3.	Cucumber Java
4.	Cucumber Junit
5.	Java Faker

Plug-Ins:
1.	Maven Compiler Plugin
2.	Maven Surefire Plugin
3.	Maven Cucumber Reporting
