## enum
1. Apa — fixed list of choice, tipe data yg value-nya cuma boleh dari daftar tetap
2. Kapan — internal logic yg punya state jelas: role user, status delivery, status voting
3. Gimana — enum Role { admin, user } trus akses pake Role.admin
4. Gotcha — di balik layar dia uint8, gak bisa langsung di-print, harus cast