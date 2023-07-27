describe('template spec', () => {
  it('Succes_login', () => {
    cy.visit('https://magento.softwaretestingboard.com/')
    cy.contains("Sign In").click()
    cy.get('#email').type('cobacoba@gmail.com')
    cy.get('.login-container > .block-customer-login > .block-content > #login-form > .fieldset > .password > .control > #pass').type('Coba123@')
    cy.get('.login-container > .block-customer-login > .block-content > #login-form > .fieldset > .actions-toolbar > div.primary > #send2 > span').click()
  })

  it('valid_email_Failed_password', () => {
    cy.visit('https://magento.softwaretestingboard.com/')
    cy.contains("Sign In").click()
    cy.get('#email').type('cobacoba@gmail.com')
    cy.get('.login-container > .block-customer-login > .block-content > #login-form > .fieldset > .password > .control > #pass').type('1234')
    cy.get('.login-container > .block-customer-login > .block-content > #login-form > .fieldset > .actions-toolbar > div.primary > #send2 > span').click()
    cy.get('.message-error > div').should('be.visible')
  })

  it('invalid_email_invalid_password', () => {
    cy.visit('https://magento.softwaretestingboard.com/')
    cy.contains("Sign In").click()
    cy.get('#email').type('testing@gmail.com')
    cy.get('.login-container > .block-customer-login > .block-content > #login-form > .fieldset > .password > .control > #pass').type('abc')
    cy.get('.login-container > .block-customer-login > .block-content > #login-form > .fieldset > .actions-toolbar > div.primary > #send2 > span').click()
    cy.get('.message-error > div').should('be.visible')
    
  })
})
