PAN and DoB are additional parameters that are supposed to be used to resolve conflict when the FIP during the discovery process cannot resolve the accounts to a single customer using just the strong identifier (Mobile number).  When an FIP receives a discovery request, the first step should be to identify all accounts that are enabled on AA and linked to the mobile number provided by the AA. If the FIP is able to resolve the discovery request to a unique customer, the FIP must return those accounts as part of the discovery response. 

If the FIP cannot resolve the discovery request to a single owner, there are multiple scenarios of how PAN and DoB should be used to resolve this conflict. 

## Case 1: User provides Mobile, PAN, and DoB

- FIP discovers more than one customer record with the mobile number.
- The FIP aims to resolve the conflict first with the PAN. If it identifies one customer record correctly with the PAN, it generates the Account reference number for the same, sends it back to the AA, and ignores other accounts where the PAN doesn’t match.
- If PAN cannot resolve the conflict, FIP uses DoB and follows the same steps as above.
- If the conflict is still unresolved, the FIP must send back the HTTP code 404 and the Error Code as “CannotIdentifyCustomer.”
- If FIP discovers only one customer record, it generates the Account reference number for the same and responds appropriately to the AA.
- If FIP cannot discover any accounts with the Mobile number (STRONG Identifier), it responds with the HTTP code 404 and the error code “NoAccountsFound.”

## Case 2: User provides Mobile and PAN only

- FIP discovers more than one customer record with the mobile number.
- The FIP aims to resolve the conflict first with the PAN. If it identifies one customer record correctly with the PAN, it generates the Account reference number for the same, sends it back to the AA, and ignores other accounts where the PAN doesn’t match.
- If PAN cannot resolve the conflict, the FIP must return the HTTP code 404 and the Error Code as “CannotIdentifyCustomer.”
- If FIP discovers only one customer record, it generates the Account reference number for the same and responds appropriately to the AA.
- If FIP cannot discover any accounts with the Mobile number (STRONG Identifier), it responds with the HTTP code 404 and the error code “NoAccountsFound.”

## Case 3: User provides Mobile and DoB only

- FIP discovers more than one customer record with the mobile number.
- The FIP aims to resolve the conflict first with the DoB. If it identifies one customer record correctly with the DoB, it generates the Account reference number for the same, sends it back to the AA, and ignores other accounts where the DoB doesn’t match.
- If DoB cannot resolve the conflict, the FIP must return the HTTP code 404 and the Error Code as “CannotIdentifyCustomer.”
- If FIP discovers only one customer record, it generates the Account reference number for the same and responds appropriately to the AA.
- If FIP cannot discover any accounts with the Mobile number (STRONG Identifier), it responds with the HTTP code 404 and the error code “NoAccountsFound.”

## Case 4: User provides only Mobile

- FIP discovers more than one customer record with the mobile number.
- Without any additional identifiers, the FIP needs to send back the HTTP code 404 and the Error Code as “CannotIdentifyCustomer.”
- If FIP discovers only one customer record, it generates the Account reference number for the same and responds appropriately to the AA.
- If FIP cannot discover any accounts with the Mobile number (STRONG Identifier), it responds with the HTTP code 404 and the error code “NoAccountsFound.”
