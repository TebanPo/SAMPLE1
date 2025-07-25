<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teban teaches Java</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Orbitron', monospace;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
            color: #00ff41;
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        
        .star {
            position: absolute;
            background: #fff;
            border-radius: 50%;
            animation: twinkle 2s infinite;
        }
        
        @keyframes twinkle {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }
        
        .container {
            position: relative;
            z-index: 2;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px;
            border: 2px solid #00ff41;
            border-radius: 10px;
            background: rgba(0, 255, 65, 0.1);
            box-shadow: 0 0 20px rgba(0, 255, 65, 0.3);
        }
        
        h1 {
            font-size: 3rem;
            font-weight: 900;
            text-shadow: 0 0 10px #00ff41;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 1.2rem;
            color: #ff6b35;
            text-shadow: 0 0 5px #ff6b35;
        }
        
        nav {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .nav-btn {
            padding: 15px 30px;
            background: linear-gradient(45deg, #ff6b35, #f7931e);
            border: none;
            border-radius: 25px;
            color: #000;
            font-family: 'Orbitron', monospace;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 107, 53, 0.4);
        }
        
        .nav-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(255, 107, 53, 0.6);
        }
        
        .nav-btn.active {
            background: linear-gradient(45deg, #00ff41, #00cc33);
            color: #000;
        }
        
        .page {
            display: none;
        }
        
        .page.active {
            display: block;
        }
        
        .tutorial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }
        
        .tutorial-card {
            background: rgba(0, 255, 65, 0.1);
            border: 2px solid #00ff41;
            border-radius: 15px;
            padding: 25px;
            transition: all 0.3s ease;
        }
        
        .tutorial-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 255, 65, 0.3);
        }
        
        .tutorial-card h3 {
            color: #ff6b35;
            font-size: 1.5rem;
            margin-bottom: 15px;
            text-shadow: 0 0 5px #ff6b35;
        }
        
        .code-block {
            background: #000;
            border: 1px solid #00ff41;
            border-radius: 8px;
            padding: 15px;
            margin: 15px 0;
            font-family: 'Courier New', monospace;
            color: #00ff41;
            overflow-x: auto;
        }
        
        .keyword {
            color: #ff6b35;
        }
        
        .string {
            color: #ffff00;
        }
        
        .comment {
            color: #888;
        }
        
        /* Game Styles */
        .game-container {
            position: relative;
            width: 100%;
            height: 600px;
            background: linear-gradient(180deg, #000428 0%, #004e92 100%);
            border: 3px solid #00ff41;
            border-radius: 15px;
            overflow: hidden;
            margin-bottom: 20px;
        }
        
        .game-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
        
        .spaceship {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 60px;
            background: #ff6b35;
            clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
            transition: left 0.1s ease;
        }
        
        .enemy-word {
            position: absolute;
            background: rgba(255, 107, 53, 0.9);
            color: #000;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: 700;
            border: 2px solid #ff6b35;
            animation: fall 8s linear;
        }
        
        @keyframes fall {
            from { top: -50px; }
            to { top: 600px; }
        }
        
        .laser {
            position: absolute;
            width: 3px;
            height: 20px;
            background: #00ff41;
            box-shadow: 0 0 10px #00ff41;
            animation: shoot 1s linear;
        }
        
        @keyframes shoot {
            from { bottom: 80px; }
            to { bottom: 600px; }
        }
        
        .game-ui {
            position: absolute;
            top: 20px;
            left: 20px;
            right: 20px;
            display: flex;
            justify-content: space-between;
            color: #00ff41;
            font-weight: 700;
            z-index: 10;
        }
        
        .type-input {
            position: absolute;
            bottom: 100px;
            left: 50%;
            transform: translateX(-50%);
            padding: 15px;
            background: rgba(0, 0, 0, 0.8);
            border: 2px solid #00ff41;
            border-radius: 25px;
            color: #00ff41;
            font-family: 'Orbitron', monospace;
            font-size: 1.2rem;
            text-align: center;
            outline: none;
            width: 300px;
        }
        
        .game-over {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0, 0, 0, 0.9);
            border: 3px solid #ff6b35;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            color: #ff6b35;
            display: none;
        }
        
        .restart-btn {
            padding: 10px 20px;
            background: #00ff41;
            border: none;
            border-radius: 20px;
            color: #000;
            font-family: 'Orbitron', monospace;
            font-weight: 700;
            cursor: pointer;
            margin-top: 15px;
        }
        
        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .nav-btn { padding: 10px 20px; font-size: 0.9rem; }
            .tutorial-grid { grid-template-columns: 1fr; }
            .game-container { height: 500px; }
            .type-input { width: 250px; }
        }
    </style>
</head>
<body>
    <div class="stars" id="stars"></div>
    
    <div class="container">
        <header>
            <h1>🚀 TEBAN TEACHES JAVA 🚀</h1>
            <p class="subtitle">Master Java Programming in Retro Style</p>
        </header>
        
        <nav>
            <button class="nav-btn active" onclick="showPage('home')">Home</button>
            <button class="nav-btn" onclick="showPage('game')">Space Impact Game</button>
        </nav>
        
        <div id="home" class="page active">
            <div class="tutorial-grid">
                <div class="tutorial-card">
                    <h3>📊 Data Types</h3>
                    <p>Java has several built-in data types to store different kinds of information:</p>
                    <div class="code-block">
<span class="comment">// Primitive data types</span>
<span class="keyword">int</span> age = <span class="string">25</span>;
<span class="keyword">double</span> price = <span class="string">19.99</span>;
<span class="keyword">boolean</span> isActive = <span class="keyword">true</span>;
<span class="keyword">char</span> grade = <span class="string">'A'</span>;
<span class="keyword">String</span> name = <span class="string">"Teban"</span>;
                    </div>
                    <p>Use <span class="keyword">int</span> for whole numbers, <span class="keyword">double</span> for decimals, <span class="keyword">boolean</span> for true/false, and <span class="keyword">String</span> for text.</p>
                </div>
                
                <div class="tutorial-card">
                    <h3>🔄 Control Statements</h3>
                    <p>Control the flow of your program with if statements and loops:</p>
                    <div class="code-block">
<span class="comment">// If statement</span>
<span class="keyword">if</span> (score >= <span class="string">90</span>) {
    System.out.println(<span class="string">"Excellent!"</span>);
} <span class="keyword">else if</span> (score >= <span class="string">70</span>) {
    System.out.println(<span class="string">"Good job!"</span>);
} <span class="keyword">else</span> {
    System.out.println(<span class="string">"Keep trying!"</span>);
}

<span class="comment">// For loop</span>
<span class="keyword">for</span> (<span class="keyword">int</span> i = <span class="string">0</span>; i < <span class="string">5</span>; i++) {
    System.out.println(<span class="string">"Count: "</span> + i);
}
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🏗️ Methods</h3>
                    <p>Methods are reusable blocks of code that perform specific tasks:</p>
                    <div class="code-block">
<span class="comment">// Method definition</span>
<span class="keyword">public static int</span> addNumbers(<span class="keyword">int</span> a, <span class="keyword">int</span> b) {
    <span class="keyword">return</span> a + b;
}

<span class="comment">// Method call</span>
<span class="keyword">int</span> result = addNumbers(<span class="string">5</span>, <span class="string">3</span>);
System.out.println(<span class="string">"Result: "</span> + result);
                    </div>
                    <p>Methods help organize code and avoid repetition. They can take parameters and return values.</p>
                </div>
                
                <div class="tutorial-card">
                    <h3>📚 Arrays</h3>
                    <p>Arrays store multiple values of the same type:</p>
                    <div class="code-block">
<span class="comment">// Array declaration and initialization</span>
<span class="keyword">int</span>[] numbers = {<span class="string">1</span>, <span class="string">2</span>, <span class="string">3</span>, <span class="string">4</span>, <span class="string">5</span>};
<span class="keyword">String</span>[] names = <span class="keyword">new String</span>[<span class="string">3</span>];

<span class="comment">// Accessing array elements</span>
System.out.println(numbers[<span class="string">0</span>]); <span class="comment">// Prints 1</span>
names[<span class="string">0</span>] = <span class="string">"Alice"</span>;

<span class="comment">// Array length</span>
System.out.println(<span class="string">"Array size: "</span> + numbers.length);
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🎯 Classes and Objects</h3>
                    <p>Classes are blueprints for creating objects:</p>
                    <div class="code-block">
<span class="comment">// Class definition</span>
<span class="keyword">class</span> Player {
    <span class="keyword">String</span> name;
    <span class="keyword">int</span> score;
    
    <span class="comment">// Constructor</span>
    <span class="keyword">public</span> Player(<span class="keyword">String</span> playerName) {
        <span class="keyword">this</span>.name = playerName;
        <span class="keyword">this</span>.score = <span class="string">0</span>;
    }
    
    <span class="comment">// Method</span>
    <span class="keyword">public void</span> increaseScore(<span class="keyword">int</span> points) {
        score += points;
    }
}

<span class="comment">// Creating objects</span>
Player player1 = <span class="keyword">new</span> Player(<span class="string">"Teban"</span>);
player1.increaseScore(<span class="string">100</span>);
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>⚠️ Exception Handling</h3>
                    <p>Handle errors gracefully with try-catch blocks:</p>
                    <div class="code-block">
<span class="keyword">try</span> {
    <span class="keyword">int</span> result = <span class="string">10</span> / <span class="string">0</span>; <span class="comment">// This will cause an error</span>
    System.out.println(result);
} <span class="keyword">catch</span> (ArithmeticException e) {
    System.out.println(<span class="string">"Error: Cannot divide by zero!"</span>);
} <span class="keyword">finally</span> {
    System.out.println(<span class="string">"This always executes"</span>);
}
                    </div>
                    <p>Use try-catch to prevent your program from crashing when errors occur.</p>
                </div>
                
                <div class="tutorial-card">
                    <h3>🔧 Constructors</h3>
                    <p>Constructors initialize objects when they are created:</p>
                    <div class="code-block">
<span class="keyword">class</span> Car {
    <span class="keyword">String</span> brand;
    <span class="keyword">int</span> year;
    
    <span class="comment">// Default constructor</span>
    <span class="keyword">public</span> Car() {
        brand = <span class="string">"Unknown"</span>;
        year = <span class="string">2023</span>;
    }
    
    <span class="comment">// Parameterized constructor</span>
    <span class="keyword">public</span> Car(<span class="keyword">String</span> b, <span class="keyword">int</span> y) {
        brand = b;
        year = y;
    }
}

Car car1 = <span class="keyword">new</span> Car();
Car car2 = <span class="keyword">new</span> Car(<span class="string">"Toyota"</span>, <span class="string">2022</span>);
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🔒 Access Modifiers</h3>
                    <p>Control access to classes, methods, and variables:</p>
                    <div class="code-block">
<span class="keyword">class</span> Example {
    <span class="keyword">public</span> <span class="keyword">String</span> publicVar;    <span class="comment">// Accessible everywhere</span>
    <span class="keyword">private</span> <span class="keyword">int</span> privateVar;     <span class="comment">// Only within this class</span>
    <span class="keyword">protected</span> <span class="keyword">double</span> protectedVar; <span class="comment">// Within package/subclasses</span>
    <span class="keyword">String</span> defaultVar;           <span class="comment">// Within package only</span>
    
    <span class="keyword">public void</span> publicMethod() {
        <span class="comment">// Anyone can call this</span>
    }
    
    <span class="keyword">private void</span> privateMethod() {
        <span class="comment">// Only this class can call</span>
    }
}
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🏗️ Inheritance</h3>
                    <p>Create new classes based on existing ones:</p>
                    <div class="code-block">
<span class="comment">// Parent class</span>
<span class="keyword">class</span> Animal {
    <span class="keyword">String</span> name;
    
    <span class="keyword">public void</span> eat() {
        System.out.println(name + <span class="string">" is eating"</span>);
    }
}

<span class="comment">// Child class</span>
<span class="keyword">class</span> Dog <span class="keyword">extends</span> Animal {
    <span class="keyword">public void</span> bark() {
        System.out.println(name + <span class="string">" is barking"</span>);
    }
}

Dog myDog = <span class="keyword">new</span> Dog();
myDog.name = <span class="string">"Buddy"</span>;
myDog.eat();  <span class="comment">// Inherited method</span>
myDog.bark(); <span class="comment">// Own method</span>
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🎭 Polymorphism</h3>
                    <p>One interface, multiple implementations:</p>
                    <div class="code-block">
<span class="keyword">class</span> Shape {
    <span class="keyword">public void</span> draw() {
        System.out.println(<span class="string">"Drawing a shape"</span>);
    }
}

<span class="keyword">class</span> Circle <span class="keyword">extends</span> Shape {
    <span class="keyword">@Override</span>
    <span class="keyword">public void</span> draw() {
        System.out.println(<span class="string">"Drawing a circle"</span>);
    }
}

<span class="keyword">class</span> Rectangle <span class="keyword">extends</span> Shape {
    <span class="keyword">@Override</span>
    <span class="keyword">public void</span> draw() {
        System.out.println(<span class="string">"Drawing a rectangle"</span>);
    }
}

Shape[] shapes = {<span class="keyword">new</span> Circle(), <span class="keyword">new</span> Rectangle()};
<span class="keyword">for</span>(Shape s : shapes) {
    s.draw(); <span class="comment">// Calls appropriate method</span>
}
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>📋 Interfaces</h3>
                    <p>Define contracts that classes must implement:</p>
                    <div class="code-block">
<span class="keyword">interface</span> Drawable {
    <span class="keyword">void</span> draw();
    <span class="keyword">void</span> resize(<span class="keyword">int</span> size);
}

<span class="keyword">class</span> Button <span class="keyword">implements</span> Drawable {
    <span class="keyword">public void</span> draw() {
        System.out.println(<span class="string">"Drawing button"</span>);
    }
    
    <span class="keyword">public void</span> resize(<span class="keyword">int</span> size) {
        System.out.println(<span class="string">"Resizing to "</span> + size);
    }
}

Drawable btn = <span class="keyword">new</span> Button();
btn.draw();
btn.resize(<span class="string">100</span>);
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>📦 Packages</h3>
                    <p>Organize related classes and interfaces:</p>
                    <div class="code-block">
<span class="comment">// At the top of your file</span>
<span class="keyword">package</span> com.teban.game;

<span class="comment">// Import classes from other packages</span>
<span class="keyword">import</span> java.util.Scanner;
<span class="keyword">import</span> java.util.ArrayList;
<span class="keyword">import</span> java.util.*;  <span class="comment">// Import all from util</span>

<span class="keyword">public class</span> GameEngine {
    <span class="comment">// Your class code here</span>
}
                    </div>
                    <p>Packages help organize code and avoid naming conflicts.</p>
                </div>
                
                <div class="tutorial-card">
                    <h3>🔄 While Loops</h3>
                    <p>Repeat code while a condition is true:</p>
                    <div class="code-block">
<span class="comment">// While loop</span>
<span class="keyword">int</span> count = <span class="string">0</span>;
<span class="keyword">while</span> (count < <span class="string">5</span>) {
    System.out.println(<span class="string">"Count: "</span> + count);
    count++;
}

<span class="comment">// Do-while loop (executes at least once)</span>
<span class="keyword">int</span> num = <span class="string">10</span>;
<span class="keyword">do</span> {
    System.out.println(<span class="string">"Number: "</span> + num);
    num--;
} <span class="keyword">while</span> (num > <span class="string">5</span>);
                    </div>
                    <p>Use while when you don't know exactly how many times to loop.</p>
                </div>
                
                <div class="tutorial-card">
                    <h3>🔀 Switch Statements</h3>
                    <p>Choose between multiple options efficiently:</p>
                    <div class="code-block">
<span class="keyword">int</span> day = <span class="string">3</span>;
<span class="keyword">String</span> dayName;

<span class="keyword">switch</span> (day) {
    <span class="keyword">case</span> <span class="string">1</span>:
        dayName = <span class="string">"Monday"</span>;
        <span class="keyword">break</span>;
    <span class="keyword">case</span> <span class="string">2</span>:
        dayName = <span class="string">"Tuesday"</span>;
        <span class="keyword">break</span>;
    <span class="keyword">case</span> <span class="string">3</span>:
        dayName = <span class="string">"Wednesday"</span>;
        <span class="keyword">break</span>;
    <span class="keyword">default</span>:
        dayName = <span class="string">"Unknown"</span>;
}

System.out.println(<span class="string">"Today is "</span> + dayName);
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>📝 String Methods</h3>
                    <p>Powerful methods to manipulate text:</p>
                    <div class="code-block">
<span class="keyword">String</span> text = <span class="string">"Hello World"</span>;

<span class="comment">// Common string methods</span>
System.out.println(text.length());        <span class="comment">// 11</span>
System.out.println(text.toUpperCase());   <span class="comment">// HELLO WORLD</span>
System.out.println(text.toLowerCase());   <span class="comment">// hello world</span>
System.out.println(text.charAt(<span class="string">0</span>));       <span class="comment">// H</span>
System.out.println(text.substring(<span class="string">0</span>, <span class="string">5</span>)); <span class="comment">// Hello</span>
System.out.println(text.contains(<span class="string">"World"</span>)); <span class="comment">// true</span>
System.out.println(text.replace(<span class="string">"World"</span>, <span class="string">"Java"</span>)); <span class="comment">// Hello Java</span>

<span class="keyword">String</span>[] words = text.split(<span class="string">" "</span>);
<span class="comment">// words = ["Hello", "World"]</span>
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>📊 ArrayList</h3>
                    <p>Dynamic arrays that can grow and shrink:</p>
                    <div class="code-block">
<span class="keyword">import</span> java.util.ArrayList;

<span class="comment">// Create ArrayList</span>
ArrayList&lt;<span class="keyword">String</span>&gt; names = <span class="keyword">new</span> ArrayList&lt;&gt;();

<span class="comment">// Add elements</span>
names.add(<span class="string">"Alice"</span>);
names.add(<span class="string">"Bob"</span>);
names.add(<span class="string">"Charlie"</span>);

<span class="comment">// Access and modify</span>
System.out.println(names.get(<span class="string">0</span>));    <span class="comment">// Alice</span>
names.set(<span class="string">1</span>, <span class="string">"Bobby"</span>);           <span class="comment">// Change Bob to Bobby</span>
names.remove(<span class="string">2</span>);                  <span class="comment">// Remove Charlie</span>

<span class="comment">// Loop through</span>
<span class="keyword">for</span>(<span class="keyword">String</span> name : names) {
    System.out.println(name);
}
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🗂️ HashMap</h3>
                    <p>Store key-value pairs for fast lookups:</p>
                    <div class="code-block">
<span class="keyword">import</span> java.util.HashMap;

<span class="comment">// Create HashMap</span>
HashMap&lt;<span class="keyword">String</span>, <span class="keyword">Integer</span>&gt; scores = <span class="keyword">new</span> HashMap&lt;&gt;();

<span class="comment">// Add key-value pairs</span>
scores.put(<span class="string">"Alice"</span>, <span class="string">95</span>);
scores.put(<span class="string">"Bob"</span>, <span class="string">87</span>);
scores.put(<span class="string">"Charlie"</span>, <span class="string">92</span>);

<span class="comment">// Get values</span>
<span class="keyword">int</span> aliceScore = scores.get(<span class="string">"Alice"</span>);
System.out.println(<span class="string">"Alice's score: "</span> + aliceScore);

<span class="comment">// Check if key exists</span>
<span class="keyword">if</span>(scores.containsKey(<span class="string">"Bob"</span>)) {
    System.out.println(<span class="string">"Bob's score found!"</span>);
}

<span class="comment">// Loop through all entries</span>
<span class="keyword">for</span>(<span class="keyword">String</span> name : scores.keySet()) {
    System.out.println(name + <span class="string">": "</span> + scores.get(name));
}
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>📥 Input/Output</h3>
                    <p>Read user input and display output:</p>
                    <div class="code-block">
<span class="keyword">import</span> java.util.Scanner;

<span class="comment">// Create Scanner for input</span>
Scanner scanner = <span class="keyword">new</span> Scanner(System.in);

<span class="comment">// Read different types of input</span>
System.out.print(<span class="string">"Enter your name: "</span>);
<span class="keyword">String</span> name = scanner.nextLine();

System.out.print(<span class="string">"Enter your age: "</span>);
<span class="keyword">int</span> age = scanner.nextInt();

System.out.print(<span class="string">"Enter your height: "</span>);
<span class="keyword">double</span> height = scanner.nextDouble();

<span class="comment">// Output</span>
System.out.println(<span class="string">"Hello "</span> + name);
System.out.printf(<span class="string">"You are %d years old and %.2f tall%n"</span>, age, height);

scanner.close(); <span class="comment">// Always close Scanner</span>
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🔢 Math Operations</h3>
                    <p>Perform mathematical calculations:</p>
                    <div class="code-block">
<span class="comment">// Basic arithmetic</span>
<span class="keyword">int</span> a = <span class="string">10</span>, b = <span class="string">3</span>;
System.out.println(a + b);  <span class="comment">// Addition: 13</span>
System.out.println(a - b);  <span class="comment">// Subtraction: 7</span>
System.out.println(a * b);  <span class="comment">// Multiplication: 30</span>
System.out.println(a / b);  <span class="comment">// Division: 3</span>
System.out.println(a % b);  <span class="comment">// Modulus: 1</span>

<span class="comment">// Math class methods</span>
System.out.println(Math.max(<span class="string">10</span>, <span class="string">20</span>));     <span class="comment">// 20</span>
System.out.println(Math.min(<span class="string">10</span>, <span class="string">20</span>));     <span class="comment">// 10</span>
System.out.println(Math.abs(<span class="string">-5</span>));        <span class="comment">// 5</span>
System.out.println(Math.sqrt(<span class="string">16</span>));       <span class="comment">// 4.0</span>
System.out.println(Math.pow(<span class="string">2</span>, <span class="string">3</span>));      <span class="comment">// 8.0</span>
System.out.println(Math.random());      <span class="comment">// Random 0.0-1.0</span>
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>📅 Date and Time</h3>
                    <p>Work with dates and times in Java:</p>
                    <div class="code-block">
<span class="keyword">import</span> java.time.LocalDate;
<span class="keyword">import</span> java.time.LocalTime;
<span class="keyword">import</span> java.time.LocalDateTime;

<span class="comment">// Current date and time</span>
LocalDate today = LocalDate.now();
LocalTime now = LocalTime.now();
LocalDateTime dateTime = LocalDateTime.now();

System.out.println(<span class="string">"Today: "</span> + today);
System.out.println(<span class="string">"Now: "</span> + now);

<span class="comment">// Create specific dates</span>
LocalDate birthday = LocalDate.of(<span class="string">1990</span>, <span class="string">5</span>, <span class="string">15</span>);
System.out.println(<span class="string">"Birthday: "</span> + birthday);

<span class="comment">// Date calculations</span>
LocalDate nextWeek = today.plusDays(<span class="string">7</span>);
LocalDate lastMonth = today.minusMonths(<span class="string">1</span>);
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>📁 File Handling</h3>
                    <p>Read from and write to files:</p>
                    <div class="code-block">
<span class="keyword">import</span> java.io.*;
<span class="keyword">import</span> java.util.Scanner;

<span class="comment">// Writing to a file</span>
<span class="keyword">try</span> {
    FileWriter writer = <span class="keyword">new</span> FileWriter(<span class="string">"data.txt"</span>);
    writer.write(<span class="string">"Hello, File!"</span>);
    writer.close();
} <span class="keyword">catch</span>(IOException e) {
    System.out.println(<span class="string">"Error writing file"</span>);
}

<span class="comment">// Reading from a file</span>
<span class="keyword">try</span> {
    File file = <span class="keyword">new</span> File(<span class="string">"data.txt"</span>);
    Scanner reader = <span class="keyword">new</span> Scanner(file);
    <span class="keyword">while</span>(reader.hasNextLine()) {
        System.out.println(reader.nextLine());
    }
    reader.close();
} <span class="keyword">catch</span>(FileNotFoundException e) {
    System.out.println(<span class="string">"File not found"</span>);
}
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🧵 Static vs Instance</h3>
                    <p>Understand the difference between static and instance members:</p>
                    <div class="code-block">
<span class="keyword">class</span> Counter {
    <span class="keyword">static int</span> totalCount = <span class="string">0</span>;  <span class="comment">// Shared by all instances</span>
    <span class="keyword">int</span> instanceCount = <span class="string">0</span>;     <span class="comment">// Unique to each instance</span>
    
    <span class="keyword">public</span> Counter() {
        totalCount++;      <span class="comment">// Increment shared counter</span>
        instanceCount++;   <span class="comment">// Increment instance counter</span>
    }
    
    <span class="keyword">static void</span> showTotal() {
        System.out.println(<span class="string">"Total objects: "</span> + totalCount);
        <span class="comment">// Can't access instanceCount here!</span>
    }
    
    <span class="keyword">void</span> showInstance() {
        System.out.println(<span class="string">"Instance count: "</span> + instanceCount);
        System.out.println(<span class="string">"Total count: "</span> + totalCount);
    }
}

Counter c1 = <span class="keyword">new</span> Counter();
Counter c2 = <span class="keyword">new</span> Counter();
Counter.showTotal(); <span class="comment">// Call static method</span>
                    </div>
                </div>
                
                <div class="tutorial-card">
                    <h3>🔄 Enhanced For Loop</h3>
                    <p>Simplified way to iterate through collections:</p>
                    <div class="code-block">
<span class="comment">// Traditional for loop</span>
<span class="keyword">int</span>[] numbers = {<span class="string">1</span>, <span class="string">2</span>, <span class="string">3</span>, <span class="string">4</span>, <span class="string">5</span>};
<span class="keyword">for</span>(<span class="keyword">int</span> i = <span class="string">0</span>; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}

<span class="comment">// Enhanced for loop (for-each)</span>
<span class="keyword">for</span>(<span class="keyword">int</span> num : numbers) {
    System.out.println(num);
}

<span class="comment">// Works with collections too</span>
ArrayList&lt;<span class="keyword">String</span>&gt; names = <span class="keyword">new</span> ArrayList&lt;&gt;();
names.add(<span class="string">"Alice"</span>);
names.add(<span class="string">"Bob"</span>);

<span class="keyword">for</span>(<span class="keyword">String</span> name : names) {
    System.out.println(<span class="string">"Hello, "</span> + name);
}
                    </div>
                    <p>Enhanced for loops are cleaner and less error-prone for simple iteration.</p>
                </div>
            </div>
        </div>
        
        <div id="game" class="page">
            <h2 style="text-align: center; margin-bottom: 20px; color: #ff6b35;">🚀 SPACE IMPACT TYPING GAME 🚀</h2>
            <p style="text-align: center; margin-bottom: 20px;">Type the Java keywords to destroy enemy ships! Improve your typing speed while learning Java!</p>
            
            <div class="game-container" id="gameContainer">
                <div class="game-ui">
                    <div>Score: <span id="score">0</span></div>
                    <div>Lives: <span id="lives">3</span></div>
                    <div>Level: <span id="level">1</span></div>
                </div>
                
                <div class="spaceship" id="spaceship"></div>
                <input type="text" class="type-input" id="typeInput" placeholder="Type the words to shoot!" autocomplete="off">
                
                <div class="game-over" id="gameOver">
                    <h3>GAME OVER</h3>
                    <p>Final Score: <span id="finalScore">0</span></p>
                    <button class="restart-btn" onclick="restartGame()">Play Again</button>
                </div>
            </div>
            
            <div style="text-align: center; margin-top: 20px;">
                <button class="nav-btn" onclick="startGame()" id="startBtn">Start Game</button>
                <button class="nav-btn" onclick="pauseGame()" id="pauseBtn" style="display: none;">Pause</button>
            </div>
        </div>
    </div>

    <script>
        // Create animated stars
        function createStars() {
            const starsContainer = document.getElementById('stars');
            for (let i = 0; i < 100; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.width = Math.random() * 3 + 1 + 'px';
                star.style.height = star.style.width;
                star.style.animationDelay = Math.random() * 2 + 's';
                starsContainer.appendChild(star);
            }
        }
        
        // Page navigation
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            
            document.getElementById(pageId).classList.add('active');
            event.target.classList.add('active');
        }
        
        // Game variables
        let gameActive = false;
        let score = 0;
        let lives = 3;
        let level = 1;
        let enemies = [];
        let gameInterval;
        let spawnInterval;
        
        const javaKeywords = [
            'class', 'public', 'static', 'void', 'int', 'String', 'boolean', 'double',
            'if', 'else', 'for', 'while', 'return', 'new', 'this', 'super',
            'try', 'catch', 'finally', 'throw', 'import', 'package', 'extends',
            'implements', 'interface', 'abstract', 'final', 'private', 'protected'
        ];
        
        function startGame() {
            gameActive = true;
            score = 0;
            lives = 3;
            level = 1;
            enemies = [];
            
            updateUI();
            document.getElementById('gameOver').style.display = 'none';
            document.getElementById('startBtn').style.display = 'none';
            document.getElementById('pauseBtn').style.display = 'inline-block';
            document.getElementById('typeInput').focus();
            
            gameInterval = setInterval(gameLoop, 50);
            spawnInterval = setInterval(spawnEnemy, 2000 - (level * 100));
        }
        
        function pauseGame() {
            gameActive = false;
            clearInterval(gameInterval);
            clearInterval(spawnInterval);
            document.getElementById('startBtn').style.display = 'inline-block';
            document.getElementById('pauseBtn').style.display = 'none';
        }
        
        function restartGame() {
            document.querySelectorAll('.enemy-word').forEach(enemy => enemy.remove());
            document.querySelectorAll('.laser').forEach(laser => laser.remove());
            startGame();
        }
        
        function spawnEnemy() {
            if (!gameActive) return;
            
            const enemy = document.createElement('div');
            enemy.className = 'enemy-word';
            enemy.textContent = javaKeywords[Math.floor(Math.random() * javaKeywords.length)];
            enemy.style.left = Math.random() * (document.getElementById('gameContainer').offsetWidth - 100) + 'px';
            enemy.style.top = '-50px';
            
            document.getElementById('gameContainer').appendChild(enemy);
            enemies.push({
                element: enemy,
                word: enemy.textContent,
                y: -50
            });
        }
        
        function gameLoop() {
            if (!gameActive) return;
            
            // Move enemies down
            enemies.forEach((enemy, index) => {
                enemy.y += 2 + level;
                enemy.element.style.top = enemy.y + 'px';
                
                // Check if enemy reached bottom
                if (enemy.y > 600) {
                    enemy.element.remove();
                    enemies.splice(index, 1);
                    lives--;
                    updateUI();
                    
                    if (lives <= 0) {
                        gameOver();
                    }
                }
            });
        }
        
        function shootLaser(targetX) {
            const laser = document.createElement('div');
            laser.className = 'laser';
            laser.style.left = targetX + 'px';
            laser.style.bottom = '80px';
            document.getElementById('gameContainer').appendChild(laser);
            
            setTimeout(() => laser.remove(), 1000);
        }
        
        function updateUI() {
            document.getElementById('score').textContent = score;
            document.getElementById('lives').textContent = lives;
            document.getElementById('level').textContent = level;
        }
        
        function gameOver() {
            gameActive = false;
            clearInterval(gameInterval);
            clearInterval(spawnInterval);
            
            document.getElementById('finalScore').textContent = score;
            document.getElementById('gameOver').style.display = 'block';
            document.getElementById('startBtn').style.display = 'inline-block';
            document.getElementById('pauseBtn').style.display = 'none';
        }
        
        // Handle typing input
        document.getElementById('typeInput').addEventListener('input', function(e) {
            if (!gameActive) return;
            
            const typedWord = e.target.value.toLowerCase().trim();
            
            // Check if typed word matches any enemy
            enemies.forEach((enemy, index) => {
                if (enemy.word.toLowerCase() === typedWord) {
                    // Hit! Remove enemy and increase score
                    const enemyRect = enemy.element.getBoundingClientRect();
                    const containerRect = document.getElementById('gameContainer').getBoundingClientRect();
                    const targetX = enemyRect.left - containerRect.left + enemyRect.width / 2;
                    
                    shootLaser(targetX);
                    enemy.element.remove();
                    enemies.splice(index, 1);
                    
                    score += 10 * level;
                    e.target.value = '';
                    
                    // Level up every 200 points
                    if (score > 0 && score % 200 === 0) {
                        level++;
                        clearInterval(spawnInterval);
                        spawnInterval = setInterval(spawnEnemy, Math.max(800, 2000 - (level * 100)));
                    }
                    
                    updateUI();
                }
            });
        });
        
        // Initialize
        createStars();
        
        // Focus input when game page is shown
        document.addEventListener('click', function(e) {
            if (e.target.textContent === 'Space Impact Game') {
                setTimeout(() => {
                    document.getElementById('typeInput').focus();
                }, 100);
            }
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9649733f3396bc51',t:'MTc1MzQyMzM2NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
