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
- [For loops (opg. 20-23)](#for-loops)
- [For loops med array (opg. 24-26)](#for-loops-med-array)
- [For-each loops (opg. 27-29)](#for-each-loops)

---

# Betingelser

## Simple betingelser

### Opgave 1: Shopping discount
**Scenario:** En butik giver 20% discount hvis totalPrice > 1000 kr.

**Opgave:**
Beregn final price efter discount.

<details>
<summary>Hjælp</summary>

 1. Start med at erklære to variable til `finalPrice` og `totalPrice`.
 2. Lav et if-else statement, hvor du tjekker om totalPrice opfylder betingelsen for discount
 3. Beregn 20% af `totalPrice` (`totalPrice * 0.2`), træk værdien fra totalPrice, tildel resultatet af hele regnestykket til `finalPrice`
 ELLER beregn 80% (`totalPrice * 0.8`) af `totalPrice` og tildel resultatet til `finalPrice` 
 4. Giv besked om at discounten er udløst.
 5. Print den endelige pris
</details>



<details>
<summary>Se svar</summary>

```java
double totalPrice = 1200.0;
double finalPrice;

if (totalPrice > 1000) {
    finalPrice = totalPrice * 0.8;  // 20% discount
    System.out.println("Discount applied!");
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
**Scenario:** Afhængig af hvad tid på dagen det er, skal der printes en passende besked.
Hvis klokken er mellem 5-11 er det formiddag, eftermiddag (12-17), aften (18-21), nat (22-4).

**Opgave:**
Klokken er 14.

<details>
<summary>Forventet output</summary>
Good afternoon!
</details>


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
<summary>Forventet output</summary>

`=== STUDENT REPORT ===`  
`Score: 88`  
`Grade: B`  
`Status: PASS`  
`Comment: Good`   

</details>
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
Beregn shipping cost (0 hvis free, ellers 50 kr).

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
En biograf tjekker om gæster må se en film. Filmen har en aldersgrænse.
Gæsten må se filmen hvis de er gamle nok, ELLER hvis de er mindst 13 og har forældretilladelse.

**Opgave:**
Skriv kode der tjekker om gæsten må se filmen.
Test med ageLimit = 15, guestAge = 14, hasParentalConsent = true.

<details>
<summary>Forventet output</summary>
Can watch movie
</details>

<details>
<summary>Se svar</summary>

```java
int ageLimit = 15;
int guestAge = 14;
boolean hasParentalConsent = true;

if (guestAge >= ageLimit || (guestAge >= 13 && hasParentalConsent)) {
System.out.println("Can watch movie");
} else {
System.out.println("Cannot watch movie");
}
```
</details>



---

### Opgave 7: Restaurant seating
**Scenario:**
En restaurant tjekker om en gruppe kan få bord. De skal have plads nok, og enten have reservation eller kort ventetid. Restauranten må heller ikke være fyldt.

**Opgave:**
Skriv kode der tjekker om gruppen kan få bord.
Test med partySize = 4, availableSeats = 6, hasReservation = false, waitTime = 20, restaurantFull = false.

<details>
<summary>Forventet output</summary>

`Table available`  
`Estimated wait: 20 minutes`
</details>

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
Et forsikringsselskab beregner præmie baseret på risiko. Højere præmie gives hvis kunden er ung (under 25) eller ældre (over 70), har haft mere end 2 ulykker, eller bor i en risikozone.

**Opgave:**
Skriv kode der beregner præmien. Basispræmie er 5000 kr, tillæg for høj risiko er 2000 kr.
Test med age = 22, hasAccidents = false, accidents = 0, riskZone = false.

<details>
<summary>Forventet output</summary>

`Higher risk category`  
`Annual premium: 7000 kr`

</details>

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
Et system har tre adgangsniveauer. Fuld adgang gives til aktive admins eller superbrugere. Begrænset adgang gives til aktive brugere der ikke er suspenderet, eller gæster med gyldig tid. Alle andre får adgang nægtet.

**Opgave:**
Skriv kode der bestemmer adgangsniveau.
Test med isAdmin = true, accountActive = true, isSuperUser = false.

<details>
<summary>Forventet output</summary>

`=== ACCESS CONTROL ===`  
`Admin: true`  
`Active: true`  
`Result: FULL ACCESS`

</details>

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

---Claude is AI and can make mistakes. Please double-check responses.

# Switch-case

### Opgave 10: Restaurant menu pricing
**Scenario:**
En restaurant har følgende menu:

| Item | Pris |
|------|------|
| burger | 89 kr |
| pizza | 95 kr |
| salad | 65 kr |
| pasta | 79 kr |
| steak | 145 kr |

**Opgave:**
Brug switch til at finde prisen og beregn total for en bestilling.
Test med item = "pizza", quantity = 2.

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
Et fragtfirma beregner pris baseret på zone og vægt:

| Zone | Pris |
|------|------|
| Local | 50 kr |
| Regional | 100 kr |
| National | 150 kr |
| International | 300 kr |

Tillæg: 20 kr per kg over 5 kg.

**Opgave:**
Brug switch til at finde zonepris og beregn total fragtomkostning.
Test med zone = "National", weight = 7 kg.

<details>
<summary>Forventet output</summary>

`Zone: National`  
`Weight: 7.0 kg`  
`Base cost: 150.0 kr`  
`Extra weight cost: 40.0 kr`  
`Total: 190.0 kr`

</details>

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

### Opgave 12: ATM-transaktion

Skriv et program der simulerer en simpel pengeautomat. Programmet skal håndtere fire forskellige operationer: "withdraw", "deposit", "balance" og "transfer".

**Brug følgende startværdier:**
- `balance` = 5000 kr
- `amount` = 1000 kr
- `operation` = "withdraw"

Programmet skal bruge en `switch` til at vælge den rigtige handling baseret på `operation`, og printe resultatet samt den nye saldo (hvis relevant).
Test dit program så der skrives korrekt output for hver operation.

**Tip:** Ved "withdraw" og "transfer" skal du tjekke om der er penge nok på kontoen.
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

### Opgave 13: Billetbestillingssystem

Skriv et program der beregner den samlede pris for en billetbestilling til et arrangement.

**Billetpriser:**
- "movie" = 100 kr
- "concert" = 250 kr
- "sports" = 200 kr
- "theater" = 150 kr

**Rabat:** Studerende får 20% rabat på "concert" og "theater".

**Brug følgende værdier:**
- `eventType` = "concert"
- `quantity` = 2
- `isStudent` = true

Brug en `switch` til at finde billetprisen baseret på `eventType`, anvend eventuelt studierabat, og udregn den samlede pris for alle billetter. Test ved at printe en oversigt over bestillingen inklusive eventtype, basispris, rabat (hvis relevant), pris per billet, antal billetter og samlet pris.
Sørg for at det virker med eventType som "movie", "concert", "sports", og "theater".

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

### Opgave 14: Bestillingssystem

Skriv et program der beregner prisen for en bestilling i en café.

**Produkter og priser:**
- "coffee" = 25 kr
- "tea" = 20 kr
- "sandwich" = 45 kr
- "cake" = 35 kr

**Størrelser (kun for drikkevarer):**
- "small" = normal pris (1.0x)
- "medium" = 1.2x pris
- "large" = 1.5x pris

**Brug følgende værdier:**
- `item` = "coffee"
- `size` = "large"
- `quantity` = 2

Brug en `switch` til at finde produktets basispris. 
Hvis produktet er en drikkevare, skal du bruge en anden `switch` (eller nested switch) til at justere prisen efter størrelse. 
Beregn den samlede pris og print resultatet.

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
Du låner 5000 kr. Du betaler 200 kr om måneden. Hvor mange måneder, før du har betalt lånet tilbage?

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

### Opgave 17: Temperaturomregningstabel
Skriv et program der printer en tabel over temperaturomregninger fra Celsius til Fahrenheit.

**Krav:**
- Print omregninger fra 0°C til 100°C
- Gå op i spring af 10 grader (0, 10, 20, ... 100)
- Brug formlen: F = C × 9/5 + 32

**pro tip:** Husk at bruge `9.0` og `5.0` i formlen for at få et decimaltal som resultat.

<details>
<summary>Hjælp: Trin-for-trin guide</summary>

1. Opret en variabel til at holde styr på den nuværende Celsius-værdi (start ved 0)
2. Brug en `while`-løkke der kører så længe Celsius er ≤ 100
3. Inde i løkken: beregn Fahrenheit ud fra den nuværende Celsius-værdi
4. Print begge værdier på en linje
5. Øg Celsius med 10 inden næste gennemløb
6. Afslut løkken når Celsius når 100
7. Print tabellen i et pænt format med overskrifter

</details>


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

### Opgave 18: Renters rente

Du sætter 10.000 kr ind på en opsparingskonto med 5% årlig rente. Hvert år vokser beløbet med 5% af det nuværende beløb (ikke kun af de oprindelige 10.000 kr).

**Opgave:**
Skriv et program der finder ud af hvor mange år der går, før du har mindst 20.000 kr.

**Eksempel på hvordan beløbet vokser:**
- År 0: 10.000 kr
- År 1: 10.500 kr (10.000 × 1.05)
- År 2: 11.025 kr (10.500 × 1.05)
- osv.

<details>
<summary>Hjælp: Trin-for-trin guide</summary>

1. Start med at erklære to variable: `principal` (start ved 10000.0) og `years` (start ved 0)
2. Opret en `while`-løkke der kører så længe `principal` er mindre end 20000.0
3. Inde i løkken: opdater `principal` ved at gange med 1.05 for at tilføje 5% rente
4. Øg `years` med 1 for hvert gennemløb
5. Efter løkken: print hvor mange år det tog at nå målet
6. 
</details>

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

### Opgave 19: Password-forsøg

Skriv et program hvor brugeren skal gætte et password. Brugeren har maksimalt 3 forsøg.

**Krav:**
- Det korrekte password er "secret123"
- Brugeren indtaster sit gæt via `Scanner`
- Programmet skal give besked om gættet var rigtigt eller forkert
- Efter 3 forkerte forsøg skal programmet udskrive "Account locked"


<details>
<summary>Hjælp: Trin-for-trin guide</summary>

1. Opret en `Scanner` til at læse brugerens input
2. Opret variabler for det korrekte password, antal forsøg (start: 0), og om login lykkedes (start: false)
3. Brug en `while`-løkke der kører så længe forsøg < 3 og login ikke er lykkedes
4. Inde i løkken: bed brugeren om at indtaste password, og læs input med Scanner
5. Tjek om input matcher det korrekte password
6. Hvis ja: sæt login til true og print "Access granted!"
7. Hvis nej: print "Wrong password" og tæl forsøg op
8. Efter løkken: hvis login stadig er false, print "Account locked"
</details>

**Hint:** Husk at bruge `.equals()` når du sammenligner Strings.

<details>
<summary>Se svar</summary>

```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);
String correctPassword = "secret123";
int maxAttempts = 3;
int attempts = 0;
boolean success = false;

while (attempts < maxAttempts && !success) {
System.out.print("Indtast password: ");
String input = scanner.nextLine();
attempts++;

    if (input.equals(correctPassword)) {
        success = true;
        System.out.println("Access granted!");
    } else {
        System.out.println("Wrong password");
        System.out.println("Forsøg brugt: " + attempts + "/" + maxAttempts);
    }
}

if (!success) {
System.out.println("Account locked");
}
```

</details>

## For loops

### Opgave 20: Savings calculator
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

### Opgave 21: Multiplication tables 1-10
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

### Opgave 22: FizzBuzz
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

### Opgave 23: Prime numbers
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

### Opgave 24: Grade statistics
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

### Opgave 25: Temperature analysis
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

### Opgave 26: Sales analysis
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


# For-each loops

### Opgave 27: Shopping cart total
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

### Opgave 28: Student names
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

### Opgave 29: Product inventory
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