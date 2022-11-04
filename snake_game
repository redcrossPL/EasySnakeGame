import tkinter as tk
import random

score = 0
long = 2
space = 20
direction = 'Down'

root = tk.Tk()
root.title('Snejk')
root.resizable(False, False)


kwadraty = []
kordy = []

class Food:
    def __init__(self):
        a = random.randint(0, (500/space )-1)*space
        b = random.randint(0, (500/space )-1)*space
        self.kordziki = [a, b]
        canvas.create_oval(a, b, a+space, b+space, fill='red', tag='jedzonko')


def ruszanie():
    global score
    x, y = kordy[0]
    if direction == 'Down':
        kwadrat = canvas.create_rectangle(x, y, x+space, y+space, fill='green')
        kwadraty.insert(0, kwadrat)
    elif direction == 'Up':
        kwadrat = canvas.create_rectangle(x, y, x+space, y+space, fill='green')
        kwadraty.insert(0, kwadrat)
    elif direction == 'Right':
        kwadrat = canvas.create_rectangle(x, y, x+space, y+space, fill='green')
        kwadraty.insert(0, kwadrat)
    elif direction == 'Left':
        kwadrat = canvas.create_rectangle(x, y, x+space, y+space, fill='green')
        kwadraty.insert(0, kwadrat)

def check_col():
    x, y = kordy[0]

    if x < 0 or x >= 500:
        return True
    elif y < 0 or y >= 500:
        return True
    for czesci_ciala in kordy[1:]:
        if x == czesci_ciala[0] and y == czesci_ciala[1]:
            return True
    return False

def zmien_kordy():
    global score
    global food
    x, y = kordy[0]

    if direction == 'Down':
        y += space
    elif direction == 'Up':
        y -= space
    elif direction == 'Left':
        x -= space
    elif direction == 'Right':
        x += space
    kordy.insert(0, [x, y])
    kwadracik = canvas.create_rectangle(x, y, x+space, y+space, fill='green')
    kwadraty.insert(0, kwadracik)

    if x == food.kordziki[0] and y == food.kordziki[1]:
        score += 1
        score_text.config(text='Wynik:{}'.format(score))
        canvas.delete('jedzonko')
        food = Food()
    else:
        del kordy[-1]
        canvas.delete(kwadraty[-1])
        del kwadraty[-1]

    if check_col():
        canvas.delete(tk.ALL)
        canvas.create_text(250, 200, text='PRZEGRAŁEŚ', fill='red', font=('consolas', 60))
    else:
        root.after(200, zmien_kordy)



def ruch(new_direction):
    global direction
    if new_direction == 'Down':
        if direction != 'Up':
            direction = new_direction


    elif new_direction == 'Up':
        if direction != 'Down':
            direction = new_direction

    elif new_direction == 'Right':
        if direction != 'Left':
            direction = new_direction

    elif new_direction == 'Left':
        if direction != 'Right':
            direction = new_direction

score_text = tk.Label(root, text='Wynik:{}'.format(score), font=('cosolas', 40), fg='#0000FF')
score_text.pack()

canvas = tk.Canvas(root, height=500, width=500, bg='#000000')
canvas.pack()

for i in range(long): #dodanie pierwszych kordow snake'a
    kordy.append([0,0])

for x,y in kordy: #dodanie pierwszych kwadratow snake'a
    kwadrat = canvas.create_rectangle(x, y, x+space, y+space, fill='green')
    kwadraty.insert(0, kwadrat)


root.bind('<Up>', lambda event: ruch('Up'))
root.bind('<Down>', lambda event: ruch('Down'))
root.bind('<Right>', lambda event: ruch('Right'))
root.bind('<Left>', lambda event: ruch('Left'))
food = Food()
zmien_kordy()
ruszanie()


root.mainloop()
