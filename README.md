# Virtual-AI
VERONICA
import pyttsx3 as pyt
import speech_recognition as sr
import webbrowser as wb
import datetime as dt
import pyjokes as pyj
import os
import time as t
import pywhatkit as pyw
import wikipedia as wiki


def sptext():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening.....")
        recognizer.adjust_for_ambient_noise(source)
        audio = recognizer.listen(source)
        
        try:
            print("recognizer...")
            data = recognizer.recognize_google(audio)
            print(data)
            return data

        except sr.UnknownValueError:
            print("Not Understand...")

def speechtx(x):
    engine = pyt.init()
    voices = engine.getProperty('voices')
    engine.setProperty('voice',voices[1].id)#male[0],female[1]
    rate = engine.getProperty('rate')
    engine.setProperty('rate',150)#speech speed.
    engine.say(x)
    engine.runAndWait()

if __name__ == '__main__':

 if  "veronica" in sptext().lower() :
        
    while True:
        data1 = sptext().lower()

        if "your name" in data1:
            name = "my name is veronica"
            print(name)
            speechtx(name)

        elif "introduction" in data1:
            intro = "veronica is the artificial intiligence like JARVIS and FRIDAY "
            print(intro)
            speechtx(intro)    
        
        elif "old are you" in data1:
            age = "iam in one minute old"
            print(age)
            speechtx(age)

        elif "english" in data1:
            lang = "my language is english"
            print(lang)
            speechtx(lang)

        elif "time" in data1:
            time = dt.datetime.now().strftime("%I%M%p")
            print(time)
            speechtx(time)    

        elif "youtube" in data1:
            wb.open("https://www.youtube.com/")

        elif "google" in data1:
            wb.open("https://www.google.co.in/")

        elif "whatsapp" in data1:
            wb.open("https://web.whatsapp.com/")

        elif "created by" in data1:
            wb.open("https://en.wikipedia.org/wiki/Tony_Stark_(Marvel_Cinematic_Universe)")

        elif "amazon alexa" in data1:
            Aa = wb.open("https://en.wikipedia.org/wiki/Amazon_Alexa")
            

        elif "joke" in data1:
            joke_en = pyj.get_joke(language="en",category="neutral")
            print(joke_en)
            speechtx(joke_en)

        elif "mini project" in data1:
            addPath = "D:\Mini project"
            openPath = os.listdir(addPath)
            print(openPath)
            os.startfile(os.path.join(addPath, openPath[2]))

        elif "movies" in data1:
            addPath1 = "E:\Movies"
            openPath1 = os.listdir(addPath1)
            print(openPath1)
            os.startfile(os.path.join(addPath1, openPath1[0]))    


        elif "play" in data1:
            song = data1.replace('play','')
            speechtx("playing..." + song)
            pyw.playonyt(song)


        elif "search" in data1:
            person = data1.replace('searching on .......', '')
            info = wiki.summary(person,1)
            print(info)
            speechtx(info)
           

        elif "goodbye" in data1:
            speechtx("bye and thank you for talk with me")
            break

        t.sleep(5)

    else:
        print("bye...bye")

       
