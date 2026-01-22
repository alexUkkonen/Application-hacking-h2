# Application-hacking-h2

## x)

### Broken Access Controll

Broken access control is the most common vounrability. It can basically be defined as being able to acces and/or modify things you shouldn't be able to, wether this is trough going to a certain link or tampering with cookies.

### Find Hidden Web Directories - Fuzz URLs with ffuf
For your convenience this has been mooved to exercise C

### Access control vulnerabilities and privilege escalation

The main takeaway i had from this was the different types of access control.

- Vertical access controll is a type of accescontrol where certain users have access to certain actions while others dont. Example: only an admin can delete an account.
- Horizontal access controll is when you can't access another users account.
- Context based acces control is one that applies only in certain contexts such as not being able to change what items you bought after payment.

### Report Writing

This was more yapping about how to write a report, emphasizing the importance of writing it simultainiously as one works. A report should also enable a person following along to reproduce all the steps. It should also use clear and structured language.

### What is SQL injection? - Web Security Academy

The video detailed what SQL injection is and how to do it. The concept is rather simple, you write code in a field to get more information than you should have access to. The methods varry but the most common is just writing something along the lines of"' or 1=1 -- "

## A)

First we download the challanges
<img width="538" height="417" alt="image" src="https://github.com/user-attachments/assets/9e6a44ad-d92e-480a-9e65-5b2a0df93aab" />

then we get the python3 alchemy flask.
<img width="1271" height="432" alt="image" src="https://github.com/user-attachments/assets/03d5e602-aab8-4681-af15-efa1ba70eb8c" />

Once we are in the program we can use inspect element to edit the imput type from number to string.

This allows us to search for potential passwords containing the string superman. From this point on wards it is all about making sure you spell the syntax correctly. In reality you would also have to experiment with different table names to ensure you get the correct table name to print. You also need to be specific as the website only shows one pass at a time.
<img width="2787" height="1551" alt="image" src="https://github.com/user-attachments/assets/c8d81c5e-db9f-4ec0-b170-142477855d85" />

## B)

I edited the python code so that it turns the pin from a string in to an int and then back to a string. this makes it crash if it recieves a string. With some error handling we could avoid the crash, but i'm too lazy.
<img width="2765" height="1534" alt="image" src="https://github.com/user-attachments/assets/d31f1816-ce69-4b0d-a8b8-a9812669a744" />



## C)

First we install the directory as instructed.
<img width="1917" height="1365" alt="image" src="https://github.com/user-attachments/assets/3432ee1c-5789-497a-aaab-2ea2bc170359" />

The next step was to install ffuf, but the instructions had incorrectly marked it as fuff, witch lead to some issues for me.
<img width="819" height="519" alt="image" src="https://github.com/user-attachments/assets/656edd03-8267-4394-9e23-ee16291c723b" />

I'm going to skip over me trying to get it the wget way, as i realized half way trough that ffuf was spelled wrong and fixed it.
<img width="822" height="519" alt="image" src="https://github.com/user-attachments/assets/d9457539-a20d-4abd-bc36-696d99b0cb7f" />

After that we downloaded the dile containing all the strings that ffuf is going to search for.
<img width="823" height="521" alt="image" src="https://github.com/user-attachments/assets/330fe5dc-98cc-44a2-87e0-7891d68417d8" />

As we can see from the size tag, the wrong size is likely 132.
<img width="1918" height="1361" alt="image" src="https://github.com/user-attachments/assets/c0816718-52f0-436a-88a8-a7bac77202ba" />

We filter out 132 to get responses that might be correct.
<img width="817" height="525" alt="image" src="https://github.com/user-attachments/assets/310717e5-fd3d-45a6-b689-8eaeac1b63ff" />

As we can see /admin turned out correct.
<img width="536" height="299" alt="image" src="https://github.com/user-attachments/assets/bdd0a115-e1a7-4500-af51-6619645fd412" />


### Part 2

I'm going to skip over the instalation process as we jsut saw it.

We emediately scan with ffuf. as we can see 154 apears to be the wrong size for a responce.
<img width="1923" height="1371" alt="image" src="https://github.com/user-attachments/assets/b3118f09-852f-4995-9398-e044ceca656f" />

We sett the filter to filter out 154 and 6 possible strings apear.
<img width="1918" height="1361" alt="image" src="https://github.com/user-attachments/assets/a8cbd17a-025e-4e3e-a892-828e8f7455c1" />

As you can see we solved both panels.
<img width="762" height="278" alt="image" src="https://github.com/user-attachments/assets/cd05c23c-2f8f-4f01-b711-68bb80494570" />
<img width="1922" height="1369" alt="image" src="https://github.com/user-attachments/assets/e0c20870-2c8f-42f3-b8db-6d4a1dc0864b" />

## D)

First we install the virtual enviorment. i did a small oopsie as i did it in the wrong order, but i soon figured it out.
<img width="1438" height="452" alt="image" src="https://github.com/user-attachments/assets/c007b9fb-f764-41ef-8433-c1b06576176a" />

Next we pip installed the requirements.txt and launched the program. (Make shure you turn of your internet)
<img width="1365" height="365" alt="image" src="https://github.com/user-attachments/assets/8440198f-ffb9-4e3e-b055-6675032c619b" />


<img width="1369" height="406" alt="image" src="https://github.com/user-attachments/assets/e7fbd9b3-ee39-4ff7-9931-166c7853c600" />

<img width="1786" height="385" alt="image" src="https://github.com/user-attachments/assets/a590a241-bcb4-4713-95ec-3ba85f491dee" />

We use ffuf again just like in esercise C to find the availible link. When we try to access it it asks for a password.

I made an account and logged in. This allowed me to access the admin console.
<img width="2781" height="1644" alt="image" src="https://github.com/user-attachments/assets/0506e34b-e473-486f-ab4f-8e90094e9eff" />

## E)

ShowAllView -> DashboardView

I had to find this using grep -ri "admin-console"

This shows all files beneath the directory where it was used.

The fix was to make the admin consol a Dashboad view as it was accidentally set as a lower permission.
<img width="2066" height="678" alt="image" src="https://github.com/user-attachments/assets/69fcdea2-a520-4335-b01f-32511232d3aa" />
