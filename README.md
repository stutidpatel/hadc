# HADC

- Attackers injected malicious JavaScript into Safe's frontend (by getting access to one of the Safe's developer's development environment)
  -That injected code update pushed to Safe, but it only and only was checking the from address against Bybit's signer adress so code only worked differently when it was signed by Bybit's adresses.
- When Bybit's signers initiated a transaction (probably internal basic transfer), the compromised UI at the first multisig initiating the transfer displayed legitimate transaction details while submitting a malicious transaction that transferred control of the wallet to the attackers
- Others multisig wallets were getting the transaction details from the Safe API so they were able to see tampered transaction as it is but it was only extra data in hexadecimal getting passed by so they didn't realize and they've just approved it.

- After transaction sent, hacker group had the control of assets and moved ETH to laundering services.

## Attack Vectors

- Compromisation of third party code supplier through phishing or another attack like social engineering.
- Targeted tampered transaction

### What do we need to be careful about

- Tamper proof multi level checks required
- Try to show as much as data to user if possible, and try to get transaction data from different levels so even if one point of the flow compromised there can be additional opportunities to realize the mistake.
- Frontend integrity checks.
