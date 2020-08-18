# Django_pdfintojson
In this repo i convert pdf text into json using tabula library.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
I would like to tell you that I complete the task(data extract
from pdf into JSON) successfully. I did this task in python Django I
will shear the project repository. In this project,
I will scrap the text with tabula library of python so inside the
project there is a web application and in a web application, we have two
methods in both  method extract pdf text into JSON but the data we are
getting is different so I create both these function,
the web project contains web applications with URLs routing and return
HTML httpresponse into the browser but behind the browser in project
directory both  JSON file available for method first, we have demo.json
and for a second we have output.json.

------------------------------------------------------------------------------------------------------------------------------------------------------------------
Installation step of the project is below
1.Extract repo in django activated envirment.
2.Go inside th project where manage.py located.
3.open cmd on that location.
4.write command python manage.py runserver

here is the code for referance.
```
from django.shortcuts import render,redirect
from django.http import HttpResponse
from PyPDF2 import PdfFileReader,PdfFileWriter
import json
import tabula
from tabula import read_pdf,convert_into



# Create your views here.
def pdftojson(request):
    df = read_pdf('./Test for json.pdf', pages = "all", multiple_tables = True)
    tabula.convert_into('./Test for json.pdf', "demo.json")
    tabula.convert_into_by_batch("demo", output_format = "json", pages = "all")


    print(df)
    return HttpResponse('This is pdftojson extractoe function..')

def demojson(request):
    filepath='./Test for json.pdf'
    df = tabula.read_pdf(filepath, pages='all')
    tabula.convert_into(filepath, "output.csv", output_format="csv", pages='all')

    print(df)
    return HttpResponse("this is demo")


```
