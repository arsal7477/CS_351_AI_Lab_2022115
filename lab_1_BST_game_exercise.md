<!-- Centered content -->
<div align="center">
  <!-- Image -->
  <img src="https://github.com/user-attachments/assets/aa697654-16be-4b74-9d79-e035dc95833d" alt="Image Description" width="300px">
  
  <!-- Title and Information -->
  <h1>Artificial Intelligence</h1>
  <h2>Lab Exercise</h2>
  <p>Arsalan Khan<br>2022115<br>Cyber Security</p>
  <br>
  <h3>Submitted to: Sir Usama Janjua</h3>
  <p>Date: September 5, 2024</p>
</div>

<!--  code -->
Below is the Python code for the AI guessing game:

```python
def guessgame():
    print("welcome guess a number from 1 to 100")
    low = 1
    high = 100
    attempts =0
    
    while (low<=high):
        guess = (low + high) // 2
        attempts +=1
        
        print(f"ai guess: {guess}")
        feedback = input("enter feedback c,l,h::").lower()
        
        if feedback == 'c':
            print(f"ai guessed correctly in {attempts} attempt(s)")
            return
    
        elif feedback == 'h':
            high = guess - 1
            print("too high")
        
        elif feedback =='l':
            low = guess + 1
            print("too low")
        
    print("something's wrong")
    
guessgame()
