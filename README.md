# test_Case_automation

## Selenium Practice Websites

1. **[Automation Exercise](https://automationexercise.com/)**  
   Shopping, Login, Products, Cart & Checkout

2. **[QA Practice Hub](https://qapracticehub.com/)**  
   Alerts, Mouse Actions, Double Click, Shopping & Dynamic Elements

3. **[The Internet – Herokuapp](https://the-internet.herokuapp.com/)**  
   Alerts, Drag & Drop, Dynamic Loading & Selenium Exercises

## Automation Code:
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

driver = webdriver.Edge()
wait = WebDriverWait(driver, 10)


print("TC01 - Open Shopping Website")

driver.get("https://automationexercise.com/")

print("TC01 PASS - Shopping website opened")

time.sleep(2)


print("TC02 - Alert Accept")

driver.get("https://the-internet.herokuapp.com/javascript_alerts")

# Click JS Alert
wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//button[text()='Click for JS Alert']")
    )
).click()

# Wait for alert
alert = wait.until(
    EC.alert_is_present()
)

print("Alert message:", alert.text)

# Accept alert
alert.accept()

print("TC02 PASS - Alert accepted")

time.sleep(1)


print("TC03 - Confirm Alert Dismiss")

# Click JS Confirm
wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//button[text()='Click for JS Confirm']")
    )
).click()

# Wait for alert
alert = wait.until(
    EC.alert_is_present()
)

print("Confirm message:", alert.text)

# Click Cancel
alert.dismiss()

print("TC03 PASS - Alert dismissed")

time.sleep(1)

print("TC04 - Prompt Alert")

# Click JS Prompt
wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//button[text()='Click for JS Prompt']")
    )
).click()

# Wait for prompt
alert = wait.until(
    EC.alert_is_present()
)

print("Prompt message:", alert.text)

# Enter text
alert.send_keys("Saranya")

# Accept
alert.accept()

print("TC04 PASS - Text entered in prompt")

time.sleep(1)


print("TC05 - Mouse Hover")

driver.get("https://qapracticehub.com/")

# Find Hover button
hover_element = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//button[normalize-space()='Hover Over Me']")
    )
)

# Move mouse over element
ActionChains(driver).move_to_element(
    hover_element
).perform()

print("TC05 PASS - Mouse hover performed")

time.sleep(2)


print("TC06 - Double Click")

# Find Double Click button
double_click_element = wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//button[normalize-space()='Double Click Me']")
    )
)

# Double click
ActionChains(driver).double_click(
    double_click_element
).perform()

print("TC06 PASS - Double click performed")

time.sleep(2)



print("TC07 - Drag and Drop")

driver.get(
    "https://the-internet.herokuapp.com/drag_and_drop"
)

# Source
source = wait.until(
    EC.visibility_of_element_located(
        (By.ID, "column-a")
    )
)

# Target
target = wait.until(
    EC.visibility_of_element_located(
        (By.ID, "column-b")
    )
)

# Drag and drop
ActionChains(driver).drag_and_drop(
    source,
    target
).perform()

print("TC07 PASS - Drag and drop performed")

time.sleep(2)


print("TC08 - Explicit Wait")

driver.get(
    "https://the-internet.herokuapp.com/dynamic_loading/1"
)

# Click Start
start_button = wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//button[text()='Start']")
    )
)

start_button.click()

# Wait for dynamic element
result = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//div[@id='finish']/h4")
    )
)

print("Dynamic result:", result.text)

print("TC08 PASS - Explicit wait completed")

time.sleep(1)


print("TC09 - Shopping Checkout")

driver.get(
    "https://automationexercise.com/"
)

# Go to Products
products = wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//a[contains(@href,'/products')]")
    )
)

products.click()

# Add first product to cart
add_cart = wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "(//a[contains(@class,'add-to-cart')])[1]")
    )
)

add_cart.click()

time.sleep(2)

# Click View Cart
view_cart = wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//u[text()='View Cart']")
    )
)

view_cart.click()

time.sleep(2)

# Click Proceed To Checkout
checkout = wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//a[contains(text(),'Proceed To Checkout')]")
    )
)

checkout.click()

print("TC09 PASS - Checkout button clicked")

time.sleep(2)

print("TC10 - Alert Wait")

driver.get(
    "https://the-internet.herokuapp.com/javascript_alerts"
)

# Click JS Alert
alert_button = wait.until(
    EC.element_to_be_clickable(
        (By.XPATH, "//button[text()='Click for JS Alert']")
    )
)

alert_button.click()

# Wait until alert appears
alert = wait.until(
    EC.alert_is_present()
)

print("Alert message:", alert.text)

# Accept alert
alert.accept()

print("TC10 PASS - Alert handled successfully")

print("\n======================================")
print("ALL TEST CASES COMPLETED SUCCESSFULLY")
print("======================================")

time.sleep(3)

driver.quit()

```
