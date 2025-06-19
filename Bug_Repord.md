# 🐞 Bug Report – Magento Automation Project

## 🧪 Test Case: TC_COC_01

### ✅ Description:
Checkout should reject invalid personal information (name, company, address, etc.)

### 📋 Precondition:
- Product ("Joust Duffle Bag") is already added to cart
- User navigates to the checkout page

### 🔍 Test Steps:
1. Enter email: `gmn@yahoo.com`
2. Fill all fields (name, address, company, city, etc.) with invalid values like `1`
3. Click "Next", then "Place Order"

### 🧾 Expected Result:
System should **prevent checkout** and display error messages asking the user to re-enter valid information.

### ❌ Actual Result:
System **accepted the invalid data** and proceeded with the order.

### 🛠 Status: `❌ FAIL`

---

## ✅ Passed Tests

### TC_SI_01: Invalid Search Term

- Input: `"fish"`
- Result: System displayed "Your search returned no results."
- ✅ Pass

### TC_ATC_01: Add to Cart with Correct Quantity

- Input: `"bag"` → Add 10 items
- Result: Quantity and total price calculated correctly.
- ✅ Pass


🔐 Security Testing

Test 1: XSS Injection

@Test
public void testXSSInjectionInSearch() {
    HomePage homePage = new HomePage(driver);
    homePage.search("<script>alert('XSS')</script>");

    // Assuming a method to verify that no alert is triggered
    Assert.assertFalse(homePage.isScriptExecuted(), "Potential XSS vulnerability detected!");
}

Test 2: SQL Injection

@Test
public void testSQLInjectionInSearch() {
    HomePage homePage = new HomePage(driver);
    homePage.search("1' OR '1'='1");

    Assert.assertTrue(homePage.isNoSearchResultDisplayed(), "Potential SQL Injection vulnerability!");
}

✅ Additional Methods to Add in HomePage.java

public boolean isScriptExecuted() {
    try {
        driver.switchTo().alert();
        return true;
    } catch (NoAlertPresentException e) {
        return false;
    }
}
