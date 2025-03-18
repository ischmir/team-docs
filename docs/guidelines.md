# Team Guidelines

<hr>

## Communication
- Check email at least twice daily
- Respond to Discord messages within 4 hours
- Attend daily standup meetings

<hr>

## Development Workflow
1. Create a branch for each feature
2. Submit pull requests for review
3. Ensure tests pass before merging

<hr>

## Refactor Guidelines
**Best Practices:**

- Make small incremental changes
- Test after each refactoring
- Commit Frequently
- Keep functions small end focused
- Avoid deep nesting
- Use constants for magic numbers and strings


<br>

**Single Responsibility Principle**

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

<br>

**Don't Repeat Yourself**

- Every piece of code should have a single representation
- Avoid copy/pasting code
- Create reusable functions and utilities

```js
    // Do this
    function calculateArea(length, width) {
        return length * width;
    }

    const area1 = calculateArea (length1, width1);
    const area2 = calculateArea (length2, width2);
    const area3 = calculateArea (length3, width3);

    // Not this
    const area1 = length1 * width1;
    const area2 = length2 * width2;
    const area3 = length3 * width3;
```

<br>

**Keep It Simple Stupid**

- Simpler code is easier to maintain
- Avoid clever tricks
- Clear and straightforward solutions are better
- Remember code is read more often than it is written

```js
    // Do this - Simple code, easy to read
    function getUserStatus(age, isMember) {
        if (age >= 18) {
            if(isMember) {
                return "Adult Member";
            } else {
                return "Adult Non-Member";
            }
        } else {
            if  (isMember) {
                return "Minor Member";
            } else {
                return "Minor Non-Member";
            }
        }
    }

    // Not this - Clever but hard to read
    function getUserStatus (age, isMember) {
        const status = >= 18 ? "Adult" : "Minor";
        return `${status} ${isMember ? "Member" : "Non-Member"}`;
    }
```

<br>

**You Aren't Going To Need It**

- Don't add it unless you need it
- Focus on current requirements

```js
    class User {
        constructor(name, email) {
            this.name = name;
            this.email = email;
            this.phonenumber = phonenumber; // We might need this later
            this.preferences = preferences; // Also for later use
        }
    }
```

<br>

**Writing Self-Documenting Code**

- Use explanitory variables, functions etc.

```js
    //Good
    const currentDate = new Date();
    const timestamp = currentDate.getTime(;)
    
    //Bad
    const d = new Date();
    const n = currentDate.getTime(;)
```

```js
    //Good
    function validateUserInput(formData) {
        // ... Validates user input
    }
    //Bad
    function data(form) {
        // ... does something with data
    }
```

<br>

**Code Comments**

- Explain why, not what
- Keep Comments up to date
- Don't overuse comments

```js
    /**
     * Calculates the total price including tax and discounts
     * @param {number} basePrise - the original price
     * @param {number} taxRate - taxrate as decimal (e.g., 0.2 for 20%)
     * @param {boolean} hasDiscount - Whether to standard discount
     * @returns {number} the final price
     */

    function calculateFinalPrice(basePrice, taxRate, hasDiscount) {
        // implementation
    }
```

<hr>
   
## Code Review

<hr>

## Error Handling and Debugging

<hr>

## Safety