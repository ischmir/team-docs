# End-to-End Testing

Compared to unit tests, which are fast and focused, End-to-End tests has some limitations. Therefore of we only focus on testing the critical paths.

## End-to-End Tests limitations

- Slower run than other tests.
- More complex to setup and maintain.
- More prone to flakiness.
- Ressource intensive.

## Have in mind

In the real world users might come upon unexpected issues that an end-to-end test cannot catch.

e.g.
- Database connection might time out.
- Race conditions between services.
- Authentication tokens might expire mid-flow.
- Network latency might cause unexpected timeouts.

## When do we use End-to-End tests

- Critical user journeys.
- Complex workflows spanning multiple pages/views.
- Features involving multiple services or third-party systems.
- Areas with high business value.

## How to run a End-to-End test

To run a test you need to start the server first, You can do that by typing the command below into your CLI. Make sure you are in the project folder.

```bash
npm run dev
```

Next You will want to run the tests. you can do it in the CLI or more visually using the cypress interactive mode.

To run the test in the CLI type the command below in your CLI.

```bash
npm run test:e2e
```

You can aslo run a specific test by using the command below.

```bash
npm run test:e2e -- --spec "cypress/e2e/LoginComp.cy.js"

// or using npx

npx run test:e2e --spec "cypress/e2e/LoginComp.cy.js"
```

To run the test in cypress interactive mode type the command below.

```bash
npm cypress open
```

choose E2E Testing followed by a browser. It will open a browser showing all E2E your tests. Simply choose the one you want to run. 

Notice when using the Cypress interactive mode, everytime you save a file it runs a test.


## Example of a End-to-End Test in the DBI Dashboard

### Signup FLow

**This flow tests:**

- Redirecting from the login view to register
- Password validation
- Successfull registration

```js
describe('Redirect from login to register view', () => {
  beforeEach(() => {
    cy.visit('/login');
  });

  it('should redirect to register page when clicking on register link', () => {
    cy.get('[data-cy="register-link"]').click();
    cy.url().should('include', '/register');
  });
});

describe('Register password validation', () => {
  beforeEach(() => {
    cy.visit('/register');
    cy.get('[data-cy="register-name"]').type('Test User');
    cy.get('[data-cy="register-email"]').type(`testuser${Date.now()}@example.com`);
  });

  it('shows error for missing lowercase letter', () => {
    cy.get('[data-cy="register-password"]').type('PASSWORD123!@#PASSWORD');
    cy.get('[data-cy="register-confirm-password"]').type('PASSWORD123!@#PASSWORD');
    cy.get('[data-cy="register-submit"]').click();
    cy.contains('Adgangskode skal indeholde mindst ét lille bogstav.').should('be.visible');
  });

  it('shows error for missing uppercase letter', () => {
    cy.get('[data-cy="register-password"]').type('password123!@#password');
    cy.get('[data-cy="register-confirm-password"]').type('password123!@#password');
    cy.get('[data-cy="register-submit"]').click();
    cy.contains('Adgangskode skal indeholde mindst ét stort bogstav.').should('be.visible');
  });

  it('shows error for missing number', () => {
    cy.get('[data-cy="register-password"]').type('Password!@#Password!');
    cy.get('[data-cy="register-confirm-password"]').type('Password!@#Password!');
    cy.get('[data-cy="register-submit"]').click();
    cy.contains('Adgangskode skal indeholde mindst ét tal.').should('be.visible');
  });

  it('shows error for missing special character', () => {
    cy.get('[data-cy="register-password"]').type('Password1234Password');
    cy.get('[data-cy="register-confirm-password"]').type('Password1234Password');
    cy.get('[data-cy="register-submit"]').click();
    cy.contains('Adgangskode skal indeholde minst et specialtegn.').should('be.visible');
  });

  it('shows error for password too short', () => {
    cy.get('[data-cy="register-password"]').type('Pass1!');
    cy.get('[data-cy="register-confirm-password"]').type('Pass1!');
    cy.get('[data-cy="register-submit"]').click();
    cy.contains('Adgangskode skal indeholde mindst 16 tegn.').should('be.visible');
  });

  it('shows multiple errors for a very weak password', () => {
    cy.get('[data-cy="register-password"]').type('abc');
    cy.get('[data-cy="register-confirm-password"]').type('abc');
    cy.get('[data-cy="register-submit"]').click();
    cy.contains('Adgangskode skal indeholde mindst ét stort bogstav.').should('be.visible');
    cy.contains('Adgangskode skal indeholde mindst ét tal.').should('be.visible');
    cy.contains('Adgangskode skal indeholde minst et specialtegn.').should('be.visible');
    cy.contains('Adgangskode skal indeholde mindst 16 tegn.').should('be.visible');
  });

  it('shows error if passwords do not match', () => {
    cy.get('[data-cy="register-password"]').type('ValidPassword123!@#');
    cy.get('[data-cy="register-confirm-password"]').type('DifferentPassword123!@#');
    cy.get('[data-cy="register-submit"]').click();
    cy.contains('Adgangskoder stemmer ikke overens.').should('be.visible');
  });
});

describe('Register flow', () => {
  beforeEach(() => {
    cy.visit('/register');
  });

  it('shows error for email  already in use', () => {
    cy.get('[data-cy="register-name"]').type('Test User');
    cy.get('[data-cy="register-email"]').type('test@mail.com');
    cy.get('[data-cy="register-password"]').type('ValidPassword123!@#');
    cy.get('[data-cy="register-confirm-password"]').type('ValidPassword123!@#');
    cy.get('[data-cy="register-submit"]').click();
    cy.contains('Ugyldig email').should('be.visible');
  });

  it('registers a new user with valid data', () => {
    const uniqueEmail = `testuser${Date.now()}@example.com`;
    cy.get('[data-cy="register-name"]').type('Test User');
    cy.get('[data-cy="register-email"]').type(uniqueEmail);
    cy.get('[data-cy="register-password"]').type('ValidPassword123!@#');
    cy.get('[data-cy="register-confirm-password"]').type('ValidPassword123!@#');
    cy.get('[data-cy="register-submit"]').click();
    cy.url().should('include', '/dashboard');
  });
});
```

### Login Flow

**This flow tests:**

- Error handling
- Successful login
- redirecting to the dashboard when successfully logging in.

```js
describe('Login flow', () => {
  beforeEach(() => {
    cy.visit('/login');
  });

  it('shows error message when the credentials are wrong', () => {
    cy.get('[data-cy="login-email"]').type('wrong@mail.com');
    cy.get('[data-cy="login-password"]').type('wrongpassword');
    cy.get('[data-cy="login-submit"]').click();
    cy.contains('Forkert email eller adgangskode.').should('be.visible');
  });

  it('logs in using the right credentials', () => {
    cy.get('[data-cy="login-email"]').type('test@mail.com');
    cy.get('[data-cy="login-password"]').type('password123');
    cy.get('[data-cy="login-submit"]').click();

    // Expect redirect to dashboard page
    cy.url().should('include', '/dashboard');
    cy.contains('Dashboard').should('exist');
  });
});
```

### Edit existing form

When user wants to edit an existing form. 

- Logs in
- Navigates to the form overview
- Selects a folder and form
- Drags new title element into the form
- Edits the text of the title element
- Saves the changes

```bash
describe('create form modal flow', () => {
  beforeEach(() => {
    // Login first
    cy.visit('/login');
    cy.get('[data-cy="login-email"]').type('test@mail.com');
    cy.get('[data-cy="login-password"]').type('password123');
    cy.get('[data-cy="login-submit"]').click();
    cy.url().should('include', '/dashboard');
    cy.contains('Dashboard').should('exist');
  });

  it('edit form in form editor', () => {
    // Navigate to form overview and access the first form in the first folder
    cy.visit('/form-overview/');
    cy.get ('[data-cy="create-folder"]').first().click();
    cy.get ('[data-cy="first-form"]').first().click();
    cy.contains('Skema Titel').should('exist');
    // Drag and drop the title palette item into the drop zone
    cy.get('[data-cy="palette-item-title"]').drag('[data-cy="drop-zone"]');
    cy.get('[data-cy="drop-zone"]').should('contain', 'Overskrift');
    // Edit the title field
    cy.get('[data-cy="form-title-input"]').first().clear();
    cy.get('[data-cy="form-title-input"]').first().type('Mit nye skema');
    cy.get('[data-cy="form-title-input"]').should('have.value', 'Mit nye skema');
    cy.get('[data-cy="save-form-btn"]').click();
  });
});
```

### Create New Form Flow

When a user wants to create a new form.

- Clicks create new form button.
- Fills in needed information in the form.
- Creates a form using the drag and drop editor.
- Save the changes
- A popup shows saved confirmation.
- Gets redirected to the form overview.

```js
describe('Drag and Drop Editor E2E', () => {
  beforeEach(() => {
    // Login first
    cy.visit('/login');
    cy.get('[data-cy="login-email"]').type('test@mail.com');
    cy.get('[data-cy="login-password"]').type('password123');
    cy.get('[data-cy="login-submit"]').click();
    cy.url().should('include', '/dashboard');
    cy.contains('Dashboard').should('exist');
    //redirect to form overview and access first folder
    cy.visit('/form-overview/');
    cy.get ('[data-cy="create-folder"]').first().click();
    cy.get('[data-cy="open-create-form-modal-btn"').click();
    cy.get('[data-cy="form-name-input"').type('Test Skema');
    cy.get('[data-cy="next-create-form-modal-btn"]').click();
    cy.get('[data-cy="next-create-form-modal-btn"]').click();
    //cy.visit('/form-editor/liqwC3KrFzmrhskGFRs7');
    cy.contains('Skema Titel').should('exist');
  });

  it('can drag title palette item into drop-zone and edit title', () => {
    // Drag and drop title palette item
    cy.get('[data-cy="palette-item-title"]').drag('[data-cy="drop-zone"]');
    cy.get('[data-cy="drop-zone"]').should('contain', 'Overskrift');

    // Edit the title field
    cy.get('[data-cy="form-title-input"]').first().clear();
    cy.get('[data-cy="form-title-input"]').first().type('Mit nye skema');
    cy.get('[data-cy="form-title-input"]').should('have.value', 'Mit nye skema');

    // Save changes
    cy.get('[data-cy="save-form-btn"]').click();

    // Assert redirect or success message (adjust as needed)
    cy.url().should('include', '/form-overview');
    cy.contains('Skemaoversigt').should('exist');
  });
});
```
