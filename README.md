# praktikum5
data_mahasiswa = {}

def hitung_akhir(tugas, uts, uas):
    return (tugas * 0.30) + (uts * 0.35) + (uas * 0.35)

while True:
    print("\nProgram Input Nilai")
    print("========================")
    print("(L)ihat, (T)ambah, (U)bah, (H)apus, (C)ari, (K)eluar")
    menu = input("Pilih menu : ").lower()

    # Tampilkan Data
    if menu == "l":
        print("\nDaftar Nilai")
        print("====================================================================")
        print("| NO |   NIM   |  NAMA  | TUGAS | UTS | UAS | AKHIR |")
        print("====================================================================")

        if len(data_mahasiswa) == 0:
            print("|                     TIDAK ADA DATA                              |")
        else:
            no = 1
            for nim, item in data_mahasiswa.items():
                print(f"| {no:2d} | {nim:6s} | {item['nama']:6s} | "
                      f"{item['tugas']:5d} | {item['uts']:3d} | {item['uas']:3d} | "
                      f"{item['akhir']:5.2f} |")
                no += 1

        print("====================================================================")

    # Tambah Data
    elif menu == "t":
        print("\nTambah Data")
        nim   = input("NIM        : ")
        nama  = input("Nama       : ")
        uts   = int(input("Nilai UTS  : "))
        uas   = int(input("Nilai UAS  : "))
        tugas = int(input("Nilai Tugas: "))

        akhir = hitung_akhir(tugas, uts, uas)

        data_mahasiswa[nim] = {
            "nama": nama,
            "tugas": tugas,
            "uts": uts,
            "uas": uas,
            "akhir": akhir
        }

        print("Data berhasil ditambahkan!")

    # Ubah Data
    elif menu == "u":
        nim = input("Masukkan NIM yang akan diubah: ")
        if nim in data_mahasiswa.keys():
            print("Ubah Data untuk", data_mahasiswa[nim]["nama"])
            nama  = input("Nama baru       : ")
            uts   = int(input("Nilai UTS baru  : "))
            uas   = int(input("Nilai UAS baru  : "))
            tugas = int(input("Nilai Tugas baru: "))

            akhir = hitung_akhir(tugas, uts, uas)

            data_mahasiswa[nim] = {
                "nama": nama,
                "tugas": tugas,
                "uts": uts,
                "uas": uas,
                "akhir": akhir
            }
            print("Data berhasil diubah!")
        else:
            print("Data dengan NIM tersebut tidak ditemukan.")

    # Hapus Data
    elif menu == "h":
        nim = input("Masukkan NIM yang akan dihapus: ")
        if nim in data_mahasiswa:
            del data_mahasiswa[nim]
            print("Data berhasil dihapus!")
        else:
            print("Data tidak ditemukan.")

    # Cari Data
    elif menu == "c":
        nim = input("Masukkan NIM yang dicari: ")
        if nim in data_mahasiswa:
            item = data_mahasiswa[nim]
            print("\nData ditemukan:")
            print(f"NIM   : {nim}")
            print(f"Nama  : {item['nama']}")
            print(f"Tugas : {item['tugas']}")
            print(f"UTS   : {item['uts']}")
            print(f"UAS   : {item['uas']}")
            print(f"Akhir : {item['akhir']:.2f}")
        else:
            print("Data tidak ditemukan.")

    # Keluar
    elif menu == "k":
        print("Program selesai.")
        break

    else:
        print("Menu tidak tersedia!")
