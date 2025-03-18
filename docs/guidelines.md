# Team Guidelines
## Communication
- Check email at least twice daily
- Respond to Discord messages within 4 hours
- Attend daily standup meetings

## Development Workflow
1. Create a branch for each feature
2. Submit pull requests for review
3. Ensure tests pass before merging

## Refactor Guidelines
- Single Responsibility Principle
    -   Each Function / Class should have one responsibility

```js
    class User {
        constructor(name, email) {
            this.name = name;
            this.email = email;
        }

        sendEmail(message) {
            console.log(`Sending email to ${this.email}: ${message}`);
        }
    }
```

- Don't Repeat Yourself
    -   Every piece of code should have a single representation
    -   Avoid copy/pasting code
    -   Create reusable functions and utilities

```js
    //Instead of this
    const area1 = length1 * width1;
    const area2 = length2 * width2;
    const area3 = length3 * width3;
    
    //Do this
    function calculateArea(length, width) {
        return length * width;
    }

    const area1 = calculateArea (length1, width1);
    const area2 = calculateArea (length2, width2);
    const area3 = calculateArea (length3, width3);
```

- Keep It Simple Stupid
## Code Review

## Error Handling and Debugging

## Better Safe than Sorry