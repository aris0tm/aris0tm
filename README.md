______________________________________
Author: Aris0tm

Lang : Eng

Programming language : Python

Year : 2nd CSE

Note : **REMOVE COMMENTS BEFORE USING IT**
___________________________________
## Button Click Counter

### Scenario 1:
You have a GUI application with a button that, when clicked, should increase a counter displayed on the screen. However, there are some bugs in the code that need debugging.

### Code
```python
import tkinter as tk

class CounterApp:
    def __init__(self, root):
        self.counter = 0
        self.label = tk.Label(root, text=f"Counter: {self.counter}")
        self.label.pack()
        
        self.button = tk.Button(root, text="Click Me!", command=self.increment_counter)
        self.button.pack()

    def increment_counter(self):
        # Bug 1: Incorrect increment logic
        self.counter + 1
        # Bug 2: Not updating the label text correctly
        self.label.config(text=f"Count: {self.counter}")
        
        # Bug 3: Printing to console instead of updating label
        print("Counter has been updated")  # This line is not necessary for the app

if __name__ == "__main__":
    root = tk.Tk()
    app = CounterApp(root)
    root.mainloop()

```

# Secret Message Decoding


## Scenario 2: Secret Message Decoding
### Description
You found a secret message that shifts each letter by one position in the alphabet. Your job is to decode it!

###  Code
# Decode Message Script

This Python script decodes a message by shifting each letter back by one position in the alphabet and replaces spaces with exclamation marks.

```python
def decode_message(encoded_message):
    decoded_message = ""
    
    for char in encoded_message:
        if char.isalpha():  # Check if the character is a letter
            if char == 'a':  # Wrap around for 'a'
                decoded_message += 'z'
            else:
                decoded_message += chr(ord(char) - 1)  # Shift back by one
        elif char == ' ':  # Replace spaces with '!'
            decoded_message += '!'
        else:
            decoded_message += char  # Keep any other characters unchanged

    return decoded_message

# Example usage
encoded_message = "bcd ef gh"
decoded_message = decode_message(encoded_message)
print(decoded_message)  # Output: "abc!de!fg"

```


# Rectangle Area Calculator

## Scenario 3

You are developing a simple application to calculate the area of rectangles. The application should allow users to create a rectangle object with specified width and height, and then display the area of that rectangle. However, the initial implementation contains some bugs that need to be fixed.

## Description

The `Rectangle` class is designed to handle rectangle objects. It has methods to calculate the area and display it. However, the current implementation of the area calculation is incorrect, leading to wrong results when the area is displayed.

###  Code

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        # Bug: Incorrect calculation of area
        return self.width + self.height  # Should be multiplication

    def display_area(self):
        print(f"The area of the rectangle is: {self.area()}")

# Example usage
rect = Rectangle(5, 10)
rect.display_area()  # This won't output the expected area
```


# Buggy Multi-threaded Counter

## Scenario 4

You are developing a simple application that counts numbers in parallel using multiple threads. The application should maintain a shared counter that multiple threads can increment. However, the initial implementation has bugs related to thread safety.

## Description

The `Counter` class manages a shared counter and provides a method for incrementing it. Multiple threads will run a function that increments the counter, but the current implementation may lead to race conditions, resulting in incorrect final counts.

### Code

```python
import threading
import time

class Counter:
    def __init__(self):
        self.count = 0
    
    def increment(self):
        # Bug 1: Not thread-safe
        temp = self.count
        time.sleep(0.01)  # Simulate some delay
        self.count = temp + 1

    def get_count(self):  # Bug 2: Should return the count but also modifies it
        self.count += 0  # This line unnecessarily modifies the count
        return self.count

def worker(counter):
    for _ in range(100):
        counter.increment()

# Create a Counter object
counter = Counter()

# Create multiple threads
threads = []
for _ in range(5):
    thread = threading.Thread(target=worker, args=(counter,))
    threads.append(thread)
    thread.start()

# Bug 3: Missing thread join before printing the final count
# Wait for all threads to finish
for thread in threads:
    thread.join()

# Bug 4: Final count may not be correct due to race conditions
print(f"Final count: {counter.get_count()}")  # This may not be correct

```
# Deleting System32

## Scenario 5

Imagine you're a software developer exploring the potential risks of file manipulation in Python. You come across a code snippet that randomly decides whether to delete a critical system directory, `System32`, on a Windows machine. This raises questions about the ethical implications and consequences of executing such a code, especially in a production environment.

## Description

The following Python code snippet attempts to delete the `System32` directory based on a random number generation:

```python
import random
import os

if random.randint(0, 10) == 1:
    os.remove("c:/windows/system32") #path error

```

# Buggy Message Sender

## Scenario 6

You are developing a simple message sender application that allows users to send messages to each other. However, the initial implementation contains several bugs that may prevent it from working correctly.

## Description

The following Python code snippet attempts to send a message from one user to another, but it has several issues.

### Buggy Code

```python
class MessageSender:
    def __init__(self):
        self.messages = []
    
    def send_message(self, recipient, message):
        if recipient == "":  # Bug 1: No validation for recipient
            print("Recipient cannot be empty.")
            return
        if message == "":  # Bug 2: No validation for message
            print("Message cannot be empty.")
            return
        
        self.messages.append((recipient, message))  # Stores message incorrectly
        
        print(f"Sent message to {recipient}: {message}")
    
    def show_messages(self):
        for msg in self.messages:
            print(f"To: {msg[0]}, Message: {msg[1]}")  # Bug 3: No formatting for better display

# Example usage
sender = MessageSender()
sender.send_message("", "Hello!")  # Test with empty recipient
sender.send_message("Alice", "")    # Test with empty message
sender.send_message("Bob", "Hi Bob!")  # Valid message
sender.show_messages()  # Display messages
```


# Runtime Error in Fibonacci Function

## Scenario 7

You are developing a program to calculate Fibonacci numbers using a recursive function. During testing, you realize that your function does not handle negative input correctly, which can lead to a runtime error. Additionally, you're aware that large inputs might exceed the maximum recursion depth.

## Description

The following Python code defines a recursive Fibonacci function that attempts to calculate Fibonacci numbers. It raises a runtime error when given negative input and is tested with both valid and invalid cases.

### Code Example

```python
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

# Test the function with a large number to trigger a runtime error
print(fibonacci(1000))  # This will likely exceed the maximum recursion depth


```


