# Ugeopgave 2: Kontrolstrukturer

Der er mange opgaver i dette sæt og det er ikke meningen at du skal lave dem alle.
Du skal i stedet **udvælge mindst 1 opgave fra hvert disse 8 emner:**. 


**Betingelser**
- [Simple if/else (opg. 1-2)](#simple-betingelser)
- [AND-operator (opg. 3-4)](#betingelser-med-and)
- [OR-operator (opg. 5-7)](#betingelser-med-or)
- [Kombinerede operatorer (opg. 8-9)](#kombinerede-operatorer)

**Loops**
- [Switch-case (opg. 10-14)](#switch-case)
- [While loops (opg. 15-19)](#while-loops)
- [For loops (opg. 20-24)](#for-loops)
- [For loops med array (opg. 25-28)](#for-loops-med-array)
- [For-each loops (opg. 29-31)](#for-each-loops)

---

# Betingelser

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

## Betingelser med AND

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

### Opgave 4: Complete student report
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

---

## Betingelser med OR

### Opgave 5: Shipping eligibility
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

### Opgave 6: Movie rating system
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

### Opgave 7: Restaurant seating
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

## Kombinerede operatorer

### Opgave 8: Insurance premium calculator
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

### Opgave 9: Complete access control system
**Scenario:**
Build et complete access control system.

Access levels:
- FULL: (isAdmin AND accountActive) OR (isSuperUser)
- LIMITED: (isUser AND accountActive AND NOT suspended) OR (isGuest AND guestTimeValid)
- DENIED: alle andre

Test med isAdmin = true, accountActive = true, isSuperUser = false.

<details>
<summary>Se svar</summary>

```java
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
```
</details>

---

# Switch-case

### Opgave 10: Restaurant menu pricing
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

### Opgave 11: Shipping cost calculator
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

### Opgave 12: ATM transaction
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

### Opgave 13: Ticket booking system
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

### Opgave 14: Complete order system
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

## While loops

### Opgave 15: Savings goal
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

### Opgave 16: Loan repayment
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

### Opgave 17: Temperature conversion table
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

### Opgave 18: Compound interest
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

### Opgave 19: Password attempts
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

# For loops

### Opgave 20: Temperature conversion table
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

### Opgave 21: Savings calculator
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

### Opgave 22: Multiplication tables 1-10
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

### Opgave 23: FizzBuzz
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

### Opgave 24: Prime numbers
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

# For loops med array

### Opgave 25: Grade statistics
**Scenario:**
En klasse har scores: {85, 92, 78, 88, 95, 73, 90}.

**Opgave:**
Calculate:
- Average
- Højeste karakter
- Laveste karakter
- Antal over 80

<details>
<summary>Se svar</summary>

```java
int[] scores = {85, 92, 78, 88, 95, 73, 90};

// Average
int sum = 0;
for (int i = 0; i < scores.length; i++) {
    sum += scores[i];
}
double average = (double) sum / scores.length;

// Min and max
int min = scores[0];
int max = scores[0];
for (int i = 1; i < scores.length; i++) {
    if (scores[i] < min) min = scores[i];
    if (scores[i] > max) max = scores[i];
}

// Count above 80
int countAbove80 = 0;
for (int i = 0; i < scores.length; i++) {
    if (scores[i] > 80) {
        countAbove80++;
    }
}

System.out.println("=== GRADE STATISTICS ===");
System.out.println("Average: " + average);
System.out.println("Highest: " + max);
System.out.println("Lowest: " + min);
System.out.println("Scores above 80: " + countAbove80);
```
</details>

---

### Opgave 26: Temperature analysis
**Scenario:**
Ugens temperaturer: {18, 22, 20, 25, 19, 21, 23} (°C).

**Opgave:**
Find:
- Gennemsnits temperatur
- Varmeste dag
- Koldeste dag
- Antal dage over 20°C

<details>
<summary>Se svar</summary>

```java
int[] temps = {18, 22, 20, 25, 19, 21, 23};
String[] days = {"Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"};

// Average
int sum = 0;
for (int i = 0; i < temps.length; i++) {
    sum += temps[i];
}
double average = (double) sum / temps.length;

// Find hottest and coldest days
int hottestIndex = 0;
int coldestIndex = 0;
for (int i = 1; i < temps.length; i++) {
    if (temps[i] > temps[hottestIndex]) {
        hottestIndex = i;
    }
    if (temps[i] < temps[coldestIndex]) {
        coldestIndex = i;
    }
}

// Count days above 20
int countAbove20 = 0;
for (int i = 0; i < temps.length; i++) {
    if (temps[i] > 20) {
        countAbove20++;
    }
}

System.out.println("=== TEMPERATURE ANALYSIS ===");
System.out.println("Average: " + average + "°C");
System.out.println("Hottest: " + days[hottestIndex] + " (" + temps[hottestIndex] + "°C)");
System.out.println("Coldest: " + days[coldestIndex] + " (" + temps[coldestIndex] + "°C)");
System.out.println("Days above 20°C: " + countAbove20);
```
</details>

---

### Opgave 27: Sales analysis
**Scenario:**
Månedens daglige salg: {1200, 1500, 900, 2100, 1800, 1300, 2500} (kr).

**Opgave:**
Calculate:
- Total salg
- Gennemsnitligt dagligt salg
- Bedste salgsdag
- Dage med salg over 1500 kr

<details>
<summary>Se svar</summary>

```java
int[] sales = {1200, 1500, 900, 2100, 1800, 1300, 2500};

// Total sales
int total = 0;
for (int i = 0; i < sales.length; i++) {
    total += sales[i];
}

// Average
double average = (double) total / sales.length;

// Best day
int bestDay = 0;
for (int i = 1; i < sales.length; i++) {
    if (sales[i] > sales[bestDay]) {
        bestDay = i;
    }
}

// Count days above 1500
int countAbove1500 = 0;
for (int i = 0; i < sales.length; i++) {
    if (sales[i] > 1500) {
        countAbove1500++;
    }
}

System.out.println("=== SALES ANALYSIS ===");
System.out.println("Total sales: " + total + " kr");
System.out.println("Average daily: " + average + " kr");
System.out.println("Best day: Day " + (bestDay + 1) + " (" + sales[bestDay] + " kr)");
System.out.println("Days above 1500 kr: " + countAbove1500);
```
</details>

---

### Opgave 28: Complete data analysis
**Scenario:**
Analyse af test scores fra to klasser.

**Opgave:**
Class A: {85, 92, 78, 88, 95, 73, 90}
Class B: {80, 85, 90, 75, 88, 92, 87}

For hver klasse, find:
- Average
- Highest og lowest score
- Antal passing (>= 60)
- Antal excellent (>= 90)

Derefter sammenlign klasserne.

<details>
<summary>Se svar</summary>

```java
int[] classA = {85, 92, 78, 88, 95, 73, 90};
int[] classB = {80, 85, 90, 75, 88, 92, 87};

// Analyze Class A
int sumA = 0;
int minA = classA[0];
int maxA = classA[0];
int passingA = 0;
int excellentA = 0;

for (int i = 0; i < classA.length; i++) {
    sumA += classA[i];
    if (classA[i] < minA) minA = classA[i];
    if (classA[i] > maxA) maxA = classA[i];
    if (classA[i] >= 60) passingA++;
    if (classA[i] >= 90) excellentA++;
}
double avgA = (double) sumA / classA.length;

// Analyze Class B
int sumB = 0;
int minB = classB[0];
int maxB = classB[0];
int passingB = 0;
int excellentB = 0;

for (int i = 0; i < classB.length; i++) {
    sumB += classB[i];
    if (classB[i] < minB) minB = classB[i];
    if (classB[i] > maxB) maxB = classB[i];
    if (classB[i] >= 60) passingB++;
    if (classB[i] >= 90) excellentB++;
}
double avgB = (double) sumB / classB.length;

// Print results
System.out.println("=== CLASS A STATISTICS ===");
System.out.println("Average: " + avgA);
System.out.println("Highest: " + maxA);
System.out.println("Lowest: " + minA);
System.out.println("Passing: " + passingA);
System.out.println("Excellent: " + excellentA);
System.out.println();

System.out.println("=== CLASS B STATISTICS ===");
System.out.println("Average: " + avgB);
System.out.println("Highest: " + maxB);
System.out.println("Lowest: " + minB);
System.out.println("Passing: " + passingB);
System.out.println("Excellent: " + excellentB);
System.out.println();

System.out.println("=== COMPARISON ===");
if (avgA > avgB) {
    System.out.println("Class A has higher average");
} else {
    System.out.println("Class B has higher average");
}
System.out.println("Difference: " + Math.abs(avgA - avgB));
```
</details>

---

# For-each loops

### Opgave 29: Shopping cart total
**Scenario:**
Prices i shopping cart: `{299.0, 149.0, 899.0, 49.0}` (kr).

**Opgave:**
Beregn total pris med for-each loop.

<details>
<summary>Se svar</summary>

```java
double[] prices = {299.0, 149.0, 899.0, 49.0};
double total = 0.0;

for (double price : prices) {
    total += price;
}

System.out.println("Total: " + total + " kr");
// Output: Total: 1396.0 kr
```
</details>

---

### Opgave 30: Student names
**Scenario:**
Class roster: `{"Emma", "Liam", "Olivia", "Noah", "Ava"}`.

**Opgave:**
1. Print en velkomst besked for hver student
2. Tæl navne med 4 bogstaver i
3. Find det længste navn

<details>
<summary>Se svar</summary>

```java
String[] students = {"Emma", "Liam", "Olivia", "Noah", "Ava"};

// 1. Welcome messages
System.out.println("=== WELCOME ===");
for (String student : students) {
    System.out.println("Welcome, " + student + "!");
}

// 2. Count 4-letter names
int count4Letters = 0;
for (String student : students) {
    if (student.length() == 4) {
        count4Letters++;
    }
}

// 3. Longest name
String longest = students[0];
for (String student : students) {
    if (student.length() > longest.length()) {
        longest = student;
    }
}

System.out.println("\n=== STATISTICS ===");
System.out.println("4-letter names: " + count4Letters);
System.out.println("Longest name: " + longest);
```
</details>

---

### Opgave 31: Product inventory
**Scenario:**
En skobutik har sko i 7 størrelser. Lad os sige fra str 38 til 44. På den første plads i tabellen kan man se at der er 45 par tilbage i størrelse 38.   

Stock levels: `{45, 12, 67, 8, 34, 5, 89}`.

Hvis der er 10 eller færre par tilbage af en størrelse, skal der genbestilles.  
Reorder threshold: 10.

**Opgave:**
Tæl hvor mange størrelser, der skal genbestilles (stock <= 10).

<details>
<summary>Forventet output</summary>

`Products needing reorder: 2 `
</details>

<details>
<summary>Se svar</summary>

```java
int[] stock = {45, 12, 67, 8, 34, 5, 89};
int reorderThreshold = 10;
int reorderCount = 0;

for (int level : stock) {
    if (level <= reorderThreshold) {
        reorderCount++;
    }
}

System.out.println("Products needing reorder: " + reorderCount);

```
</details>

---