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
