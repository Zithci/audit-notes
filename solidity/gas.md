# Gas
_______________

## Foundry test gas limit
- default: ~1 miliar gas (sengaja tinggi biar test complex bisa jalan)
- mainnet block gas limit: 30 juta
- infinite loop di test = ~1 miliar gas dipake → OutOfGas → revert
- error muncul sebagai `ReentrancySentryOOG` di Foundry (bukan OOG polos)

## Deployment
- deployment cost = gas buat naruh contract di chain
- deployment size = ukuran bytecode
- max size: 24,576 byte (EIP-170)
- lewat itu → gak bisa deploy ke mainnet
- workaround: split contract, proxy pattern, external library

## Gas built-in Solidity
- `gasleft()` = sisa gas di transaction sekarang
- `tx.gasprice` = harga per unit gas (wei)
- `block.gaslimit` = max gas per block
- `block.basefee` = base fee EIP-1559

## Command Foundry buat cek gas
- `forge test --gas-report` → summary gas per function
- `forge test -vvv` → trace lengkap kalo test fail
- gas per function di-report cuma kalo function sukses (revert = 0)