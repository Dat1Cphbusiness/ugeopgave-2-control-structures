# ugeopave 2 controlstrukturere


- [while loops opg.20-26](#while-opgaver)
- [for loops opg.27-33](#loops-opgaver)


Conditions (betingelser) og loops (Løkker)

## Simple betingelser 
### Opgave 1: Shopping discount
**Scenario:** Butik giver 20% discount hvis totalPrice > 1000 kr.

**Opgave:**
Beregn final price efter discount.

<details>
<summary>Se svar</summary>

```java
double totalPrice = 1200.0;
double finalPrice;

if (totalPrice > 1000) {
    finalPrice = totalPrice * 0.8;  // 20% discount
    System.out.println("Discount applied!");
} else {
    finalPrice = totalPrice;
}

System.out.println("Final price: " + finalPrice + " kr");
// Output: Discount applied! Final price: 960.0 kr
```
</details>

---

### Opgave 2: BMI calculator
**Scenario:** BMI = weight / (height * height). BMI >= 25 er overweight.

**Opgave:**
Beregn BMI og print status.

<details>
<summary>Se svar</summary>

```java
double weight = 80.0;  // kg
double height = 1.75;  // meters
double bmi = weight / (height * height);

System.out.println("BMI: " + bmi);

if (bmi >= 25) {
    System.out.println("Overweight");
} else if (bmi >= 18.5) {
    System.out.println("Normal weight");
} else {
    System.out.println("Underweight");
}
```
</details>

---

### Opgave 3: Time of day greeting
**Scenario:** Baseret på time (0-23), print different greeting.

**Opgave:**
Morning (5-11), Afternoon (12-17), Evening (18-21), Night (22-4).

<details>
<summary>Se svar</summary>

```java
int hour = 14;

if (hour >= 5 && hour <= 11) {
    System.out.println("Good morning!");
} else if (hour >= 12 && hour <= 17) {
    System.out.println("Good afternoon!");
} else if (hour >= 18 && hour <= 21) {
    System.out.println("Good evening!");
} else {
    System.out.println("Good night!");
}
// Output: Good afternoon!
```
</details>

---

### Opgave 4: Shipping cost
**Scenario:**
- Free shipping hvis totalPrice > 500
- 50 kr hvis totalPrice > 200
- 100 kr ellers

**Opgave:**
Beregn shipping cost og total.

<details>
<summary>Se svar</summary>

```java
double totalPrice = 350.0;
double shippingCost;

if (totalPrice > 500) {
    shippingCost = 0.0;
} else if (totalPrice > 200) {
    shippingCost = 50.0;
} else {
    shippingCost = 100.0;
}

double finalTotal = totalPrice + shippingCost;

System.out.println("Items: " + totalPrice + " kr");
System.out.println("Shipping: " + shippingCost + " kr");
System.out.println("Total: " + finalTotal + " kr");
```
</details>

---

### Opgave 5: Grade pass/fail with message
**Scenario:**
Print både grade OG om det er pass/fail.

**Opgave:**
Score = 82. Print grade og pass/fail status.

<details>
<summary>Se svar</summary>

```java
int score = 82;
String grade;
String status;

if (score >= 90) {
    grade = "A";
} else if (score >= 80) {
    grade = "B";
} else if (score >= 70) {
    grade = "C";
} else if (score >= 60) {
    grade = "D";
} else {
    grade = "F";
}

if (score >= 60) {
    status = "PASS";
} else {
    status = "FAIL";
}

System.out.println("Grade: " + grade);
System.out.println("Status: " + status);
```
</details>

---

### Opgave 6: Complete student report
**Scenario:**
Lav en komplet student rapport med score, grade, status, og comment.

**Opgave:**
- Score = 88
- Print grade (A/B/C/D/F)
- Print status (PASS/FAIL)
- Print comment baseret på grade: A="Excellent", B="Good", C="Satisfactory", D="Needs improvement", F="Failing"

<details>
<summary>Se svar</summary>

```java
int score = 88;
String grade;
String status;
String comment;

// Determine grade
if (score >= 90) {
    grade = "A";
    comment = "Excellent";
} else if (score >= 80) {
    grade = "B";
    comment = "Good";
} else if (score >= 70) {
    grade = "C";
    comment = "Satisfactory";
} else if (score >= 60) {
    grade = "D";
    comment = "Needs improvement";
} else {
    grade = "F";
    comment = "Failing";
}

// Determine status
if (score >= 60) {
    status = "PASS";
} else {
    status = "FAIL";
}

// Print report
System.out.println("=== STUDENT REPORT ===");
System.out.println("Score: " + score);
System.out.println("Grade: " + grade);
System.out.println("Status: " + status);
System.out.println("Comment: " + comment);
System.out.println("===================");
```
</details>

## Betingelser med OR operatoren (||, eller)

### Opgave 7: Shipping eligibility
**Scenario:**
Free shipping hvis: (totalPrice > 500) OR (isMember AND totalPrice > 200).
Calculate shipping cost (0 hvis free, ellers 50 kr).

Test med totalPrice = 350, isMember = true.

<details>
<summary>Se svar</summary>

```java
double totalPrice = 350.0;
boolean isMember = true;
double shippingCost;

if (totalPrice > 500 || (isMember && totalPrice > 200)) {
    shippingCost = 0.0;
    System.out.println("Free shipping!");
} else {
    shippingCost = 50.0;
}

double finalTotal = totalPrice + shippingCost;
System.out.println("Subtotal: " + totalPrice + " kr");
System.out.println("Shipping: " + shippingCost + " kr");
System.out.println("Total: " + finalTotal + " kr");
```
</details>

---

### Opgave 8: Movie rating system
**Scenario:**
Kan se film hvis: (age >= ratingAge) OR (age >= 13 AND hasParentalConsent).

Test med movieRating = 15, age = 14, hasParentalConsent = true.

<details>
<summary>Se svar</summary>

```java
int movieRating = 15;
int age = 14;
boolean hasParentalConsent = true;

if (age >= movieRating || (age >= 13 && hasParentalConsent)) {
    System.out.println("Can watch movie");
} else {
    System.out.println("Cannot watch movie");
}
// Output: Can watch movie
```
</details>

---

### Opgave 9: Restaurant seating
**Scenario:**
Kan få bord hvis: (partySize <= availableSeats) AND ((hasReservation OR waitTime < 30) AND NOT restaurantFull).

Test med partySize = 4, availableSeats = 6, hasReservation = false, waitTime = 20, restaurantFull = false.

<details>
<summary>Se svar</summary>

```java
int partySize = 4;
int availableSeats = 6;
boolean hasReservation = false;
int waitTime = 20;
boolean restaurantFull = false;

if ((partySize <= availableSeats) && 
    ((hasReservation || waitTime < 30) && !restaurantFull)) {
    System.out.println("Table available");
    System.out.println("Estimated wait: " + waitTime + " minutes");
} else {
    System.out.println("No table available");
}
```
</details>

---

### Opgave 10: Insurance premium calculator
**Scenario:**
Higher premium hvis: (age < 25 OR age > 70) OR (hasAccidents AND accidents > 2) OR riskZone.
Base premium = 5000 kr, add 2000 kr hvis higher premium.

Test med age = 22, hasAccidents = false, accidents = 0, riskZone = false.

<details>
<summary>Se svar</summary>

```java
int age = 22;
boolean hasAccidents = false;
int accidents = 0;
boolean riskZone = false;

int basePremium = 5000;
int premium;

if ((age < 25 || age > 70) || (hasAccidents && accidents > 2) || riskZone) {
    premium = basePremium + 2000;
    System.out.println("Higher risk category");
} else {
    premium = basePremium;
    System.out.println("Standard risk category");
}

System.out.println("Annual premium: " + premium + " kr");
```
</details>

---

### Opgave 11: Complete access control system
**Scenario:**
Build et complete access control system.

Access levels:
- FULL: (isAdmin AND accountActive) OR (isSuperUser)
- LIMITED: (isUser AND accountActive AND NOT suspended) OR (isGuest AND guestTimeValid)
- DENIED: alle andre

Test multiple scenarios og print access level for hver.

<details>
<summary>Se svar</summary>

```java
// Scenario 1: Admin user
boolean isAdmin = true;
boolean accountActive = true;
boolean isSuperUser = false;
boolean isUser = false;
boolean suspended = false;
boolean isGuest = false;
boolean guestTimeValid = false;

String accessLevel;

if ((isAdmin && accountActive) || isSuperUser) {
    accessLevel = "FULL ACCESS";
} else if ((isUser && accountActive && !suspended) || (isGuest && guestTimeValid)) {
    accessLevel = "LIMITED ACCESS";
} else {
    accessLevel = "ACCESS DENIED";
}

System.out.println("=== ACCESS CONTROL ===");
System.out.println("Admin: " + isAdmin);
System.out.println("Active: " + accountActive);
System.out.println("Result: " + accessLevel);
System.out.println("====================");

// Scenario 2: Regular user
isAdmin = false;
isSuperUser = false;
isUser = true;
accountActive = true;
suspended = false;

if ((isAdmin && accountActive) || isSuperUser) {
    accessLevel = "FULL ACCESS";
} else if ((isUser && accountActive && !suspended) || (isGuest && guestTimeValid)) {
    accessLevel = "LIMITED ACCESS";
} else {
    accessLevel = "ACCESS DENIED";
}

System.out.println("
=== ACCESS CONTROL ===");
System.out.println("User: " + isUser);
System.out.println("Active: " + accountActive);
System.out.println("Suspended: " + suspended);
System.out.println("Result: " + accessLevel);
System.out.println("====================");

// Test more scenarios...
```
</details>

# Switch-case

### Opgave 12: Restaurant menu pricing
**Scenario:**
Menu items: "burger"=89kr, "pizza"=95kr, "salad"=65kr, "pasta"=79kr, "steak"=145kr.
Calculate total for quantity. Test med item = "pizza", quantity = 2.

<details>
<summary>Se svar</summary>

```java
String item = "pizza";
int quantity = 2;
double price;

switch (item) {
    case "burger":
        price = 89.0;
        break;
    case "pizza":
        price = 95.0;
        break;
    case "salad":
        price = 65.0;
        break;
    case "pasta":
        price = 79.0;
        break;
    case "steak":
        price = 145.0;
        break;
    default:
        price = 0.0;
        System.out.println("Item not found");
}

double total = price * quantity;

System.out.println("Item: " + item);
System.out.println("Price: " + price + " kr");
System.out.println("Quantity: " + quantity);
System.out.println("Total: " + total + " kr");
```
</details>

---

### Opgave 13: Traffic fine calculator
**Scenario:**
Speed limit = 130 km/h. Fines: 131-140 = 500kr, 141-150 = 1000kr, 151+ = 2000kr + license suspension.
Calculate fine for speed = 145.

<details>
<summary>Se svar</summary>

```java
int speedLimit = 130;
int speed = 145;
int fine;
boolean licenseSuspended = false;

int overSpeed = speed - speedLimit;

// Group overspeed into categories
int category;
if (overSpeed <= 0) {
    category = 0;  // No violation
} else if (overSpeed <= 10) {
    category = 1;  // 1-10 over
} else if (overSpeed <= 20) {
    category = 2;  // 11-20 over
} else {
    category = 3;  // 21+ over
}

switch (category) {
    case 0:
        fine = 0;
        System.out.println("Within speed limit");
        break;
    case 1:
        fine = 500;
        break;
    case 2:
        fine = 1000;
        break;
    case 3:
        fine = 2000;
        licenseSuspended = true;
        break;
    default:
        fine = 0;
}

System.out.println("Speed: " + speed + " km/h");
System.out.println("Limit: " + speedLimit + " km/h");
System.out.println("Fine: " + fine + " kr");
if (licenseSuspended) {
    System.out.println("License suspended!");
}
```
</details>

---

### Opgave 14: Shipping cost calculator
**Scenario:**
Shipping zones: "Local"=50kr, "Regional"=100kr, "National"=150kr, "International"=300kr.
Add 20kr per kg over 5kg. Test med zone = "National", weight = 7kg.

<details>
<summary>Se svar</summary>

```java
String zone = "National";
double weight = 7.0;
double baseCost;
double extraCost = 0.0;

switch (zone) {
    case "Local":
        baseCost = 50.0;
        break;
    case "Regional":
        baseCost = 100.0;
        break;
    case "National":
        baseCost = 150.0;
        break;
    case "International":
        baseCost = 300.0;
        break;
    default:
        baseCost = 0.0;
        System.out.println("Invalid zone");
}

// Calculate extra cost for weight
if (weight > 5.0) {
    double extraKg = weight - 5.0;
    extraCost = extraKg * 20.0;
}

double totalCost = baseCost + extraCost;

System.out.println("Zone: " + zone);
System.out.println("Weight: " + weight + " kg");
System.out.println("Base cost: " + baseCost + " kr");
System.out.println("Extra weight cost: " + extraCost + " kr");
System.out.println("Total: " + totalCost + " kr");
```
</details>

---

### Opgave 15: ATM transaction
**Scenario:**
ATM operations: "withdraw", "deposit", "balance", "transfer".
Balance = 5000kr, amount = 1000kr, operation = "withdraw".

<details>
<summary>Se svar</summary>

```java
double balance = 5000.0;
double amount = 1000.0;
String operation = "withdraw";
boolean success = true;

switch (operation) {
    case "withdraw":
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawn: " + amount + " kr");
        } else {
            System.out.println("Insufficient funds");
            success = false;
        }
        break;
    case "deposit":
        balance += amount;
        System.out.println("Deposited: " + amount + " kr");
        break;
    case "balance":
        System.out.println("Current balance: " + balance + " kr");
        break;
    case "transfer":
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Transferred: " + amount + " kr");
        } else {
            System.out.println("Insufficient funds");
            success = false;
        }
        break;
    default:
        System.out.println("Invalid operation");
        success = false;
}

if (success && !operation.equals("balance")) {
    System.out.println("New balance: " + balance + " kr");
}
```
</details>

---

### Opgave 16: Ticket booking system
**Scenario:**
Event types: "movie"=100kr, "concert"=250kr, "sports"=200kr, "theater"=150kr.
Discounts: students get 20% off concerts and theater.
Calculate total for eventType = "concert", quantity = 2, isStudent = true.

<details>
<summary>Se svar</summary>

```java
String eventType = "concert";
int quantity = 2;
boolean isStudent = true;
double basePrice;
double discount = 0.0;

switch (eventType) {
    case "movie":
        basePrice = 100.0;
        break;
    case "concert":
        basePrice = 250.0;
        if (isStudent) {
            discount = 0.20;
        }
        break;
    case "sports":
        basePrice = 200.0;
        break;
    case "theater":
        basePrice = 150.0;
        if (isStudent) {
            discount = 0.20;
        }
        break;
    default:
        basePrice = 0.0;
        System.out.println("Invalid event type");
}

double pricePerTicket = basePrice * (1 - discount);
double total = pricePerTicket * quantity;

System.out.println("Event: " + eventType);
System.out.println("Base price: " + basePrice + " kr");
if (discount > 0) {
    System.out.println("Student discount: " + (discount * 100) + "%");
}
System.out.println("Price per ticket: " + pricePerTicket + " kr");
System.out.println("Quantity: " + quantity);
System.out.println("Total: " + total + " kr");
```
</details>

---

### Opgave 17: Complete order system
**Scenario:**
Build a simple order system.

Items:
- "coffee" = 25kr (sizes: small=1.0x, medium=1.2x, large=1.5x)
- "tea" = 20kr (sizes: small=1.0x, medium=1.2x, large=1.5x)
- "sandwich" = 45kr (no sizes)
- "cake" = 35kr (no sizes)

Calculate total for: item = "coffee", size = "large", quantity = 2.

<details>
<summary>Se svar</summary>

```java
String item = "coffee";
String size = "large";
int quantity = 2;
double basePrice;
double sizeMultiplier = 1.0;

// Get base price
switch (item) {
    case "coffee":
        basePrice = 25.0;
        break;
    case "tea":
        basePrice = 20.0;
        break;
    case "sandwich":
        basePrice = 45.0;
        break;
    case "cake":
        basePrice = 35.0;
        break;
    default:
        basePrice = 0.0;
        System.out.println("Invalid item");
}

// Get size multiplier (only for drinks)
if (item.equals("coffee") || item.equals("tea")) {
    switch (size) {
        case "small":
            sizeMultiplier = 1.0;
            break;
        case "medium":
            sizeMultiplier = 1.2;
            break;
        case "large":
            sizeMultiplier = 1.5;
            break;
        default:
            System.out.println("Invalid size");
    }
}

double unitPrice = basePrice * sizeMultiplier;
double total = unitPrice * quantity;

System.out.println("=== ORDER ===");
System.out.println("Item: " + item);
if (item.equals("coffee") || item.equals("tea")) {
    System.out.println("Size: " + size);
}
System.out.println("Quantity: " + quantity);
System.out.println("Unit price: " + unitPrice + " kr");
System.out.println("Total: " + total + " kr");
System.out.println("=============");
```
</details>

---

### Opgave 18: Grade calculator with multiple inputs
**Scenario:**
Calculate final grade baseret på 3 assignments.

Grade conversion: 90-100=A, 80-89=B, 70-79=C, 60-69=D, 0-59=F.

Test med assignment1=85, assignment2=92, assignment3=78.

<details>
<summary>Se svar</summary>

```java
int assignment1 = 85;
int assignment2 = 92;
int assignment3 = 78;

double average = (assignment1 + assignment2 + assignment3) / 3.0;
int avgRounded = (int) Math.round(average);

// Convert to grade category for switch
int gradeCategory;
if (avgRounded >= 90) {
    gradeCategory = 5;
} else if (avgRounded >= 80) {
    gradeCategory = 4;
} else if (avgRounded >= 70) {
    gradeCategory = 3;
} else if (avgRounded >= 60) {
    gradeCategory = 2;
} else {
    gradeCategory = 1;
}

String letterGrade;
String comment;

switch (gradeCategory) {
    case 5:
        letterGrade = "A";
        comment = "Excellent work!";
        break;
    case 4:
        letterGrade = "B";
        comment = "Good job!";
        break;
    case 3:
        letterGrade = "C";
        comment = "Satisfactory";
        break;
    case 2:
        letterGrade = "D";
        comment = "Needs improvement";
        break;
    case 1:
        letterGrade = "F";
        comment = "Failing";
        break;
    default:
        letterGrade = "?";
        comment = "Error";
}

System.out.println("=== GRADE REPORT ===");
System.out.println("Assignment 1: " + assignment1);
System.out.println("Assignment 2: " + assignment2);
System.out.println("Assignment 3: " + assignment3);
System.out.println("Average: " + average);
System.out.println("Letter Grade: " + letterGrade);
System.out.println("Comment: " + comment);
System.out.println("===================");
```
</details>

---

### Opgave 19: Multi-level menu system
**Scenario:**
Create a two-level menu system med switch statements.

Main menu: 1=Account, 2=Transactions, 3=Settings, 4=Exit.
For Account (choice=1), submenu: 1=View, 2=Edit, 3=Delete.

Test med mainChoice = 1, subChoice = 2.

<details>
<summary>Se svar</summary>

```java
int mainChoice = 1;
int subChoice = 2;

System.out.println("=== MAIN MENU ===");

switch (mainChoice) {
    case 1:
        System.out.println("Account Menu");
        System.out.println("-------------");
        
        switch (subChoice) {
            case 1:
                System.out.println("Viewing account details...");
                break;
            case 2:
                System.out.println("Editing account...");
                break;
            case 3:
                System.out.println("Deleting account...");
                break;
            default:
                System.out.println("Invalid account option");
        }
        break;
        
    case 2:
        System.out.println("Transactions Menu");
        System.out.println("----------------");
        
        switch (subChoice) {
            case 1:
                System.out.println("View history");
                break;
            case 2:
                System.out.println("New transaction");
                break;
            default:
                System.out.println("Invalid transaction option");
        }
        break;
        
    case 3:
        System.out.println("Settings Menu");
        break;
        
    case 4:
        System.out.println("Exiting...");
        break;
        
    default:
        System.out.println("Invalid main menu choice");
}

System.out.println("================");
// Output: Account Menu, Editing account...
```
</details>

---
---

## While opgaver

### Opgave 20: Savings goal
**Scenario:**
Du sparer 500 kr om måneden. Hvor mange måneder før du har 10,000 kr?

**Opgave:**
Simulate saving med while loop.

<details>
<summary>Se svar</summary>

```java
double savings = 0.0;
double monthlyDeposit = 500.0;
double goal = 10000.0;
int months = 0;

while (savings < goal) {
    savings += monthlyDeposit;
    months++;
    System.out.println("Month " + months + ": " + savings + " kr");
}

System.out.println("Goal reached in " + months + " months");
// Output: Goal reached in 20 months
```
</details>

---

### Opgave 21: Loan repayment
**Scenario:**
Du låner 5000 kr. Du betaler 200 kr om måneden. Hvor lang tid tager det?

**Opgave:**
Simulate loan repayment.

<details>
<summary>Se svar</summary>

```java
double debt = 5000.0;
double monthlyPayment = 200.0;
int months = 0;

while (debt > 0) {
    debt -= monthlyPayment;
    months++;
    
    if (debt < 0) {
        debt = 0;  // Last payment might be smaller
    }
    
    System.out.println("Month " + months + ": " + debt + " kr left");
}

System.out.println("Loan paid off in " + months + " months");
// Output: Loan paid off in 25 months
```
</details>

---

### Opgave 22: Temperature conversion table
**Scenario:**
Print Celsius til Fahrenheit conversion table.

**Opgave:**
Print conversions fra 0°C til 100°C i steps of 10.
Formula: F = C × 9/5 + 32

<details>
<summary>Se svar</summary>

```java
int celsius = 0;

System.out.println("Celsius | Fahrenheit");
System.out.println("--------|------------");

while (celsius <= 100) {
    double fahrenheit = celsius * 9.0 / 5.0 + 32.0;
    System.out.println(celsius + "°C     | " + fahrenheit + "°F");
    celsius += 10;
}
// Output: Conversion table from 0°C to 100°C
```
</details>

---

### Opgave 23: Compound interest
**Scenario:**
Du investerer 10,000 kr med 5% årlig rente. Hvor mange år før du har 20,000 kr?

**Opgave:**
Calculate compound interest med while loop.

<details>
<summary>Se svar</summary>

```java
double principal = 10000.0;
double rate = 0.05;  // 5%
double target = 20000.0;
int years = 0;

while (principal < target) {
    principal = principal * (1 + rate);
    years++;
    System.out.println("Year " + years + ": " + principal + " kr");
}

System.out.println("Target reached in " + years + " years");
// Output: Target reached in approximately 15 years
```
</details>

---

### Opgave 24: Password attempts
**Scenario:**
User har 3 attempts til at gætte password.

**Opgave:**
Simulate password attempts. Correct password = "secret123".
Test passwords: "wrong1", "wrong2", "secret123".

<details>
<summary>Se svar</summary>

```java
String correctPassword = "secret123";
int maxAttempts = 3;
int attempts = 0;
boolean success = false;

// Simulate attempts
String attempt1 = "wrong1";
String attempt2 = "wrong2";
String attempt3 = "secret123";

while (attempts < maxAttempts && !success) {
    attempts++;
    
    String currentAttempt;
    if (attempts == 1) {
        currentAttempt = attempt1;
    } else if (attempts == 2) {
        currentAttempt = attempt2;
    } else {
        currentAttempt = attempt3;
    }
    
    System.out.println("Attempt " + attempts + ": " + currentAttempt);
    
    if (currentAttempt.equals(correctPassword)) {
        success = true;
        System.out.println("Access granted!");
    } else {
        System.out.println("Wrong password");
    }
}

if (!success) {
    System.out.println("Account locked");
}
// Output: Access granted on attempt 3
```
</details>

---

### Opgave 25: Number guessing game
**Scenario:**
Computer "tænker" på et tal mellem 1-100. Du gætter systematisk.

**Opgave:**
Find tallet 73 ved at guess 1, 2, 3, ... indtil correct.

<details>
<summary>Se svar</summary>

```java
int secretNumber = 73;
int guess = 1;
int attempts = 0;

while (guess != secretNumber) {
    attempts++;
    guess++;
}

System.out.println("Found " + secretNumber + " in " + attempts + " attempts");
// Output: Found 73 in 72 attempts
```
</details>

---

### Opgave 26: Complete simulation - Population growth
**Scenario:**
En by har 10,000 indbyggere. Befolkningen vokser 3% om året.

**Opgave:**
Calculate:
1. Hvor mange år før population > 20,000?
2. Hvad er population efter 10 år?
3. Hvor mange år før population > 30,000?

<details>
<summary>Se svar</summary>

```java
double population = 10000.0;
double growthRate = 0.03;  // 3%
int years = 0;

System.out.println("Year " + years + ": " + (int)population + " people");

// Part 1: Years to reach 20,000
while (population <= 20000) {
    population = population * (1 + growthRate);
    years++;
    System.out.println("Year " + years + ": " + (int)population + " people");
}

int yearsTo20k = years;
System.out.println();
System.out.println("Reached 20,000 in " + yearsTo20k + " years");

// Part 2: Population after 10 years from start
population = 10000.0;
years = 0;
while (years < 10) {
    population = population * (1 + growthRate);
    years++;
}
System.out.println("After 10 years: " + (int)population + " people");

// Part 3: Years to reach 30,000
population = 10000.0;
years = 0;
while (population <= 30000) {
    population = population * (1 + growthRate);
    years++;
}
System.out.println("Reached 30,000 in " + years + " years");

System.out.println();
System.out.println("=== SUMMARY ===");
System.out.println("20,000 reached: " + yearsTo20k + " years");
System.out.println("Population at year 10: " + (int)(10000 * Math.pow(1.03, 10)));
```
</details>

---


## Loops opgaver

### Opgave 27: Temperature conversion table
**Scenario:**
Print Celsius til Fahrenheit conversion table.

**Opgave:**
Print conversions fra -10°C til 40°C i steps of 5.
Formula: F = C × 9/5 + 32

<details>
<summary>Se svar</summary>

```java
System.out.println("Celsius | Fahrenheit");
System.out.println("--------|------------");

for (int c = -10; c <= 40; c += 5) {
    double f = c * 9.0 / 5.0 + 32.0;
    System.out.println(c + "°C     | " + f + "°F");
}
```
</details>

---

### Opgave 28: Savings calculator
**Scenario:**
Du sparer 1000 kr om måneden i 12 måneder.

**Opgave:**
Print savings efter hver måned.

<details>
<summary>Se svar</summary>

```java
double monthlySavings = 1000.0;
double total = 0.0;

System.out.println("Month | Total Savings");
System.out.println("------|---------------");

for (int month = 1; month <= 12; month++) {
    total += monthlySavings;
    System.out.println(month + "     | " + total + " kr");
}

System.out.println();
System.out.println("Total after 1 year: " + total + " kr");
```
</details>

---

### Opgave 29: Compound interest table
**Scenario:**
Investering på 10,000 kr med 5% årlig rente.

**Opgave:**
Print værdi efter 1-10 år.

<details>
<summary>Se svar</summary>

```java
double principal = 10000.0;
double rate = 0.05;

System.out.println("Year | Balance");
System.out.println("-----|----------");

for (int year = 1; year <= 10; year++) {
    principal = principal * (1 + rate);
    System.out.println(year + "    | " + (int)principal + " kr");
}
```
</details>

---

### Opgave 30: Multiplication tables 1-10
**Scenario:**
Print gangetabeller for alle tal fra 1 til 10.

**Opgave:**
For hvert tal, print n×1 til n×10.

<details>
<summary>Se svar</summary>

```java
for (int n = 1; n <= 10; n++) {
    System.out.println("=== Table for " + n + " ===");
    for (int i = 1; i <= 10; i++) {
        System.out.println(n + " × " + i + " = " + (n * i));
    }
    System.out.println();
}
```
</details>

---

### Opgave 31: FizzBuzz
**Scenario:**
Classic FizzBuzz problem.

**Opgave:**
Print tal 1-30, men:
- Hvis delelig med 3: print "Fizz"
- Hvis delelig med 5: print "Buzz"
- Hvis delelig med begge: print "FizzBuzz"
- Ellers: print tallet

<details>
<summary>Se svar</summary>

```java
for (int i = 1; i <= 30; i++) {
    if (i % 3 == 0 && i % 5 == 0) {
        System.out.println("FizzBuzz");
    } else if (i % 3 == 0) {
        System.out.println("Fizz");
    } else if (i % 5 == 0) {
        System.out.println("Buzz");
    } else {
        System.out.println(i);
    }
}
```
</details>

---

### Opgave 32: Prime numbers
**Scenario:**
Find om et tal er primtal.

**Opgave:**
Check om 29 er et primtal ved at teste om det er deleligt med noget fra 2 til 28.

<details>
<summary>Se svar</summary>

```java
int number = 29;
boolean isPrime = true;

for (int i = 2; i < number; i++) {
    if (number % i == 0) {
        isPrime = false;
        break;  // No need to check further
    }
}

if (isPrime) {
    System.out.println(number + " is prime");
} else {
    System.out.println(number + " is not prime");
}
// Output: 29 is prime
```
</details>

---

### Opgave 33: Complete statistics calculator
**Scenario:**
Beregn statistik for tallene 1-100.

**Opgave:**
Calculate og print:
1. Sum af alle tal
2. Sum af lige tal
3. Sum af ulige tal
4. Antal tal delelige med 7
5. Product af første 10 tal (10!)
6. Gennemsnit af alle tal

<details>
<summary>Se svar</summary>

```java
// Variables
int totalSum = 0;
int evenSum = 0;
int oddSum = 0;
int divisibleBy7 = 0;
int factorial = 1;
int count = 0;

// Main calculation loop
for (int i = 1; i <= 100; i++) {
    // Total sum
    totalSum += i;
    count++;
    
    // Even/odd sum
    if (i % 2 == 0) {
        evenSum += i;
    } else {
        oddSum += i;
    }
    
    // Divisible by 7
    if (i % 7 == 0) {
        divisibleBy7++;
    }
    
    // Factorial (first 10 only)
    if (i <= 10) {
        factorial *= i;
    }
}

// Calculate average
double average = (double) totalSum / count;

// Print results
System.out.println("=== STATISTICS FOR 1-100 ===");
System.out.println("Total sum: " + totalSum);
System.out.println("Sum of even numbers: " + evenSum);
System.out.println("Sum of odd numbers: " + oddSum);
System.out.println("Count divisible by 7: " + divisibleBy7);
System.out.println("10! = " + factorial);
System.out.println("Average: " + average);
System.out.println("============================");
```
</details>

---