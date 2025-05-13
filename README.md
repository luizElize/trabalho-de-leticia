# trabalho-de-leticia

import tkinter as tk

def clicar(valor):
    entrada.insert(tk.END, valor)

def calcular():
    try:
        resultado = eval(entrada.get())
        entrada.delete(0, tk.END)
        entrada.insert(tk.END, str(resultado))
    except:
        entrada.delete(0, tk.END)
        entrada.insert(tk.END, "Erro")

def limpar():
    entrada.delete(0, tk.END)

# Interface
app = tk.Tk()
app.title("Calculadora")
app.geometry("300x400")

entrada = tk.Entry(app, font=("Arial", 20), bd=10, relief=tk.RIDGE, justify='right')
entrada.grid(row=0, column=0, columnspan=4)

# Botões
botoes = [
    ("7", 1, 0), ("8", 1, 1), ("9", 1, 2), ("/", 1, 3),
    ("4", 2, 0), ("5", 2, 1), ("6", 2, 2), ("*", 2, 3),
    ("1", 3, 0), ("2", 3, 1), ("3", 3, 2), ("-", 3, 3),
    ("0", 4, 0), (".", 4, 1), ("=", 4, 2), ("+", 4, 3),
]

for (texto, linha, coluna) in botoes:
    if texto == "=":
        cmd = calcular
    else:
        cmd = lambda t=texto: clicar(t)
    tk.Button(app, text=texto, width=5, height=2, font=("Arial", 18), command=cmd).grid(row=linha, column=coluna)

tk.Button(app, text="C", width=22, height=2, font=("Arial", 18), command=limpar).grid(row=5, column=0, columnspan=4)

app.mainloop()
