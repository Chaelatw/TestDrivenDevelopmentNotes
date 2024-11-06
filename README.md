# TestDrivenDevelopmentNotes

What is Test-Driven Development?
-
Cost of Developing Software

There are many phases to creating and delivering software, 
starting with analysis and design of what needs to be built, 
through:
- development and testing
- integrating with other systems
- features 
- maintaining the software and features once they're released

Maintenance Challenges:

- Code Enthropy
  - Brittle over time
  - Increased rigidness
- Isolated Ownership
  - Coder-owned silos
  - Lack of team empowerment
- Infrequent Validation
  - Regression prone
  - High Risk of code changes


Legacy Code

- "source code inherited from someone else"
- "source code inherited from an older version of the software"
- "code without tests"


Test:
"A procedure intended to establish the quality, performance, or reliability of something
especially before it is taken into widespread use."

- Satisfied requirements
- Responds correctly to all input
- Acceptable performance

Test-Driven Development

" A software development process that relies on the
repetition of a very short development cycle: requirements
are turned into very specific test cases, then the software is
improved to pass the new tests, only. ” - Wikipedia
 
- "Red - Green - Refactor"

- Red
  - Write test that fails
- Green
  - Make test pass
- Refactor
  - Refactor/cleanup code


Why Practice TDD?
-
Business Benefits:

- Requirements Verification
- Regression Catching
- Lower Maintenance Costs


Developer Benefits

- Designer first
- provides a way to catch regressions where previously working 
functionality stops working with a newer release.
- regressions end up causing test failures, catching the 
problems as early as possible
- Keeps focused on customer's needs


Testing Application
-
Different Types of Testing

Units of Computation

- Classes
- Functions
- Dependencies

Test-Driven Development != Unit Testing

Balanced Testing

- Satisfaction : Acceptance Tests
  - Behavioral : Build : Integration Tests
    - Quick : Inner Circle : Unit Tests


Black Box Testing

| Component | Test           |
|-----------|----------------|
| X         | Less Brittle + |
|           | Standing up -  |

White Box Testing

| Component | Test           |
|-----------|----------------|
|           | Powerful +     |
|           | More Brittle - |

Many other types of Testing

- Penetration Testing 
- Boundary Testing
- Fuzz Testing
- Smoke Testing
- Stress Testing
- A/B Testing


Testing Frameworks and Tools
-

xUnit Frameworks

SUnit(Smalltalk)

JUnit(Java)

NUnit   RUnit   CppUnit  EUnit  PerlUnit  PHPUnit   xUnit.net

Mocha   AVA   py.test   minitest    FsTest


User Interface Frameworks

- Selenium                  Visual Studio Coded UI Test (Microsoft)
- Watir                     Test Studio (Telerik)
- cypress.io                Silk Test (Micro Focus) 


Testing Concepts
-

Test Concepts

| Before |
|--------|
| Before |  
| Test   |          
| After  |
| Before |
| Test   |
| After  |
| After  |

Test
- Before Test
- After Test

Test Suite
- Before Suite
- After Suite


Verification Concepts

Assert

        Assert.IsTrue(someBoolean);
        Assert.IsFalse(someBoolean);

        Assert.IsNull(someValue);
        Assert.AreEqual(3, someValue);
        Asser.Contains(obj, someCollection);
        Assert.StartsWith("foo", someString);

Test Execution

| Before |
|--------|
| Before |  
| Test   |          
| After  |
| Before |
| Test   |
| After  |
| After  |

Test Runner
- Synchronous (One at a time)
- Asynchronous (in parallel)

| User Item Suite       |
|-----------------------|
| Add Item to Cart      |
| Remove Item from Cart |
| Change Item Quantity  |

        myCart.Add(someItem);
        Assert(myCart.Items.Length == 1);

        myCart.Remove(someItem);
        Assert(myCart.Items.Length == 0);


Common Techniques for Testing Code
-

Dependencies Injection

What Is Dependency Injection?
In software engineering, dependency injection is a technique whereby
one object supplies the dependencies of another object.

Wikipedia - https://en.wikipedia.org/wiki/Dependency_injection

- A dependency is an object that can be used.
- An injection is the passing of a dependency to a dependent object that
  would use it


Dependency Injection Mechanisms

- Constructor (or Method) Injection 
  - Providing dependencies through a class constructor or method. 
- Property/Setter Injection 
  - Using a property or setter method to inject a dependency.


Constructor Injection

        class Greeter {
            nameService: NameService;
        
        constructor(nameService) {
            this.nameService = nameService;
        }

        sayHello(): string {
            return 'Hello, ${this.nameService.getName()}';
        }
    }

Test

        class BadNameService {
            getName(): string {
                throw new Error('Could not get name');
            }
        }


        var service = new BadNameService();
        var greeter = new Greeter(service);
        expect(() => greeter.sayHello()).toThrow();



High Order Functions

        function getName() {
            return "Jason";
        }
        function greet() {
            return `Hello, ${getName()}`;
        }
        greet();
        //=> Hello, Jason


        function greet(getName) {
            return `Hello, ${getName()}`;
        }
        greet(() => {
            return "Jason";
        });
        //=> Hello, Jason

Trade-offs of Dependency Injection

Self-contained Code
- Easier to Understand
- Harder to Test

Dependency-injected Code
- Harder to Understand
- Easier to Test


Test Doubles

Test Double is a “generic term for any kind of
pretend object used in place of a real object
for testing purposes.”
Martin Fowler


Types of Test Doubles

Test Doubles

- Stubs: provide canned answers to calls made during the test
- Mocks: pre-programmed with expectations which form a specification to be verified
- Fakes
- Spies

Brittle code:

- Change only code
- Change only tests
- Change code and tests

Treat Test Code like Production Code

- Write readable and maintainable test code
- Address both positive and negative test cases
- Separate common set-up and teardown logic


Looking out for Test driven Development Gotchas
-

Testing Anti-Patterns

Anti-Pattern: Dependencies between Tests

- Test Ordering
  - Order of tests should not matter
- Cascading Failures
  - Cascading failures can be difficult to track down
- Execution
  - Tests should work regardless of serial vs. parallel execution


Focus on the “what”, not the “how”

Testing the “how” leads to brittle code when refactoring


Limitations of TDD

- Possible holes in tests
- TDD is not sufficient by itself
  - Deployment Verification
  - Network Changes
  - Integration Testing

Test-driven Development shines within an Agile Process

Do I need to write tests first?
Not always

- Avoid over-engineering
- Momentum
- Confidence



Is Test driven Development All I need?
-

Latency

150-300 milliseconds is acceptable

Core Web Vitals

“Core Web Vitals includes metrics, as well as target thresholds for each metric, which
help developers qualitatively understand whether the experience of their site is ‘good’,
‘needs improvement’, or is ‘poor’”

- LPC: Largest Contentful Paint (Loading)
- FID: First Input Delay (Interactivity)
- CLS: Cumulative Layout Shift (Visual Stability)

- Synthetic Monitoring
  - Simulated Load --> System --> Monitoring
- Chaos Engineering
  - Resource exhaustion
  - Long latencies
  - Machine failure
  - Bugs
  - Bottlenecks
  - Design Flaws

Is my Software Secure?

- Simulated attacks
- Software vulnerability


Compliance

- Privacy by design
- Data breach notification
- Right to be forgotten

- General
- Data 
- Protection
- Regulation









