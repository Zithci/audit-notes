# Struct

____________
1. struct = container yang berisi campuran data dengan berbagai type :
- Example:

```solidity
        struct DeviceSpec{ //struct name

        //type data + var name
        string deviceModel;
        string androidVersion;
        uint256 currentOsVersion;
    }

```

- usecase : kalo ada s yang saling terkait dan kemungkinan susah utk di lepas better just be struct

- 2. bkin slot (declare state)buat simpen hasil dari struct itu sndiri contoh

```solidity
    /// declare buat simpen smua struct yang brusan kita bkin biar bs di pake di other other incoming functions  
    /// device di sini di pake buat simpen hasi dari struct
    DeviceSpec public device;

```
