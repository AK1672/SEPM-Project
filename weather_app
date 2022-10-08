from tkinter import *
from tkinter import ttk
from turtle import left
from bs4 import BeautifulSoup
import requests
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3'}

def save():
    l=label.get(1.0, "end-1c")
    c=text.get(1.0, "end-1c")
    with open(c+'weather report.txt', 'w') as f:
        f.write(''+l)

def weather(city):
    city = city.replace(" ", "+")
    res = requests.get(
        f'https://www.google.com/search?q={city}&oq={city}&aqs=chrome.0.35i39l2j0l4j46j69i60.6128j1j7&sourceid=chrome&ie=UTF-8', headers=headers)
    soup = BeautifulSoup(res.text, 'html.parser')
    try:
        location = soup.select('#wob_loc')[0].getText().strip()
    except:
        return "Error! No such city exists"
    time = soup.select('#wob_dts')[0].getText().strip()
    info = soup.select('#wob_dc')[0].getText().strip()
    weather = soup.select('#wob_tm')[0].getText().strip()
    s=location+"\n"+time+"\n"+info+"\n"+weather+"°C"
    return s;

def get_input():
    city_name=text.get(1.0, "end-1c")
    l=weather(city_name+" weather")
    label.delete(1.0,END)
    label.insert(INSERT,""+l)


win=Tk()
win.geometry("800x600")
win.title("Weather Forecast")
bg = PhotoImage(file = "bg.png")
ic = PhotoImage(file = "weather-app-icon-4.jpg")
label1 = Label( win, image = bg)
label1.place(x = 0, y = 0)
win.iconphoto(False, ic)


label1=Label(win,text="Weather Forecast",fg="blue",bg="Yellow",relief="solid",font=("arial",25,"bold")).pack()
label2=Label(win,text="By Default shows your current location weather report\nYou can enter city name to check Weather Report",fg="orange",bg='light blue',font=("arial",15,"bold")).pack()


text=Text(win, width=30, height=1)
text.insert(END, "")
text.pack()

b=ttk.Button(win, text="Check Weather", command=get_input)
b.pack()

weather_now = Label(win, text = "The Weather is: ", font = 'arial 12 bold',bg='blue',fg='yellow').pack()
L=weather(" weather")
label=Text(win,width=40,height=10)
label.insert(INSERT,""+L)
label.pack()

b=ttk.Button(win, text="Save Result", command=save)
b.pack()

win.mainloop()
