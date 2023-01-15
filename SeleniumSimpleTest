import pytest
from selenium import webdriver
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.by import By


def test_browser_init():
    #   r = result
    #   Navigate to main page /r = main page is open
    driver = webdriver.Chrome(ChromeDriverManager().install())

    driver.implicitly_wait(0.5)
    driver.get("https://store.steampowered.com")
    get_title = driver.title
    assert get_title == 'Welcome to Steam'

    #   Click on ABOUT button /r = About page is open
    driver.find_element(By.XPATH, "//a[normalize-space()='ABOUT']").click()
    assert True

    #   Compare number of players online and in game /r = nr of in-g player < nr of online pl.
    online = driver.find_element(By.XPATH, "(//div[@class='online_stat'])[1]").text
    online_players = float(online.replace("ONLINE\n", "").replace(",", ""))
    print(type(online_players))

    inline = driver.find_element(By.XPATH, "(//div[@class='online_stat'])[2]").text
    inline_players = float(inline.replace("PLAYING NOW\n", "").replace(",", ""))
    print(type(inline_players))

    if online_players > inline_players:
        print("Test passed")
    else:
        print("Test failed")

    true = online_players > inline_players
    assert true == True

    #   Click on STORE button /r = Store page is open

    driver.find_element(By.XPATH, "(//a[normalize-space()='STORE'])[1]").click()
    title = driver.title
    assert True

    driver.quit()

