<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BrandKraft ID - Personal Branding & Sales Suite</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background-color: #f8fafc;
      color: #0f172a;
    }
    
    .tab-btn.active {
      background-color: #2563eb;
      color: #ffffff;
      box-shadow: 0 4px 12px rgba(37, 99, 235, 0.25);
    }

    /* Target CV A4 Paper */
    .cv-paper {
      width: 210mm;
      min-height: 297mm;
      background: #ffffff;
      box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1);
      margin: 0 auto;
    }

    /* Print Setup */
    @media print {
      body * {
        visibility: hidden;
      }
      #print-area, #print-area * {
        visibility: visible;
      }
      #print-area {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        margin: 0;
        box-shadow: none;
      }
      .no-print {
        display: none !important;
      }
    }

    /* Custom Color Dynamic Variables */
    :root {
      --cv-accent: #2563eb;
    }
    .cv-accent-bg { background-color: var(--cv-accent); }
    .cv-accent-text { color: var(--cv-accent); }
    .cv-accent-border { border-color: var(--cv-accent); }
  </style>
</head>
<body class="min-h-screen flex flex-col">

  <!-- Header Navigation -->
  <header class="bg-white border-b border-slate-200 sticky top-0 z-50 no-print">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
      <div class="flex items-center space-x-3">
        <div class="w-10 h-10 rounded-xl bg-blue-600 flex items-center justify-center text-white font-bold text-xl shadow-md">
          BK
        </div>
        <div>
          <h1 class="font-bold text-lg text-slate-900 leading-tight">BrandKraft <span class="text-blue-600">ID</span></h1>
          <p class="text-xs text-slate-500">Suite Personal Branding & Promosi</p>
        </div>
      </div>

      <!-- Navigation Tabs -->
      <nav class="hidden md:flex space-x-1 bg-slate-100 p-1 rounded-xl text-sm font-medium">
        <button onclick="switchTab('cv')" id="tab-cv" class="tab-btn active px-4 py-2 rounded-lg transition-all">CV Builder</button>
        <button onclick="switchTab('surat')" id="tab-surat" class="tab-btn px-4 py-2 rounded-lg text-slate-600 hover:text-slate-900 transition-all">Surat Lamaran</button>
        <button onclick="switchTab('pitch')" id="tab-pitch" class="tab-btn px-4 py-2 rounded-lg text-slate-600 hover:text-slate-900 transition-all">Elevator Pitch</button>
        <button onclick="switchTab('logo')" id="tab-logo" class="tab-btn px-4 py-2 rounded-lg text-slate-600 hover:text-slate-900 transition-all">Logo AI</button>
        <button onclick="switchTab('banner')" id="tab-banner" class="tab-btn px-4 py-2 rounded-lg text-slate-600 hover:text-slate-900 transition-all flex items-center gap-1.5">
          <span>Banner Jualan</span>
          <span class="bg-amber-400 text-slate-900 text-[10px] font-bold px-1.5 py-0.5 rounded-full">Baru</span>
        </button>
      </nav>

      <button onclick="window.print()" class="bg-blue-600 hover:bg-blue-700 text-white font-medium text-sm px-4 py-2 rounded-lg flex items-center space-x-2 transition-all shadow-sm">
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 17h2a2 2 0 002-2v-4a2 2 0 00-2-2H5a2 2 0 00-2 2v4a2 2 0 002 2h2m2 4h6a2 2 0 002-2v-4a2 2 0 00-2-2H9a2 2 0 00-2 2v4a2 2 0 002 2zm8-12V5a2 2 0 00-2-2H9a2 2 0 00-2 2v4h10z"></path></svg>
        <span>Cetak / PDF</span>
      </button>
    </div>
  </header>

  <!-- Mobile Subnav -->
  <div class="md:hidden bg-white border-b border-slate-200 p-2 flex overflow-x-auto space-x-2 no-print">
    <button onclick="switchTab('cv')" class="px-3 py-1.5 text-xs font-semibold rounded-lg bg-blue-50 text-blue-600 whitespace-nowrap">CV Builder</button>
    <button onclick="switchTab('surat')" class="px-3 py-1.5 text-xs font-semibold rounded-lg text-slate-600 whitespace-nowrap">Surat Lamaran</button>
    <button onclick="switchTab('pitch')" class="px-3 py-1.5 text-xs font-semibold rounded-lg text-slate-600 whitespace-nowrap">Elevator Pitch</button>
    <button onclick="switchTab('logo')" class="px-3 py-1.5 text-xs font-semibold rounded-lg text-slate-600 whitespace-nowrap">Logo AI</button>
    <button onclick="switchTab('banner')" class="px-3 py-1.5 text-xs font-semibold rounded-lg text-slate-600 whitespace-nowrap">Banner Jualan</button>
  </div>

  <main class="flex-grow max-w-7xl w-full mx-auto p-4 sm:p-6 lg:p-8">

    <!-- TAB 1: CV BUILDER -->
    <section id="sec-cv" class="tab-content block">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
        
        <!-- Form Controls -->
        <div class="lg:col-span-5 space-y-6 no-print">
          
          <!-- Kustomisasi Warna CV -->
          <div class="bg-white p-5 rounded-2xl border border-slate-200 shadow-sm">
            <h3 class="font-bold text-slate-900 text-sm mb-3 flex items-center justify-between">
              <span>🎨 Ubah Warna Aksen CV</span>
            </h3>
            <div class="flex items-center space-x-3">
              <input type="color" id="cvAccentPicker" value="#2563eb" onchange="updateCvAccent(this.value)" class="w-10 h-10 rounded-lg cursor-pointer border-0">
              <div class="flex flex-wrap gap-2">
                <button onclick="updateCvAccent('#2563eb')" class="w-6 h-6 rounded-full bg-blue-600 ring-2 ring-offset-1 ring-transparent hover:ring-blue-400"></button>
                <button onclick="updateCvAccent('#1e3a8a')" class="w-6 h-6 rounded-full bg-blue-900 ring-2 ring-offset-1 ring-transparent hover:ring-blue-800"></button>
                <button onclick="updateCvAccent('#0d9488')" class="w-6 h-6 rounded-full bg-teal-600 ring-2 ring-offset-1 ring-transparent hover:ring-teal-400"></button>
                <button onclick="updateCvAccent('#dc2626')" class="w-6 h-6 rounded-full bg-red-600 ring-2 ring-offset-1 ring-transparent hover:ring-red-400"></button>
                <button onclick="updateCvAccent('#7c3aed')" class="w-6 h-6 rounded-full bg-purple-600 ring-2 ring-offset-1 ring-transparent hover:ring-purple-400"></button>
                <button onclick="updateCvAccent('#334155')" class="w-6 h-6 rounded-full bg-slate-700 ring-2 ring-offset-1 ring-transparent hover:ring-slate-500"></button>
              </div>
            </div>
          </div>

          <!-- Form Data Diri -->
          <div class="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm space-y-4">
            <h3 class="font-bold text-slate-900 text-base border-b border-slate-100 pb-2">Informasi Pribadi</h3>
            <div>
              <label class="block text-xs font-semibold text-slate-600 mb-1">Nama Lengkap</label>
              <input type="text" id="cvName" oninput="renderCv()" value="Ahmad Rizky" class="w-full px-3 py-2 text-sm rounded-lg border border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none">
            </div>
            <div>
              <label class="block text-xs font-semibold text-slate-600 mb-1">Posisi / Judul Profesional</label>
              <input type="text" id="cvTitle" oninput="renderCv()" value="Digital Marketing & Content Specialist" class="w-full px-3 py-2 text-sm rounded-lg border border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none">
            </div>
            <div class="grid grid-cols-2 gap-3">
              <div>
                <label class="block text-xs font-semibold text-slate-600 mb-1">Email</label>
                <input type="email" id="cvEmail" oninput="renderCv()" value="ahmad.rizky@email.com" class="w-full px-3 py-2 text-sm rounded-lg border border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none">
              </div>
              <div>
                <label class="block text-xs font-semibold text-slate-600 mb-1">Nomor HP / WhatsApp</label>
                <input type="text" id="cvPhone" oninput="renderCv()" value="+62 812-3456-7890" class="w-full px-3 py-2 text-sm rounded-lg border border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none">
              </div>
            </div>
            <div>
              <label class="block text-xs font-semibold text-slate-600 mb-1">Lokasi</label>
              <input type="text" id="cvLocation" oninput="renderCv()" value="Jakarta, Indonesia" class="w-full px-3 py-2 text-sm rounded-lg border border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none">
            </div>
            <div>
              <label class="block text-xs font-semibold text-slate-600 mb-1">Ringkasan Diri</label>
              <textarea id="cvSummary" oninput="renderCv()" rows="3" class="w-full px-3 py-2 text-sm rounded-lg border border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none">Spesialis pemasaran digital dengan pengalaman 4+ tahun dalam strategi konten, kampanye iklan berbayar, dan pertumbuhan media sosial. Berhasil meningkatkan conversion rate hingga 35%.</textarea>
            </div>
          </div>
        </div>

        <!-- Preview Document (Print Area) -->
        <div class="lg:col-span-7 flex justify-center">
          <div id="print-area" class="cv-paper p-8 text-slate-800">
            <!-- CV Header -->
            <div class="border-b-2 pb-6 mb-6 cv-accent-border">
              <h1 id="pvName" class="text-3xl font-extrabold text-slate-900 tracking-tight">Ahmad Rizky</h1>
              <p id="pvTitle" class="text-lg font-semibold cv-accent-text mt-1">Digital Marketing & Content Specialist</p>
              
              <div class="flex flex-wrap gap-4 text-xs text-slate-600 mt-3">
                <span id="pvEmail" class="flex items-center gap-1">📧 ahmad.rizky@email.com</span>
                <span id="pvPhone" class="flex items-center gap-1">📱 +62 812-3456-7890</span>
                <span id="pvLocation" class="flex items-center gap-1">📍 Jakarta, Indonesia</span>
              </div>
            </div>

            <!-- Profile Summary -->
            <div class="mb-6">
              <h2 class="text-sm font-bold uppercase tracking-wider text-slate-900 mb-2 cv-accent-text">Tentang Saya</h2>
              <p id="pvSummary" class="text-xs text-slate-600 leading-relaxed">
                Spesialis pemasaran digital dengan pengalaman 4+ tahun dalam strategi konten, kampanye iklan berbayar, dan pertumbuhan media sosial. Berhasil meningkatkan conversion rate hingga 35%.
              </p>
            </div>

            <!-- Experience -->
            <div class="mb-6">
              <h2 class="text-sm font-bold uppercase tracking-wider text-slate-900 mb-3 cv-accent-text">Pengalaman Kerja</h2>
              <div class="space-y-4 text-xs">
                <div>
                  <div class="flex justify-between font-bold text-slate-800">
                    <span>Senior Digital Marketer — PT Growth Agency</span>
                    <span class="text-slate-500 font-normal">2022 - Sekarang</span>
                  </div>
                  <ul class="list-disc list-inside text-slate-600 mt-1 space-y-1">
                    <li>Mengelola anggaran kampanye iklan bulanan senilai Rp 50 Juta di Meta Ads & Google Ads.</li>
                    <li>Merancang strategi konten media sosial yang menaikkan jumlah pengikut sebesar 120k+.</li>
                  </ul>
                </div>
                <div>
                  <div class="flex justify-between font-bold text-slate-800">
                    <span>Content Specialist — Creative Studio</span>
                    <span class="text-slate-500 font-normal">2020 - 2022</span>
                  </div>
                  <ul class="list-disc list-inside text-slate-600 mt-1 space-y-1">
                    <li>Menulis salinan penulisan iklan (copywriting) untuk 20+ klien bisnis.</li>
                  </ul>
                </div>
              </div>
            </div>

            <!-- Education & Skills Grid -->
            <div class="grid grid-cols-2 gap-6">
              <div>
                <h2 class="text-sm font-bold uppercase tracking-wider text-slate-900 mb-2 cv-accent-text">Pendidikan</h2>
                <div class="text-xs space-y-2">
                  <div>
                    <p class="font-bold text-slate-800">S1 Ilmu Komunikasi</p>
                    <p class="text-slate-500">Universitas Indonesia (2016 - 2020)</p>
                  </div>
                </div>
              </div>
              <div>
                <h2 class="text-sm font-bold uppercase tracking-wider text-slate-900 mb-2 cv-accent-text">Keahlian</h2>
                <div class="flex flex-wrap gap-1.5 text-[11px]">
                  <span class="bg-slate-100 text-slate-700 px-2 py-0.5 rounded font-medium">Meta Ads</span>
                  <span class="bg-slate-100 text-slate-700 px-2 py-0.5 rounded font-medium">SEO & Copywriting</span>
                  <span class="bg-slate-100 text-slate-700 px-2 py-0.5 rounded font-medium">Google Analytics</span>
                  <span class="bg-slate-100 text-slate-700 px-2 py-0.5 rounded font-medium">Canva & Content Plan</span>
                </div>
              </div>
            </div>

          </div>
        </div>

      </div>
    </section>

    <!-- TAB 2: SURAT LAMARAN -->
    <section id="sec-surat" class="tab-content hidden">
      <div class="max-w-4xl mx-auto bg-white p-8 rounded-2xl border border-slate-200 shadow-sm space-y-6">
        <h2 class="text-xl font-bold text-slate-900">Generator Surat Lamaran Kerja</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <input type="text" id="letterCompany" placeholder="Nama Perusahaan Target" value="PT Teknologi Nusantara" class="px-3 py-2 text-sm border rounded-lg">
          <input type="text" id="letterRole" placeholder="Posisi yang Dilamar" value="Digital Marketing Lead" class="px-3 py-2 text-sm border rounded-lg">
        </div>
        <button onclick="generateLetter()" class="bg-blue-600 text-white text-sm px-4 py-2 rounded-lg font-semibold hover:bg-blue-700">Buat Teks Surat</button>

        <div id="letterOutput" class="bg-slate-50 p-6 rounded-xl text-xs text-slate-700 leading-relaxed font-mono whitespace-pre-line border border-slate-200">
          Klik tombol di atas untuk membuat teks surat lamaran kerja otomatis.
        </div>
      </div>
    </section>

    <!-- TAB 3: ELEVATOR PITCH -->
    <section id="sec-pitch" class="tab-content hidden">
      <div class="max-w-3xl mx-auto bg-white p-8 rounded-2xl border border-slate-200 shadow-sm space-y-4">
        <h2 class="text-xl font-bold text-slate-900">Elevator Pitch Builder (30 Detik)</h2>
        <p class="text-xs text-slate-500">Format ringkas perkenalan diri untuk wawancara kerja atau bio LinkedIn.</p>
        <div class="p-4 bg-blue-50 text-blue-900 rounded-xl text-sm border border-blue-100">
          "Halo, nama saya <strong>Ahmad Rizky</strong>. Saya seorang <strong>Digital Marketing Specialist</strong> yang berfokus pada eksekusi kampanye berbayar dan pertumbuhan organik. Selama 4 tahun terakhir, saya telah membantu meningkatkan konversi penjualan sebesar 35%. Saya sangat antusias untuk membawa keahlian ini ke tim Anda."
        </div>
      </div>
    </section>

    <!-- TAB 4: LOGO AI GENERATOR -->
    <section id="sec-logo" class="tab-content hidden">
      <div class="max-w-3xl mx-auto bg-white p-8 rounded-2xl border border-slate-200 shadow-sm space-y-6 text-center">
        <h2 class="text-xl font-bold text-slate-900">Pembuat Logo Inisial Vector</h2>
        <p class="text-xs text-slate-500">Buat logo SVG minimalis untuk ditempel di CV atau profil Anda.</p>

        <div class="w-32 h-32 mx-auto rounded-full bg-blue-600 text-white font-extrabold text-4xl flex items-center justify-center shadow-lg tracking-widest border-4 border-blue-100" id="logoPreview">
          AR
        </div>

        <div class="flex justify-center space-x-2">
          <input type="text" id="logoInitials" value="AR" maxlength="3" class="px-3 py-2 text-center text-sm border rounded-lg w-24 uppercase font-bold" oninput="document.getElementById('logoPreview').innerText = this.value.toUpperCase()">
        </div>
      </div>
    </section>

    <!-- TAB 5: PEMBUAT BANNER JUALAN -->
    <section id="sec-banner" class="tab-content hidden">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
        
        <!-- Controls -->
        <div class="lg:col-span-5 bg-white p-6 rounded-2xl border border-slate-200 shadow-sm space-y-4">
          <h2 class="text-lg font-bold text-slate-900 flex items-center gap-2">
            <span>🚀 Pengaturan Banner Promo</span>
          </h2>

          <div>
            <label class="block text-xs font-semibold text-slate-600 mb-1">Rasio Banner</label>
            <select id="bannerRatio" onchange="renderBanner()" class="w-full px-3 py-2 text-sm border rounded-lg">
              <option value="1:1">Instagram Post (1:1)</option>
              <option value="9:16">IG Story / TikTok (9:16)</option>
              <option value="2
