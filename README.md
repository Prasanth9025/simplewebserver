# Developing a Simple Webserver
## AIM:
To develop a simple webserver to display three programming language

## DESIGN STEPS:
### Step 1: 
HTML content creation
### Step 2:
Design of webserver workflow
### Step 3:
Implementation using Python code
### Step 4:
Serving the HTML pages.
### Step 5:
Testing the webserver

## PROGRAM:
Home Page html Code:
```
<!DOCTYPE html>
<html>
    <head>
        <Title>Calculate Area of Rectangle</Title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <style>
        body{background-color: rgba(0, 255, 76, 0.521)
        }
        .edge
        { 
        width: 1080px;
        margin-left:auto; 
        margin-right:auto; 
        padding-top:200px; 
        padding-left:75px; 
        } 
        .box
        { 
        display:block; 
        border:rgb(255, 208, 0)
        width:500px; 
        min-height:300px; 
        font-size:20px;
        background-color:rgba(90, 29, 102, 0.8); 
        } 
        .formelt{
        color: rgb(22, 19, 19); 
        text-align:center; 
        margin-top:5px; 
        margin-bottom:5px; 
        } 
        h1 
        {
        color: black; 
        text-align:center; 
        padding-top:20px; 
        }
        </style>
    </head>
    <body>
        <div class="edge">
            <div class="box">
                <h1>Area of Rectangle</h1>
                <form method="POST">
                {% csrf_token%}
                <div class="formelt">
                    Length: <input type="text" name="length" value="{{1}}"></input>(in m)<br/>
                </div>
                <div class="formelt">
                    Breadth: <input type="text" name="breadth" value="{{1}}"></input>(in m)<br/>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"></input><br/>
                </div>
                <div class="formelt">
                    Area: <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
                </div>
                </form>
            </div>

        </div>
    <h4 style="text-align: center;">Copyright @ 2023, Developed by Prasanth</h4>
    </body>
</html>
```
Views.py Code:
```
from django.shortcuts import render
from django.contrib.auth.decorators import permission_required

# Create your views here.

def serverside(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area= int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=', area)
    return render(request,"html/serverside.html",context)
```
## OUTPUT:
![Screenshot_20230126_045012](https://user-images.githubusercontent.com/118343686/214825646-6a4bedaa-bf41-4f3d-a087-f1dfe12d57d1.png)
## RESULT:
Thus the webserver is developed to display the Calculate the rectangular
