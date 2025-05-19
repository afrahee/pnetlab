# pnetlab
Jika kamu sudah mengatur BIOS agar VT-x (Virtualization Technology) aktif dan Hyper-V dinonaktifkan, tetapi fitur Nested Virtualization (Nested VT) masih belum aktif di VM kamu, maka kemungkinan masalahnya ada pada konfigurasi VM atau sistem host. Berikut beberapa langkah untuk memastikan Nested VT aktif dengan benar:

✅ Checklist Aktivasi Nested VT
1. Pastikan Virtualisasi Diaktifkan di BIOS
✅ Intel VT-x atau AMD-V diaktifkan.

✅ Intel VT-d (opsional, tapi berguna untuk passthrough/performance).

2. Pastikan Hyper-V Sepenuhnya Dinonaktifkan (jika menggunakan VMware/VirtualBox)
Jalankan perintah ini di CMD (as Administrator):

<pre><code>bcdedit /set hypervisorlaunchtype off</code></pre>
Restart PC setelah itu.

Catatan: Jika kamu menggunakan WSL2, itu membutuhkan Hyper-V — jadi nested VT bisa konflik.

🎯 Jika kamu menggunakan VMware Workstation / Player
Aktifkan Nested Virtualization:
Matikan VM terlebih dahulu.

Buka file .vmx dari VM-mu.

Tambahkan baris ini:

<pre><code>vhv.enable = "TRUE"</code></pre>
Simpan file .vmx, lalu buka ulang VMware dan jalankan VM.

🎯 Jika kamu menggunakan VirtualBox
Matikan VM.

Jalankan perintah berikut (di CMD/PowerShell):
<pre><code>VBoxManage modifyvm "Nama_VM" --nested-hw-virt on</code></pre>
Jalankan VM kembali.
