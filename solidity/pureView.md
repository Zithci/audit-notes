# pure and view 

## 1

- view =  cm bs baca state dari dalam atau luar 

ex :

````
uint256 ngawi = 01;

function readNgawi() public view returns(uint256){
    return ngawi;
}
````
ini di sbut view karena dia ambil somthin dari luar

---
## 2
- pure = kg baca kg liat kg ngapa ngapain suci bro cm return doang

```
function jawir(uint256 A,uint256 B) public pure returns(uint256){
    return  A + B;
}
```
- kenapa param 2 tp return cm 1 ?
krena kita emg cm mau ambil hasilnya doang bassicly angka = 1  uint256 is enough tho kira kira gitu

---
## 3 - kenapa hrs nulis view/pure?

kalo ga ditulis view/pure, function dianggep bisa modify state → kena gas fee tiap dipanggil.
kalo ditulis view/pure, function bisa dipanggil gratis dari luar (off-chain), ga kena gas.