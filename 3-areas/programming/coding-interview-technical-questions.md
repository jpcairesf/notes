+++
date = 2024-03-09T07:50:00-00:00
+++

# Walking Through A Problem

1. **Listen**: pay attention very closely
2. **Example**: debug your example and find special cases
3. **Brute force**: state a naive algorithm and then optimize it
4. **Optimize**: BUD Optimization or look (or ask) for unused info, make time vs. space tradeoff
5. **Walk Through**: make sure you understand each detail of your optimal solution before coding
6. **Implement**: modularize your code from the beginning and refactor
7. **Test**: code review, look for hot spots and special and edge cases

### Technique #1: BUD Optimization

Acronym for **B**ottlenecks, **U**nnecessary work and **D**uplicated work. Bottleneck is a part of your algorithm that slows down the overral runtime. Common ways this occurs are having one-time work that slows down your algorithm and having a chunk of work that is done repeatedly (like searching). Then look for unnecessary and duplicated work.

### Technique #2: Do It Yourself

Use a nice, big example and intuitively solve it. Think hard about how you solved it and reverse engineer your own approach.

### Technique #3: Simplify And Generalize

Multi-step approach that simplify some constraint (such as the data type). Solve the simplified version of the problem and then adapt for a more complex version.

### Technique #4: Base Case And Build

Solve the problem first for a base case and then build up for more complex cases. Generally lead to recursive algorithms.

### Technique #5: Data Structure Brainstorm

Solving a problem may be trivial once it occurs to use a specific data structure. The more problems you do, the more developed your instinct on which data structure to apply will be.

# Handling Situations

### Handling Incorrect Answers

Candidates don't need to get every question right. You will be evaluated about how optimal your final solution was, how long it took to get there, hhow much help you needed, and how clean was your code. You will also be evaluated in comparison to other candidates and the questions my be too difficult to expect even a strong candidate to immediately spit out the optimal algorithm.

### When You've Heard A Question Before

If it occurs, admit this to your interviewer. Otherwise it may be highly dishonest if you don't reveal that you know the question and, conversely, you'll get big honesty points if you do reveal this.

### The Perfect Language For Interviews

Many top companies interviewers aren't picky about languages. Choose whatever language you're most comfortable with considering some points.

- **Prevalence**: It's ideal for your interviewer to know the language you're coding in. Prefer widely known languages.
- **Readability**: Languages such as Scala or Objective-C have fairly different syntax.
- **Potential Problems**: For example, using C++ means that, in addition to all the usual bugs you can have in your code, you can have memory management and pointer issues.
- **Verbosity**: Languages with simple syntax may be preferred, but some verbosity can be reduced by abbreviating code (most interviewers wouldn't mind)
- **Ease of Use**: Some operations are easier in some languages than others.

# Writing Good Code

A good code is correct, efficient, simple, readable and maintainable. Striving for these aspects requires a balancing act. For example, it's often advisable to sacrifice some degree of efficiency to make code more maintainable, and vice versa.

### Use Data Structures Generously

Design your own data structure may be a good solution in some cases. It's a good point to evaluate with the interviewer. Some might argued that this is over-optimizing.

### Modular

Separate isolated chunks of code out into their own methods. This helps keep the code more maintainable, readable, testable and reusable.

### Flexible And Robust

Use variables instead of hard-coded values, use templates to solve a problem. You should write your code to solve a more general problem.

### Error Checking

Adopt failing fast and don't make assumptions about the input. If the error checks are much more than a quick if-statement, it may be best to leave some space where the error checks would go and indicate to your interviewer that you'll fill them in when you're finished with the rest of the code.

# Don't Give Up!

Interview questions can be overwhelming, but this is how they are supposed to be. It shouldn't be a surprise when you get a really tough problem. Show excitement about solving hard problems for extra points.
