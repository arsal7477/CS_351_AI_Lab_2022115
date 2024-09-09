<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Guessing Game</title>
    <style>
        pre {
            background: #f5f5f5;
            border: 1px solid #ddd;
            border-radius: 4px;
            padding: 10px;
            overflow: auto;
            font-family: Consolas, Monaco, 'Andale Mono', 'Ubuntu Mono', monospace;
            font-size: 14px;
        }
        code {
            color: #d63384; /* Pink for keywords */
        }
        .variable {
            color: #0056b3; /* Blue for variables */
        }
        .comment {
            color: #6c757d; /* Gray for comments */
            font-style: italic;
        }
        .string {
            color: #28a745; /* Green for strings */
        }
    </style>
</head>
<body>
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

    <pre><code>
<span class="comment"># Binary Search Algorithm</span>
<span class="variable">def</span> <span class="variable">guessgame</span>():
    <span class="variable">print</span>(<span class="string">"welcome guess a number from 1 to 100"</span>)
    <span class="variable">low</span> = <span class="number">1</span>
    <span class="variable">high</span> = <span class="number">100</span>
    <span class="variable">attempts</span> = <span class="number">0</span>
    
    <span class="variable">while</span> (<span class="variable">low</span> <= <span class="variable">high</span>):
        <span class="variable">guess</span> = (<span class="variable">low</span> + <span class="variable">high</span>) // <span class="number">2</span>
        <span class="variable">attempts</span> += <span class="number">1</span>
        
        <span class="variable">print</span>(f<span class="string">"ai guess: {guess}"</span>)
        <span class="variable">feedback</span> = <span class="variable">input</span>(<span class="string">"enter feedback c,l,h::"</span>).<span class="variable">lower</span>()
        
        <span class="variable">if</span> <span class="variable">feedback</span> == <span class="string"> 'c'</span>:
            <span class="variable">print</span>(f<span class="string">"ai guessed correctly in {attempts} attempt(s)"</span>)
            <span class="variable">return</span>
    
        <span class="variable">elif</span> <span class="variable">feedback</span> == <span class="string"> 'h'</span>:
            <span class="variable">high</span> = <span class="variable">guess</span> - <span class="number">1</span>
            <span class="variable">print</span>(<span class="string">"too high"</span>)
        
        <span class="variable">elif</span> <span class="variable">feedback</span> == <span class="string"> 'l'</span>:
            <span class="variable">low</span> = <span class="variable">guess</span> + <span class="number">1</span>
            <span class="variable">print</span>(<span class="string">"too low"</span>)
        
    <span class="variable">print</span>(<span class="string">"something's wrong"</span>)
    
<span class="variable">guessgame</span>()
    </code></pre>

    <!-- Separator -->
    <hr>

    <!-- Code Block 2 -->
    <h3>Below is the Python code for the AI guessing game using Breadth First Search Algorithm:</h3>

    <pre><code>
<span class="comment"># Breadth First Search Algorithm</span>
<span class="variable">def</span> <span class="variable">guessgame1</span>():
    <span class="variable">print</span>(<span class="string">"wellcome to ai guess game(BFS)"</span>)
    <span class="variable">low</span> = <span class="number">1</span>
    <span class="variable">high</span> = <span class="number">100</span>
    
    <span class="variable">queue</span> = <span class="variable">list</span>(<span class="variable">range</span>(<span class="variable">low</span>, <span class="variable">high</span> + <span class="number">1</span>))  <span class="comment"># high + 1 includes 100</span>
    <span class="variable">attempts</span> = <span class="number">0</span>
    
    <span class="variable">while</span> <span class="variable">queue</span>:
        <span class="variable">guess</span> = <span class="variable">queue</span>.<span class="variable">pop</span>(<span class="number">0</span>)
        <span class="variable">attempts</span> += <span class="number">1</span>
        
        <span class="variable">print</span>(f<span class="string">"ai guess is {guess}"</span>)
        
        <span class="variable">feedback</span> = <span class="variable">input</span>(<span class="string">"enter 1 of the following c,h,l: "</span>).<span class="variable">lower</span>()
        
        <span class="variable">if</span> <span class="variable">feedback</span> == <span class="string"> 'c'</span>:
            <span class="variable">print</span>(f<span class="string">"ai guessed correctly in {attempts} attempts"</span>)
            <span class="variable">return</span>
        
        <span class="variable">elif</span> <span class="variable">feedback</span> == <span class="string"> 'h'</span>:
            <span class="variable">print</span>(<span class="string">"too high..."</span>)
        <span class="variable">elif</span> <span class="variable">feedback</span> == <span class="string"> 'l'</span>:
            <span class="variable">print</span>(<span class="string">"too low"</span>)
        
        <span class="variable">else</span>:
            <span class="variable">print</span>(<span class="string">"Invalid feedback please enter one of 'c', 'h', or 'l'"</span>)
        
<span class="variable">guessgame1</span>()
    </code></pre>
    <p>In this code, if the correct number was 10, the AI would have started guessing from 1 and sequentially increased each guess by 1. It would have needed 10 attempts to correctly guess the number 10. This code uses a queue-based logic where all the numbers in the range are initially placed inside the queue, and each number is popped from the top of the queue for guessing.</p>

    <!-- Code Block 3 -->
    <h4>Below is the Python code for the AI guessing game using Depth First Search Algorithm:</h4>
    <pre><code>
<span class="comment"># Depth First Search Algorithm</span>
<span class="variable">def</span> <span class="variable">guessgame2</span>():
    <span class="variable">print</span>(<span class="string">"wellcome to ai guess game, guess a number from 1 to 100"</span>)
    <span class="variable">low</span> = <span class="number">1</span>
    <span class="variable">high</span> = <span class="number">100</span>
    <span class="variable">attempts</span> = <span class="number">0</span>
    
    <span class="variable">stack</span> = <span class="variable">list</span>(<span class="variable">range</span>(<span class="variable">low</span>, <span class="variable">high</span> + <span class="number">1</span>))
    
    <span class="variable">while</span> <span class="variable">stack</span>:
        <span class="variable">guess</span> = <span class="variable">stack</span>.<span class="variable">pop</span>()
        <span class="variable">attempts</span> += <span class="number">1</span>
        <span class="variable">print</span>(f<span class="string">"ai guess is {guess}"</span>)
        <span class="variable">feedback</span> = <span class="variable">input</span>(<span class="string">"select one of the following c,h,l: "</span>).<span class="variable">lower</span>()
        
        <span class="variable">if</span> <span class="variable">feedback</span> == <span class="string"> 'c'</span>:
            <span class="variable">print</span>(f<span class="string">"ai guessed correctly in {attempts} attempts"</span>)
            <span class="variable">return</span>
        <span class="variable">elif</span> <span class="variable">feedback</span> == <span class="string"> 'h'</span>:
            <span class="variable">print</span>(<span class="string">"too high"</span>)
        <span class="variable">elif</span> <span class="variable">feedback</span> == <span class="string"> 'l'</span>:
            <span class="variable">print</span>(<span class="string">"too low"</span>)
        
        <span class="variable">else</span>:
            <span class="variable">print</span>(<span class="string">"invalid choice"</span>)
        
<span class="variable">guessgame2</span>()
    </code></pre>
    <p>In this code, if the correct number was 10, the AI would have started guessing from 100 and sequentially decreased the guesses by 1 each time. It would have needed 90 attempts to correctly guess the number 10. This code uses stack logic, where numbers are pushed onto the stack in descending order and then popped from the top of the stack for guessing. Because a stack follows LIFO (Last In, First Out) order, the AI would first guess the highest number and work its way down to the correct number.</p>

    <!-- Code Block 4 -->
    <h3>Below is the Python code for the AI guessing game using Adaptive Search Algorithm:</h3>
    <pre><code>
<span class="comment"># Adaptive Search Algorithm</span>
<span class="variable">def</span> <span class="variable">guessgame3</span>():
    <span class="variable">print</span>(<span class="string">"welcome to the guess game using adaptive search"</span>)
    
    <span class="variable">low</span> = <span class="number">1</span>
    <span class="variable">high</span> = <span class="number">100</span>
    <span class="variable">attempts</span> = <span class="number">0</span>
    
    <span class="variable">prev_guess</span> = <span class="keyword">None</span>
    <span class="variable">prev_feedback</span> = <span class="keyword">None</span>
    
    <span class="variable">while</span> <span class="variable">low</span> <= <span class="variable">high</span>:
        
        <span class="variable">if</span> <span class="variable">prev_guess</span> <span class="variable">is</span> <span class="keyword">None</span>:
            <span class="variable">guess</span> = (<span class="variable">low</span> + <span class="variable">high</span>) // <span class="number">2</span>
        <span class="variable">elif</span> <span class="variable">prev_feedback</span> == <span class="string"> 'h'</span>:
            <span class="variable">guess</span> = <span class="variable">prev_guess</span> - (<span class="variable">prev_guess</span> - <span class="variable">low</span>) // <span class="number">2</span>
        <span class="variable">elif</span> <span class="variable">prev_feedback</span> == <span class="string"> 'l'</span>:
            <span class="variable">guess</span> = <span class="variable">prev_guess</span> + (<span class="variable">high</span> - <span class="variable">prev_guess</span>) // <span class="number">2</span>
        <span class="variable">else</span>:
            <span class="variable">guess</span> = (<span class="variable">low</span> + <span class="variable">high</span>) // <span class="number">2</span>
        
        <span class="variable">print</span>(f<span class="string">"ai guess: {guess}"</span>)
        <span class="variable">feedback</span> = <span class="variable">input</span>(<span class="string">"enter feedback c,h,l: "</span>).<span class="variable">lower</span>()
        
        <span class="variable">if</span> <span class="variable">feedback</span> == <span class="string"> 'c'</span>:
            <span class="variable">print</span>(f<span class="string">"ai guessed correctly in {attempts} attempt(s)"</span>)
            <span class="variable">return</span>
        
        <span class="variable">elif</span> <span class="variable">feedback</span> == <span class="string"> 'h'</span>:
            <span class="variable">print</span>(<span class="string">"too high"</span>)
            <span class="variable">high</span> = <span class="variable">guess</span> - <span class="number">1</span>
            
        <span class="variable">elif</span> <span class="variable">feedback</span> == <span class="string"> 'l'</span>:
            <span class="variable">print</span>(<span class="string">"too low"</span>)
            <span class="variable">low</span> = <span class="variable">guess</span> + <span class="number">1</span>
        
        <span class="variable">else</span>:
            <span class="variable">print</span>(<span class="string">"invalid feedback please enter one of 'c', 'h', or 'l'"</span>)
            <span class="variable">continue</span>  
        
        <span class="variable">prev_guess</span> = <span class="variable">guess</span>
        <span class="variable">prev_feedback</span> = <span class="variable">feedback</span>
        <span class="variable">attempts</span> += <span class="number">1</span>
    
    <span class="variable">print</span>(<span class="string">"something's wrong"</span>)

<span class="variable">guessgame3</span>()
    </code></pre>
    <p>Adaptive Search: This approach produces results similar to a binary search, but instead of simply halving the search range each time, it adjusts its guesses based on previous guesses and feedback. The algorithm uses the information from earlier guesses to adaptively adjust its future guesses, making it more flexible and potentially faster in converging to the correct number. The correct number that I had chosen was 10. It took 4 attempts for the AI to guess it correctly.</p>
</body>
</html>
