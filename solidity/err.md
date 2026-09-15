# err
#1 
- ada 3 jenis error yang bs di pake tergantung kebutuhan:
---
### 1. Require:validasi input dan kondisi awal
- cek input dari user (angka harus > 10, address gak boleh 0, dll)
- cek kondisi sebelum function jalan (msg.sender harus owner, balance harus cukup)
- cek return value dari function lain
```
    function kita (uint256 _i) public pure {
        require(_i > 10, "hrus lebih gde dari 10 nyet "); //nilai i harus lebih dari 10 
    }    
```

---

### 2. Revert : just like require tp buat kondisi logic yang udh agak berat cuy,kek banyak if else gitu lah

```
function ngawi(uint256 _i) public pure {
    if(_i <= 10){
        revert("input must be greater than 10");
    }
}

```

---
### 3. assert : cek kondisi yg secara logika mustahil salah(invariant);

- cek bug internal biasanbya kalo dia revert berarti ada tai tuh di kode u,kek gua percaya kode ini no bug but double check in case

```
//declare state 
uint public totalSupply;
mapping(address => uint) public balances;

function transfer(address to, uint amount) public {
    balances[msg.sender] -= amount;
    balances[to] += amount;
    
    // invariant: totalSupply gak boleh berubah gara-gara transfer
    // karena transfer cuma mindahin dari A ke B
    assert(totalSupply == totalSupplyLama);
}
```


