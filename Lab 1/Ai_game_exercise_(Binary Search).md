<!-- Centered content -->
<div align="center">
  <!-- Image -->
  <img src="https://github.com/user-attachments/assets/aa697654-16be-4b74-9d79-e035dc95833d" alt="Image Description" width="300px">
  
  <!-- Title and Information -->
  <h1>Artificial Intelligence (Lab)</h1>
  <h2>Lab Exercise</h2>
  <p>Arsalan Khan<br>2022115<br>Cyber Security</p>
  <br>
  <h3>Submitted to: Sir Usama Janjua</h3>
  <p>Date: September 5, 2024</p>
</div>

<!-- Separator -->
<hr>

<!-- Code Block 1 -->
<h3>Below is the Python code for the AI guessing game using Binary Search Algorithm:</h3>

<pre>
<code>
def guessgame():
    print("welcome guess a number from 1 to 100")
    low = 1
    high = 100
    attempts = 0
    
    while (low <= high):
        guess = (low + high) // 2
        attempts += 1
        
        print(f"ai guess: {guess}")
        feedback = input("enter feedback c,l,h::").lower()
        
        if feedback == 'c':
            print(f"ai guessed correctly in {attempts} attempt(s)")
            return
    
        elif feedback == 'h':
            high = guess - 1
            print("too high")
        
        elif feedback == 'l':
            low = guess + 1
            print("too low")
        
    print("something's wrong")
    
guessgame()
</code>
</pre>

<!-- Separator -->
<hr>

<!-- Code Block 2 -->
<h3>Below is the Python code for the AI guessing game using Breadth First Search Algorithm:</h3>

<pre>
<code>
def guessgame1():
    print("wellcome to ai guess game(BFS)")
    low = 1
    high = 100
    
    queue = list(range(low, high + 1))  # high + 1 includes 100
    attempts = 0
    
    while queue:
        guess = queue.pop(0)
        attempts += 1
        
        print(f"ai guess is {guess}")
        
        feedback = input("enter 1 of the following c,h,l: ").lower()
        
        if feedback == 'c':
            print(f"ai guessed correctly in {attempts} attempts")
            return
        
        elif feedback == 'h':
            print("too high...")
        elif feedback == 'l':
            print("too low")
        
        else:
            print("Invalid feedback. Please enter one of 'c', 'h', or 'l'.")
        
guessgame1()
</code>
</pre>

<!-- Code Block 3 -->
<h4>Below is the Python code for the AI guessing game using Depth First Search Algorithm:</h4>
<pre>
<code>
def guessgame2():
    print("wellcome to ai guess game,guess a number from 1 t0 100")
    low =1 
    high = 100
    attempts = 0
    
    stack = list(range(low,high+1))
    
    while stack:
        guess = stack.pop()
        attempts +=1
        print(f"ai guess is {guess}")
        feedback = input("select one of the following c,h,l").lower()
        
        if feedback =='c':
            print(f"ai guessed correctly in {attempts} attempts")
            return
        elif feedback =='h':
            print("too high")
        elif feedback == 'l':
            print("too low...")
        
        else:
            print("invalid choice,,,")

guessgame2()
</code>
</pre>
