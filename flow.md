I'll go through each round systematically and provide answers for all the questions from **Round 2 (Technical) to Round 4 (HR).**  

---

# **📌 Round 2: (Technical)**  

### 👉 **1. Write Java Program to find the maximum sum subarray (Kadane's Algorithm).**  

```java
public class MaxSumSubarray {
    public static int maxSubArray(int[] nums) {
        int maxSum = nums[0];
        int currentSum = nums[0];

        for (int i = 1; i < nums.length; i++) {
            currentSum = Math.max(nums[i], currentSum + nums[i]);
            maxSum = Math.max(maxSum, currentSum);
        }
        return maxSum;
    }

    public static void main(String[] args) {
        int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println("Maximum sum subarray: " + maxSubArray(arr));
    }
}
```

---

### 👉 **2. How does `System.out.println()` work?**  
- `System`: A final class in `java.lang` package.  
- `out`: A static PrintStream object inside `System`.  
- `println()`: A method inside `PrintStream` which prints the data to the console.

Internally, `System.out.println()` writes data to the console using `PrintStream`’s native method.

---

### 👉 **3. Write code to achieve multiple Inheritance using Interface.**  

```java
interface A {
    void showA();
}

interface B {
    void showB();
}

class C implements A, B {
    public void showA() {
        System.out.println("Class A method");
    }
    public void showB() {
        System.out.println("Class B method");
    }
}

public class MultipleInheritance {
    public static void main(String[] args) {
        C obj = new C();
        obj.showA();
        obj.showB();
    }
}
```

---

### 👉 **4. Why is String immutable in Java? StringBuffer use.**  
- **String is immutable** to ensure security, caching, synchronization, and performance optimizations.  
- `StringBuffer` is **mutable** and thread-safe because it is synchronized.  

Example:
```java
String s = "Hello";
s.concat(" World"); // Doesn't change original value
System.out.println(s); // Hello

StringBuffer sb = new StringBuffer("Hello");
sb.append(" World");
System.out.println(sb); // Hello World
```

---

### 👉 **5. How would you design test cases for an unclear application requirement?**  
- **Exploratory Testing:** Start testing the application without formal test cases.  
- **Ad-hoc Testing:** Identify possible scenarios based on experience.  
- **Requirement Gathering:** Talk to stakeholders to clarify requirements.  
- **Risk-Based Testing:** Focus on critical application features.  

---

### 👉 **6. Suppose 10 test cases are failing randomly. How will you fix them?**  
- Check if failures are **consistent or intermittent.**  
- Analyze **logs** and error messages.  
- **Check environment stability.**  
- **Use retry mechanism** for flaky tests.  
- **Increase wait time** if needed.  

---

### 👉 **7. Explain Bug Life Cycle.**  
1. **New** → When a bug is reported.  
2. **Assigned** → Assigned to a developer.  
3. **In Progress** → Developer starts fixing it.  
4. **Fixed** → Bug is fixed.  
5. **Pending Retest** → Tester retests the fix.  
6. **Retest Failed/Passed** → If the bug exists, reopens; if fixed, closed.  

---

### 👉 **8. How to wait until the number of opened tabs is equal to 4 in Selenium?**  

```java
WebDriver driver = new ChromeDriver();
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
wait.until(ExpectedConditions.numberOfWindowsToBe(4));
```

---

### 👉 **9. How to wait for file download to finish in Selenium?**  

```java
File file = new File("C:\\Downloads\\myfile.pdf");
while (!file.exists()) {
    Thread.sleep(1000); // Check every second
}
```

---

### 👉 **10. What are DataProviders in TestNG?**  

- `@DataProvider` is used for **parameterized testing**.  

```java
@DataProvider(name = "loginData")
public Object[][] getData() {
    return new Object[][] { {"user1", "pass1"}, {"user2", "pass2"} };
}
```

---

### 👉 **11. Challenges faced in working with frameworks?**  
- **Flaky Tests** due to unstable environments.  
- **Synchronization Issues** in Selenium.  
- **Maintaining Test Data.**  
- **Dynamic Element Handling.**  

---

### 👉 **12. What are Listeners in TestNG?**  
- They **listen to test execution events** and modify behavior accordingly.  
- Example: `ITestListener` for logging failures.

```java
public class TestListener implements ITestListener {
    public void onTestFailure(ITestResult result) {
        System.out.println("Test Failed: " + result.getName());
    }
}
```

---

### 👉 **13. Write XPath using sibling concept.**  
```xpath
//div[@id='parent']/following-sibling::div[1]
```

---

### 👉 **14. Disagreement with developer & how did you handle it?**  
- **Understand their perspective** first.  
- **Provide evidence** of the issue.  
- **Suggest a workaround** if needed.  

---

### 👉 **15. Do you know Factory Design Pattern?**  
- Used for **creating objects** without exposing creation logic.  

```java
interface Shape { void draw(); }

class Circle implements Shape {
    public void draw() { System.out.println("Circle drawn"); }
}

class ShapeFactory {
    public static Shape getShape() { return new Circle(); }
}
```

---

# **📌 Round 3: (Technical Round 2)**  

### 👉 **1. When should testing for a feature stop?**  
- When all test cases pass and coverage is **sufficient**.  

---

### 👉 **2. Handling unclear requirements?**  
- **Ask stakeholders for clarification.**  
- **Exploratory testing** to identify risks.  

---

### 👉 **3. Handling calendars in Selenium?**  
- Use `sendKeys()` or JavaScript Executor:  

```java
WebElement date = driver.findElement(By.id("date"));
date.sendKeys("2025-03-24");
```

---

### 👉 **4. Actions class vs Select class?**  
- **Actions** → Used for mouse and keyboard interactions.  
- **Select** → Used for dropdown handling.  

---

### 👉 **5. Fetch attribute value in Selenium?**  

```java
String value = driver.findElement(By.id("element")).getAttribute("value");
```

---

### 👉 **6. What is Multithreading in Java?**  
- Running multiple tasks in parallel using `Thread` class or `Runnable`.  

---

### 👉 **7. Global vs Environment variables in Postman?**  
- **Global Variables**: Accessible across all collections.  
- **Environment Variables**: Limited to a specific environment.  

---

### 👉 **8. Alternative to GET API taking 1 min?**  
- Use **HEAD** request if you only need headers.  

---

### 👉 **9. TRACE API method?**  
- Used for debugging, returns received request.  

---

### 👉 **10. Ensuring test cases completeness?**  
- Use **Requirement Traceability Matrix (RTM).**  

---

### 👉 **11. Security vulnerability testing?**  
- **SQL Injection, XSS, CSRF, Broken Authentication.**  

---

### 👉 **12. Finding duplicate elements in Java Streams?**  

```java
List<Integer> list = Arrays.asList(1, 2, 3, 1, 2);
Set<Integer> duplicates = list.stream()
    .filter(i -> Collections.frequency(list, i) > 1)
    .collect(Collectors.toSet());
```

---

# **📌 Round 4: (HR)**  
1. **How soon can you join?** → Answer based on your notice period.  
2. **Why did you leave your last job?** → Mention **growth opportunities.**  
3. **Are you willing to relocate?** → Answer honestly.  
4. **Salary discussion** → Negotiate smartly.  

---

Would you like me to expand on any topic? 🚀