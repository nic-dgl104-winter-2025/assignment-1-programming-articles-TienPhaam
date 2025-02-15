[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/_Y4t8UXw)
# dgl104-programming-article-repo

# Review Best Practices: 
### Introduction
Code reviews are a super important part of working on software with other people. They help catch mistakes, make sure code is easy to read, and teach us better coding habits. But, if you're new to it, code reviews can seem a bit scary. This article will explain some best practices for reviewing code in a way that's helpful and not overwhelming. We'll go over key ideas, give practical tips, and include example code to show what works best.

### Why Code Reviews Are Important

**Here are some good reasons why code reviews matter:**

- Code reviews are crucial for maintaining code quality, preventing bugs, and fostering knowledge sharing within teams.
- They help enforce coding standards, ensure maintainability, and improve overall project efficiency. Code reviews are not antagonistic, but it  is the job of the reviewer to ask questions to help clarify code purpose or consequences.
- Code review is an key part of development on most public projects and development studios.
- Code review helps make better programmers. For juniors coders, it helps to learn better technique, heuristics, patterns and idioms.
- Knowledge Sharing – They enable developers to learn from each other, share best practices, and understand different parts of the codebase.

**Common Pitfalls in Code Reviews:**

- Many teams treat code reviews as a checklist rather than an opportunity for meaningful collaboration.
- Reviews often focus too much on superficial issues (e.g., style inconsistencies) instead of critical architectural or logic flaws.
There’s a tendency for reviews to become confrontational, leading to defensiveness and discouraging open discussion.

**Best Practices for Effective Code Reviews:**
- Reviewers should ask whether the code is easy to read and understand rather than just checking if it works.
- Keep Reviews Small: Large reviews can be overwhelming and harder to process; smaller, incremental changes make reviews more manageable.
- Encourage a Positive Culture: Feedback should be constructive, respectful, and focused on improvement rather than criticism.
- Use Automated Tools: Linters, formatters, and static analysis tools should handle routine style and syntax checks, allowing human reviewers to focus on logic and design.

**Balancing Speed and Thoroughness:**

- Reviews should be efficient but not rushed; taking the time to review code thoroughly prevents future technical debt.
- Encouraging an iterative approach where developers and reviewers work together can improve code quality without slowing down development.
- Suggest Improvements with Examples. Rather than just pointing out issues, provide alternative approaches with examples.

## Improving Readability (Java) 
A function should be easy to understand at first glance. Here’s an example of hard-to-read code:
```Java
public class Calculator {
    public int calc(int[] arr) {
        int res = 0;
        for (int i = 0; i < arr.length; i++) {
            res += arr[i] * arr[i];
        }
        return res;
    }
}
```
Why this is problematic: The function name calc is vague, and the logic is difficult to follow.

**Improved Version: Using meaningful method names and enhanced readability:**
```Java
public class Calculator {
    public int calculateSumOfSquares(int[] numbers) {
        return Arrays.stream(numbers)
                     .map(num -> num * num)
                     .sum();
    }
}
```
Why this is better:
- The method name clearly describes its functionality.
- The use of Java streams makes the code more concise and readable by removing the need for a loop.
- It promotes functional programming practices, which improve maintainability.

## Using Meaningful Variable Names

Poor variable names make the code harder to understand:
```JavaScript
function p(d) {
    let r = [];
    for (let i = 0; i < d.length; i++) {
        r.push(d[i].trim().toLowerCase());
    }
    return r;
}
```
Why this is problematic:
- Single letter variable names p, d, r provide no context about what the function does
- The logic is not immediately clear.

Improved Version: Using descriptive variable names improves clarity:
```JavaScript
function processStrings(strings) {
    return strings.map(str => str.trim().toLowerCase());
}
```
Why this is better:
- processStrings clearly describes the function's purpose.
- The map method simplifies the operation, making it easier to understand at a glance.
- Readability is significantly improved, making it easier for new developers to modify.

## Avoiding Code Duplication
Duplicated logic makes maintenance harder. The following example has redundant methods:
```Java
public class Order {
    public double calculateTotalPrice(double price, int quantity) {
        return price * quantity;
    }

    public double calculateDiscountedTotalPrice(double price, int quantity, double discount) {
        return (price * quantity) - discount;
    }
}
```
Why this is problematic:
- Both methods share similar logic but are separate, leading to redundant code.
- Maintaining changes would require modifying multiple locations.

Improved Version: Merging similar methods reduces redundancy:
```Java
public class Order {
    public double calculateTotalPrice(double price, int quantity, double discount) {
        return (price * quantity) - discount;
    }
}
```
Why this is better:
- It consolidates logic into a single method, reducing maintenance overhead.
- It provides flexibility by including the discount parameter in the same method.

## Conclusion:
Code reviews are essential for maintaining high-quality software and fostering team collaboration. They help catch bugs early, improve readability, and ensure consistency. By keeping reviews small, using automation, encouraging a positive culture, and balancing speed with thoroughness, teams can make the process more effective. Providing clear, constructive feedback with alternative solutions not only enhances code but also supports learning and professional growth. For junior developers, code reviews serve as a valuable learning tool, offering insights into best practices, coding standards, and problem-solving approaches. A strong review culture leads to continuous improvement, better teamwork, and higher-quality software, making code reviews a vital practice in any development process.


### References ###

1. Stack Overflow. (2019, September 30). How to make good code reviews better. Stack Overflow Blog. https://stackoverflow.blog/2019/09/30/how-to-make-good-code-reviews-better/

2. Google. (n.d.). Code review standards. Google Engineering Practices. https://google.github.io/eng-practices/review/reviewer/standard.html

3. Video:  Ashley, B. (2024, April 24th). dgl104 code review 2024. https://www.youtube.com/watch?v=DCZ6_bcxdGg

4. SmartBear Software. (n.d.). Best practices for peer code review. SmartBear. Retrieved February 15, 2025, from https://smartbear.com/learn/code-review/best-practices-for-peer-code-review/

5. Ghani, U. (2022, February 3). 5 code review best practices. Atlassian. https://www.atlassian.com/blog/add-ons/code-review-best-practices
