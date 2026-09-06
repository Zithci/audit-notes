### Delete mapping

- Delete = reset value di key tertentu ke DEFAULT (bukan hapus beneran)
- Mapping-nya tetep ada, cuma value di key itu ke-reset
- Sama efek-nya kayak: myMap[_key] = 0 (buat uint)
- Formula:
```solidity
delete namaMapping[_key];
```
- Contoh function:
```solidity
function remove(address _addr) public {
    delete myMap[_addr];
}
```

### Set vs Get vs Delete — kenapa returns beda

- set → ubah state, gak balikin apa-apa → GAK PAKE returns
- delete → ubah state (reset ke default), gak balikin apa-apa → GAK PAKE returns
- get → tugasnya ngasih tau isi mapping → WAJIB pake returns
