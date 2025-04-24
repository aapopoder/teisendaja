import tkinter as tk
from tkinter import ttk

def celsius_kohta_fahrenheit(celsius):
    return (celsius * 9/5) + 32

def fahrenheit_kohta_celsius(fahrenheit):
    return (fahrenheit - 32) * 5/9

def kelvin_kohta_celsius(kelvin):
    return kelvin - 273.15

def celsius_kohta_kelvin(celsius):
    return celsius + 273.15

def kelvin_kohta_fahrenheit(kelvin):
    celsius = kelvin_kohta_celsius(kelvin)
    return celsius_kohta_fahrenheit(celsius)

def fahrenheit_kohta_kelvin(fahrenheit):
    celsius = fahrenheit_kohta_celsius(fahrenheit)
    return celsius_kohta_kelvin(celsius)

def teisenda():
    try:
        # Saame kasutaja valiku ja sisendi
        temperatuur = float(entry_temp.get())
        valik = combobox_valik.get()

        if valik == "Celsius -> Fahrenheit":
            tulemus = celsius_kohta_fahrenheit(temperatuur)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} °F")
        elif valik == "Fahrenheit -> Celsius":
            tulemus = fahrenheit_kohta_celsius(temperatuur)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} °C")
        elif valik == "Celsius -> Kelvin":
            tulemus = celsius_kohta_kelvin(temperatuur)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} K")
        elif valik == "Kelvin -> Celsius":
            tulemus = kelvin_kohta_celsius(temperatuur)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} °C")
        elif valik == "Kelvin -> Fahrenheit":
            tulemus = kelvin_kohta_fahrenheit(temperatuur)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} °F")
        elif valik == "Fahrenheit -> Kelvin":
            tulemus = fahrenheit_kohta_kelvin(temperatuur)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} K")
    except ValueError:
        label_tulemus.config(text="Palun sisesta kehtiv temperatuur!")

root = tk.Tk()
root.title("Temperatuuri teisendaja")

label_vali = tk.Label(root, text="Vali teisendus tüüp:")
label_vali.grid(row=0, column=0, padx=10, pady=10)

combobox_valik = ttk.Combobox(root, values=[
    "Celsius -> Fahrenheit", "Fahrenheit -> Celsius", 
    "Celsius -> Kelvin", "Kelvin -> Celsius", 
    "Kelvin -> Fahrenheit", "Fahrenheit -> Kelvin"
])
combobox_valik.grid(row=0, column=1, padx=10, pady=10)
combobox_valik.set("Celsius -> Fahrenheit")  # Algne valik

label_temp = tk.Label(root, text="Sisesta temperatuur:")
label_temp.grid(row=1, column=0, padx=10, pady=10)

entry_temp = tk.Entry(root)
entry_temp.grid(row=1, column=1, padx=10, pady=10)

button_teisenda = tk.Button(root, text="Teisenda", command=teisenda)
button_teisenda.grid(row=2, column=0, columnspan=2, pady=20)

label_tulemus = tk.Label(root, text="Tulemus:")
label_tulemus.grid(row=3, column=0, columnspan=2, pady=10)

root.mainloop()





















import tkinter as tk
from tkinter import ttk

# Temperatuuri teisendamise funktsioonid
def celsius_kohta_fahrenheit(celsius):
    return (celsius * 9/5) + 32

def fahrenheit_kohta_celsius(fahrenheit):
    return (fahrenheit - 32) * 5/9

def kelvin_kohta_celsius(kelvin):
    return kelvin - 273.15

def celsius_kohta_kelvin(celsius):
    return celsius + 273.15

def kelvin_kohta_fahrenheit(kelvin):
    celsius = kelvin_kohta_celsius(kelvin)
    return celsius_kohta_fahrenheit(celsius)

def fahrenheit_kohta_kelvin(fahrenheit):
    celsius = fahrenheit_kohta_celsius(fahrenheit)
    return celsius_kohta_kelvin(celsius)

# Uued funktsioonid mõõtühikute teisendamiseks
def cm_kohta_metreid(cm):
    return cm / 100

def metreid_kohta_cm(metreid):
    return metreid * 100

def kg_kohta_tonne(kg):
    return kg / 1000

def tonne_kohta_kg(tonne):
    return tonne * 1000

def km_kohta_metreid(km):
    return km * 1000

def metreid_kohta_km(metreid):
    return metreid / 1000

# Teisendamise funktsioon
def teisenda_temperatuur():
    try:
        väärtus = float(entry_temp.get())  # Sisendi väärtus
        valik = combobox_valik.get()  # Valiku tüüp

        if valik == "Celsius -> Fahrenheit":
            tulemus = celsius_kohta_fahrenheit(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} °F")
        elif valik == "Fahrenheit -> Celsius":
            tulemus = fahrenheit_kohta_celsius(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} °C")
        elif valik == "Celsius -> Kelvin":
            tulemus = celsius_kohta_kelvin(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} K")
        elif valik == "Kelvin -> Celsius":
            tulemus = kelvin_kohta_celsius(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} °C")
        elif valik == "Kelvin -> Fahrenheit":
            tulemus = kelvin_kohta_fahrenheit(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} °F")
        elif valik == "Fahrenheit -> Kelvin":
            tulemus = fahrenheit_kohta_kelvin(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} K")
    except ValueError:
        label_tulemus.config(text="Palun sisesta kehtiv väärtus!")

# Eraldi funktsioon arvude teisendamiseks
def teisenda_arvud():
    try:
        väärtus = float(entry_temp.get())  # Sisendi väärtus
        valik = combobox_arvud.get()  # Arvude valiku tüüp

        if valik == "Sentimeetrid -> Meetrit":
            tulemus = cm_kohta_metreid(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} m")
        elif valik == "Meetrit -> Sentimeetrid":
            tulemus = metreid_kohta_cm(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} cm")
        elif valik == "Kilogrammid -> Tonnid":
            tulemus = kg_kohta_tonne(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} t")
        elif valik == "Tonnid -> Kilogrammid":
            tulemus = tonne_kohta_kg(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} kg")
        elif valik == "Kilomeetrid -> Meetrit":
            tulemus = km_kohta_metreid(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} m")
        elif valik == "Meetrit -> Kilomeetrid":
            tulemus = metreid_kohta_km(väärtus)
            label_tulemus.config(text=f"Tulemus: {tulemus:.2f} km")
    except ValueError:
        label_tulemus.config(text="Palun sisesta kehtiv väärtus!")

# Graafilise liidese loomine
root = tk.Tk()
root.title("Teisendaja")

# Temperatuuri valik
label_vali = tk.Label(root, text="Vali temperatuuri teisenduse tüüp:")
label_vali.grid(row=0, column=0, padx=10, pady=10)

combobox_valik = ttk.Combobox(root, values=[
    "Celsius -> Fahrenheit", "Fahrenheit -> Celsius", 
    "Celsius -> Kelvin", "Kelvin -> Celsius", 
    "Kelvin -> Fahrenheit", "Fahrenheit -> Kelvin"
])
combobox_valik.grid(row=0, column=1, padx=10, pady=10)
combobox_valik.set("Celsius -> Fahrenheit")

# Arvude valik
label_arvud = tk.Label(root, text="Vali mõõtühiku teisendus:")
label_arvud.grid(row=1, column=0, padx=10, pady=10)

combobox_arvud = ttk.Combobox(root, values=[
    "Sentimeetrid -> Meetrit", "Meetrit -> Sentimeetrid",
    "Kilogrammid -> Tonnid", "Tonnid -> Kilogrammid",
    "Kilomeetrid -> Meetrit", "Meetrit -> Kilomeetrid"
])
combobox_arvud.grid(row=1, column=1, padx=10, pady=10)
combobox_arvud.set("Sentimeetrid -> Meetrit")

# Sisendi väli
label_temp = tk.Label(root, text="Sisesta väärtus:")
label_temp.grid(row=2, column=0, padx=10, pady=10)

entry_temp = tk.Entry(root)
entry_temp.grid(row=2, column=1, padx=10, pady=10)

# Nupp temperatuuri teisendamiseks
button_teisenda_temp = tk.Button(root, text="Teisenda temperatuur", command=teisenda_temperatuur)
button_teisenda_temp.grid(row=3, column=0, columnspan=2, pady=10)

# Nupp arvude teisendamiseks
button_teisenda_arvud = tk.Button(root, text="Teisenda mõõtühikud", command=teisenda_arvud)
button_teisenda_arvud.grid(row=4, column=0, columnspan=2, pady=10)

# Tulemus
label_tulemus = tk.Label(root, text="Tulemus:")
label_tulemus.grid(row=5, column=0, columnspan=2, pady=10)

root.mainloop()




