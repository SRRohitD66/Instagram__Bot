from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.by import By
import os
import wget
import webbrowser
import datetime
import instaloader
import numpy as np
import time
import tkinter as tk
from tkinter import ttk
from PIL import Image, ImageTk
from functools import partial
from tkinter import messagebox

def insta_login(u, p):
    driver.get('https://www.instagram.com/')
    username = WebDriverWait(driver, 10).until(EC.element_to_be_clickable((By.CSS_SELECTOR, "input[name= 'username']")))
    password = WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, "input[name= 'password']")))
    username.clear()
    password.clear()
    username.send_keys(u)
    password.send_keys(p)

    log_in = WebDriverWait(driver, 10).until(EC.element_to_be_clickable(
        (By.CSS_SELECTOR, "button[type='submit']"))).click()
    not_now = WebDriverWait(driver, 10).until(EC.element_to_be_clickable((By.XPATH, "//button[contains(text(), 'Not Now')]"))).click()
    not_now2 = WebDriverWait(driver, 10).until(EC.element_to_be_clickable((By.XPATH, "//button[contains(text(), 'Not Now')]"))).click()
    driver.find_element_by_xpath("/html/body/div[1]/section/main/section/div[3]/div[1]/div/div/div[2]/div[1]/div/div/a").click()
    time.sleep(2)
    driver.find_element_by_xpath("/html/body/div[1]/section/main/div/header/section/ul/li[2]/a").click()
    time.sleep(5)
    driver.get("https://www.instagram.com/" + u +"/")


def insta_follower(x,y):
    bot = instaloader.Instaloader()
    profile = instaloader.Profile.from_username(bot.context, x)
    root1=tk.Tk()
    root1.geometry("800x600")
    profile_username=ttk.Label(root1,text=profile.username,font=('Arial',25),padding=100,compound='bottom').pack(side='top',fill='x')
    profile_1=ttk.Label(root1,text='Followers',font=('Arial',20),padding=100).pack(side='left',fill='x')
    profile_2=ttk.Label(root1,text='Followings',font=('Arial',20),padding=100).pack(side='right',fill='x')
    profile_follower=ttk.Label(root1,text=profile.followers).pack(side='left')
   
    profile_following=ttk.Label(root1,text=profile.followees).pack(side='right')
    
    bot.login(user=x, passwd=y)
    followersi = [follower.username for follower in profile.get_followers()]
    def burn():
        root1.destroy()
    def unfollow():
        followersf = [follower.username for follower in profile.get_followers()]
        unfollow = np.setdiff1d(followersi, followersf)
        messagebox.showinfo("Unfollowed", unfollow)
    unfollowed=ttk.Button(root1,text='Unfollowed Recently',command=unfollow).pack()
    quit1=ttk.Button(root1,text='Like',command=like).pack()
    quit2=ttk.Button(root1,text='Quit',command=burn).pack()
    root1.mainloop()
       

    

def like():
    hashtag = "marketing"
    driver.get("https://www.instagram.com/explore/tags/" + hashtag + "/")
    time.sleep(5)
    for i in range(1, 2):
        driver.execute_script("window.scrollTo(0,document.body.scrollHeight);")
        time.sleep(3)
    
    hrefs = driver.find_elements_by_tag_name('a')
    images_links = []
    for item in hrefs:
        href = item.get_attribute('href')
        if "/p/" not in href:
            continue

        images_links.append(href)
    
    count = 0
    for images_link in images_links:
        count = count+1
        if(count == 2):
            time.sleep(2)
            driver.get("https://www.instagram.com/" + userinput +"/")
            break
        driver.get(images_link)
        driver.execute_script("window.scrollTo(0,document.body.scrollHeight);")
        try:
            time.sleep(2)
            driver.find_element_by_xpath(
                "/html/body/div[1]/section/main/div/div[1]/article/div[3]/section[1]/span[1]/button/div/span/svg").click()
            time.sleep()
            driver.find_element_by_xpath(
                "/html/body/div[1]/section/nav/div[2]/div/div/div[3]/div/div[5]/div[2]/div[2]/div[2]/a[1]/div").click()
            count=count+1
            time.sleep(5)
        except Exception:
            time.sleep(2)

def validateLogin():
    userinput=user_name.get()
    passinput= password.get()
    root.destroy()

    insta_login(userinput, passinput)
    insta_follower(userinput, passinput)
    
    
    return



root=tk.Tk()
root.geometry("800x600")
image=Image.open(r"C:\Users\koche\Downloads\Logo.png").resize((54,54)) #ENTER THE CORRECT PATH FROM YOUR COMPUTER
photo=ImageTk.PhotoImage(image)
label=ttk.Label(root,image=photo,text='SMT-Analyser',font=('Arial',25),padding=100,compound='bottom')
label.pack(side='top')

password=tk.StringVar()
usernameEntry = ttk.Entry(root, textvariable=password).pack(side='right')
usernameLabel = ttk.Label(root, text="Password").pack(side='right')
user_name=tk.StringVar()
usernameEntry = ttk.Entry(root, textvariable=user_name).pack(side='right')
usernameLabel = ttk.Label(root, text="User Name").pack(side='right')

#login button
loginButton = ttk.Button(root, text="Login", command=validateLogin).pack(side='bottom',expand=True)
driver=webdriver.Chrome(executable_path='C://Users/koche/Downloads/chromedriver_win32/chromedriver.exe') #ENTER CORRECT PATH FROM YOUR COMPUTER




