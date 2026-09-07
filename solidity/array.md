# Array
_______________

## Apa itu array
- List berurutan yg nyimpen banyak data dengan tipe SAMA
- Akses pake index (mulai dari 0)
- 2 jenis:
  - Dynamic: `uint256[] arr;` (ukuran bisa berubah)
  - Fixed: `uint256[10] arr;` (ukuran tetap 10)

## Declare array

```solidity
uint256[] public arr;              // dynamic, kosong
uint256[] public arr2 = [1,2,3];   // dynamic, ada isi
uint256[10] public myFixedArr;     // fixed size 10, isi default 0 semua
```

- Fixed size array = semua slot otomatis keisi 0
- Bebas tipe apa aja (uint256[], address[], bool[], string[], dll)
- Satu array = satu tipe, gak bisa campur

## Index vs Value
- Index = posisi (0, 1, 2, ...)
- Value = isi (10, 20, 30, ...)
- `arr.push(10)` → arr = [10], value: 10, index: 0
- `arr.push(20)` → arr = [10,20], value: 20, index: 1

## Method built-in

```solidity
arr.push(value);      // nambah element di akhir (dynamic only)
arr.pop();            // hapus element terakhir (dynamic only)
arr.length;           // jumlah element
delete arr[index];    // reset element di index tertentu ke default
```

- `delete arr[1]` pada [1,2,3,4] → hasil [1,0,3,4]
- delete gak hapus beneran, cuma reset value ke default, panjang tetep

## Formula function
- Butuh input dari luar → pake param
- Cuma interaksi ke state → gak butuh param
- `push(value)` → butuh param (mau push apa?)
- `pop()` → gak butuh (auto yg terakhir)
- `getLength()` → gak butuh (cuma baca)
- `get(index)` → butuh param (ambil dari index mana?)
- `remove(index)` → butuh param (hapus index mana?)

Contoh function lengkap:

```solidity
function push(uint256 i) public {
    arr.push(i);
}

function pop() public {
    arr.pop();
}

function get(uint256 i) public view returns (uint256) {
    return arr[i];
}

function getLength() public view returns (uint256) {
    return arr.length;
}

function remove(uint256 index) public {
    delete arr[index];
}
```

## Out of bounds
- Akses index yg gak ada = revert
- Array kosong akses index apapun = revert
- Fuzz random index (uint256) sering bikin revert karena angka gede
- Fix: push dulu di setUp biar array ada isi, atau hardcode index kecil
