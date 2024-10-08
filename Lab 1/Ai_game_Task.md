<!-- Centered content -->
<div align="center">
  <!-- Image -->
  <img src="https://github.com/user-attachments/assets/aa697654-16be-4b74-9d79-e035dc95833d" alt="Image Description" width="300px">
  
  <!-- Title and Information -->
  <h1>Artificial Intelligence (Lab)</h1>
  <h2>Lab Exercise</h2>
  <p><strong>Arsalan Khan</strong><br>2022115<br>Cyber Security</p>
  <br>
  <h3>Submitted to: Sir Usama Arshad</h3>
  <p>Date: September 9, 2024</p>
</div>

<!-- Separator -->
<hr>

<!-- Code Block 1 -->
<h3>Below is the Python code for the AI guessing game using Binary Search Algorithm:</h3>

```python
def guessgame():
    print("Welcome, guess a number from 1 to 100")
    low = 1
    high = 100
    attempts = 0
    
    while (low <= high):
        guess = (low + high) // 2
        attempts += 1
        
        print(f"AI guess: {guess}")
        feedback = input("Enter feedback (c, l, h): ").lower()
        
        if feedback == 'c':
            print(f"AI guessed correctly in {attempts} attempt(s)")
            return
    
        elif feedback == 'h':
            high = guess - 1
            print("Too high")
        
        elif feedback == 'l':
            low = guess + 1
            print("Too low")
        
    print("Something's wrong")
    
guessgame()
```
<!-- Code Block 2 -->
<h3>Below is the Python code for the AI guessing game using Breadth First Search Algorithm:</h3>

```python
def guessgame1():
    print("Welcome to AI guess game (BFS)")
    low = 1
    high = 100
    
    queue = list(range(low, high + 1))  # high + 1 includes 100
    attempts = 0
    
    while queue:
        guess = queue.pop(0)
        attempts += 1
        
        print(f"AI guess: {guess}")
        
        feedback = input("Enter 1 of the following (c, h, l): ").lower()
        
        if feedback == 'c':
            print(f"AI guessed correctly in {attempts} attempts")
            return
        
        elif feedback == 'h':
            print("Too high...")
        elif feedback == 'l':
            print("Too low")
        
        else:
            print("Invalid feedback. Please enter one of 'c', 'h', or 'l'")
        
guessgame1()
```
![1](https://github.com/user-attachments/assets/eb024925-28f7-4029-a297-3aa1b8cddaca)

<p>In this code, if the correct number was 10, the AI would have started guessing from 1 and sequentially increased each guess by 1. It would have needed 10 attempts to correctly guess the number 10. This code uses a queue-based logic where all the numbers in the range are initially placed inside the queue, and each number is popped from the top of the queue for guessing.</p>

<!-- Code Block 3 -->
<h4>Below is the Python code for the AI guessing game using Depth First Search Algorithm:</h4>

```python
def guessgame2():
    print("Welcome to AI guess game, guess a number from 1 to 100")
    low = 1 
    high = 100
    attempts = 0
    
    stack = list(range(low, high + 1))
    
    while stack:
        guess = stack.pop()
        attempts += 1
        print(f"AI guess: {guess}")
        feedback = input("Select one of the following (c, h, l): ").lower()
        
        if feedback == 'c':
            print(f"AI guessed correctly in {attempts} attempts")
            return
        elif feedback == 'h':
            print("Too high")
        elif feedback == 'l':
            print("Too low")
        
        else:
            print("Invalid choice")
        
guessgame2()
```
![2](https://github.com/user-attachments/assets/d3685b25-4d54-40ea-ba40-4d504562a1c8)

<p>In this code, if the correct number was 10, the AI would have started guessing from 100 and sequentially decreased the guesses by 1 each time. It would have needed 90 attempts to correctly guess the number 10. This code uses stack logic, where numbers are pushed onto the stack in descending order and then popped from the top of the stack for guessing. Because a stack follows LIFO (Last In, First Out) order, the AI would first guess the highest number and work its way down to the correct number.</p>

<!-- Code Block 4 -->
<h3>Below is the Python code for the AI guessing game using Adaptive Search Algorithm:</h3>

```python
def guessgame3():
    print("Welcome to the guess game using adaptive search")
    
    low = 1
    high = 100
    attempts = 0
    
    prev_guess = None
    prev_feedback = None
    
    while low <= high:
        
        if prev_guess is None:
            guess = (low + high) // 2
        elif prev_feedback == 'h':
            guess = prev_guess - (prev_guess - low) // 2
        elif prev_feedback == 'l':
            guess = prev_guess + (high - prev_guess) // 2
        else:
            guess = (low + high) // 2
        
        print(f"AI guess: {guess}")
        feedback = input("Enter feedback (c, h, l): ").lower()
        
        if feedback == 'c':
            print(f"AI guessed correctly in {attempts} attempt(s)")
            return
        
        elif feedback == 'h':
            print("Too high")
            high = guess - 1
            
        elif feedback == 'l':
            print("Too low")
            low = guess + 1
        
        else:
            print("Invalid feedback. Please enter one of 'c', 'h', or 'l'")
            continue  
        
        prev_guess = guess
        prev_feedback = feedback
        attempts += 1
    
    print("Something's wrong")

guessgame3()
```
![3](https://github.com/user-attachments/assets/19169622-04a1-43b2-95cb-5c4c3daa7ca5)

<p>Adaptive Search: This approach produces results similar to a binary search, but instead of simply halving the search range each time, it adjusts its guesses based on previous guesses and feedback. The algorithm uses the information from earlier guesses to adaptively adjust its future guesses, making it more flexible and potentially faster in converging to the correct number. The correct number that I had chosen was 10. It took 4 attempts for the AI to guess it correctly.</p>
