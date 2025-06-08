# Documentation for the "Split-fair - shared expenses calculator" Project

## Introduction

This project is a web application for calculating shared expenses among participants. The application allows users to
input expense data, distribute it among participants, and obtain final results.

## Initial Requirements

### Technical Requirements

Single-page website. Use simple HTML, very simple CSS, and only vanilla, very simple JS.

### Functional Requirements

Requirements for the functionality and logic of a single-page website for calculating equal expenses among participants
of a shared purchase. Website functionality:

1. **Data Input**

* Form for adding participants:
    * Field for the person's name (required).
    * Field for the amount they spent (required, numeric, with a check for non-negativity).
* "Add Participant" button
    * Allows adding as many people as needed.
    * When a new participant is added, a new row with fields for name and amount appears.
* Display a list of added participants with their names and amounts.

2. **Calculate Total Button**

* When clicked:
    * Calculate the total amount spent.
    * Calculate the average amount per person (total amount / number of participants).
    * For each participant, calculate the difference between their expenses and the average amount.
    * Generate a list of transactions showing who owes whom how much to equalize expenses.

3. **Result Display**

* Total amount spent.
* Average amount per person.
* For each participant:
    * How much they spent.
    * How much they should receive or pay.
* List of specific money transfers between participants, for example:
    * "Ivan should transfer 500 rubles to Maria"
    * "Peter should receive 300 rubles from Anna"

4. **Additional Useful Features (optional)**

* "Clear All" button to reset data.
* Field validation (name is not empty, amount is a number and >= 0).
* Responsive design for mobile devices.
* Ability to save the result in PDF or copy to clipboard.

### Logic for Calculating Debt Distribution

1. Calculate the total sum:
   S=∑i=1nsiS = \sum_{i=1}^n s_iS=i=1∑nsi
   where sis_isi — the amount spent by the i-th participant.
2. Find the average amount per person:
   M=SnM = \frac{S}{n}M=nS
3. For each participant, calculate the difference:
   di=si−Md_i = s_i - Mdi=si−M
    * If di>0d_i > 0di>0, the participant overpaid and should receive money.
    * If di<0d_i < 0di<0, the participant should pay more.
4. Create lists of debtors and creditors.
5. Distribute debts to minimize the number of transfers:
    * Go through the list of debtors and the list of creditors.
    * The debtor pays the creditor either the entire debt amount or as much as the creditor needs to receive.
    * Continue until all debts are settled.

## Non-Functional Requirements

1. **Performance**:
    - The application should work quickly and responsively, even when entering a large volume of data.

2. **Security**:
    - The application should protect user data from unauthorized access.
    - A content security policy (CSP) should be implemented.

3. **Compatibility**:
    - The application should be compatible with the latest versions of modern browsers (Chrome, Firefox, Safari, Edge).

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
