describe('Slider Interaction Test', () => {
  it('Should interact with the slider and validate the result', () => {
    // Visit the website
    cy.visit('https://www.lambdatest.com/selenium-playground');

    // Click “Drag & Drop Sliders” under “Progress Bars & Sliders”
    cy.contains('Progress Bars & Sliders').click();
    cy.contains('Drag & Drop Sliders').click();

    // Select the slider “Default value 15”
    const sliderLabel = 'Default value 15';
    cy.contains(sliderLabel).click();

    // Drag the slider to make it 95
    const initialValue = 15;
    const targetValue = 95;
    const difference = targetValue - initialValue;

    // Perform drag operation using mouse events
    cy.get('.range-slider')
      .invoke('val', initialValue)
      .trigger('input', { force: true })
      .trigger('mousedown', { which: 1 })
      .trigger('mousemove', { clientX: 10 * difference, clientY: 0 })
      .trigger('mouseup', { force: true });

    // Validate whether the range value shows 95
    cy.get('.range-value').should('have.text', `${targetValue}`);
  });
});





// cypress/integration/form_submission_spec.js

describe('Form Submission Test', () => {
  it('Should submit the form and perform various validations', () => {
    // Step 1: Open the page and change the port to Samsung Note 9
    cy.visit('https://www.lambdatest.com/selenium-playground', {
      headers: {
        'user-agent':
          'Mozilla/5.0 (Linux; Android 8.1.0; SM-N960F Build/M1AJQ; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/78.0.3904.108 Mobile Safari/537.36',
      },
    });

    // Wait for all elements on the page to load
    cy.wait(5000); // Adjust the wait time based on your application's load time

    // Step 2: Click “Input Form Submit” under “Input Forms”
    cy.contains('Input Form Submit').click();

    // Step 3: Verify accessibility using cypress-axe or cypress-audit
    cy.injectAxe();
    cy.checkA11y();

    // Step 4: Fill in all the fields using different locators
    cy.get('#contact-form-name').type('John Doe'); // Using ID locator
    cy.get('[placeholder="Email"]').type('john.doe@example.com'); // Using attribute locator
    cy.xpath('//label[contains(text(),"Subject")]/following-sibling::input').type('Test Subject'); // Using XPath locator
    cy.get('#contact-form-comment').type('This is a test comment.'); // Using ID locator

    // Step 5: Click on submit the form and assert that the form gets submitted
    cy.get('[type="submit"]').click();

    // Step 6: Verify performance metrics using Cypress lighthouse commands
    cy.lighthouse({
      performance: 90,
      accessibility: 90,
      'best-practices': 90,
      seo: 90,
      pwa: 90,
    });

    // Step 7: Validate the success message using different locator
    cy.contains('Thanks for contacting us, we will get back to you shortly.').should('exist');

    // Step 8: Close browser tab and session
    cy.window().then((win) => {
      win.close();
    });
  });
});
