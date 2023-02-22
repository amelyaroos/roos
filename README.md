import math as m

#Database
ListPasienRumahSakit = [
    {
        "IDPasien" : 1,
        "Nama Pasien" : "Gerry",
        "Usia Pasien" : 25,
        "Jenis Kelamin" : "Pria",
        "Penyakit" : "Maag",
        "Poli" : "SpPD",
        "Biaya Pengobatan" : 170000,  
    },
    {
        "IDPasien" : 2,
        "Nama Pasien" : "Ghina",
        "Usia Pasien" : 5,
        "Jenis Kelamin" : "Wanita",
        "Penyakit" : "Demam",
        "Poli" : "SpA",
        "Biaya Pengobatan" : 150000,  
    },
    {
        "IDPasien" : 3,
        "Nama Pasien" : "Fira",
        "Usia Pasien" : 18,
        "Jenis Kelamin" : "Wanita",
        "Penyakit" : "Flu",
        "Poli" : "Umum",
        "Biaya Pengobatan" : 100000,
    }
]

# Function List Semua Database
def TampilkanListSemuaDataPasien() :
    if len(ListPasienRumahSakit)==0 :
        print("Tidak Ada List Data Pasien")
    else:
        print('IDPasien\t|Nama Pasien\t|Jenis Kelamin\t| Usia Pasien\t| Penyakit\t| Poli\t\t| Biaya Pengobatan')
        for i in range(len(ListPasienRumahSakit)):
            print('{}\t\t|{}\t\t|{}\t\t| {}\t\t| {}\t\t| {}\t\t| {}\t'.format(ListPasienRumahSakit[i].get('IDPasien'),ListPasienRumahSakit[i].get('Nama Pasien'),ListPasienRumahSakit[i].get('Jenis Kelamin'),ListPasienRumahSakit[i].get('Usia Pasien'),ListPasienRumahSakit[i].get('Penyakit'),ListPasienRumahSakit[i].get('Poli'),ListPasienRumahSakit[i].get('Biaya Pengobatan')))

#Function untuk update data
def UpdateData(key, id:int, value):
    for i, k in enumerate(list(ListPasienRumahSakit[0].keys())):
        if(str(key).strip().casefold() == k.strip().casefold()):
            newValue = {k:value}
            ListPasienRumahSakit[id].update(newValue)
            break

#function untuk cek apakah id unique
def isUniqueId(id):
    for i in range(len(ListPasienRumahSakit)):
        if(ListPasienRumahSakit[i].get('IDPasien') == id):
            return False
    return True
        
# mencari index dengan id yang diberikan
def getIndexByID(id):
    for i in range(len(ListPasienRumahSakit)):
        if(ListPasienRumahSakit[i].get('IDPasien') == id):
            return i
    return -1

# Menu Read Data
def MenampilkanListPasienRumahSakit() :
    while True:
        PilihanMenuRead = int(input('''
        List Data Pasien Rumah Sakit Brawijaya
        
        1. Data Seluruh Pasien
        2. Filter Pencarian Data Pasien Tertentu
        3. Kembali ke Menu Utama
        
        Silahkan Masukkan Pilihan Menu Read Data Pasien : '''))
        if PilihanMenuRead == 1:
            if len(ListPasienRumahSakit)==0 :
                print("Tidak Ada List Data Pasien")
            else:
                TampilkanListSemuaDataPasien()
        elif PilihanMenuRead == 2:
            IDPasien = int(input("Masukkan IDPasien: "))
            print()
            while True: 
                for i in range(len(ListPasienRumahSakit)):
                    if IDPasien == ListPasienRumahSakit[i].get('IDPasien'):
                        print('IDPasien\t|Nama Pasien\t|Jenis Kelamin\t| Usia Pasien\t| Penyakit\t| Poli\t\t| Biaya Pengobatan')
                        print('{}\t\t|{}\t\t|{}\t\t| {}\t\t| {}\t\t| {}\t\t| {}\t'.format(ListPasienRumahSakit[i].get('IDPasien'),ListPasienRumahSakit[i].get('Nama Pasien'),ListPasienRumahSakit[i].get('Jenis Kelamin'),ListPasienRumahSakit[i].get('Usia Pasien'),ListPasienRumahSakit[i].get('Penyakit'),ListPasienRumahSakit[i].get('Poli'),ListPasienRumahSakit[i].get('Biaya Pengobatan')))
                        break
                    elif i == len(ListPasienRumahSakit):
                        print("Maaf ID Pasien Tidak Ada")
                        break
                break
        elif PilihanMenuRead == 3:
            Back = input("Apakah Anda Ingin Kembali ke Menu Utama? (Y/N) : ")
            Back = Back.upper()
            if Back == 'Y':
                break
            elif Back == 'N':
                continue
            else:
                print("Silahkan Ketik 'Y' Jika Ingin Kembali ke Menu Utama atau Ketik 'N' Jika Ingin Menggagalkan")
                continue
        else:
            print("Maaf, Menu yang Anda pilih tidak tersedia. Silahkan Memilih Menu yang lain")
        
#Menu Create Data
def MenambahkanDataPasienRumahSakit() :
    while True:
        pilihanMenambahkanPasien = int(input('''
        Menambahkan Data Pasien Rumah Sakit Brawijaya
        
        1. Menambah Data Pasien Baru 
        2. Kembali ke Menu Utama
        
        Silahkan Masukkan Pilihan Menu : '''))
        print()
        if pilihanMenambahkanPasien == 1:
            IDPasien = int(input('''
            Silahkan Masukkan ID Pasien : '''))
            print()
            if isUniqueId(IDPasien):
                NamaPasien = input("Masukkan Nama Pasien : ")
                UsiaPasien = int(input("Masukkan Usia Pasien : "))
                JenisKelamin = input("Masukkan Jenis Kelamin Pasien : ")
                Penyakit = input("Masukkan Penyakit Yang Dialami : ")
                Poli = input("Masukkan Poli Yang Dikunjungi : ")
                BiayaPengobatan = int(input("Masukkan Biaya Pengobatan : "))
                MenambahData = input("Apakah Anda Yakin Ingin Menambah Data Ini? (Y/N) : ")
                print()
                if MenambahData.casefold() == 'Y'.casefold():
                    print("Data Berhasil Disimpan")
                    ListPasienRumahSakit.append({"IDPasien": IDPasien,"Nama Pasien": NamaPasien,"Usia Pasien": UsiaPasien,"Jenis Kelamin": JenisKelamin,"Penyakit": Penyakit,"Poli": Poli,"Biaya Pengobatan": BiayaPengobatan})
                    TampilkanListSemuaDataPasien()
                    break
                elif MenambahData.casefold() == 'N'.casefold():
                    print("Data Gagal Disimpan")
                    break
                else:
                    print("Menu yang Anda masukkan tidak ada. Silahkan ketik 'Y' jika ingin data disimpan atau 'N' jika tidak ingin data disimpan")
                    break
            else:
                print("Tidak Dapat Menambah Daftar Pasien Karena ID Tersebut Sudah Ada")
                break
        elif pilihanMenambahkanPasien == 2:
            Back = input("Apakah Anda Ingin Kembali ke Menu Utama? (Y/N) : ")
            if Back.casefold() == 'Y'.casefold():
                break
            elif Back.casefold() == 'N'.casefold():
                continue
            else:
                print("Silahkan Ketik 'Y' Jika Ingin Kembali ke Menu Utama atau Ketik 'N' Jika Ingin Menggagalkan")
                continue
        else:
            print("Maaf, Menu yang Anda pilih tidak tersedia. Silahkan Memilih Menu yang lain")

#Menu Update Data
def MengubahDataPasien():
    while True:
        PilihanMengubahData = int(input('''
        Mengubah Data Pasien Rumah Sakit Brawijaya
        
        1. Mengubah Data Pasien
        2. Kembali ke Menu Utama
        
        Silahkan Masukkan Pilihan Menu : '''))
       
        if PilihanMengubahData == 1:
            IDPasien = int(input("Masukkan ID Pasien : "))
            print()
            for i in range(len(ListPasienRumahSakit)):
                if IDPasien == ListPasienRumahSakit[i].get("IDPasien"):
                    print('IDPasien\t|Nama Pasien\t|Jenis Kelamin\t| Usia Pasien\t| Penyakit\t| Poli\t\t| Biaya Pengobatan')
                    print('{}\t\t|{}\t\t|{}\t\t| {}\t\t| {}\t\t| {}\t\t| {}\t'.format(ListPasienRumahSakit[i].get('IDPasien'),ListPasienRumahSakit[i].get('Nama Pasien'),ListPasienRumahSakit[i].get('Jenis Kelamin'),ListPasienRumahSakit[i].get('Usia Pasien'),ListPasienRumahSakit[i].get('Penyakit'),ListPasienRumahSakit[i].get('Poli'),ListPasienRumahSakit[i].get('Biaya Pengobatan')))
                    YakinMengubahData = input("Apakah Anda Yakin Ingin Mengubah Data Pasien? (Y/N)")
                    YakinMengubahData = YakinMengubahData.upper()
                    print()
                    if YakinMengubahData == 'Y':
                        Data = input("Masukkan Data Pasien Yang Ingin Diubah")
                        Data = Data.strip().lower()
                        if Data == 'IDPasien'.casefold():
                            print("Maaf, ID Pasien Tidak Dapat Diubah")
                            break
                        elif Data in list({k.strip().lower(): v for k, v in ListPasienRumahSakit[i].items()}):
                            newValue = input(f"Masukkan {Data} baru : ")
                            YakinMengubahData2 = input(f"Apakah Anda Yakin Ingin Mengubah Data {Data}'? (Y/N)")
                            YakinMengubahData2 = YakinMengubahData2.upper()
                            if YakinMengubahData2 == "Y":
                                UpdateData(Data, i, newValue)
                                print()
                                print(f"Data '{Data}' berhasil diubah dan disimpan")
                                TampilkanListSemuaDataPasien()
                                break
                            elif YakinMengubahData2 == "N":
                                print(f"Data {Data} tidak jadi diubah")
                                break
                            else:
                                print("Silahkan Ketik 'Y' Jika Ingin Menyimpan Data Yang Telah Diubah atau 'N' Jika Ingin Membatalkan Mengubah Data Pasien")
                                break
                        else:
                            print(f"Maaf Data '{Data}' Tidak Ada")
                            break
                    elif YakinMengubahData == 'N':
                        print("Data Pasien Tidak Jadi Diubah")
                        break
                    else:
                        print("Silahkan Ketik 'Y' Jika Ingin Mengubah Data Pasien atau 'N' Jika Ingin Membatalkan Mengubah Data Pasien")
                        break
                elif i == len(ListPasienRumahSakit):
                    print("Maaf ID Pasien Tidak Ada")
                    break
        elif PilihanMengubahData == 2:
            inginKembali = input("Apakah Anda Ingin Kembali ke Menu Utama? (Y/N) : ")
            if inginKembali.casefold() == 'Y'.casefold():
                break
            elif inginKembali.casefold() == 'N'.casefold():
                continue
            else:
                print("Silahkan Ketik 'Y' Jika Ingin Kembali ke Menu Utama atau Ketik 'N' Jika Ingin Tetap di Menu Mengubah Data Pasien")
                continue
        else:
            print("Maaf, Menu yang Anda pilih tidak tersedia. Silahkan Memilih Menu yang lain")

#Menu Delete Data
def MenghapusDataPasien():
    while True:
        pilihanMenghapusData = int(input('''
        Menghapus Data Pasien Rumah Sakit Brawijaya
        
        1. Hapus Data Pasien
        2. Kembali ke Menu Utama
        
        Silahkan Masukkan Pilihan Menu : '''))
        print()
        if pilihanMenghapusData == 1:
            IDPasien = int(input("Masukkan ID Pasien Yang Ingin Di Hapus : "))
            i = getIndexByID(IDPasien)
            if(i != -1):
                print('IDPasien\t|Nama Pasien\t|Jenis Kelamin\t| Usia Pasien\t| Penyakit\t| Poli\t\t| Biaya Pengobatan')
                print('{}\t\t|{}\t\t|{}\t\t| {}\t\t| {}\t\t| {}\t\t| {}\t'.format(ListPasienRumahSakit[i].get('IDPasien'),ListPasienRumahSakit[i].get('Nama Pasien'),ListPasienRumahSakit[i].get('Jenis Kelamin'),ListPasienRumahSakit[i].get('Usia Pasien'),ListPasienRumahSakit[i].get('Penyakit'),ListPasienRumahSakit[i].get('Poli'),ListPasienRumahSakit[i].get('Biaya Pengobatan')))
                YakinMenghapusData = input("Apakah Anda Yakin Ingin Menghapus Data Pasien? (Y/N)")
                print()
                if YakinMenghapusData.casefold() == 'Y'.casefold():
                    print("Data Pasien Berhasil Dihapus")
                    del ListPasienRumahSakit[i]
                    break
                elif YakinMenghapusData.casefold() == 'N'.casefold():
                    print("Data Batal Untuk Dihapus")
                    break
                else:
                    print("Silahkan Ketik 'Y' Jika Ingin Melanjutkan Penghapusan Data atau 'N' Jika Ingin Membatalkan Penghapusan Data")
            else:
                print()
                print("Pasien Yang Anda Cari Tidak Ada")
                break

        elif pilihanMenghapusData == 2:
            inginKembali = input("Apakah Anda Ingin Kembali ke Menu Utama? (Y/N) : ")
            if inginKembali.casefold() == 'Y'.casefold():
                break
            elif inginKembali.casefold() == 'N'.casefold():
                continue
            else:
                print("Silahkan Ketik 'Y' Jika Ingin Kembali ke Menu Utama atau Ketik 'N' Jika Ingin Tetap di Menu Mengubah Data Pasien")
                continue
        else:
            print("Maaf, Menu yang Anda pilih tidak tersedia. Silahkan Memilih Menu yang lain")

# Menu Transaksi Pengobatan
def MembayarBiayaPengobatan():
    TampilkanListSemuaDataPasien()
    while True :
        IDPasien = int(input('Masukkan ID pasien: '))
        indexPasien = getIndexByID(IDPasien)
        if(indexPasien != -1) :
            print('IDPasien\t|Nama Pasien\t|Jenis Kelamin\t| Usia Pasien\t| Penyakit\t| Poli\t\t| Biaya Pengobatan')
            print('{}\t\t|{}\t\t|{}\t\t| {}\t\t| {}\t\t| {}\t\t| {}\t'.format(ListPasienRumahSakit[indexPasien].get('IDPasien'),ListPasienRumahSakit[indexPasien].get('Nama Pasien'),ListPasienRumahSakit[indexPasien].get('Jenis Kelamin'),ListPasienRumahSakit[indexPasien].get('Usia Pasien'),ListPasienRumahSakit[indexPasien].get('Penyakit'),ListPasienRumahSakit[indexPasien].get('Poli'),ListPasienRumahSakit[indexPasien].get('Biaya Pengobatan')))
            break
        else :
            print('ID Pasien Tidak Ditemukan!')
            checker = input('Ingin membayar yang lain? (Y/N) = ')
            if checker.casefold() == 'N'.casefold() :
                break

    print('Daftar Biaya Pengobatan: ')
    print('IDPasien\t|Nama Pasien\t|Jenis Kelamin\t| Usia Pasien\t| Penyakit\t| Poli\t\t| Biaya Pengobatan')
    print('{}\t\t|{}\t\t|{}\t\t| {}\t\t| {}\t\t| {}\t\t| {}\t'.format(ListPasienRumahSakit[indexPasien].get('IDPasien'),ListPasienRumahSakit[indexPasien].get('Nama Pasien'),ListPasienRumahSakit[indexPasien].get('Jenis Kelamin'),ListPasienRumahSakit[indexPasien].get('Usia Pasien'),ListPasienRumahSakit[indexPasien].get('Penyakit'),ListPasienRumahSakit[indexPasien].get('Poli'),ListPasienRumahSakit[indexPasien].get('Biaya Pengobatan')))
    

    BIAYAPENGOBATAN = ListPasienRumahSakit[indexPasien].get('Biaya Pengobatan')

    while True :
        print('Total Yang Harus Dibayar = Rp.{}'.format(BIAYAPENGOBATAN))
        jmlUang = int(input('Masukkan Jumlah Uang : '))
        NAMAPASIEN = input('Masukkan Nama Anda : ')
        if(jmlUang >= BIAYAPENGOBATAN) :
            Kembalian = jmlUang - BIAYAPENGOBATAN

            if(Kembalian > 0):
                print('Terima kasih {} \n\nUang kembali anda sebesar : {}'.format(NAMAPASIEN, Kembalian))
            else:
                print('Terima kasih {}'.format(NAMAPASIEN))
            del ListPasienRumahSakit[indexPasien]
            break
        else :
            Kekurangan = BIAYAPENGOBATAN - jmlUang
            print('Maaf {}, Uang Anda Kurang Sebesar: {}'.format(NAMAPASIEN, Kekurangan))

# Function Main Menu
def main():
    global runProgram
    PilihanMenuUtama = input('''
    Selamat Datang di Rumah Sakit Brawijaya
    
    1. Lihat Data Pasien Rumah Sakit
    2. Menambahkan Data Pasien Rumah Sakit
    3. Mengubah Data Pasien
    4. Menghapus Data Pasien
    5. Melakukan Transaksi Pengobatan
    6. Exit Program
    
    Masukkan Pilihan Menu Utama : ''')
    if PilihanMenuUtama == '1' :
        MenampilkanListPasienRumahSakit()
    elif PilihanMenuUtama == '2' :
        MenambahkanDataPasienRumahSakit()
    elif PilihanMenuUtama == '3' :
        MengubahDataPasien()
    elif PilihanMenuUtama == '4' :
        MenghapusDataPasien()
    elif PilihanMenuUtama == '5' :
        MembayarBiayaPengobatan()
    elif PilihanMenuUtama == '6' :
        print('Program Berhenti Untuk Dijalankan')
        runProgram = False
    else :
        print('Maaf, Menu Yang Dipilih Tidak Ada. Silahkan Pilih Menu Utama Yang Tersedia')

if __name__ == "__main__":
    runProgram = True
    while(runProgram):
        main()
