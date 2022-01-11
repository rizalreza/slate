---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation Dompet Kilat Middleware API
---

# Introduction


<!-- Dokumentasi API  -->

Welcome to the Dompet Kilat Middleware API

Catatan : Mohon menginformasikan IP yang akan melakukan request ke API agar dimasukan ke withelist IP 


# Borrower

## Register Borrower


```shell
curl --location --request POST '{{host}}/v1/borrower/register' \
--header 'Content-Type: application/json' \
--data-raw '{
    "map" : "PERSONAL_BORROWER",
    "productCode" : "95",
    "phoneNumber" : "62123123123",
    "email" : "johndoe@mail.com",
    "fullName" : "John",
    "idNumber" : "362638287638783",
    "birthDate" : "30/09/1999"
}'
```

> Response Sukses:

```json
{
    "status": "00",
    "message": "success",
    "data": {
        "id": 139,
        "borrowerBankId": 0,
        "jobId": 0,
        "jobTypeId": 0,
        "jobOnlineId": 0,
        "incomeId": 0,
        "assetId": 0,
        "referenceId": 0,
        "workExperienceId": 0,
        "emergencyContactId": 0,
        "maritalId": 0,
        "educationId": 0,
        "religionId": 0,
        "borrowerType": "PERSONAL_BORROWER",
        "phoneNumber": "62123123123",
        "idNumber": "362638287638783",
        "email": "johndoe@mail.com",
        "fullName": "John",
        "gender": "",
        "birthDate": "1999-09-30T00:00:00Z",
        "birthPlace": "",
        "address": "",
        "village": "",
        "subdistrict": "",
        "city": "",
        "province": "",
        "postalCode": "",
        "motherMaidenName": "",
        "jobPosition": null,
        "familyCard": "",
        "npwp": "",
        "fotoKtp": null,
        "fotoSelfie": null,
        "isVerified": false,
        "status": "",
        "borrowerBanks": null,
        "jobs": null,
        "jobTypes": null,
        "jobOnlines": null,
        "incomes": null,
        "assets": null,
        "borrowerReferences": null,
        "workExperiences": null,
        "emergencyContacts": null,
        "maritals": null,
        "educations": null,
        "religions": null,
        "createdAt": "2022-01-11T06:16:30Z",
        "updatedAt": "2022-01-11T06:16:30Z",
        "deletedAt": null
    }
}
```

> Response Jika Gagal (Sudah Terdaftar):

```json
{
    "data": {},
    "status": "02",
    "message": "Error 1062: Duplicate entry '362638287638783' for key 'id_number'"
}
```


API Registrasi Borrower.

### HTTP Request

`POST {{host}}/v1/borrower/register`

### HTTP Headers

Name     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
Content-Type       | application/json   |     Ya    | - |

### Request Body

Field     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
map       | varchar   |     Ya    | PERSONAL_BORROWER |
productCode       | varchar   |     Ya    | Kode Produk |
phoneNumber       | number   |     Ya    | Nomor Handphone Peminjam yang akan dijadikan sebagai username peminjam. Hanya boleh diawali dengan angka 62. phoneNumber harus unik (tidak boleh duplikat). |
email       | varchar   |     Ya    | Email Peminjam. Email harus unik (tidak boleh duplikat). |
fullName           | varchar   |     Ya    | Nama Lengkap Peminjam |
idNumber           | varchar(16)   |     Ya    | Berisi Nomor Induk Kependudukan (NIK). NIK harus unik (tidak boleh duplikat).|
birthDate           | varchar   |     Ya    | Tanggal Lahir Peminjam. Format: (dd/MM/yyyy) Contoh: 30/09/1999 |


## Get Data Borrower


```shell
curl --location --request GET '{{host}}v1/borrower/{idNumber}'
```

> Response Sukses:

```json
{
    "status": "00",
    "message": "success",
    "data": {
        "map": "PERSONAL_BORROWER",
        "productCode": "95",
        "phoneNumber": "62123123123",
        "idNumber": "362638287638783",
        "email": "johndoe@mail.com",
        "fullName": "John",
        "gender": "L",
        "birthDate": "30/09/1999",
        "birthPlace": "Jakarta",
        "officeName": "PT ABC",
        "startDate": "15/04/2001",
        "address": "Jl Merdeka No. 20",
        "village": "Kampung Jawa",
        "subdistrict": "Tanah Abang",
        "city": "Jakarta Pusat",
        "province": "DKI Jakarta",
        "postalCode": "10250",
        "plafons": "1000000",
        "job": "Karyawan Swasta",
        "jobType": "Perantara Keuangan",
        "jobOnline": "Berbasis Internet / online",
        "income": "Rp 5.934.041 - Rp 11.868.080",
        "asset": "Rp 50.000.001 - Rp 500.000.000",
        "homeOwnership": "MILIK SENDIRI",
        "religion": "Islam",
        "maritalStatus": "BELUM KAWIN",
        "education": "SARJANA",
        "motherMaidenName": "Shizuka",
        "emergencyContactNumber": "6281234567892",
        "emergencyContactName": "Banu",
        "emergencyContactRelationship": "Saudara",
        "bankName": "BANK SINARMAS",
        "bankAccountNumber": "007812342",
        "familyCard": "123123123123123",
        "workExperience": "> 3 Tahun",
        "fotoKtp": "iVBORw0KGgoAAAANSUhEUgAAA+gAAAPoCAYAAABNo9TkAAAgAElEQVR4nOzd+ VcTf7ru/fOnP2fv091fBZkcUeZ5HpRBQRQQEUGcERRBEMhQQ+a5klzPD9UJGFNJZeK uJhrWuFxhBopffaL941/J//9/8BYub3z//wXuP/1s9a/asda",
        "fotoSelfie": "iVBORw0KGgoAAAANSUhEUgAAA+gAAAPoCAYAAABNo9TkAAAgAElEQVR4nOzd+ VcTf7ru/fOnP2fv091fBZkcUeZ5HpRBQRQQEUGcERRBEMhQQ+a5klzPD9UJGFNJZeK uu/JhrWuFxhBopffaL941/J//9/8BYub3z//wXuP/1s9a/asda",
        "loanData": {
            "tenor": 2,
            "unit": "MONTH",
            "amount": "1000000",
            "contractNo": "TEKENAJA-01FS3YVWZEZ93CBTRHJ724N5CH",
            "contractDate": "11/01/2022"
        },
        "references": {
            "interest": "1.0",
            "businessAddress": "Jl. Kyai Tapa",
            "businessVillage": "Grogol",
            "businessSubdistrict": "Grogol Petamburan",
            "businessCity": "Jakarta Barat",
            "businessProvince": "DKI Jakarta",
            "businessOwnership": "MILIK SENDIRI",
            "npwp": "123456789012345",
            "jobPosition": "Staff Akunting"
        }
    }
}
```

> Response Jika Gagal (Data Tidak Ditemukan):

```json
{
    "data": {},
    "status": "001",
    "message": "IdNumber 3626382876387831 record not found"
}
```


API GET Data Borrower.

### HTTP Request

`GET {{host}}/v1/borrower/{idNumber}`

### HTTP Headers

Name     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
Content-Type       | application/json   |     Ya    | - |

# Loan
## Pengajuan Pinjaman


```shell
curl --location --request POST '{{host}}/v1/loan/register' \
--header 'Content-Type: application/json' \
--data-raw '{
    "map" : "PERSONAL_BORROWER",
    "productCode" : "95",
    "phoneNumber" : "62123123123",
    "email" : "johndoe@mail.com",
    "fullName" : "John",
    "idNumber" : "362638287638783",
    "gender" : "L",
    "birthPlace" : "Jakarta",
    "birthDate" : "30/09/1999",
    "officeName" : "PT ABC",
    "startDate" : "15/04/2001",
    "address" : "Jl Merdeka No. 20",
    "village" : "Kampung Jawa",
    "subdistrict": "Tanah Abang",
    "city": "Jakarta Pusat",
    "province": "DKI Jakarta",
    "postalCode": "10250",
    "plafons": "1000000",
    "job": "Karyawan Swasta",
    "jobType": "Perantara Keuangan",
    "jobOnline": "Berbasis Internet / online", 
    "income": "Rp 5.934.041 - Rp 11.868.080", 
    "homeOwnership": "MILIK SENDIRI", 
    "emergencyContactRelationship": "Saudara", 
    "emergencyContactName": "Banu", 
    "emergencyContactNumber": "6281234567892", 
    "religion": "Islam",
    "maritalStatus": "BELUM KAWIN",
    "education": "SARJANA", 
    "motherMaidenName": "Shizuka",
    "bankName": "BANK SINARMAS", 
    "bankAccountNumber": "007812342", 
    "asset":"Rp 50.000.001 - Rp 500.000.000", 
    "familyCard": "123123123123123", 
    "workExperience": "> 3 Tahun",
    "fotoKtp":"iVBORw0KGgoAAAANSUhEUgAAA+gAAAPoCAYAAABNo9TkAAAgAElEQVR4nOzd+ VcTf7ru/fOnP2fv091fBZkcUeZ5HpRBQRQQEUGcERRBEMhQQ+a5klzPD9UJGFNJZeK uJhrWuFxhBopffaL941/J//9/8BYub3z//wXuP/1s9a/asda",
    "fotoSelfie" : "iVBORw0KGgoAAAANSUhEUgAAA+gAAAPoCAYAAABNo9TkAAAgAElEQVR4nOzd+ VcTf7ru/fOnP2fv091fBZkcUeZ5HpRBQRQQEUGcERRBEMhQQ+a5klzPD9UJGFNJZeK uu/JhrWuFxhBopffaL941/J//9/8BYub3z//wXuP/1s9a/asda",
    "loanData": { 
        "tenor": 2,
        "unit": "MONTH",
        "amount": "1000000" 
    },
    "references": {
        "interest": "1.0",
        "businessAddress": "Jl. Kyai Tapa", 
        "businessVillage": "Grogol", 
        "businessSubdistrict": "Grogol Petamburan", 
        "businessCity": "Jakarta Barat", 
        "businessProvince": "DKI Jakarta", 
        "businessOwnership": "MILIK SENDIRI", 
        "npwp": "123456789012345",
        "jobPosition": "Staff Akunting"
    }
}
'
```

> Response Sukses:

```json
{
    "status": "00",
    "message": "success",
    "data": {
        "id": 141,
        "borrowerId": 139,
        "productId": 2,
        "state": 1,
        "status": "INACTIVE",
        "loanCode": "",
        "plafons": 1000000,
        "tenor": 2,
        "tenorUnit": "MONTH",
        "amount": 1000000,
        "contractNo": "",
        "contractDate": null,
        "interest": "1.0",
        "updatedAt": "2022-01-11T06:58:03.866405316Z",
        "createdAt": "2022-01-11T06:16:30Z",
        "deletedAt": null
    }
}
```

> Response Jika Gagal (Sudah Terdaftar):

```json
{
    "data": {},
    "status": "001",
    "message": "borrower with idNumber 362638287638712, is not found"
}
```


API Pengajuan Pinjaman.

### HTTP Request

`POST {{host}}/v1/loan/register`


### HTTP Headers

Name     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
Content-Type       | application/json   |     Ya    | - |

### Request Body

Field     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
map       | varchar   |     Ya    | PERSONAL_BORROWER |
productCode       | varchar   |     Ya    | Kode produk |
phoneNumber       | number   |     Ya    | Nomor handphone peminjam yang akan dijadikan sebagai username peminjam. Hanya boleh diawali dengan angka 62. phoneNumber harus unik (tidak boleh duplikat). |
email       | varchar   |     Ya    | Email peminjam. email harus unik (tidak boleh duplikat). |
fullName           | varchar   |     Ya    | Nama lengkap peminjam |
idNumber           | varchar(16)   |     Ya    | Berisi Nomor Induk Kependudukan (NIK). NIK harus unik (tidak boleh duplikat).|
gender           | varchar(1)   |     Ya    | Berisi kode jenis kelamin (L/P) |
birthPlace           | varchar   |     Ya    | Tempat lahir peminjam |
birthDate           | varchar   |     Ya    | Tanggal lahir peminjam. Format: (dd/MM/yyyy) Contoh: 30/09/1999 |
officeName           | varchar   |     Ya    | Nama kantor tempat peminjam |
startDate           | date   |     Ya    | Tanggal berdiri usaha peminjam atau mulai bekerja. Format: (dd/MM/yyyy = 15/04/2001) |
address           | varchar   |     Ya    | Alamat peminjam |
village           | varchar   |     Ya    | Desa/kelurahan peminjam |
subdistrict           | varchar   |     Ya    | Kecamatan peminjam |
city           | varchar   |     Ya    | Kota peminjam |
province           | varchar   |     Ya    | Provinsi peminjam |
postalCode           | varchar   |     Ya    | Kode Pos peminjam |
plafons           | varchar   |     Ya    | Plafons yang akan diberikan kepada peminjam |
job           | varchar   |     Ya    | Pekerjaan peminjam |
jobType           | varchar   |     Ya    | Jenis pekerjaan peminjam |
jobOnline           | varchar   |     Ya    | Data usaha online sesuai mapping yang diberikan |
income           | varchar   |     Ya    | Rentang penghasilan peminjam |
homeOwnership           | varchar   |     Ya    | Status kepemilikan rumah |
emergencyContactName           | varchar   |     Ya    | Nama kontak darurat peminjam |
emergencyContactNumber           | varchar   |     Ya    | Nomor handphone kontak darurat peminjam. Hanya boleh diawali dengan angka 62. |
emergencyContactRelationship           | varchar   |     Ya    | Hubungan peminjam dengan kontak darurat |
religion           | varchar   |     Ya    | Agama peminjam |
maritalStatus           | varchar   |     Ya    | Status perkawinan peminjam |
education           | varchar   |     Ya    | Pendidikan terakhir peminjam |
motherMaidenName           | varchar   |     Ya    | Nama gadis ibu kandung peminjam |
bankName           | varchar   |     Ya    | Nama bank peminjam |
bankAccountNumber           | varchar   |     Ya    | Nomor rekening bank peminjam |
asset           | varchar   |     Ya    | Rentang nilai aset peminjam |
familyCard           | varchar   |     Ya    | Nomor kartu keluarga peminjam |
workExperience           | varchar   |     Ya    | Pengalaman bekerja peminjam |
fotoKtp           | varchar   |     Ya    | Link file foto KTP peminjam |
fotoSelfie           | varchar   |     Ya    | Link file foto selfie peminjam |
loanData           | JSON   |     Ya    | Rincian pinjaman |
references           | JSON   |     Ya    | Referensi |

# Disbursement
## Callback Disbursement


```shell
curl --location --request POST '{{host}}/v1/loan/disburse' \
--header 'Content-Type: application/json' \
--data-raw '{
    "transactionId"  : "cb82f2ea-901d-49cc-97d3-34846d8d8e29",
    "loanCode" : "LC1635132008",
    "bankCode" : "BNI",
    "paymentAccountNumber" : "8808999966040139",
    "status" : "active",
    "loanAmount" : 1000000,
    "loanAmountPaid" : 0,
    "tenor": 4,
    "tenorUnit" : "day",
    "numberOfPay" : 0,
    "histories" : null
}'
```

> Response Sukses:

```json
{
  "status": "00",
  "message": "success",
  "data": nil
}

```


API Callback Informasi Pencairan Dana

### HTTP Request

`POST {{host}}/v1/loan/register`


### HTTP Headers

Name     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
Content-Type       | application/json   |     Ya    | - |

### Request Body

Field     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
transactionId       | varchar   |     Ya    | Transaction ID referensi |
loanCode       | varchar   |     Ya    | Kode pinjaman |
bankCode       | varchar   |     Ya    | Kode bank untuk pencairan |
paymentAccountNumber       | varchar   |     Ya    | No VA untuk repayment |
status       | varchar   |     Ya    | Status Pinjaman, active, completed, rejected, closed |
loanAmount       | int   |     Ya    | Jumlah pinjaman |
loanAmountPaid       | int   |    Tidak    | Jumlah pembayaran (will be filled when re-payment) |
tenor       | int   |     Ya    | Jumlah lama pinjaman |
tenorUnit       | varchar   |     Ya    | Tipe tenor pinjaman |
numberOfPay       | int   |     Tidak    | Jumlah pembayaran yang sudah di lakukan (will be filled when re- payment) |
histories       | Array   |     Tidak    | Object array data pembayaran |


# Repayment
## Callback Repayment


```shell
curl --location --request POST '{{host}}/v1/callback/loan/repayment' \
--header 'Content-Type: application/json' \
--data-raw '{
    "transactionId"  : "cb82f2ea-901d-49cc-97d3-34846d8d8e29",
    "loanCode" : "LC1635132008",
    "bankCode" : "BNI",
    "paymentAccountNumber" : "8808999966040139",
    "status" : "completed",
    "loanAmount" : 1000000,
    "loanAmountPaid" : 250000,
    "tenor": 4,
    "tenorUnit" : "day",
    "numberOfPay" : 1,
    "histories": [
        {
            "transactionTime": "2021-10-25T15:20:16.921Z", 
            "paymentAmount": 250000
        } 
    ]
}'
```

> Response Sukses:

```json
{
  "status": "00",
  "message": "success",
  "data": nil
}

```


API callback informasi pembayaran dari customer

### HTTP Request

`POST {{host}}/v1/callback/loan/repayment`


### HTTP Headers

Name     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
Content-Type       | application/json   |     Ya    | - |

### Request Body

Field     | Data Type | Mandatory | Keterangan        |
--------- | ----------| --------- | ----------------- |
transactionId       | varchar   |     Ya    | Transaction ID referensi |
loanCode       | varchar   |     Ya    | Kode pinjaman |
bankCode       | varchar   |     Ya    | Kode bank untuk pencairan |
paymentAccountNumber       | varchar   |     Ya    | No VA untuk repayment |
status       | varchar   |     Ya    | Status Pinjaman, active, completed, rejected, closed |
loanAmount       | int   |     Ya    | Jumlah pinjaman |
loanAmountPaid       | int   |    Tidak    | Jumlah pembayaran (will be filled when re-payment) |
tenor       | int   |     Ya    | Jumlah lama pinjaman |
tenorUnit       | varchar   |     Ya    | Tipe tenor pinjaman |
numberOfPay       | int   |     Tidak    | Jumlah pembayaran yang sudah di lakukan (will be filled when re- payment) |
histories       | Array   |     Tidak    | Object array data pembayaran |



<!-- <aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>  -->