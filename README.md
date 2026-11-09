# Bukalapak
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bukalapak Affiliate - Selamat datang Mitra </title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        bl: {
                            red: '#E02045',
                            darkRed: '#C01336',
                            lightRed: '#FFF0F3',
                            dark: '#1E293B',
                            gray: '#F8FAFC'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 4px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #e02045;
            border-radius: 4px;
        }
        .bg-pattern {
            background-color: #e02045;
            background-image: radial-gradient(#c01336 1px, transparent 1px);
            background-size: 16px 16px;
        }
    </style>
</head>
<body class="bg-slate-900 font-sans text-slate-800 min-h-screen flex justify-center items-center p-0 sm:p-4">

    <!-- Mobile Frame Container (Responsif: Fullscreen di Mobile, Frame di Desktop) -->
    <div id="appContainer" class="w-full max-w-md bg-slate-50 min-h-screen sm:min-h-[844px] sm:max-h-[844px] sm:rounded-[36px] shadow-2xl overflow-hidden flex flex-col relative border-0 sm:border-[8px] sm:border-slate-800">
        
        <!-- HEADER APPS (Mobile Status Bar Mock) -->
        <div class="bg-bl-red text-white text-xs px-6 pt-3 pb-1 flex justify-between items-center select-none">
            <span class="font-semibold">09:41</span>
            <div class="flex items-center space-x-1.5">
                <i class="fa-solid fa-signal"></i>
                <i class="fa-solid fa-wifi"></i>
                <i class="fa-solid fa-battery-full text-sm"></i>
            </div>
        </div>

        <!-- APP HEADER (Tampil saat sudah Log In) -->
        <header id="mainHeader" class="hidden bg-bl-red text-white px-5 py-3 flex justify-between items-center shadow-md">
            <div class="flex items-center space-x-3">
                <div class="w-9 h-9 rounded-full bg-white text-bl-red font-extrabold flex items-center justify-center shadow-inner text-lg">
                    B
                </div>
                <div>
                    <h1 class="font-bold text-sm leading-tight">Bukalapak <span class="font-light opacity-90">Affiliate</span></h1>
                    <p class="text-[10px] text-red-100 flex items-center">
                        <span class="w-1.5 h-1.5 bg-green-400 rounded-full inline-block mr-1"></span> Mitra Aktif
                    </p>
                </div>
            </div>
            <div class="flex items-center space-x-2">
                <button onclick="switchTab('notifications')" class="relative p-2 text-white hover:bg-white/10 rounded-full transition">
                    <i class="fa-regular fa-bell text-lg"></i>
                    <span class="absolute top-1 right-1 w-2 h-2 bg-yellow-400 rounded-full"></span>
                </button>
                <button onclick="logout()" title="Keluar" class="p-2 text-white hover:bg-white/10 rounded-full transition">
                    <i class="fa-solid fa-right-from-bracket text-lg"></i>
                </button>
            </div>
        </header>

        <!-- Dynamic Content Body -->
        <main id="appBody" class="flex-1 overflow-y-auto relative pb-20">
            
            <!-- 1. HALAMAN LOGIN -->
            <section id="loginScreen" class="p-6 flex flex-col justify-between min-h-[750px] bg-white">
                <div class="pt-8 text-center">
                    <div class="w-20 h-20 bg-bl-red rounded-3xl flex items-center justify-center mx-auto mb-4 shadow-lg shadow-bl-red/30">
                        <i class="fa-solid fa-sack-dollar text-white text-4xl"></i>
                    </div>
                    <h2 class="text-2xl font-black text-slate-800 tracking-tight">Mitra Keuangan</h2>
                    <p class="text-xs text-slate-500 mt-1">Kelola Komisi & Penarikan Dana Afiliasi Bukalapak</p>
                </div>

                <form id="loginForm" onsubmit="handleLogin(event)" class="mt-6 space-y-4">
                    <div id="loginError" class="hidden p-3 text-xs bg-red-100 border border-red-300 text-red-700 rounded-xl flex items-center gap-2">
                        <i class="fa-solid fa-circle-exclamation text-sm"></i>
                        <span>Username atau password salah!</span>
                    </div>

                    <div>
                        <label class="block text-xs font-semibold text-slate-600 mb-1">Username / ID Afiliasi</label>
                        <div class="relative">
                            <span class="absolute left-3.5 top-3 text-slate-400"><i class="fa-solid fa-user text-sm"></i></span>
                            <input type="text" id="usernameInput" required value="Salim133" class="w-full pl-10 pr-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-xs focus:ring-2 focus:ring-bl-red focus:outline-none transition">
                        </div>
                    </div>

                    <div>
                        <label class="block text-xs font-semibold text-slate-600 mb-1">Password</label>
                        <div class="relative">
                            <span class="absolute left-3.5 top-3 text-slate-400"><i class="fa-solid fa-lock text-sm"></i></span>
                            <input type="password" id="passwordInput" required value="123456" class="w-full pl-10 pr-10 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-xs focus:ring-2 focus:ring-bl-red focus:outline-none transition">
                            <button type="button" onclick="togglePasswordVisibility()" class="absolute right-3.5 top-3 text-slate-400">
                                <i id="eyeIcon" class="fa-solid fa-eye text-sm"></i>
                            </button>
                        </div>
                    </div>

                    <div class="flex items-center justify-between text-xs text-slate-500">
                        <label class="flex items-center space-x-2 cursor-pointer">
                            <input type="checkbox" checked class="rounded border-slate-300 text-bl-red focus:ring-bl-red">
                            <span>Ingat saya</span>
                        </label>
                        <a href="#" class="text-bl-red font-semibold hover:underline">Lupa Password?</a>
                    </div>

                    <button type="submit" class="w-full bg-bl-red hover:bg-bl-darkRed text-white font-bold py-3 rounded-xl shadow-lg shadow-bl-red/30 transition transform active:scale-95 text-xs flex items-center justify-center space-x-2">
                        <span>MASUK </span>
                        <i class="fa-solid fa-arrow-right"></i>
                    </button>
                </form>

                <!-- Info Akses Cepat -->
                <div class="bg-bl-lightRed p-3 rounded-xl border border-red-100 text-[11px] text-slate-600 space-y-1">
                    <p class="font-bold text-bl-darkRed flex items-center"><i class="fa-solid fa-key mr-1.5"></i> Akun :</p>
                    <p>• Username: <code class="bg-white px-1.5 py-0.5 rounded border border-red-200 font-semibold text-slate-700">Salim133</code></p>
                    <p>• Password: <code class="bg-white px-1.5 py-0.5 rounded border border-red-200 font-semibold text-slate-700">123456</code></p>
                </div>

                <p class="text-center text-[10px] text-slate-400 mt-4">
                    &copy; 2026 PT Bukalapak.com Tbk. All Rights Reserved.
                </p>
            </section>

            <!-- 2. MAIN DASHBOARD CONTENT -->
            <div id="dashboardScreen" class="hidden p-4 space-y-4">
                
                <!-- Card User Profile Ringkas -->
                <div class="flex items-center justify-between bg-white p-3.5 rounded-2xl border border-slate-100 shadow-sm">
                    <div class="flex items-center space-x-3">
                        <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=120&q=80" class="w-10 h-10 rounded-full object-cover border-2 border-bl-red" alt="Avatar">
                        <div>
                            <h3 class="font-bold text-slate-800 text-xs">SALIM</h3>
                            <p class="text-[10px] text-slate-400">ID: BL-AFF-88291</p>
                        </div>
                    </div>
                    <span class="bg-emerald-50 text-emerald-600 text-[10px] font-bold px-2.5 py-1 rounded-full border border-emerald-200">
                        Tier Tier Platinum ⚡
                    </span>
                </div>

                <!-- CARD RINGKASAN DANA & KOMISI -->
                <div class="bg-gradient-to-br from-bl-red to-bl-darkRed rounded-3xl p-5 text-white shadow-xl shadow-bl-red/20 relative overflow-hidden">
                    <!-- Background Accent Circle -->
                    <div class="absolute -right-6 -bottom-6 w-32 h-32 bg-white/10 rounded-full pointer-events-none"></div>
                    <div class="absolute right-12 -top-8 w-24 h-24 bg-white/5 rounded-full pointer-events-none"></div>

                    <div class="flex justify-between items-start mb-2">
                        <div>
                            <p class="text-xs text-red-100 font-medium">Saldo Siap Ditarik (Available)</p>
                            <h2 id="saldoUtamaText" class="text-2xl font-extrabold tracking-tight mt-0.5">Rp 30.850.000</h2>
                        </div>
                        <button onclick="openWithdrawModal()" class="bg-white text-bl-darkRed hover:bg-slate-100 px-3.5 py-1.5 rounded-xl font-bold text-xs shadow-md active:scale-95 transition flex items-center space-x-1.5">
                            <i class="fa-solid fa-wallet"></i>
                            <span>Tarik Dana</span>
                        </button>
                    </div>

                    <div class="grid grid-cols-3 gap-2 mt-4 pt-3 border-t border-white/20 text-center">
                        <div>
                            <p class="text-[10px] text-red-100">Total Komisi</p>
                            <p id="totalPendapatanText" class="text-xs font-bold mt-0.5">Rp 12.450.000</p>
                        </div>
                        <div class="border-x border-white/15">
                            <p class="text-[10px] text-red-100">Hari Ini</p>
                            <p id="komisiHariIniText" class="text-xs font-bold text-amber-200 mt-0.5">+Rp 320.000</p>
                        </div>
                        <div>
                            <p class="text-[10px] text-red-100">Telah Ditarik</p>
                            <p id="totalPenarikanText" class="text-xs font-bold mt-0.5">Rp 0</p>
                        </div>
                    </div>
                </div>

                <!-- QUICK ACTIONS & STATS -->
                <div class="grid grid-cols-4 gap-2 text-center">
                    <button onclick="openWithdrawModal()" class="bg-white p-2.5 rounded-2xl border border-slate-100 shadow-sm hover:border-bl-red transition flex flex-col items-center">
                        <div class="w-9 h-9 rounded-xl bg-red-50 text-bl-red flex items-center justify-center text-sm mb-1">
                            <i class="fa-solid fa-hand-holding-dollar"></i>
                        </div>
                        <span class="text-[10px] font-semibold text-slate-700">Tarik Saldo</span>
                    </button>
                    <button onclick="switchTab('tasks')" class="bg-white p-2.5 rounded-2xl border border-slate-100 shadow-sm hover:border-bl-red transition flex flex-col items-center relative">
                        <span id="taskBadge" class="absolute -top-1 -right-1 w-4 h-4 bg-bl-red text-white text-[9px] font-bold rounded-full flex items-center justify-center border-2 border-white">2</span>
                        <div class="w-9 h-9 rounded-xl bg-purple-50 text-purple-600 flex items-center justify-center text-sm mb-1">
                            <i class="fa-solid fa-list-check"></i>
                        </div>
                        <span class="text-[10px] font-semibold text-slate-700">Tugas Item</span>
                    </button>
                    <button onclick="switchTab('commission')" class="bg-white p-2.5 rounded-2xl border border-slate-100 shadow-sm hover:border-bl-red transition flex flex-col items-center">
                        <div class="w-9 h-9 rounded-xl bg-amber-50 text-amber-600 flex items-center justify-center text-sm mb-1">
                            <i class="fa-solid fa-percent"></i>
                        </div>
                        <span class="text-[10px] font-semibold text-slate-700">Komisi</span>
                    </button>
                    <button onclick="switchTab('withdrawHistory')" class="bg-white p-2.5 rounded-2xl border border-slate-100 shadow-sm hover:border-bl-red transition flex flex-col items-center">
                        <div class="w-9 h-9 rounded-xl bg-blue-50 text-blue-600 flex items-center justify-center text-sm mb-1">
                            <i class="fa-solid fa-clock-rotate-left"></i>
                        </div>
                        <span class="text-[10px] font-semibold text-slate-700">Riwayat</span>
                    </button>
                </div>

                <!-- NAVIGATION TAB BAR INTERNAL -->
                <div class="flex bg-slate-200 p-1 rounded-xl text-xs font-semibold">
                    <button id="tabBtnTugas" onclick="switchTab('tasks')" class="flex-1 py-1.5 rounded-lg text-bl-red bg-white shadow-sm font-bold transition">
                        Tugas Item
                    </button>
                    <button id="tabBtnKomisi" onclick="switchTab('commission')" class="flex-1 py-1.5 rounded-lg text-slate-600 transition">
                        Komisi Masuk
                    </button>
                    <button id="tabBtnPenarikan" onclick="switchTab('withdrawHistory')" class="flex-1 py-1.5 rounded-lg text-slate-600 transition">
                        Riwayat Penarikan
                    </button>
                </div>

                <!-- SECTION TAB 0: TUGAS PENYELESAIAN ITEM PRODUK (NEW) -->
                <div id="tabTasksContent" class="space-y-3">
                    <!-- Info Keterangan Syarat ACC Penarikan -->
                    <div class="bg-amber-50 border border-amber-200 rounded-2xl p-3.5 flex items-start space-x-3 shadow-sm">
                        <div class="w-8 h-8 rounded-full bg-amber-100 text-amber-700 flex items-center justify-center shrink-0 mt-0.5">
                            <i class="fa-solid fa-triangle-exclamation text-sm"></i>
                        </div>
                        <div class="text-[11px] text-amber-900 leading-snug">
                            <p class="font-bold text-amber-800">Syarat Pengajuan & ACC Penarikan Dana:</p>
                            <p class="mt-0.5">Penarikan dana Anda <strong>hanya akan disetujui (ACC)</strong> dan diproses ke rekening/e-wallet apabila Anda telah menyelesaikan semua pembayaran tugas item produk di bawah ini.</p>
                        </div>
                    </div>

                    <div class="flex justify-between items-center px-1">
                        <h4 class="text-xs font-bold text-slate-800 uppercase tracking-wider">Daftar Tugas Produk Aktif</h4>
                        <span id="pendingTaskCount" class="text-[10px] bg-red-100 text-bl-red font-bold px-2 py-0.5 rounded-full">2 Tugas Belum Selesai</span>
                    </div>

                    <div id="taskList" class="space-y-2.5">
                        <!-- Rendered by JS -->
                    </div>
                </div>

                <!-- SECTION TAB 1: DAFTAR KOMISI AFILIASI -->
                <div id="tabCommissionContent" class="hidden space-y-3">
                    <div class="flex justify-between items-center px-1">
                        <h4 class="text-xs font-bold text-slate-800 uppercase tracking-wider">Riwayat Komisi Afiliasi</h4>
                        <span class="text-[10px] text-slate-400">Terbaru</span>
                    </div>
                    <div id="commissionList" class="space-y-2 text-xs">
                        <!-- Rendered by JS -->
                    </div>
                </div>

                <!-- SECTION TAB 2: RIWAYAT PENARIKAN DANA -->
                <div id="tabWithdrawContent" class="hidden space-y-3">
                    <!-- Info Keterangan Syarat ACC Penarikan -->
                    <div class="bg-red-50 border border-red-200 rounded-2xl p-3 flex items-center space-x-2.5">
                        <i class="fa-solid fa-[#E02045] fa-circle-info text-bl-red text-base shrink-0"></i>
                        <p class="text-[10px] text-red-800 font-medium leading-tight">
                            Status penarikan akan disetujui <strong>(ACC)</strong> oleh sistem secara otomatis setelah seluruh <strong>Tugas Penyelesaian Item Produk</strong> diselesaikan.
                        </p>
                    </div>

                    <div class="flex justify-between items-center px-1">
                        <h4 class="text-xs font-bold text-slate-800 uppercase tracking-wider">Status Penarikan Dana</h4>
                        <button onclick="openWithdrawModal()" class="text-[10px] bg-bl-red text-white px-2.5 py-1 rounded-lg font-semibold">
                            + Penarikan Baru
                        </button>
                    </div>

                    <div id="withdrawList" class="space-y-2.5">
                        <!-- Rendered by JS -->
                    </div>
                </div>

            </div>
        </main>

        <!-- FOOTER BOTTOM NAVIGATION -->
        <nav id="bottomNav" class="hidden absolute bottom-0 left-0 right-0 bg-white border-t border-slate-200 px-6 py-2 flex justify-around items-center z-10 shadow-lg">
            <button onclick="switchTab('tasks')" class="nav-btn flex flex-col items-center text-bl-red" id="navHome">
                <i class="fa-solid fa-list-check text-base"></i>
                <span class="text-[10px] font-medium mt-0.5">Tugas</span>
            </button>
            <button onclick="openWithdrawModal()" class="nav-btn flex flex-col items-center text-slate-400 hover:text-bl-red">
                <div class="w-10 h-10 bg-bl-red text-white rounded-full flex items-center justify-center -mt-5 shadow-lg shadow-bl-red/40 border-4 border-white">
                    <i class="fa-solid fa-plus text-lg"></i>
                </div>
                <span class="text-[10px] font-medium mt-0.5 text-slate-600">Tarik</span>
            </button>
            <button onclick="switchTab('withdrawHistory')" class="nav-btn flex flex-col items-center text-slate-400 hover:text-bl-red" id="navHistory">
                <i class="fa-solid fa-receipt text-base"></i>
                <span class="text-[10px] font-medium mt-0.5">Riwayat</span>
            </button>
        </nav>

        <!-- MODAL FORM PENARIKAN DANA (WITHDRAWAL) -->
        <div id="withdrawModal" class="hidden fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 flex items-end sm:items-center justify-center p-0 sm:p-4">
            <div class="bg-white w-full max-w-md rounded-t-3xl sm:rounded-3xl p-5 space-y-4 animate-slide-up shadow-2xl">
                
                <div class="flex justify-between items-center border-b pb-3">
                    <div class="flex items-center space-x-2">
                        <div class="w-8 h-8 rounded-full bg-red-100 text-bl-red flex items-center justify-center">
                            <i class="fa-solid fa-money-bill-transfer text-sm"></i>
                        </div>
                        <h3 class="font-bold text-slate-800 text-sm">Pengajuan Penarikan Dana</h3>
                    </div>
                    <button onclick="closeWithdrawModal()" class="text-slate-400 hover:text-slate-600 p-1">
                        <i class="fa-solid fa-xmark text-lg"></i>
                    </button>
                </div>

                <!-- Warning Peringatan Syarat Task -->
                <div id="modalTaskWarning" class="hidden bg-amber-50 border border-amber-300 p-2.5 rounded-xl text-[10px] text-amber-900 flex items-start space-x-2">
                    <i class="fa-solid fa-lock text-amber-600 text-xs mt-0.5"></i>
                    <span><strong>Perhatian:</strong> Penarikan dana disetujui (ACC) otomatis setelah penyelesaian tugas item produk aktif diselesaikan.</span>
                </div>

                <form id="withdrawForm" onsubmit="handleWithdrawSubmit(event)" class="space-y-3.5">
                    
                    <!-- Info Saldo -->
                    <div class="bg-slate-50 p-3 rounded-xl border border-slate-200 flex justify-between items-center">
                        <span class="text-xs text-slate-500">Saldo Maksimal Ditarik</span>
                        <span id="modalMaxSaldo" class="text-xs font-bold text-bl-darkRed">Rp 30.850.000</span>
                    </div>

                    <!-- Nominal Penarikan -->
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">Nominal Penarikan (Rp)</label>
                        <div class="relative">
                            <span class="absolute left-3 top-2.5 text-xs font-bold text-slate-400">Rp</span>
                            <input type="number" id="withdrawAmount" min="50000" step="10000" placeholder="Min. 50.000" required class="w-full pl-9 pr-3 py-2 bg-white border border-slate-300 rounded-xl text-xs font-bold focus:ring-2 focus:ring-bl-red focus:outline-none">
                        </div>
                        <p class="text-[10px] text-slate-400 mt-1">Biaya admin penarikan: <span class="font-semibold text-emerald-600">GRATIS</span></p>
                    </div>

                    <!-- Pilihan Metode Pembayaran / Bank / E-Wallet -->
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">Tujuan Transfer (Bank / E-Wallet)</label>
                        <select id="withdrawDestination" required class="w-full px-3 py-2 bg-white border border-slate-300 rounded-xl text-xs focus:ring-2 focus:ring-bl-red focus:outline-none">
                            <option value="">-- Pilih Rekening / E-Wallet --</option>
                            <optgroup label="Bank Transfer">
                                <option value="Mandiri - 1060020240928 (KUSNIATI)">Mandiri - 1060020240928 a.n KUSNIATI</option>
                            </optgroup>
                        </select>
                    </div>

                    <!-- Catatan Tambahan -->
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">Catatan (Opsional)</label>
                        <input type="text" id="withdrawNote" placeholder="Contoh: Penarikan rutin mingguan" class="w-full px-3 py-2 bg-white border border-slate-300 rounded-xl text-xs focus:ring-2 focus:ring-bl-red focus:outline-none">
                    </div>

                    <div class="pt-2">
                        <button type="submit" class="w-full bg-bl-red hover:bg-bl-darkRed text-white font-bold py-2.5 rounded-xl shadow-md text-xs transition flex items-center justify-center space-x-2">
                            <i class="fa-solid fa-paper-plane"></i>
                            <span>KIRIM PENGAJUAN PENARIKAN</span>
                        </button>
                    </div>
                </form>

            </div>
        </div>

        <!-- MODAL PEMBAYARAN TUGAS TRANSFER BANK MANDIRI (NEW) -->
        <div id="payTaskModal" class="hidden fixed inset-0 bg-slate-900/70 backdrop-blur-sm z-50 flex items-end sm:items-center justify-center p-0 sm:p-4">
            <div class="bg-white w-full max-w-md rounded-t-3xl sm:rounded-3xl p-5 space-y-4 animate-slide-up shadow-2xl">
                <div class="flex justify-between items-center border-b pb-3">
                    <div class="flex items-center space-x-2">
                        <div class="w-8 h-8 rounded-full bg-blue-100 text-blue-700 flex items-center justify-center font-bold">
                            <i class="fa-solid fa-building-columns text-sm"></i>
                        </div>
                        <div>
                            <h3 class="font-bold text-slate-800 text-sm">Pembayaran Tugas Item</h3>
                            <p class="text-[10px] text-slate-400">Transfer Manual Ke Rekening Resmi</p>
                        </div>
                    </div>
                    <button onclick="closePayTaskModal()" class="text-slate-400 hover:text-slate-600 p-1">
                        <i class="fa-solid fa-xmark text-lg"></i>
                    </button>
                </div>

                <!-- Detail Tugas yang dibayar -->
                <div class="bg-slate-50 p-3 rounded-2xl border border-slate-200 flex justify-between items-center">
                    <div>
                        <span id="modalTaskTitle" class="text-[10px] font-bold text-bl-red block">TSK-01</span>
                        <span id="modalTaskItem" class="text-xs font-semibold text-slate-700">Smartphone Samsung Galaxy A54</span>
                    </div>
                    <div class="text-right">
                        <span class="text-[10px] text-slate-400 block">Total Pembayaran</span>
                        <span id="modalTaskAmount" class="text-xs font-extrabold text-slate-900">Rp 793.299</span>
                    </div>
                </div>

                <!-- Info Catatan Penting -->
                <div class="bg-amber-50 border border-amber-200 text-amber-900 p-2.5 rounded-xl text-[10px] flex items-start space-x-2">
                    <i class="fa-solid fa-circle-info text-amber-600 text-xs mt-0.5"></i>
                    <span>Pembayaran tugas <strong>tidak dapat menggunakan saldo akun</strong>. Silakan lakukan transfer antarbank/m-Banking sesuai nominal persis ke rekening di bawah ini:</span>
                </div>

                <!-- Card Rekening Mandiri Resmi -->
                <div class="bg-gradient-to-r from-blue-900 to-blue-700 rounded-2xl p-4 text-white shadow-lg space-y-2 relative overflow-hidden">
                    <div class="flex justify-between items-center">
                        <span class="text-xs font-bold tracking-wider opacity-80">BANK MANDIRI</span>
                        <i class="fa-solid fa-credit-card text-lg opacity-70"></i>
                    </div>
                    
                    <div class="pt-1">
                        <p class="text-[10px] text-blue-200">Nomor Rekening Tujuan:</p>
                        <div class="flex justify-between items-center bg-black/20 px-3 py-1.5 rounded-xl mt-0.5">
                            <span id="rekeningNomor" class="font-mono text-base font-extrabold tracking-wider">1060020240928</span>
                            <button onclick="copyRekening()" class="text-[10px] bg-white/20 hover:bg-white/30 px-2 py-1 rounded-lg font-semibold flex items-center space-x-1 transition active:scale-95">
                                <i class="fa-solid fa-copy"></i>
                                <span>Salin</span>
                            </button>
                        </div>
                    </div>

                    <div class="flex justify-between items-center text-xs pt-1 border-t border-white/10">
                        <div>
                            <p class="text-[9px] text-blue-200">Nama Pemilik Rekening</p>
                            <p class="font-bold text-xs uppercase">KUSNIATI</p>
                        </div>
                        <div class="text-right">
                            <p class="text-[9px] text-blue-200">Status Rekening</p>
                            <span class="text-[10px] bg-green-500/30 text-green-300 font-bold px-2 py-0.5 rounded-full border border-green-400/40">Verified / Official</span>
                        </div>
                    </div>
                </div>

                <!-- Form Upload Bukti Transfer -->
                <div class="space-y-3 pt-1">
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">Bukti Transfer Pembayaran</label>
                        <div class="border-2 border-dashed border-slate-300 rounded-xl p-3 text-center bg-slate-50 hover:bg-slate-100 transition cursor-pointer relative">
                            <input type="file" accept="image/*" id="buktiTransferInput" onchange="handleFileSelected(event)" class="absolute inset-0 opacity-0 cursor-pointer w-full h-full">
                            <div id="fileUploadPlaceholder" class="space-y-1">
                                <i class="fa-solid fa-cloud-arrow-up text-bl-red text-xl"></i>
                                <p class="text-xs font-medium text-slate-600">Klik untuk unggah foto Struk / Bukti Transfer</p>
                                <p class="text-[9px] text-slate-400">Format JPG, PNG, atau Screenshot m-Banking</p>
                            </div>
                            <div id="fileSelectedInfo" class="hidden text-xs font-bold text-emerald-600 flex items-center justify-center space-x-1">
                                <i class="fa-solid fa-circle-check"></i>
                                <span id="fileNameText">Bukti_Transfer.jpg</span>
                            </div>
                        </div>
                    </div>

                    <button onclick="confirmTaskPayment()" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2.5 rounded-xl shadow-md text-xs transition flex items-center justify-center space-x-2 active:scale-95">
                        <i class="fa-solid fa-circle-check"></i>
                        <span>KONFIRMASI PEMBAYARAN TUGAS</span>
                    </button>
                </div>
            </div>
        </div>

        <!-- TOAST NOTIFICATION -->
        <div id="toast" class="hidden fixed top-16 left-1/2 transform -translate-x-1/2 bg-slate-800 text-white text-xs px-4 py-2.5 rounded-full shadow-xl border border-slate-700 z-50 flex items-center space-x-2 transition">
            <i id="toastIcon" class="fa-solid fa-circle-check text-green-400"></i>
            <span id="toastMessage">Pesan Notifikasi</span>
        </div>

    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // DATA STATE MOCK
        let state = {
            isLoggedIn: false,
            saldoUtama: 30850000,
            totalPendapatan: 12450000,
            komisiHariIni: 320000,
            totalPenarikan: 0,
            selectedTaskId: null,
            tasks: [
                { id: 'TSK-01', title: 'Penyelesaian Item Produk #1', item: 'Smartphone Samsung Galaxy A54 5G', amount: 793299, status: 'Pending', commissionReward: 120000 },
                { id: 'TSK-02', title: 'Penyelesaian Item Produk #2', item: 'Smart TV LG 43 Inch Ultra HD 4K', amount: 1482499, status: 'Pending', commissionReward: 250000 }
            ],
            commissions: [
                { id: 'COMM-1092', product: 'Laptop Gaming Asus ROG Strix G15', category: 'Elektronik', percent: '5%', amount: 180000, date: 'Hari ini, 14:20', status: 'Confirmed', buyer: 'Budi S.' },
                { id: 'COMM-1091', product: 'Sepatu Running Nike Air Zoom', category: 'Fashion', percent: '8%', amount: 95000, date: 'Hari ini, 11:05', status: 'Confirmed', buyer: 'Rina T.' },
                { id: 'COMM-1090', product: 'Smartwatch Samsung Galaxy Watch 6', category: 'Gadget', percent: '6%', amount: 45000, date: 'Hari ini, 08:30', status: 'Confirmed', buyer: 'Dimas P.' },
                { id: 'COMM-1089', product: 'Kemeja Casual Pria Premium Slimfit', category: 'Fashion', percent: '10%', amount: 25000, date: 'Kemarin', status: 'Confirmed', buyer: 'Eko W.' },
                { id: 'COMM-1088', product: 'Air Fryer Philips HD9252 Digital', category: 'Perabotan', percent: '4%', amount: 62000, date: '10 Nov 2026', status: 'Pending', buyer: 'Sari M.' }
            ],
            withdrawals: []
        };

        // INITIAL LOAD
        document.addEventListener('DOMContentLoaded', () => {
            renderTasks();
            renderCommissions();
            renderWithdrawals();
            updateBalanceUI();
            switchTab('tasks');
        });

        // GENERATE RANDOM TASK UNTUK TUGAS SELANJUTNYA
        function generateRandomTask() {
            const sampleProducts = [
                'Tablet Apple iPad 10th Gen 64GB',
                'Kamera Mirrorless Canon EOS R50',
                'Soundbar Speaker Bose TV Speaker',
                'Drone DJI Mini 2 SE Fly More Combo',
                'Console PlayStation 5 Slim Edition'
            ];
            
            const randomAmount = Math.floor(Math.random() * (2500 - 800) + 800) * 1000 + 999;
            const randomReward = Math.floor(randomAmount * 0.15);
            const taskIndex = state.tasks.length + 1;
            const randomProduct = sampleProducts[Math.floor(Math.random() * sampleProducts.length)];

            return {
                id: 'TSK-0' + taskIndex,
                title: `Penyelesaian Item Produk #${taskIndex}`,
                item: randomProduct,
                amount: randomAmount,
                status: 'Pending',
                commissionReward: randomReward
            };
        }

        // RENDER DAFTAR TUGAS ITEM PRODUK
        function renderTasks() {
            const container = document.getElementById('taskList');
            container.innerHTML = '';

            const pendingTasks = state.tasks.filter(t => t.status === 'Pending');
            const pendingBadge = document.getElementById('pendingTaskCount');
            const taskBadgeNav = document.getElementById('taskBadge');

            if (pendingBadge) {
                pendingBadge.innerText = `${pendingTasks.length} Tugas Belum Selesai`;
            }
            if (taskBadgeNav) {
                if (pendingTasks.length > 0) {
                    taskBadgeNav.innerText = pendingTasks.length;
                    taskBadgeNav.classList.remove('hidden');
                } else {
                    taskBadgeNav.classList.add('hidden');
                }
            }

            state.tasks.forEach((task) => {
                const isCompleted = task.status === 'Completed';
                const statusBadge = isCompleted
                    ? `<span class="bg-emerald-100 text-emerald-700 text-[10px] font-bold px-2.5 py-1 rounded-full"><i class="fa-solid fa-circle-check mr-1"></i>Selesai & Di-ACC</span>`
                    : `<span class="bg-amber-100 text-amber-700 text-[10px] font-bold px-2.5 py-1 rounded-full"><i class="fa-solid fa-clock mr-1"></i>Menunggu Pembayaran</span>`;

                const actionButton = isCompleted
                    ? `<button disabled class="w-full bg-slate-200 text-slate-500 font-bold py-2 rounded-xl text-xs cursor-not-allowed">
                        <i class="fa-solid fa-check-double mr-1"></i> Tugas Telah Diselesaikan
                       </button>`
                    : `<button onclick="openPayTaskModal('${task.id}')" class="w-full bg-bl-red hover:bg-bl-darkRed text-white font-bold py-2.5 rounded-xl shadow-md text-xs transition flex items-center justify-center space-x-1.5 active:scale-95">
                        <i class="fa-solid fa-building-columns"></i>
                        <span>Transfer Bank Mandiri (${formatRupiah(task.amount)})</span>
                       </button>`;

                const card = `
                    <div class="bg-white p-4 rounded-2xl border ${isCompleted ? 'border-emerald-200' : 'border-slate-200'} shadow-sm space-y-3 relative overflow-hidden">
                        ${isCompleted ? '<div class="absolute top-0 right-0 w-16 h-16 bg-emerald-500/10 rounded-bl-full pointer-events-none"></div>' : ''}
                        
                        <div class="flex justify-between items-start">
                            <div>
                                <span class="text-[10px] font-extrabold text-bl-red uppercase tracking-wider">${task.id}</span>
                                <h5 class="font-bold text-slate-800 text-xs mt-0.5">${task.title}</h5>
                                <p class="text-[11px] font-medium text-slate-600 mt-0.5"><i class="fa-solid fa-box text-slate-400 mr-1"></i>${task.item}</p>
                            </div>
                            <div>${statusBadge}</div>
                        </div>

                        <div class="bg-slate-50 p-2.5 rounded-xl border border-slate-100 grid grid-cols-2 gap-2 text-center text-xs">
                            <div>
                                <p class="text-[10px] text-slate-400">Nominal Tugas Item</p>
                                <p class="font-black text-slate-800 text-xs">${formatRupiah(task.amount)}</p>
                            </div>
                            <div class="border-l border-slate-200">
                                <p class="text-[10px] text-slate-400">Estimasi Bonus Komisi</p>
                                <p class="font-extrabold text-emerald-600 text-xs">+${formatRupiah(task.commissionReward)}</p>
                            </div>
                        </div>

                        <div class="pt-1">
                            ${actionButton}
                        </div>
                    </div>
                `;
                container.innerHTML += card;
            });
        }

        // BUKA MODAL PEMBAYARAN TUGAS TRANSFER BANK MANDIRI
        function openPayTaskModal(taskId) {
            const task = state.tasks.find(t => t.id === taskId);
            if (!task) return;

            state.selectedTaskId = taskId;
            document.getElementById('modalTaskTitle').innerText = task.id;
            document.getElementById('modalTaskItem').innerText = task.item;
            document.getElementById('modalTaskAmount').innerText = formatRupiah(task.amount);

            // Reset upload file preview
            document.getElementById('fileUploadPlaceholder').classList.remove('hidden');
            document.getElementById('fileSelectedInfo').classList.add('hidden');
            document.getElementById('buktiTransferInput').value = '';

            document.getElementById('payTaskModal').classList.remove('hidden');
        }

        function closePayTaskModal() {
            document.getElementById('payTaskModal').classList.add('hidden');
            state.selectedTaskId = null;
        }

        // SALIN NO REKENING MANDIRI
        function copyRekening() {
            const rek = "1060020240928";
            const dummy = document.createElement("input");
            document.body.appendChild(dummy);
            dummy.value = rek;
            dummy.select();
            document.execCommand("copy");
            document.body.removeChild(dummy);
            showToast("Nomor Rekening Mandiri berhasil disalin!");
        }

        // PREVIEW HANDLE FILE UPLOAD BUKTI TRANSFER
        function handleFileSelected(e) {
            const file = e.target.files[0];
            if (file) {
                document.getElementById('fileUploadPlaceholder').classList.add('hidden');
                document.getElementById('fileNameText').innerText = file.name;
                document.getElementById('fileSelectedInfo').classList.remove('hidden');
            }
        }

        // KONFIRMASI PEMBAYARAN TUGAS TRANSFER BANK
        function confirmTaskPayment() {
            const task = state.tasks.find(t => t.id === state.selectedTaskId);
            if (!task) return;

            // Bebas saldo siap ditarik (Saldo Siap Ditarik TIDAK dipotong)
            // Saldo bertambah bonus komisi tugas
            state.saldoUtama += task.commissionReward; 
            state.totalPendapatan += task.commissionReward;
            task.status = 'Completed';

            // Jika semua tugas pending selesai, buatkan tugas acak berikutnya
            const remainingPending = state.tasks.filter(t => t.status === 'Pending');
            if (remainingPending.length === 0) {
                const newRandomTask = generateRandomTask();
                state.tasks.push(newRandomTask);
                showToast(`Pembayaran Tugas ${task.id} terkonfirmasi! Tugas acak selanjutnya (${newRandomTask.title}) ditambahkan.`, 'success');
            } else {
                showToast(`Pembayaran Tugas ${task.id} berhasil dikonfirmasi!`, 'success');
            }

            updateBalanceUI();
            renderTasks();
            closePayTaskModal();
        }

        // SWITCH TAB (Tugas / Komisi / Riwayat Penarikan)
        function switchTab(tabName) {
            const btnTugas = document.getElementById('tabBtnTugas');
            const btnKomisi = document.getElementById('tabBtnKomisi');
            const btnPenarikan = document.getElementById('tabBtnPenarikan');
            
            const contentTugas = document.getElementById('tabTasksContent');
            const contentKomisi = document.getElementById('tabCommissionContent');
            const contentPenarikan = document.getElementById('tabWithdrawContent');
            
            const navHome = document.getElementById('navHome');
            const navHistory = document.getElementById('navHistory');

            [btnTugas, btnKomisi, btnPenarikan].forEach(btn => {
                if(btn) btn.className = "flex-1 py-1.5 rounded-lg text-slate-600 hover:text-slate-900 transition";
            });

            [contentTugas, contentKomisi, contentPenarikan].forEach(content => {
                if(content) content.classList.add('hidden');
            });

            if (tabName === 'tasks') {
                contentTugas.classList.remove('hidden');
                btnTugas.className = "flex-1 py-1.5 rounded-lg text-bl-red bg-white shadow-sm font-bold transition";
                if (navHome) navHome.className = "nav-btn flex flex-col items-center text-bl-red";
                if (navHistory) navHistory.className = "nav-btn flex flex-col items-center text-slate-400 hover:text-bl-red";
            } else if (tabName === 'commission') {
                contentKomisi.classList.remove('hidden');
                btnKomisi.className = "flex-1 py-1.5 rounded-lg text-bl-red bg-white shadow-sm font-bold transition";
                if (navHome) navHome.className = "nav-btn flex flex-col items-center text-slate-400 hover:text-bl-red";
                if (navHistory) navHistory.className = "nav-btn flex flex-col items-center text-slate-400 hover:text-bl-red";
            } else if (tabName === 'withdrawHistory') {
                contentPenarikan.classList.remove('hidden');
                btnPenarikan.className = "flex-1 py-1.5 rounded-lg text-bl-red bg-white shadow-sm font-bold transition";
                if (navHome) navHome.className = "nav-btn flex flex-col items-center text-slate-400 hover:text-bl-red";
                if (navHistory) navHistory.className = "nav-btn flex flex-col items-center text-bl-red";
            }
        }

        // MODAL WITHDRAW CONTROL
        function openWithdrawModal() {
            const warningEl = document.getElementById('modalTaskWarning');
            const hasPendingTasks = state.tasks.some(t => t.status === 'Pending');

            if (hasPendingTasks && warningEl) {
                warningEl.classList.remove('hidden');
            } else if (warningEl) {
                warningEl.classList.add('hidden');
            }

            document.getElementById('withdrawModal').classList.remove('hidden');
        }

        function closeWithdrawModal() {
            document.getElementById('withdrawModal').classList.add('hidden');
            document.getElementById('withdrawForm').reset();
        }

        // HANDLE SUBMIT PENARIKAN DANA BARU
        function handleWithdrawSubmit(e) {
            e.preventDefault();
            const amount = parseInt(document.getElementById('withdrawAmount').value);
            const destination = document.getElementById('withdrawDestination').value;

            // Cek syarat kelengkapan tugas penyelesaian item produk
            const pendingTasks = state.tasks.filter(t => t.status === 'Pending');
            if (pendingTasks.length > 0) {
                showToast(`Penarikan terkunci! Harap selesaikan ${pendingTasks.length} tugas item produk aktif terlebih dahulu agar di-ACC.`, 'error');
                switchTab('tasks');
                closeWithdrawModal();
                return;
            }

            if (amount > state.saldoUtama) {
                showToast('Saldo Anda tidak mencukupi untuk penarikan ini!', 'error');
                return;
            }

            if (amount < 50000) {
                showToast('Minimal penarikan dana adalah Rp 50.000', 'error');
                return;
            }

            // Kurangi saldo & update statistik
            state.saldoUtama -= amount;
            state.totalPenarikan += amount;

            // Tambahkan ke riwayat penarikan
            const newWithdrawal = {
                id: 'WD-' + Math.floor(1000 + Math.random() * 9000),
                destination: destination,
                amount: amount,
                date: 'Hari ini, ' + new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }),
                status: 'Diproses (Di-ACC)'
            };

            state.withdrawals.unshift(newWithdrawal);

            // Update UI & Close Modal
            updateBalanceUI();
            renderWithdrawals();
            closeWithdrawModal();
            switchTab('withdrawHistory');

            showToast(`Pengajuan penarikan ${formatRupiah(amount)} berhasil dikirim & di-ACC!`);
        }

        // HANDLE LOGIN
        function handleLogin(e) {
            e.preventDefault();
            const usernameInput = document.getElementById('usernameInput').value;
            const passwordInput = document.getElementById('passwordInput').value;
            const errorMsg = document.getElementById('loginError');

            if (usernameInput === 'Salim133' && passwordInput === '123456') {
                state.isLoggedIn = true;
                if (errorMsg) errorMsg.classList.add('hidden');
                
                document.getElementById('loginScreen').classList.add('hidden');
                document.getElementById('mainHeader').classList.remove('hidden');
                document.getElementById('dashboardScreen').classList.remove('hidden');
                document.getElementById('bottomNav').classList.remove('hidden');
                
                showToast('Login berhasil! Selamat datang, SALIM.');
            } else {
                if (errorMsg) errorMsg.classList.remove('hidden');
            }
        }

        // HANDLE LOGOUT
        function logout() {
            state.isLoggedIn = false;
            document.getElementById('loginScreen').classList.remove('hidden');
            document.getElementById('mainHeader').classList.add('hidden');
            document.getElementById('dashboardScreen').classList.add('hidden');
            document.getElementById('bottomNav').classList.add('hidden');
            showToast('Anda telah berhasil keluar.');
        }

        // TOGGLE SHOW/HIDE PASSWORD
        function togglePasswordVisibility() {
            const input = document.getElementById('passwordInput');
            const icon = document.getElementById('eyeIcon');
            if (input.type === 'password') {
                input.type = 'text';
                icon.classList.replace('fa-eye', 'fa-eye-slash');
            } else {
                input.type = 'password';
                icon.classList.replace('fa-eye-slash', 'fa-eye');
            }
        }

        // FORMAT RUPIAH
        function formatRupiah(number) {
            return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', maximumFractionDigits: 0 }).format(number);
        }

        // UPDATE BALANCE ON UI
        function updateBalanceUI() {
            document.getElementById('saldoUtamaText').innerText = formatRupiah(state.saldoUtama);
            document.getElementById('totalPendapatanText').innerText = formatRupiah(state.totalPendapatan);
            document.getElementById('komisiHariIniText').innerText = '+' + formatRupiah(state.komisiHariIni);
            document.getElementById('totalPenarikanText').innerText = formatRupiah(state.totalPenarikan);
            document.getElementById('modalMaxSaldo').innerText = formatRupiah(state.saldoUtama);
        }

        // RENDER LIST KOMISI
        function renderCommissions() {
            const container = document.getElementById('commissionList');
            container.innerHTML = '';

            state.commissions.forEach(item => {
                const isConfirmed = item.status === 'Confirmed';
                const statusBadge = isConfirmed 
                    ? `<span class="bg-emerald-100 text-emerald-700 text-[9px] font-bold px-2 py-0.5 rounded-full">Terkonfirmasi</span>`
                    : `<span class="bg-amber-100 text-amber-700 text-[9px] font-bold px-2 py-0.5 rounded-full">Diproses</span>`;

                const card = `
                    <div class="bg-white p-3 rounded-2xl border border-slate-100 shadow-sm flex items-center justify-between hover:shadow-md transition">
                        <div class="flex items-center space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-red-50 text-bl-red flex items-center justify-center font-bold text-xs">
                                ${item.percent}
                            </div>
                            <div>
                                <h5 class="font-bold text-slate-800 text-xs line-clamp-1">${item.product}</h5>
                                <div class="flex items-center space-x-2 text-[10px] text-slate-400 mt-0.5">
                                    <span>${item.date}</span>
                                    <span>•</span>
                                    <span>Pembeli: ${item.buyer}</span>
                                </div>
                            </div>
                        </div>
                        <div class="text-right">
                            <p class="font-extrabold text-xs text-slate-800">+${formatRupiah(item.amount)}</p>
                            <div class="mt-0.5">${statusBadge}</div>
                        </div>
                    </div>
                `;
                container.innerHTML += card;
            });
        }

        // RENDER LIST PENARIKAN DANA
        function renderWithdrawals() {
            const container = document.getElementById('withdrawList');
            container.innerHTML = '';

            if (state.withdrawals.length === 0) {
                container.innerHTML = `<p class="text-center text-xs text-slate-400 py-4">Belum ada riwayat penarikan dana.</p>`;
                return;
            }

            state.withdrawals.forEach(item => {
                let statusColor = 'bg-emerald-100 text-emerald-700';
                let iconStatus = 'fa-circle-check';

                if (item.status === 'Diproses') {
                    statusColor = 'bg-amber-100 text-amber-700';
                    iconStatus = 'fa-clock';
                } else if (item.status === 'Gagal') {
                    statusColor = 'bg-red-100 text-red-700';
                    iconStatus = 'fa-circle-xmark';
                }

                const card = `
                    <div class="bg-white p-3 rounded-2xl border border-slate-100 shadow-sm flex items-center justify-between">
                        <div class="flex items-center space-x-3">
                            <div class="w-9 h-9 rounded-xl bg-slate-100 text-slate-600 flex items-center justify-center text-sm">
                                <i class="fa-solid fa-building-columns"></i>
                            </div>
                            <div>
                                <h5 class="font-bold text-slate-800 text-xs">${item.destination}</h5>
                                <p class="text-[10px] text-slate-400 mt-0.5">${item.date} • ID: ${item.id}</p>
                            </div>
                        </div>
                        <div class="text-right">
                            <p class="font-extrabold text-xs text-bl-darkRed">-${formatRupiah(item.amount)}</p>
                            <span class="${statusColor} text-[9px] font-bold px-2 py-0.5 rounded-full inline-flex items-center gap-1 mt-0.5">
                                <i class="fa-solid ${iconStatus} text-[8px]"></i> ${item.status}
                            </span>
                        </div>
                    </div>
                `;
                container.innerHTML += card;
            });
        }

        // TOAST NOTIFIKASI HELPER
        function showToast(msg, type = 'success') {
            const toast = document.getElementById('toast');
            const toastMsg = document.getElementById('toastMessage');
            const toastIcon = document.getElementById('toastIcon');

            toastMsg.innerText = msg;

            if (type === 'error') {
                toastIcon.className = 'fa-solid fa-circle-exclamation text-red-400';
            } else {
                toastIcon.className = 'fa-solid fa-circle-check text-emerald-400';
            }

            toast.classList.remove('hidden');

            setTimeout(() => {
                toast.classList.add('hidden');
            }, 3000);
        }
    </script>
</body>
</html>
