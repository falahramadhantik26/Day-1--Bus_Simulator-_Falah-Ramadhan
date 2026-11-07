# Day-1--Bus_Simulator-_Falah-Ramadhan
# Day 1 – Dokumentasi Workshop: Building with AI, Managing Change with GitHub


## Deskripsi Repository

Repository ini berisi dokumentasi pribadi saya selama mengikuti workshop Day 1 pada kegiatan OSJUR. Isinya adalah rangkuman materi, poin penting yang saya pelajari, dan pendapat saya tentang Day 1 Proyek Workshop.

## Tujuan Repository

- Menjadi catatan terstruktur materi workshop yang bisa dibuka kembali kapan saja.
- Memenuhi tugas dokumentasi Day 1 dari panitia.
- Menjadi latihan langsung penggunaan Git dan GitHub (membuat repository, commit, dan push).

## Informasi Kegiatan Workshop

| Keterangan | Detail |
|---|---|
| Judul | Building with AI, Managing Change with GitHub |
| Pemateri | Nugi Farhan (Senior Product Designer, 6 tahun pengalaman) |
| Hari | Day 1 |
| Tema | Membuat dan mengembangkan dengan AI, serta manajemen perubahan dan kolaborasi dengan Git/GitHub |

### Capaian Pembelajaran

- Menjelaskan bagaimana prompt AI yang lebih spesifik menghasilkan hasil yang lebih baik.
- Membedakan Git dan GitHub.
- Mengidentifikasi repository, commit, branch, dan pull request.
- Melakukan version controlling.

---

## 1. Rangkuman Materi

### A. Prompt Engineering

**Pengertian.** Prompt adalah instruksi atau masukan yang diberikan ke model AI untuk mendapatkan hasil tertentu. Bentuknya bisa berupa pertanyaan sederhana, kata kunci, instruksi rumit, atau potongan kode. Prompt engineering adalah cara merancang instruksi agar jawaban AI tepat, relevan, dan layak digunakan.

**Context is key.** Prompt tanpa konteks (misalnya "Create student task planner") menghasilkan jawaban yang umum dan tidak terarah. Prompt dengan konteks memberi AI tujuan, kebutuhan, dan batasan yang jelas.

**Struktur prompt yang baik:**

| Elemen | Fungsi | Contoh dari materi |
|---|---|---|
| Role | Peran yang diminta dari AI | "You are helping me build a beginner-friendly student task planner..." |
| Task | Tujuan yang ingin dicapai | Membuat task planner untuk mahasiswa tahun pertama |
| Context | Kebutuhan dan batasan | Daftar tugas, filter status, gunakan HTML/CSS/vanilla JS |
| Format | Bentuk output yang diminta | Kode lengkap tiap file, cara menjalankan, cara menguji |

**Taktik tambahan** (sumber: Google Cloud, *What is prompt engineering*):
- Gunakan kata kerja aksi untuk menentukan tindakan.
- Tentukan panjang dan format output.
- Tentukan target audiens.
- Sertakan fakta dan data yang relevan.
- Rujuk sumber atau dokumen tertentu.
- Definisikan istilah dan konsep kunci.

**Keuntungan prompt engineering:** meningkatkan performa model AI, mengurangi bias dan respons yang ofensif, meningkatkan kontrol dan prediktabilitas, serta memberi pengalaman yang lebih baik.

### B. Git dan GitHub

**Git** adalah version control system terdistribusi (DVCS) yang melacak siapa, kapan, dan apa saja yang diubah dalam suatu file. Git dibuat oleh Linus Torvalds pada 2005 dan bekerja secara lokal.

**GitHub** adalah platform berbasis web untuk menyimpan repository Git secara online dan mendukung kolaborasi.

**Alur kerja Git (3 area):**

| Area | Penjelasan |
|---|---|
| Working directory | Salinan satu versi proyek yang sedang dikerjakan di komputer |
| Staging area (index) | Tempat menampung perubahan yang akan masuk ke commit berikutnya |
| .git directory (repository) | Tempat Git menyimpan metadata dan object database proyek; bagian ini yang disalin saat `clone` |

Alurnya: **edit file → `git add` (staging) → `git commit` (repository) → `git push` (GitHub)**.

**Perintah dasar:**

```bash
git init                         # memulai repo baru
git add .                        # memindahkan file ke staging area
git commit -m "message"          # menyimpan perubahan ke repository
git remote add origin <url>      # menghubungkan repo lokal ke GitHub
git push origin main             # mengirim perubahan ke GitHub
git pull origin main             # mengambil dan menggabungkan perubahan dari GitHub
git clone "url"                  # menyalin repo dari GitHub
```

**Varian `git add`:** `git add --all` dan `git add -A` menambahkan semua perubahan di repository. `git add .` menambahkan semua file di direktori saat ini beserta isinya. `git add *` menambahkan file yang cocok dengan wildcard di shell.

### C. Setup Environment

1. **Git:** install sesuai perangkat, cek dengan `git --version`.
2. **Identitas Git:**
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your-email@example.com"
   git config --global --list
   ```
3. **VS Code:** install, lalu pasang perintah `code` lewat Command Palette (`Ctrl/Cmd+Shift+P` → *Shell Command: Install 'code' command in PATH*), cek dengan `code --version`.
4. **SSH key untuk GitHub:**
   ```bash
   ssh-keygen -t ed25519 -C "email@domain.com"
   eval "$(ssh-agent -s)"
   ssh-add --apple-use-keychain ~/.ssh/id_ed25519   # macOS
   pbcopy < ~/.ssh/id_ed25519.pub                   # salin public key
   ```
   Lalu tambahkan key di GitHub: *Settings → SSH and GPG keys → New SSH key*, dan verifikasi dengan `ssh -T git@github.com`.

   > Ed25519 adalah skema tanda tangan kurva eliptik (EdDSA pada Curve25519) yang aman dan cepat.

5. **Cek setup:** `git --version`, `git config --global user.name`, `git config --global user.email`, `code --version`, `ssh -T git@github.com`.

### D. Proyek Hari Ini: Student Task Planner

Alur pengerjaan proyek:
1. Siapkan platform AI (Claude, Antigravity, ChatGPT).
2. Tulis prompt untuk membuat web/aplikasi.
3. Tambahkan ke Git dengan `git init`.
4. Commit dan push ke GitHub.
5. Lakukan perubahan.
6. Commit dan push kembali ke GitHub.

---

## 2. Poin Penting dan Pengetahuan Baru

- Hasil AI sangat bergantung pada kualitas prompt. Struktur **Role, Task, Context, Format** membuat output lebih terarah.
- Meminta AI memverifikasi hasilnya ("jangan klaim aplikasi berjalan sebelum diverifikasi") membantu mengurangi jawaban asal.
- **Git ≠ GitHub.** Git adalah alat version control lokal, GitHub adalah layanan online untuk menyimpan dan berkolaborasi.
- Git punya tiga area (working directory, staging area, repository), dan perubahan harus melewati `add` lalu `commit` sebelum di-`push`.
- Commit message yang jelas membantu melacak siapa mengubah apa dan kapan.
- Autentikasi SSH key lebih praktis dan aman dibanding memasukkan kredensial setiap kali push.
- Slide pembuka menyebut alur darurat: `git commit` → `git push` → keluar gedung. Intinya, simpan dan cadangkan pekerjaan secara rutin.

---

## 3. Pendapat Pribadi tentang Day 1 Proyek Workshop

Menurut saya Day 1 adalah pembuka yang pas karena menggabungkan dua hal yang saling melengkapi: membuat sesuatu dengan bantuan AI, lalu mengelola dan menyimpan hasilnya dengan Git dan GitHub. Sebagai mahasiswa baru, saya sebelumnya mengira prompt hanyalah "bertanya ke AI". Ternyata ada struktur yang membuat hasilnya jauh lebih baik. Bagian Git dan GitHub awalnya terasa banyak istilah baru, tetapi penjelasan tentang tiga area Git dan praktik langsung membuatnya lebih mudah dipahami. Proyek sederhana seperti Student Task Planner juga cocok untuk pemula karena hasilnya langsung terlihat. Harapan saya, di hari-hari berikutnya kami bisa berlatih lebih banyak soal branch, pull request, dan kolaborasi dalam tim.


