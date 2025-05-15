# HADC 

## Introduction 
- On February 21, 2025, Bybit, a major cryptocurrency exchange based in Dubai, experienced the largest digital theft in crypto history, with over $1.5 billion in Ethereum stolen [1]

## How the attack was executed? [2]
The attackers exploited a vulnerability in Bybit's multi-signature (multi-sig) cold wallet system, which required multiple approvals to authorize transactions. They manipulated the user interface of the Safe{Wallet} application, used by Bybit for transaction approvals, by injecting malicious JavaScript code through a compromised developer's machine. This code altered the transaction details displayed to the signers, making them believe they were approving legitimate transfers when, in fact, they were authorizing the transfer of funds to the attackers' control

1. Phishing and Social Engineering 
    - Giving access to employee credentials
2. Manipulating the Signing Process
   - Manipulated the transaction data displayed on their screens.
3. Exploiting Technical Vulnerabilities
   - The attackers exploited zero-day vulnerabilities—previously unknown flaws—in Bybit’s security software.
4. Laundering the Stolen Funds

## Summary
- Attackers injected malicious JavaScript into Safe's frontend (by getting access to one of the Safe's developer's development environment)
- That injected code update pushed to Safe, but it only and only was checking the from address against Bybit's signer adress so code only worked differently when it was signed by Bybit's adresses.
- When Bybit's signers initiated a transaction (probably internal basic transfer), the compromised UI at the first multisig initiating the transfer displayed legitimate transaction details while submitting a malicious transaction that transferred control of the wallet to the attackers
- Others multisig wallets were getting the transaction details from the Safe API so they were able to see tampered transaction as it is but it was only extra data in hexadecimal getting passed by so they didn't realize and they've just approved it.
- After transaction sent, hacker group had the control of assets and moved ETH to laundering services.

## Why did it happen? [3]

- Blind Signing
    - Signers approved transactions without fully verifying their content, a practice known as blind signing [3]

- UI Manipulation
    - The malicious code altered the Safe{Wallet} interface to deceive signers into approving fraudulent transactions.

- Human Error
    - Phishing attacks and compromised developer tools facilitated the initial breach

## Attack Vectors

- Compromisation of third party code supplier through phishing or another attack like social engineering.
- Targeted tampered transaction

### What Could Have Prevented It?
- Multi-Layered Security
    - Tamper proof multi level checks required
    - Combining technical check as well human checks in order to create a robust model 
        - SoD Segregation of Duties
        - 4 eye check
        - Least Privilege Access
        - Time-Limited Transactions
        - Behavioural Analytics

- Try to show as much as data to user if possible, and try to get transaction data from different levels so even if one point of the flow compromised there can be additional opportunities to realize the mistake.
- Frontend integrity checks.
- Staff Training 
   - Training staff to recognize phishing attempts and other social engineering tactics can prevent initial breaches


# Sources

[1] https://www.theguardian.com/technology/2025/feb/23/crypto-exchange-seeks-bybit-ethereum-stolen-digital-wallet

[2] https://coin.space/the-bybit-hack/

[3] https://www.blockaid.io/blog/how-to-prevent-the-next-15b-bybit-hack-a-strategic-approach-to-solving-blind-signing
