# Data Allocation

-formula =  function(nama var) +(type data + data allocatio)+ visibilty
- 1. there 3 type for data allocation :

1. memory : data yg disimpen di memory itu sementara, ilang pas function selesai.

```solidity 
function contoh1(uint256[] memory _arr)internal{
    _arr[0] =100 // change value di index 0 ke 100 @ memory
} 
````

2. storage: kita ubaha data yang di storage(permanent),gas costnya mahal
- NOTE : visibilty utk storage wajib internal

- why? :karena storage = pointer ke data internal contract. orang dari luar (user, contract lain) gak punya akses ke storage lu — mereka cuma bisa kirim value biasa lewat transaksi.

    kalo function-nya public/external, orang luar bisa manggil. tapi mereka gak bisa kasih pointer storage sebagai argumen, karena storage-nya lu, bukan mereka. jadi gak masuk akal.

    internal/private = cuma dipanggil dari dalem contract. dari dalem, akses ke storage jelas ada. jadi kirim pointer storage sbg argumen masuk akal.


``` solidity
function contoh2(uint256[] storage _arr2)internal{
    _arr2[5] = 1; //ubah/isi index 5 jadi bervalue 1,  
}
```

3. calldata: konsepnya mirip sama memory tp cuma bs liat doang cuy ,gbs ubah apapun

``` solidity
function contoh3(uint256[] calldata _arr3)public {
    uint256 valueVar= _arr3[2]//ubah/isi index 5 jadi bervalue 3,  
}
``` 