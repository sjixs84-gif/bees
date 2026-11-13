import tkinter as tk
from tkinter import messagebox
import pygame
import os
import sys

# Определяем путь к вшитой музыке внутри .exe
base_path = getattr(sys, '_MEIPASS', os.path.dirname(os.path.abspath(__file__)))
music_file = os.path.join(base_path, "music.mp3")

# Инициализация и запуск музыки
pygame.mixer.init()
if os.path.exists(music_file):
    pygame.mixer.music.load(music_file)
    pygame.mixer.music.play(-1)  # Бесконечный повтор

def show_bsod():
    # Создаем полноэкранное синее окно
    bsod = tk.Toplevel()
    bsod.attributes("-fullscreen", True)
    bsod.attributes("-topmost", True)
    bsod.configure(bg="#0078D7")
    bsod.config(cursor="none")  # Скрываем курсор

    # Грустный смайлик
    sad_face = tk.Label(bsod, text=":(", font=("Segoe UI", 100), fg="white", bg="#0078D7")
    sad_face.pack(anchor="w", padx=100, pady=(80, 20))

    # Основной текст ошибки
    msg = (
        "На вашем ПК возникла проблема, так как вы не уважаете пчёлок.\n"
        "Мы лишь собираем сведения об ошибке, а затем выполним перезагрузку.\n\n"
        "0% завершено"
    )
    info = tk.Label(bsod, text=msg, font=("Segoe UI", 22), fg="white", bg="#0078D7", justify="left")
    info.pack(anchor="w", padx=100)

    # Код остановки и подсказка для выхода
    hint = tk.Label(
        bsod,
        text="Код остановки: BEE_RESPECT_NOT_FOUND\n(Нажмите ESC, чтобы выйти из розыгрыша)",
        font=("Segoe UI", 14),
        fg="white",
        bg="#0078D7",
        justify="left"
    )
    hint.pack(anchor="w", padx=100, pady=50)

    # Выход по нажатию клавиши Escape
    bsod.bind("<Escape>", lambda e: root.destroy())

def ask_bees():
    root.withdraw()
    answer = messagebox.askyesno("Важный системный вопрос", "Уважаешь ли ты пчёлок?")
    
    if answer:
        messagebox.showinfo("Отлично", "Пчёлки тоже тебя уважают! Проверка пройдена.")
        root.destroy()
    else:
        show_bsod()

root = tk.Tk()
root.after(100, ask_bees)
root.mainloop()
