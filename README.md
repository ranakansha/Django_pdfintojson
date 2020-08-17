# Django_pdfintojson
In this repo i convert pdf text into json using tabula library.
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
