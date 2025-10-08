# Ex.05 Design a Website for Server Side Processing
## Date:08.10.2025

## AIM:
 To design a website to calculate the Body Mass Index (BMI) in the server side. 


## FORMULA:
BMI= W/H<sup>2</sup>
<br> BMI --> Body Mass Index
<br> W --> Weight
<br> H --> Height

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
math.html

<html>
<head>
    <!DOCTYPE html>
<html>
<head>
<style>
    body {
        font-family: Arial, sans-serif;
        background-color: #3e423e;
        text-align: center;
        margin: 0;
        padding: 20px;
    }

    .edge {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 90vh;
    }

    .box {
        width: 42%;
        background-color: #00ffb3;
        border: 5px solid #0c8bd4;
        border-radius: 20px;
        padding: 30px;
        box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.3);
    }

    h1 {
        color: #2c3e50;
        margin-bottom: 20px;
    }

    .formelt {
        margin: 10px 0;
    }

    input {
        padding: 8px;
        margin: 8px 0;
        border: 1px solid #ff006f;
        border-radius: 5px;
    }

    input[type="submit"] {
        background-color: #ff0000;
        color: white;
        border: none;
        padding: 10px 20px;
        margin-top: 10px;
        cursor: pointer;
        border-radius: 5px;
        font-size: 16px;
    }

    input[type="submit"]:hover {
        background-color: #27ae60;
    }
</style>
</head>
<body>
    <div class="edge">
        <div class="box">
            <h1>BMI Calculator</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Weight: <input type="text" name="weight" value="{{w}}">(in kg)<br/>
                </div>
                <div class="formelt">
                    Height: <input type="text" name="height" value="{{h}}">(in m)<br/>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"><br/>
                </div>
                <div class="formelt">
                    BMI: <input type="text" name="bmi" value="{{bmi}}"><br/>
                </div>
            </form>
        </div>
    </div>
</body>
</html>

urls.py
from django.contrib import admin 
from django.urls import path 
from myapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('calculate_bmi/',views.calculate_bmi,name="areaofrectangle"),
    path('',views.calculate_bmi,name="bmi_calculater")
]

views.py
from django.shortcuts import render
def calculate_bmi(request): 
    context={} 
    context['bmi'] = "0" 
    context['w'] = "0" 
    context['h'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        w = request.POST.get('weight','0')
        h = request.POST.get('height','0')
        print('request=',request) 
        print('Weight=',w)
        print('Height=',h) 
        bmi = round(int(w) / ((int(h)/100) ** 2), 2)
        context['bmi'] = bmi
        context['w'] = w
        context['h'] = h 
        print('BMI=',bmi) 
    return render(request,'myapp/math.html',context)


```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot (22).png>)

## HOMEPAGE:
![alt text](<Screenshot (23).png>)

## RESULT:
The program for performing server side processing is completed successfully.
