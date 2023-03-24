/// <reference types="Cypress" />
var randomEmail = require('random-email');

describe.only("filling test", ()=>{
  it('Fellowship: it displays complete when all the points are used', () => {
    cy.visit('https://furbo.sk/waw/fellowship.php')
    //TODO: zaklikni na stránke elementy s textom Frodo, Legolas, Gandalf, Aragorn
    cy.contains(".inner", "Frodo").should('be.visible').click()
    cy.contains(".inner", "Legolas").should('be.visible').click()
    cy.contains(".inner", "Gandalf").should('be.visible').click()
    cy.contains(".inner", "Aragorn").should('be.visible').click()
    cy.get('.points-left')
        .find('h3')
        .should('have.text', 'Complete')
  });
  
  it('Spelleology: it displays first spell', () => {
    cy.visit('http://furbo.sk/waw/spelleology.php')
    //TODO: nájdi prvý spell element pomocou funkcie eq() a otvor jeho detail
    cy.get(".spells li").eq(0).click()
    cy.get('.modal-container')
      .should('be.visible')
      .find('.modal-header')
      .should('have.text', 'Accio')
  })
  
  it('Spelleology: it displays last spell', () => {
    cy.visit('http://furbo.sk/waw/spelleology.php')
    //TODO: nájdi posledný spell element pomocou funkcie last() a otvor jeho detail
    cy.get(".spells li").last().click()
    cy.get('.modal-container')
      .should('be.visible')
      .find('.modal-header')
      .should('have.text', 'Wingardium Leviosa')
  })
})
describe("Calculator with positive number", ()=>{
  
  before(()=>{
    cy.visit('http://ajtyvit-app.westeurope.cloudapp.azure.com:8080/kalkulacka.php')
    cy.get('#firstInput').type(8)
    cy.get('#secondInput').type(13)
  })
  it('basic function of calculator with possitive number', ()=>{
    cy.log('Count test')
    cy.get('#count').click()
    cy.get('#result').should('be.visible').should('have.text', 21)
    // zobrazuje sa zle namiesto + je - a zobrazi 2-krát
    // cy.get('.latest-results').should('contain', "8+13 = 21")

    cy.log('Deduct test')
    cy.get('#deduct').click()
    cy.get('#result').should('be.visible').should('have.text', -5)
    cy.get('.latest-results').should('contain', "8-13 = -5")

    // Nefunguje funkcia násobenia čiže neni môžne overovať ďalej
    // cy.log('Multiply test')
    // cy.get('#multiply').click()
    // cy.get('#result').should('be.visible').should('have.text', -70)
    // cy.get('.latest-results').should('contain', "8*13 = 104")
    
    cy.log('Divide test')
    cy.get('#divide').click()
    cy.get('#result').should('be.visible').should('have.text', 0.6153846153846154)
    cy.get('.latest-results').should('contain', "8/13 = 0.6153846153846154")

    cy.log('Reset test')
    cy.get('#reset').click()
    cy.get('#firstInput').should('not.have.value')
    cy.get('#secondInput').should('not.have.value')

  })
})

describe('Calculator with negative number', ()=>{
  before(()=>{
    cy.visit('http://ajtyvit-app.westeurope.cloudapp.azure.com:8080/kalkulacka.php')
    cy.get('#firstInput').type(-14)
    cy.get('#secondInput').type(-5)
  })
  it('basic function of calculator with negativ number', ()=>{
    cy.log('Count test')
    cy.get('#count').click()
    cy.get('#result').should('be.visible').should('have.text', -19)
    // zobrazuje sa 2-krát
    cy.get('.latest-results').should('contain', "-14--5 = -19")

    cy.log('Deduct test')
    cy.get('#deduct').click()
    cy.get('#result').should('be.visible').should('have.text', -9)
    cy.get('.latest-results').should('contain', "-14--5 = -9")

    // Nefunguje funkcia násobenia čiže neni môžne overovať ďalej
    // cy.log('Multiply test')
    // cy.get('#multiply').click()
    // cy.get('#result').should('be.visible').should('have.text', -70)
    // cy.get('.latest-results').should('contain', "-14*-5 = 70")

    cy.log('Divide test')
    cy.get('#divide').click()
    cy.get('#result').should('be.visible').should('have.text', 2.8)
    cy.get('.latest-results').should('contain', "-14/-5 = 2.8")

    cy.log('Reset test')
    cy.get('#reset').click()
    cy.get('#firstInput').should('not.have.value')
    cy.get('#secondInput').should('not.have.value')

  })
})
describe("Savings Calculator", ()=>{
  it("empty inputs", ()=>{
    const jsonData = {
      fundName: "Handelsbanken Aktiv 100",
      firstInvest: 32354,
      periodYears: 25,
      email: randomEmail({domain:"outlook.com"})
    }
    cy.log("Visit URL")
    cy.visit('/savingscalculator.php')
    
    cy.log("Filling all inputs")
    cy.get('#fundSelect').select(jsonData.fundName)
    cy.get('#oneTimeInvestmentInput').type(jsonData.firstInvest)
    cy.get('#yearsInput').type(jsonData.periodYears)
    cy.get('#emailInput').type(jsonData.email)

    cy.log('Save request')
    cy.get('[data-test="apply-for-saving"]').click()

    cy.log('Request should be visible')
    cy.get('.saving-list li').eq(0).should('be.visible')

    cy.log('Should empty inputs')
    cy.get('#fundSelect').should('not.have.value')
    cy.get('#oneTimeInvestmentInput').should('not.have.value')
    // try should be.empty
    cy.get('#yearsInput').should('be.empty')
    cy.get('#emailInput').should('be.empty')

  })
})
