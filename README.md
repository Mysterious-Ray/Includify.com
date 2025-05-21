import tkinter as tk
from tkinter import ttk, messagebox
import random

# Root window setup
root = tk.Tk()
root.title("LifeLink AI - Community Support App")
root.geometry("650x550")
root.configure(bg="#e6f0fa")  # Soft blue background

# Title label
title_label = tk.Label(
    root, text="🌐 LifeLink AI 🌱",
    font=("Segoe UI", 28, "bold"),
    fg="#004080", bg="#e6f0fa"
)
title_label.pack(pady=30)

# Frame box with rounded border illusion
frame = tk.Frame(root, bg="white", bd=2, relief="ridge")
frame.place(relx=0.5, rely=0.55, anchor="center", width=480, height=400)

# Styling buttons
style = ttk.Style()
style.theme_use("clam")
style.configure(
    "RoundedButton.TButton",
    font=("Segoe UI", 12),
    padding=10,
    relief="flat",
    background="#007acc",
    foreground="white"
)
style.map("RoundedButton.TButton",
          background=[('active', '#005f99')],
          relief=[('pressed', 'sunken')])

# Functions
def launch_tutor():
    def start_tutor():
        topic = topic_entry.get().lower()
        lessons = {
            "math": "Let's learn about addition and subtraction!",
            "science": "Today's topic is the water cycle.",
            "english": "Let's practice simple past and present tenses."
        }
        result = lessons.get(topic, "Sorry, topic not found.")
        messagebox.showinfo("AI Tutor 📘", result)

    popup = tk.Toplevel(root)
    popup.title("AI Tutor")
    popup.geometry("300x150")
    popup.configure(bg="#f0f8ff")
    tk.Label(popup, text="Enter Topic (Math/Science/English):", bg="#f0f8ff").pack(pady=5)
    topic_entry = tk.Entry(popup)
    topic_entry.pack(pady=5)
    ttk.Button(popup, text="Start Lesson", style="RoundedButton.TButton", command=start_tutor).pack(pady=10)

def launch_classifier():
    def classify():
        item = entry.get().lower()
        recyclable = ['plastic bottle', 'paper', 'can', 'glass']
        non_recyclable = ['food', 'diaper', 'tissue']
        if item in recyclable:
            result = "♻️ Recyclable"
        elif item in non_recyclable:
            result = "🚫 Non-Recyclable"
        else:
            result = "❓ Unknown item"
        messagebox.showinfo("Waste Classifier 🗑️", f"Item: {result}")

    popup = tk.Toplevel(root)
    popup.title("Waste Classifier")
    popup.geometry("300x150")
    popup.configure(bg="#f0f8ff")
    tk.Label(popup, text="Enter item name:", bg="#f0f8ff").pack(pady=5)
    entry = tk.Entry(popup)
    entry.pack(pady=5)
    ttk.Button(popup, text="Classify", style="RoundedButton.TButton", command=classify).pack(pady=10)

def launch_emergency():
    status = random.choice(['✅ Normal', '⚠️ Fall Detected', '🔥 Fire Detected'])
    alert = f"Status: {status}"
    if status != '✅ Normal':
        alert += "\nAlert sent to emergency services!"
    messagebox.showinfo("Emergency Check 🚨", alert)

def launch_volunteer():
    popup = tk.Toplevel(root)
    popup.title("Volunteer Connect")
    popup.geometry("300x150")
    popup.configure(bg="#f0f8ff")
    tk.Label(popup, text="Connects volunteers with:\n🧓 Elderly\n♿ People of Determination\n🤝 NGOs", bg="#f0f8ff").pack(pady=10)
    ttk.Button(popup, text="Simulate Match", style="RoundedButton.TButton",
               command=lambda: messagebox.showinfo("Volunteer Match 🤗", "You’ve been matched with a request in your area!")).pack(pady=10)

def launch_tips():
    tips = [
        "💡 Turn off lights when not needed.",
        "💧 Use reusable water bottles.",
        "🗑️ Separate wet and dry waste.",
        "🌳 Plant a tree in your neighborhood.",
        "📢 Educate others about recycling."
    ]
    tip = random.choice(tips)
    messagebox.showinfo("Eco Tip 🌍", tip)

# Buttons
buttons = [
    ("📘 AI Tutor", launch_tutor),
    ("🗑️ Waste Classifier", launch_classifier),
    ("🚨 Emergency Check", launch_emergency),
    ("🤝 Volunteer Connector", launch_volunteer),
    ("🌍 Environmental Tip", launch_tips)
]

for text, command in buttons:
    ttk.Button(frame, text=text, style="RoundedButton.TButton", command=command).pack(pady=8, ipadx=10)

# Run App
root.mainloop()
