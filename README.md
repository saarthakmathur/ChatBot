# ChatBot

import tkinter as tk
from tkinter import scrolledtext

class Chatbox:
    def __init__(self, root):
        self.root = root
        self.root.title("Chatbox")

        # Create a text area for displaying messages
        self.chat_area = scrolledtext.ScrolledText(self.root, state='disabled', wrap='word', width=50, height=20)
        self.chat_area.grid(row=0, column=0, columnspan=2)

        # Create an entry box for typing messages
        self.message_entry = tk.Entry(self.root, width=40)
        self.message_entry.grid(row=1, column=0)

        # Create a send button
        self.send_button = tk.Button(self.root, text="Send", command=self.send_message)
        self.send_button.grid(row=1, column=1)

    def send_message(self):
        message = self.message_entry.get()
        if message:
            self.chat_area.config(state='normal')  # Enable the text area to insert text
            self.chat_area.insert(tk.END, "You: " + message + "\n")  # Display the user's message
            self.chat_area.config(state='disabled')  # Disable the text area to prevent editing
            self.message_entry.delete(0, tk.END)  # Clear the entry box

            # Here you can add logic for a response from the bot or another user
            self.chat_area.config(state='normal')
            self.chat_area.insert(tk.END, "Bot: " + self.get_bot_response(message) + "\n")  # Display bot's response
            self.chat_area.config(state='disabled')

    def get_bot_response(self, message):
        # Simple bot response logic (you can expand this)
        return "This is a placeholder response."

if __name__ == "__main__":
    root = tk.Tk()
    chatbox = Chatbox(root)
    root.mainloop()
