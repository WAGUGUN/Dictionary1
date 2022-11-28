## Latihan Dictionary pada python membuat program crud sederhanaLatihan Dictionary pada python membuat program crud sederhana
1. Pertama kita buat buat folder Dictionary dan didalam kita buat file bernama Latihan1.py dan Praktikum.py.
  ![p6 1](https://user-images.githubusercontent.com/115972485/204191076-12624338-362f-4c7c-9c6e-9a1fde5a40f4.png)
  
2. Lalu buka Pratikum.py dan masukan coding sebagai berikut lalu run dengan mengetikan perintah berikut diterminal python Pratikum.py:
```
   print("===================================================================")
   print("Nama         :   Gugun Gunawan")
   print("NIM          :   312210280")
   print("Kelas        :   TI.22.B1")
   print("Mata Kuliah  :   Bahasa Pemrograman")
   print("===================================================================")

    # import tabulate 
   from tabulate import tabulate
    # membuat dictionary
   dict = {'Nama' : ['Ari', 'Dina'], 'Nomor Telepon' : [6281267888, 6287677776]}

    # menampilkan kontak ari pada dictionary
   print("menampilkan Nomor Telepon Ari")
   print(dict['Nomor Telepon'][0])
   print('')

    # menambah data baru Nama dan Nomor telepon
   print("Menambahkan data baru")
   dict['Nama'].append('Riko')
   dict['Nomor Telepon'].append('6287654544')
   print(dict)

    # merubah kontak dina 
    # mencari nama dina apakah didalam data Dictionary
   if 'Dina' in dict ['Nama']:
       # jika ada cari position dina ada di index berapa
       DinaIndex = dict['Nama'].index('Dina')
       # lalu dapatkan index untuk merubah no telepon
       dict['Nomor Telepon'][DinaIndex] =  6288999776
   else:
       print("Tidak ada namanya dina")
   print("Merubah Nomor telepon dina")
   print(dict)

    # menampilkan semua nama
   print("Menampilkan semua Nama")
   print(dict['Nama'])

    # menampilkan semua nomor
   print("Menampilkan semua Nomor")
   print(dict['Nomor Telepon'])

    # menampilkan semua Nama & Nomor Telepon
   print("Menampilkan semua Nama & Nomor Telepon")
   print(tabulate(dict, headers=["Nama", "Nomor Telepon"], tablefmt="fancy_grid"))
   ```
   Dan berikut hasinya:
   ![Praktikum6 1](https://user-images.githubusercontent.com/115972485/204191700-d2195e60-a4a1-4419-9006-38ace276950e.PNG)
   
3. Selanjutnya kita akan buat program crud sederhana dan berikut flowchart program yang akan dibuat
  ![image](https://user-images.githubusercontent.com/115972485/204191865-908a3259-5c6b-494c-9fa2-d35275418ebd.png)
  
4. Lalu buka file Praktikum1.py dan masukan codingan sebagai berikut lalu run dengan mengetikan perintah berikut diterminal python Praktikum1.py from tabulate
```
# Gugun Gunawan
# TI.22.B1
# 312210280

#Import tabulate
from tabulate import tabulate

dictmahasiswa = {
    'No': [],
    'Nim': [],
    'Nama': [],
    'Tugas': [],
    'UTS': [],
    'UAS': [],
    'Nilai Akhir': [],
}
no = 0
# Fungsi untuk menambahkan data


def tambahData(no):
    # Menginput data
    nim = int(input("Masukan Nim : "))
    nama = input("Masukan Nama : ")
    tugas = int(input("Masukan Nilai Tugas : "))
    uts = int(input("Masukan Nilai UTS : "))
    uas = int(input("Masukan NIlai UAS : "))
    nial_akhir = int(input("Masukan Nilai Tugas Akhir : "))
    # Menambah data
    dictmahasiswa['No'].append(no)
    dictmahasiswa['Nim'].append(nim)
    dictmahasiswa['Nama'].append(nama)
    dictmahasiswa['Tugas'].append(tugas)
    dictmahasiswa['UTS'].append(uts)
    dictmahasiswa['UAS'].append(uas)
    dictmahasiswa['Nilai Akhir'].append(nial_akhir)
    # print(tabulate(dictmahasiswa, headers=[
    #       'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))

# fungsi untuk mengedit data


def editData (nim):
    # cek jika ada nim tersebut di dictmahasiswa
    if nim in dictmahasiswa['Nim']:
        # cari posisi indexnya lalu simpan du nimIndex
        nimIndex = dictmahasiswa['Nim'].index(nim)
        print("Pilih data yang mau diedit")
        # perulangan mengedit data dalam bentuk pilihan
        while True:
            editApa = int(input(
                "(1) Nim, \n (2) Nama, \n (3) Nilai Tugas, \n (4) Nilai UTS, \n (5) Nilai UAS, \n (0) Simpan Perubahan & Exit \n :"))
            if editApa == 1:
                # Merubah Nim
                newNim = int(input("Masukan Nim :"))
                dictmahasiswa['Nim'][nimIndex] = newNim
            elif editApa == 2:
                # Merubah Nama
                newNama = input("Masukan Nama :")
                dictmahasiswa['Nama'][nimIndex] = newNama
            elif editApa == 3:
                # Merubah nilai tugas & nilai akhir
                newTugas = int(input("Masukan Nilai Tugas :"))
                nilai_akhir = (newTugas * 30 / 100) + (dictmahasiswa['UTS'][nimIndex] * 35 / 100) + (
                    dictmahasiswa['UAS'][nimIndex] * 35 / 100)
                dictmahasiswa['Tugas'][nimIndex] = newTugas
                dictmahasiswa['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa == 4:
                # Meeubah nilai uts & nilai akhir
                newUTS = int(input("Masukan Nilai UTS :"))
                nilai_akhir = (dictmahasiswa['Tugas'][nimIndex] * 30 / 100) + (newUTS * 35 / 100) + (
                    dictmahasiswa['UAS'][nimIndex] * 35 / 100)
                dictmahasiswa['UTS'][nimIndex] = newUTS
                dictmahasiswa['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa == 5:
                # Menambah nilai uas & nilai akhir
                newUAS = int(input("Masukan Nilai UAS :"))
                nilai_akhir = (dictmahasiswa['Tugas'][nimIndex] * 35 / 100) + (dictmahasiswa['UTS'][nimIndex] * 35 / 100) + (
                    newUAS * 35 / 100)
                dictmahasiswa['UAS'][nimIndex] = newUAS
                dictmahasiswa['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa == 0:
                break
    else:
        print("Data tidak ditemukan")

# Fungsi menghapus data
def deleteData(nim):
    if nim in dictmahasiswa['Nim']:
        nimIndex = dictmahasiswa['Nim'].index(nim)
        # Menghapus data berdasarkan position index pada nim
        del dictmahasiswa['No'][nimIndex]
        del dictmahasiswa['Nim'][nimIndex]
        del dictmahasiswa['Nama'][nimIndex]
        del dictmahasiswa['Tugas'][nimIndex]
        del dictmahasiswa['UTS'][nimIndex]
        del dictmahasiswa['UAS'][nimIndex]
        del dictmahasiswa['Nilai Akhir'][nimIndex]
        print("Data berhasil dihapus")
    else:
        print("Data tidak dapat ditemukan")

# Fungsi untuk mencari data

def cariData(nim):
    if nim in dictmahasiswa['Nim']:
        nimIndex = dictmahasiswa['Nim'].index(nim)
        # MEnuimpan data hasil pencarian berdasarkan nim
        hasilCari = {
            'No': dictmahasiswa['No'][nimIndex],
            'Nim': dictmahasiswa['Nim'][nimIndex],
            'Nama': dictmahasiswa['Nama'][nimIndex],
            'Tugas': dictmahasiswa['Tugas'][nimIndex],
            'UTS': dictmahasiswa['UTS'][nimIndex],
            'UAS': dictmahasiswa['UAS'][nimIndex],
            'Nilai Akhir': dictmahasiswa['Nilai Akhir'][nimIndex],
        }
        print(hasilCari)
    else:
        print("Data tidak ditemukan")

# Melakukan perulangan menggunakan while sampai user menekan huruf K perulangan akan berhenti
while True:
    # Opsi input pilihan C,R,U,D,F,Q
    tanya = input(
        "(C) Menambah Data,\n (R) Melihat semua Data,\n (U) Mengubah Data,\n (D) Menghapus Data,\n (F) Mencari Data,\n (Q) Keluar Program : ")
    
    if tanya == "C":
        while True:
            no =+ 1
            # Memanggil fungsi tambahData dan memparsing data no
            tambahData(no)
            tambahDataLagi = input("Tambah Data lagi? (y/n) :")
            if tambahDataLagi == 'n':
                break
    elif tanya == "R":
        # Menampilkan data dalam bentuk table package tabulate
        print(tabulate(dictmahasiswa, headers=[
            'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid")) 
    elif tanya == "U":
        print(tabulate(dictmahasiswa, headers=[
            'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid")) 
        nim = input(int('Masukan NIM untuk edit data :'))
        editData(nim)
    elif tanya == "D":
        print(tabulate(dictmahasiswa, headers=[
            'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))
        nim = input(int('Masukan NIM yang mau dihapus :'))
    elif tanya == "F":
        nim = int(input('masukan NIM untuk melihat detail Data :'))
        cariData(nim)
    elif tanya == "Q":
        break
```

Dan berikut hasilnya:
![Praktikum6 2](https://user-images.githubusercontent.com/115972485/204193323-bb028eff-8de2-4fb8-8c45-098bdbcef540.PNG)

# Selesai. Seperti itulah program crud sederhana yang sudah kita buat.
## Terima Kasih
