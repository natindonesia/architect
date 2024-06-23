# 🪪 Identities

## User Identity Entity
The following properties for idt_users table (associative table for Users and Access):

| Name                | Type      | Description                                      | Unique | Required  |
|---------------------|-----------|--------------------------------------------------|--------|-----------|
| user_id             | String    | Foreign key from Users table                     |   ❌   |    ✅    |
| idt_personal_id     | INT       | Foreign key from Access table                    |   ❌   |    ✅    |


## Personal Identity Entity
The following properties for idt_personals table:

| Name              | Type      | Description                                             | Unique | Required  |
|-------------------|-----------|---------------------------------------------------------|--------|-----------|
| id                | INT       | Primary key, unique record ID                           |   ✅   |    ✅    |
| user_id           | INT       | Foreign key from User table                             |   ❌   |    ❌    |
| agama             | STRING    | Religion of the individual                              |   ❌   |    ❌    |
| alamat            | STRING    | Address of the individual                               |   ❌   |    ❌    |
| berlaku_hingga    | STRING    | Validity period of the ID                               |   ❌   |    ❌    |
| golongan_darah    | STRING    | Blood type of the individual                            |   ❌   |    ❌    |
| jenis_kelamin     | STRING    | Gender of the individual                                |   ❌   |    ❌    |
| kecamatan         | STRING    | Sub-district of the individual's address                |   ❌   |    ❌    |
| kelurahan_desa    | STRING    | Village/Urban village of the individual's address       |   ❌   |    ❌    |
| kewarganegaraan   | STRING    | Nationality of the individual                           |   ❌   |    ❌    |
| kota_kabupaten    | STRING    | City/Regency of the individual's address                |   ❌   |    ❌    |
| nama              | STRING    | Name of the individual                                  |   ❌   |    ❌    |
| nik               | STRING    | National ID number                                      |   ❌   |    ❌    |
| pekerjaan         | STRING    | Occupation of the individual                            |   ❌   |    ❌    |
| provinsi          | STRING    | Province of the individual's address                    |   ❌   |    ❌    |
| rt_rw             | STRING    | Neighborhood unit/community of the individual's address |   ❌   |    ❌    |
| status_perkawinan | STRING    | Marital status of the individual                        |   ❌   |    ❌    |
| tanggal_lahir     | DATE      | Birth date of the individual                            |   ❌   |    ❌    |
| tempat_lahir      | STRING    | Place of birth of the individual                        |   ❌   |    ❌    |
| ktp_image_file    | JSON      | JSON object containing KTP image file                   |   ❌   |    ❌    |
| verified_at       | DATETIME  | Timestamp when the record was verified                  |   ❌   |    ❌    |

NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.


Here is a sample of a identity data
...
{
  "id": "00000001",
  "alamat": "JUS AGUNG WAY HALIM",
  "agama": "ISLAM",
  "berlaku_hingga": "SEUMUR HIDUP",
  "golongan_darah": "-",
  "jenis_kelamin": "LAKI-LAKI",
  "kecamatan": "KEDATON",
  "kelurahan_desa": "KEDATON",
  "kewarganegaraan": "WNI",
  "kota_kabupaten": "BANDAR LAMPUNG",
  "nama": "JOHN DOE",
  "nik": "1871010907930009",
  "pekerjaan": "PELAJAR / MAHASISWA",
  "provinsi": "LAMPUNG",
  "rt_rw": "014/000",
  "status_perkawinan": "BELUM KAWIN",
  "tanggal_lahir": "1993-07-09",
  "tempat_lahir": "BANDAR LAMPUNG",
  "ktp_image_file": {
    "photo": "/9j/4AAQSkZJRgABAQAAAQABAAD/...",
    "sign": "/9j/4AAQSkZJRgABAQAAAQABAAD/..."
  },
  "verified_at": "2023-05-29T12:34:56",
}
...
