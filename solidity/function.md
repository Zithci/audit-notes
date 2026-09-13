# Function 

###  1
---
 - a blok kode yg bisa dipanggil buat ngelakuin sesuatu — 
bisa baca state, tulis state, atau ngitung sesuatu tanpa nyentuh state. 
Tiap function punya visibility (siapa yg boleh manggil), mutability 
(boleh ngubah state atau enggak), dan bisa return 0 atau lebih nilai.


```
function(isi param(opsional)) +visibilty returns {}
```
---


## 2
return di kasih nama biar readable
//return bs di namain (opsional).

``` solidity 
return(param X ,param Y ,param Z){} //can up to >1 param
```


---

## 3
kalo return di namain bs langsung assign skip 'return' 

```
function()public returns(param X ,param Y ,param Z) {}
    x=1(value);
    y=2(value);
    x=3(value);
```

## 4
  destructuring = nangkep multi return, bisa skip nilai pake `,,`

```solidity
(uint256 i, bool b, uint256 j) = returnMany();
(uint256 x,, uint256 y) = (4, 5, 6);   // 5 dibuang
```
---

# 5. 
 mapping GAK BISA jadi input/output di public/external function
- alasan: mapping gak bisa di-copy (gak ada daftar key yang keisi + size 2^160)
- exception: bisa jadi parameter di `internal`/`library` pake keyword `storage`

```solidity
function update(mapping(address => uint256) storage _map) internal {
    _map[msg.sender] = 100;
}

```

---

# 6.
 storage slot mapping dihitung pake hash:

slot number = urutan declcare di contract 
```
// declare state
uint256 (visibilty ) x//slot 0 
address (visibilty) ngawi slot 1

```

- pas akses nu uint256 x :
```
keccak256(key(adderess u . no slot var = 0))
keccak256(0xhfsdjhfdsjfds . 0) = 0xdfdndfjd(random number 256 bit)
```

---
## 7
 key-value call = manggil function pake nama param, bukan urutan,intinya bebas aja urutannya cm nama paramnya kudu sama
 
- guna: aman kalo banyak param dengan tipe sama

```solidity
someFunc({x: 1, y: 2, z: 3, a: address(0), b: true, c: "c"});
```








