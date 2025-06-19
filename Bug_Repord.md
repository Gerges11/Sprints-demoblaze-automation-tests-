🐞 Bug Report - Demoblaze Automation Testing

Bug #1: "Add to Cart" Button Not Responsive After Alert

Description: After dismissing the alert, clicking "Add to Cart" again has no effect.

Steps to Reproduce:

Visit https://www.demoblaze.com/

Click on any product

Click "Add to cart"

Manually dismiss the alert

Try clicking "Add to cart" again

Expected: Product should be added again or confirmation should appear

Actual: Nothing happens

Severity: Medium

Bug #2: Broken Product Images

Description: Some product images on the homepage fail to load (404 error)

Steps to Reproduce:

Open https://www.demoblaze.com/

Expected: All product images should load

Actual: Some images show broken icon

Severity: Low

Bug #3: Search Button Clickable with Empty Input

Description: Clicking search with no input triggers a reload or unnecessary request

Steps to Reproduce:

Leave the search bar empty

Click search button

Expected: No action should be triggered or display a validation message

Actual: Page reloads

Severity: Low

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
