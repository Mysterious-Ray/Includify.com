import tkinter as tk
from tkinter import ttk, messagebox
import random

# Root window setup
root = tk.Tk()
root.title("LifeLink AI - Community Support App")
root.geometry("600x500")
root.configure(bg="#f2f2f2")

# Title label
title_label = tk.Label(root, text="LifeLink AI", font=("Helvetica", 24, "bold"), bg="#f2f2f2")
title_label.pack(pady=20)

# Frame Box
frame = tk.Frame(root, bg="white", bd=2, relief="groove")
frame.place(relx=0.5, rely=0.5, anchor="center", width=450, height=350)

# Functions
def launch_tutor():
    def start_tutor():
        topic = topic_entry.get().lower()
        lessons = {
            "math": "Let's learn about addition and subtraction!",
            "science": "Today's topic is the water cycle.",
            "english": "Let's practice simple past and present tenses."
        }
        result = lessons.get(topic, "Topic not found.")
        messagebox.showinfo("AI Tutor", result)

    popup = tk.Toplevel(root)
    popup.title("AI Tutor")
    popup.geometry("300x150")
    tk.Label(popup, text="Enter Topic (Math/Science/English):").pack(pady=5)
    topic_entry = tk.Entry(popup)
    topic_entry.pack(pady=5)
    tk.Button(popup, text="Start Lesson", command=start_tutor).pack(pady=10)

def launch_classifier():
    def classify():
        item = entry.get().lower()
        recyclable = ['plastic bottle', 'paper', 'can', 'glass']
        non_recyclable = ['food', 'diaper', 'tissue']
        if item in recyclable:
            result = "Recyclable"
        elif item in non_recyclable:
            result = "Non-Recyclable"
        else:
            result = "Unknown item"
        messagebox.showinfo("Waste Classifier", f"Item: {result}")

    popup = tk.Toplevel(root)
    popup.title("Waste Classifier")
    popup.geometry("300x150")
    tk.Label(popup, text="Enter item name:").pack(pady=5)
    entry = tk.Entry(popup)
    entry.pack(pady=5)
    tk.Button(popup, text="Classify", command=classify).pack(pady=10)

def launch_emergency():
    status = random.choice(['Normal', 'Fall Detected', 'Fire Detected'])
    alert = f"Status: {status}"
    if status != 'Normal':
        alert += "\nAlert sent to emergency services!"
    messagebox.showinfo("Emergency Check", alert)

def launch_volunteer():
    popup = tk.Toplevel(root)
    popup.title("Volunteer Connect")
    popup.geometry("300x150")
    tk.Label(popup, text="Feature connects volunteers with:\n- Elderly\n- People of Determination\n- NGOs").pack(pady=10)
    tk.Button(popup, text="Simulate Match", command=lambda: messagebox.showinfo("Volunteer Match", "Volunteer matched with a request in your area!")).pack(pady=10)

def launch_tips():
    tips = [
        "Turn off lights when not needed.",
        "Use reusable water bottles.",
        "Separate wet and dry waste.",
        "Help plant a tree in your neighborhood.",
        "Educate others about recycling."
    ]
    tip = random.choice(tips)
    messagebox.showinfo("Eco Tip", tip)

# Buttons
style = ttk.Style()
style.configure("TButton", font=("Helvetica", 12), padding=6)

buttons = [
    ("AI Tutor", launch_tutor),
    ("Waste Classifier", launch_classifier),
    ("Emergency Check", launch_emergency),
    ("Volunteer Connector", launch_volunteer),
    ("Environmental Tip", launch_tips)
]

for i, (text, command) in enumerate(buttons):
    ttk.Button(frame, text=text, command=command).pack(pady=6)

# Run App
root.mainloop()
