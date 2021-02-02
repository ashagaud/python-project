# python-project
Web scrapping 

import requests
import bs4

url= input("emter your url")
response= requests.get(url)
print(type(response))
#print(response.text)
filename= "company.html"
bs= bs4.BeautifulSoup(response.text,"html.parser")

formatted_text= bs.prettify()
#print(formatted_text)

try:
    with open(filename,"w+") as f:
        f.write(formatted_text)

except Exception as e:
    print(e)

list_imgs= bs.find_all('img')
no_of_imgs=len(list_imgs)

print("number of img tags ",no_of_imgs)

for imgTag in list_imgs:
    #print(imgTag)
    imgLink=imgTag.get('src')
    print(imgLink)

