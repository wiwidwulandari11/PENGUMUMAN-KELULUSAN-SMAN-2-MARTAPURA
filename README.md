<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pengumuman Kelulusan XII SMAN 2 Martapura</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            min-height: 100vh;
            color: white;
        }
        .glass-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 1.5rem;
        }
        .countdown-item {
            background: rgba(59, 130, 246, 0.1);
            border: 1px solid rgba(59, 130, 246, 0.2);
            padding: 1rem;
            border-radius: 1rem;
            min-width: 75px;
        }
        .fade-in {
            animation: fadeIn 0.6s ease-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        input:disabled {
            background-color: rgba(255, 255, 255, 0.05);
            cursor: not-allowed;
            color: rgba(255, 255, 255, 0.3);
        }
    </style>
</head>
<body class="flex items-center justify-center p-4">

    <div class="max-w-2xl w-full text-center fade-in">
        <!-- Header Sekolah -->
        <div class="mb-8">
            <div class="bg-blue-600 w-16 h-16 rounded-2xl flex items-center justify-center mx-auto mb-4 shadow-lg shadow-blue-500/20">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path d="M12 14l9-5-9-5-9 5 9 5z" />
                    <path d="M12 14l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14z" />
                </svg>
            </div>
            <h1 class="text-3xl md:text-4xl font-bold mb-1 tracking-tight">SMAN 2 MARTAPURA</h1>
            <p class="text-blue-400 font-medium tracking-widest uppercase text-sm">Portal Pengumuman Kelulusan 2026</p>
        </div>

        <!-- Tampilan Utama -->
        <div id="main-view" class="glass-card p-6 md:p-10 shadow-2xl relative overflow-hidden">
            
            <div class="absolute -top-10 -right-10 w-32 h-32 bg-blue-500/10 rounded-full blur-3xl"></div>
            <div class="absolute -bottom-10 -left-10 w-32 h-32 bg-indigo-500/10 rounded-full blur-3xl"></div>

            <!-- Bagian Countdown -->
            <div id="countdown-wrapper" class="mb-10">
                <h2 class="text-gray-400 text-sm mb-4 uppercase font-semibold">Pengumuman akan dibuka dalam:</h2>
                <div class="flex justify-center gap-3 md:gap-4 text-center">
                    <div class="countdown-item">
                        <span id="days" class="text-3xl font-bold block text-blue-400">00</span>
                        <span class="text-[10px] uppercase text-gray-400">Hari</span>
                    </div>
                    <div class="countdown-item">
                        <span id="hours" class="text-3xl font-bold block text-blue-400">00</span>
                        <span class="text-[10px] uppercase text-gray-400">Jam</span>
                    </div>
                    <div class="countdown-item">
                        <span id="minutes" class="text-3xl font-bold block text-blue-400">00</span>
                        <span class="text-[10px] uppercase text-gray-400">Menit</span>
                    </div>
                    <div class="countdown-item">
                        <span id="seconds" class="text-3xl font-bold block text-blue-400">00</span>
                        <span class="text-[10px] uppercase text-gray-400">Detik</span>
                    </div>
                </div>
            </div>

            <!-- Pesan Belum Dibuka -->
            <div id="closed-message" class="mb-6 p-4 bg-yellow-500/10 border border-yellow-500/30 rounded-xl">
                <p class="text-yellow-200 text-sm">Akses pengecekan NISN belum dibuka. Silakan kembali pada waktu yang ditentukan.</p>
            </div>

            <!-- Form Input -->
            <div class="space-y-5">
                <div class="text-left">
                    <label for="nisn-input" class="block text-xs font-semibold text-gray-400 mb-2 ml-1 uppercase">Nomor Induk Siswa Nasional (NISN)</label>
                    <input type="text" id="nisn-input" disabled placeholder="Masukkan 10 digit NISN" 
                        class="w-full p-4 rounded-xl bg-white/10 border border-white/10 text-white focus:ring-2 focus:ring-blue-500 outline-none transition-all text-center text-xl font-bold tracking-widest">
                </div>
                <button id="check-btn" onclick="checkGraduation()" disabled
                    class="w-full bg-blue-600/50 cursor-not-allowed text-white/50 font-bold py-4 rounded-xl transition-all shadow-lg flex items-center justify-center gap-2">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
                    </svg>
                    Cek Kelulusan
                </button>
                <div id="error-msg" class="text-red-400 text-sm font-medium hidden">NISN tidak ditemukan. Pastikan nomor yang Anda masukkan benar.</div>
            </div>
        </div>

        <!-- Tampilan Hasil (Lulus) -->
        <div id="result-view" class="glass-card p-10 shadow-2xl hidden fade-in">
            <div class="mb-8">
                <div class="w-24 h-24 bg-green-500 rounded-full flex items-center justify-center mx-auto mb-6 shadow-xl shadow-green-500/30">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-14 w-14 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="4" d="M5 13l4 4L19 7" />
                    </svg>
                </div>
                <h1 class="text-4xl font-extrabold text-white mb-2 italic">SELAMAT!</h1>
                <h2 id="student-name" class="text-2xl text-blue-300 font-bold mb-6 uppercase tracking-tight">...</h2>
                <div class="bg-green-500 text-white py-2 px-8 rounded-full inline-block font-black text-xl shadow-lg">
                    ANDA LULUS
                </div>
            </div>

            <p class="text-gray-300 text-sm leading-relaxed mb-10 px-4">
                Berdasarkan hasil rapat pleno dewan guru SMAN 2 Martapura, Anda dinyatakan <strong>LULUS</strong>. 
                Silakan unduh Surat Keterangan Penetapan Kelulusan melalui tombol di bawah ini.
            </p>

            <div class="space-y-4">
                <a href="https://drive.google.com/drive/folders/1Pv7KfTJQ1LbMfA-K2UfwmS72hwlYZzeB?usp=sharing" target="_blank"
                    class="flex items-center justify-center gap-3 bg-white text-blue-900 font-bold py-4 px-8 rounded-xl hover:scale-105 transition-all shadow-xl w-full">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
                    </svg>
                    Download SK Kelulusan
                </a>
                <button onclick="resetView()" class="text-gray-500 hover:text-white text-xs font-medium uppercase tracking-widest transition-colors">
                    Periksa NISN Lain
                </button>
            </div>
        </div>

        <footer class="mt-10">
            <p class="text-gray-500 text-[10px] uppercase tracking-widest">&copy; 2026 Panitia Kelulusan SMAN 2 Martapura</p>
        </footer>
    </div>

    <script>
        // Database Siswa Lengkap (XII-1 sampai XII-8)
        const databaseSiswa = [
            // XII 1 (34 Siswa)
            {nama: "ABU ILHAM ISLAMMUDDIN", nisn: "0073962451"}, {nama: "Ahmad Husaini", nisn: "0067518986"}, {nama: "Ahmad Rafiq Ridwan", nisn: "0074471329"}, {nama: "Akhmad Rofhal Akhwan", nisn: "0072885445"}, {nama: "ANISA AULIA RAHMAN", nisn: "0071246209"}, {nama: "Artika Dwi Septiasa", nisn: "0078457349"}, {nama: "Badrudin", nisn: "0087366303"}, {nama: "Dewi Noor Isra", nisn: "3081024190"}, {nama: "Farel Eka Saputra", nisn: "0082604212"}, {nama: "GABRIELLE EZRA PAFORZA PAULO", nisn: "0089546986"}, {nama: "GITA SEPTIANA RAMADHAN", nisn: "0074818946"}, {nama: "Harmony Cinta Syntia Della", nisn: "0083637778"}, {nama: "Jamaliana", nisn: "0075851395"}, {nama: "Lenny Ellya Sari", nisn: "0087896236"}, {nama: "MAKAYLA SUKMA MUTIA", nisn: "0087763500"}, {nama: "MUHAMMAD AHDAN MUSYAFFA", nisn: "0087624425"}, {nama: "MUHAMMAD BAYU FEBRIAN", nisn: "0084770913"}, {nama: "MUHAMMAD INDRA", nisn: "0088306060"}, {nama: "MUHAMMAD NAJIB", nisn: "0074981647"}, {nama: "MUHAMMAD NOUVAL", nisn: "0089326414"}, {nama: "Muhammad Qasthalani", nisn: "0084767443"}, {nama: "MUHAMMAD RAFI DARMAWAN", nisn: "0072815215"}, {nama: "Muhammad Riswan Ilham", nisn: "0075439396"}, {nama: "Najwa Ayu Salsabila", nisn: "0088905341"}, {nama: "NAZWA AZIZAH", nisn: "0099115041"}, {nama: "Nazwa Nazzaro", nisn: "0085614929"}, {nama: "NEILIS SILFIA RACHMAN", nisn: "0083546713"}, {nama: "NUUR SYAMSA FITHRIANI", nisn: "0085422194"}, {nama: "Patimah", nisn: "0079406494"}, {nama: "Rahma Nada Handini", nisn: "0065082650"}, {nama: "Rizka Dewi Oktavia", nisn: "0074196242"}, {nama: "SHOPIA RAHMA", nisn: "0086719193"}, {nama: "TAMI NURAINI", nisn: "0085981661"}, {nama: "Zahro Tannur", nisn: "0085144092"},
            
            // XII 2 (36 Siswa)
            {nama: "Abdul Haris Sulthon Al Kahfi", nisn: "0073887693"}, {nama: "ADITYA RIZKY ERLANGGA", nisn: "0086306857"}, {nama: "Ahmad Humaidi", nisn: "0055168491"}, {nama: "Ahmad Solihin", nisn: "0088669692"}, {nama: "Aisyah Muslimah", nisn: "0089481108"}, {nama: "Allika Fernanda", nisn: "0085962858"}, {nama: "Aura Martha Az-zahra", nisn: "0082458309"}, {nama: "Dina Rahma Lestari", nisn: "0081266239"}, {nama: "FUJIA", nisn: "0084953029"}, {nama: "Indri Apriliani", nisn: "0082533177"}, {nama: "Isna", nisn: "0063055805"}, {nama: "Jihan Fitri Yani", nisn: "0084045905"}, {nama: "Khalisya Kyani Noor Syahrina", nisn: "0087469584"}, {nama: "Meisya Otavia Mentari", nisn: "0083752861"}, {nama: "MEY LISMA WATI", nisn: "0085089952"}, {nama: "Muhammad Aditya Rangga", nisn: "0083036922"}, {nama: "Muhammad Andhika Putra Dayyan", nisn: "0076329802"}, {nama: "Muhammad Hisyam Nazrulaya", nisn: "0075908771"}, {nama: "MUHAMMAD RIZKY FADILAH", nisn: "0082630235"}, {nama: "MUHAMMAD SAUFI", nisn: "0083739049"}, {nama: "Mutiara Muji Larasati", nisn: "0081295089"}, {nama: "NADIA ULFA", nisn: "0085537882"}, {nama: "NOOR SHILA", nisn: "0075943967"}, {nama: "Nor Azilla Silki Munayya", nisn: "0087578642"}, {nama: "NUR HUSNA RAMADHANI", nisn: "0074145937"}, {nama: "Nurul Madina", nisn: "0084758243"}, {nama: "OKTAVIA NIZAMMI ADNYZA", nisn: "0077474831"}, {nama: "Rachel Angellia Koesuma Putri", nisn: "0087800817"}, {nama: "RADITYA YOGA PRATAMA", nisn: "0083402071"}, {nama: "Reva Linda Oktavia", nisn: "0075046605"}, {nama: "Ridho Luthfi", nisn: "0085638435"}, {nama: "Rozita Dewi Vortuna", nisn: "0085344805"}, {nama: "SHEFI ADISTIA RAMADHANI", nisn: "0089819456"}, {nama: "Shella Putri Armyta", nisn: "0077177221"}, {nama: "SITI AISYAH NOPRIYANTI", nisn: "0099267583"}, {nama: "SITI ASVIA ULFA", nisn: "0087792743"},

            // XII 3 (35 Siswa)
            {nama: "Ahmad Riyan", nisn: "0079730110"}, {nama: "Aldiansyah Yusup Habibi", nisn: "0088012444"}, {nama: "ALIFIYA NAILA ANDINI", nisn: "0088192274"}, {nama: "Alya Kyani Noorsyahrida", nisn: "0088746464"}, {nama: "Anindya Gendis Witarani", nisn: "0081564002"}, {nama: "DIFFO NURINDRA BAKHTI", nisn: "0073791269"}, {nama: "DIZA HUMAIRO", nisn: "0085491699"}, {nama: "FAJAR DIAN UTAMI", nisn: "0087824976"}, {nama: "FARADILA EKSTI SYIFA NURAINI", nisn: "0077364612"}, {nama: "FATHURRAHMAN", nisn: "0073356954"}, {nama: "JIHAN ALMAYDA", nisn: "0079928514"}, {nama: "Luthfia Sartika Suri", nisn: "0088353494"}, {nama: "Mayda Resiana", nisn: "0084167437"}, {nama: "Melati Ismadinia Puspa Ningrum", nisn: "0083473987"}, {nama: "MUHAMMAD ABDULLAH HUSIN", nisn: "3074040585"}, {nama: "MUHAMMAD ARIFANSYAH", nisn: "0086097342"}, {nama: "MUHAMMAD DAMHANI", nisn: "3076981619"}, {nama: "Muhammad Firdaus Saputra", nisn: "0089068532"}, {nama: "MUHAMMAD RAYHAN", nisn: "0083179986"}, {nama: "MUHAMMAD RIZKY PRATAMA", nisn: "0081923643"}, {nama: "Muhammad Saputra Pandu Perdana", nisn: "0075648720"}, {nama: "MUTIARA", nisn: "0089194878"}, {nama: "NAYLA AULIA", nisn: "0061051156"}, {nama: "NOVI AULIA PUTRI", nisn: "0073692433"}, {nama: "Nur Hani'ah Putri", nisn: "0087263655"}, {nama: "Nur Shifa Seyla Azzahra", nisn: "0086341903"}, {nama: "NUR SYIFA RAMADHINI", nisn: "0088187118"}, {nama: "PUTRI RIZKY MAULIDA", nisn: "0085252308"}, {nama: "Rafika Amalia Putri", nisn: "0079685835"}, {nama: "Rima Yuliani", nisn: "0081909074"}, {nama: "Siska Ramadhani", nisn: "0069907832"}, {nama: "SYARIFAH NADDILLA NORWULANDARI", nisn: "0087873099"}, {nama: "VITA AYU MAHDALENA", nisn: "0088274337"}, {nama: "WASYFAH ALYA MUKHBITA", nisn: "0082137170"}, {nama: "Widia Aurelia", nisn: "0074303964"},

            // XII 4 (35 Siswa)
            {nama: "Ahmad Alief Madani", nisn: "0083232249"}, {nama: "Alina Putri", nisn: "0072512030"}, {nama: "AULIA RAHMAH", nisn: "0088731630"}, {nama: "DEVI PERMATA SARI", nisn: "0082755367"}, {nama: "Dwi Risma Zahra", nisn: "0087393283"}, {nama: "Eva Anindya Maisie Maheswari", nisn: "0086147493"}, {nama: "Firdausi Akbari", nisn: "3086425157"}, {nama: "Gusti Muhammad Zein Ramadhan", nisn: "0088593617"}, {nama: "Hary Purnomo Joyo", nisn: "0086131428"}, {nama: "Hidayah Putri Ramadhani", nisn: "0076994105"}, {nama: "Jihan Latifa", nisn: "0086688450"}, {nama: "Kirana Rahmadina", nisn: "0087902400"}, {nama: "Laily Solatiah", nisn: "0077963281"}, {nama: "M. Nabil Hibatullah", nisn: "0086366839"}, {nama: "MAULIDA", nisn: "0086479645"}, {nama: "MUHAMMAD AFGAN SAFUTRA", nisn: "0081526549"}, {nama: "Muhammad Arsyad", nisn: "0075198657"}, {nama: "MUHAMMAD AUFARRIDHA ALGIFARI", nisn: "0083520749"}, {nama: "Muhammad Fachri Rozzaq", nisn: "0088317887"}, {nama: "Muhammad Pasya Ramadhan", nisn: "0084515593"}, {nama: "Muhammad Rizqon Jazuli", nisn: "3078003850"}, {nama: "MUTIA INDAH SARI", nisn: "0087175650"}, {nama: "Nandif Difa Erliyandi", nisn: "0078208982"}, {nama: "Noor Zahro Ain", nisn: "0082891623"}, {nama: "NURIDAWATI", nisn: "0075143960"}, {nama: "PUTRI STEVANI MAHARANI", nisn: "0073790474"}, {nama: "RABIATUL HASANAH", nisn: "3072553541"}, {nama: "RADITYA PANDU ALVYANSYAH", nisn: "0089993928"}, {nama: "Rahmad Maulidin", nisn: "0083818303"}, {nama: "Raudhatun Najwa", nisn: "0088504856"}, {nama: "RUSIDA AFIFAH", nisn: "0084202581"}, {nama: "Salsabela Suci Oktaviani", nisn: "0089651558"}, {nama: "Shefia Adisti Ramadhani", nisn: "0084207514"}, {nama: "Tsani Nor Fazri", nisn: "0088206870"}, {nama: "Zahra", nisn: "0089840511"},

            // XII 5 (30 Siswa)
            {nama: "Achmad Syauki", nisn: "0085899140"}, {nama: "Ahmad", nisn: "0076352693"}, {nama: "AHMAD HABIBI", nisn: "0087242422"}, {nama: "ARIS", nisn: "0076633174"}, {nama: "AULIA SEPTIA RAMADHANI", nisn: "0087380951"}, {nama: "Ayudya Putri Maharani", nisn: "0082991983"}, {nama: "Bima Noor Pradana", nisn: "0073485414"}, {nama: "Desy Arlianti", nisn: "0073923509"}, {nama: "ENDA RAMDANI", nisn: "0075229409"}, {nama: "JANNATUN NISA", nisn: "0071671483"}, {nama: "Khairunnisa", nisn: "0075163052"}, {nama: "M. Ajwa Maulana", nisn: "0075573487"}, {nama: "M.RAFLI ILYAS SAPUTRA", nisn: "0082095700"}, {nama: "MAULANA HASAN", nisn: "0079258151"}, {nama: "MUHAMAD ROYYAN", nisn: "0074098082"}, {nama: "MUHAMMAD FAUZI CANDRA SAPUTRA", nisn: "0082744285"}, {nama: "Muhammad Firdaus", nisn: "0084771146"}, {nama: "MUHAMMAD HAFIDZI", nisn: "0071049955"}, {nama: "MUHAMMAD RAYHAN", nisn: "0082083250"}, {nama: "Muhammad Rifani", nisn: "0087698720"}, {nama: "Muhammad Yuda Febrian Maulana", nisn: "3087705243"}, {nama: "NAZWATUN AZIZAH", nisn: "0078094766"}, {nama: "Nisfa Aulia", nisn: "0071508244"}, {nama: "NUR MAHDALENA", nisn: "0077151621"}, {nama: "RAPIK", nisn: "0072969705"}, {nama: "Reivina Azhalia Dwi Emanda", nisn: "0071658457"}, {nama: "RISMATUL AULIA", nisn: "0084980711"}, {nama: "SITI MAWADDAH", nisn: "0089976421"}, {nama: "Weny", nisn: "0072831032"}, {nama: "WINDY PURWASIH SAFITRI", nisn: "0064185301"},

            // XII 6 (28 Siswa)
            {nama: "AHMAD PADILLAH", nisn: "0075958523"}, {nama: "AHMAD ZAINI ZEIN", nisn: "0074317391"}, {nama: "Akhmad Hanafi", nisn: "0085128943"}, {nama: "Annisa", nisn: "0085281737"}, {nama: "Azwa Zahra", nisn: "0056994902"}, {nama: "Betha Korlita", nisn: "0073299982"}, {nama: "Donny Rafijal Akhmad", nisn: "0086352469"}, {nama: "Eka Novitasari", nisn: "0081597552"}, {nama: "HUSNUL KHATIMAH", nisn: "0084032795"}, {nama: "Jika Andini", nisn: "0075650610"}, {nama: "khoirunnisa Azahra Yanza", nisn: "0082895083"}, {nama: "Kurniawan Firdaus", nisn: "0088764567"}, {nama: "M. Najihan Maududi", nisn: "0084989875"}, {nama: "MUHAMMAD ADHI NUR RAYA", nisn: "0082727051"}, {nama: "Muhammad Nur Ilyas", nisn: "0071554558"}, {nama: "Muhammad Rafi Setiawan", nisn: "0087435879"}, {nama: "Muhammad Rio Al - Gazali", nisn: "0076900033"}, {nama: "MUHAMMAD SAIDILLAH", nisn: "0079574572"}, {nama: "NABILA ZALFA KIRANA PABEANG", nisn: "0078353862"}, {nama: "Nikky Dimas Armando", nisn: "0078286249"}, {nama: "NOOR SHILI", nisn: "0074461373"}, {nama: "NOR FITRIANI", nisn: "0063202630"}, {nama: "Nur Azizah", nisn: "0071761769"}, {nama: "RAHMAT HIDAYAT", nisn: "0086033391"}, {nama: "SALFINA KAMALIA", nisn: "3078159153"}, {nama: "Siti Khadijah", nisn: "0079808664"}, {nama: "SITI MAYSYAROH DWI RAMADANI", nisn: "0074680273"}, {nama: "Widya Noviantari", nisn: "0077769000"},

            // XII 7 (30 Siswa)
            {nama: "Ade Rieswan Saputra", nisn: "0068494998"}, {nama: "Ahmad Baihaqi", nisn: "0074932394"}, {nama: "AHMAD RIFKI", nisn: "0066661007"}, {nama: "AHMAD ZIKRI ALFAJAR", nisn: "0083572318"}, {nama: "Alisha Nuur Fiyantika", nisn: "0099207006"}, {nama: "BAHRUL ILMI", nisn: "0052262394"}, {nama: "CANDY PUTRI HARIANI", nisn: "0072165059"}, {nama: "DINA KAMALIYA", nisn: "0062964784"}, {nama: "Fahry", nisn: "3088550643"}, {nama: "Laila Shalatiah", nisn: "0069815117"}, {nama: "M. Hasanudin", nisn: "0073209323"}, {nama: "M. RIDWAN", nisn: "0071259172"}, {nama: "Muhammad Afriza Ramadhani", nisn: "0076669289"}, {nama: "MUHAMMAD ALFIN", nisn: "0074327845"}, {nama: "Muhammad Khulaifi", nisn: "0083138528"}, {nama: "Muhammad Raihan Alfarizi", nisn: "0077295288"}, {nama: "MUHAMMAD SYIFA RISANDI", nisn: "0068464494"}, {nama: "Muhammad Yudha Atmanto", nisn: "0077917530"}, {nama: "Nabila Nur Kamilah", nisn: "0078502685"}, {nama: "NAILA SHOLEHAH", nisn: "0072733631"}, {nama: "NOR RAYA AQWAN", nisn: "0073994855"}, {nama: "NUR HALIZA", nisn: "0087418690"}, {nama: "Rahmawati", nisn: "0071816736"}, {nama: "RIDHA SOVIA AZZAHRA", nisn: "0083917927"}, {nama: "Rizki Ridho Pratama", nisn: "0083336621"}, {nama: "Ryan Al Azhar", nisn: "0086635377"}, {nama: "SAUGI MUBAROK", nisn: "0074564135"}, {nama: "SHOPIA", nisn: "0089440855"}, {nama: "Veronica Juliani Putri", nisn: "0084756135"}, {nama: "Yoggi Pristiardi", nisn: "0052116555"},

            // XII 8 (26 Siswa)
            {nama: "Achmad Dhani Maulana", nisn: "0078621768"}, {nama: "AHMAD MAULANA", nisn: "0071615390"}, {nama: "Amanda Devia Indriani", nisn: "0076386746"}, {nama: "CAHAYA INDRI", nisn: "0085262059"}, {nama: "Chairil Firdaus", nisn: "0089888638"}, {nama: "Faujiah", nisn: "0063526649"}, {nama: "M. Irwan", nisn: "0079486031"}, {nama: "M.RIPAI", nisn: "0069074196"}, {nama: "Muhamad Ramadani", nisn: "0068105336"}, {nama: "Muhammad Fikri Hidayat", nisn: "0079584969"}, {nama: "MUHAMMAD MAULANA", nisn: "0086839930"}, {nama: "Muhammad Noval", nisn: "3089802104"}, {nama: "Muhammad Ridho Alpiansyah", nisn: "0081133182"}, {nama: "MUHAMMAD RIFAN", nisn: "0086269053"}, {nama: "Muhammad Rifqi Fadillah", nisn: "3074222032"}, {nama: "MUHAMMAD RIZALDI NOOR", nisn: "0069691055"}, {nama: "MUHAMMAD RIZKI MAULANA", nisn: "0075097412"}, {nama: "NAFIAN KURNIAWAN", nisn: "0088389288"}, {nama: "NAPISAH", nisn: "0086785829"}, {nama: "NUR HAMIDAH", nisn: "0076433416"}, {nama: "Nurnazwa Sabila", nisn: "0071124106"}, {nama: "RAISSA ADISTY PUTRI", nisn: "3089699474"}, {nama: "Rendy Maulana", nisn: "0082687491"}, {nama: "Ridhoni", nisn: "0078900122"}, {nama: "Septia Ramadina", nisn: "0071726474"}, {nama: "SUPIANNOR", nisn: "0077182887"}
        ];

        // KONFIGURASI WAKTU: 4 MEI 2026, 12:00 WITA
        const targetDate = new Date("May 4, 2026 12:00:00").getTime();

        function updateCountdown() {
            const now = new Date().getTime();
            const distance = targetDate - now;

            if (distance < 0) {
                document.getElementById("countdown-wrapper").innerHTML = `
                    <div class="bg-green-500/10 py-3 px-6 rounded-xl border border-green-500/50 mb-2">
                        <p class="text-sm font-bold text-green-400 uppercase tracking-widest">PENGUMUMAN TELAH DIBUKA</p>
                    </div>`;
                document.getElementById("closed-message").classList.add('hidden');
                
                const input = document.getElementById("nisn-input");
                const btn = document.getElementById("check-btn");
                if(input.disabled) {
                    input.disabled = false;
                    btn.disabled = false;
                    btn.classList.remove('bg-blue-600/50', 'text-white/50', 'cursor-not-allowed');
                    btn.classList.add('bg-blue-600', 'hover:bg-blue-500', 'hover:shadow-blue-500/40');
                }
                return;
            }

            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            document.getElementById("days").innerText = days.toString().padStart(2, '0');
            document.getElementById("hours").innerText = hours.toString().padStart(2, '0');
            document.getElementById("minutes").innerText = minutes.toString().padStart(2, '0');
            document.getElementById("seconds").innerText = seconds.toString().padStart(2, '0');
        }

        setInterval(updateCountdown, 1000);
        updateCountdown();

        function checkGraduation() {
            const inputVal = document.getElementById('nisn-input').value.trim();
            const errorMsg = document.getElementById('error-msg');
            
            if (!inputVal) return;

            const student = databaseSiswa.find(s => s.nisn === inputVal);

            if (student) {
                errorMsg.classList.add('hidden');
                showResult(student.nama);
            } else {
                errorMsg.classList.remove('hidden');
                const inputEl = document.getElementById('nisn-input');
                inputEl.classList.add('ring-2', 'ring-red-500');
                setTimeout(() => inputEl.classList.remove('ring-2', 'ring-red-500'), 2000);
            }
        }

        function showResult(name) {
            document.getElementById('main-view').classList.add('hidden');
            document.getElementById('result-view').classList.remove('hidden');
            document.getElementById('student-name').innerText = name;
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function resetView() {
            document.getElementById('nisn-input').value = "";
            document.getElementById('main-view').classList.remove('hidden');
            document.getElementById('result-view').classList.add('hidden');
        }

        document.getElementById('nisn-input').addEventListener('keypress', function (e) {
            if (e.key === 'Enter' && !this.disabled) {
                checkGraduation();
            }
        });
    </script>
</body>
</html>
