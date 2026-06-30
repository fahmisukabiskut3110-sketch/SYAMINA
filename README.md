<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generator Script Konten Afiliasi</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        body { font-family: 'Inter', sans-serif; }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col justify-between">

    <header class="bg-white border-b border-slate-200 py-4 shadow-sm">
        <div class="container mx-auto px-4 max-w-4xl flex justify-between items-center">
            <h1 class="text-xl font-bold text-indigo-600">Affiliate<span class="text-slate-700">ScriptGen</span></h1>
            <span class="text-xs bg-indigo-50 text-indigo-700 px-2.5 py-1 rounded-full font-medium">v1.0</span>
        </div>
    </header>

    <main class="container mx-auto px-4 max-w-4xl my-8 flex-grow">
        <div class="text-center mb-8">
            <h2 class="text-3xl font-extrabold text-slate-900 tracking-tight sm:text-4xl">Generator Script Konten Afiliasi</h2>
            <p class="mt-2 text-sm text-slate-600">Buat skrip video promosi TikTok, Reels, atau Shorts dalam hitungan detik.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 space-y-4">
                <h3 class="text-lg font-semibold text-slate-900 border-b pb-2">Detail Produk</h3>
                
                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-slate-500 mb-1">Nama Produk</label>
                    <input type="text" id="productName" placeholder="Contoh: Lampu Meja LED Estetik" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm">
                </div>

                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-slate-500 mb-1">Target Audiens</label>
                    <input type="text" id="targetAudience" placeholder="Contoh: Mahasiswa, Pekerja WFH" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm">
                </div>

                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-slate-500 mb-1">Kelebihan Utama (Pisahkan dengan koma)</label>
                    <textarea id="features" rows="3" placeholder="Contoh: Baterai awet 12 jam, 3 tingkat kecerahan, desain minimalis" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm resize-none"></textarea>
                </div>

                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-slate-500 mb-1">Call to Action (CTA)</label>
                    <input type="text" id="cta" placeholder="Contoh: Klik keranjang kuning sekarang!" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm">
                </div>

                <button onclick="generateScript()" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-medium py-2.5 px-4 rounded-lg transition duration-200 text-sm cursor-pointer shadow-sm">
                    Generate Script ✨
                </button>
            </div>

            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 flex flex-col justify-between">
                <div>
                    <h3 class="text-lg font-semibold text-slate-900 border-b pb-2 mb-4">Hasil Script</h3>
                    
                    <div id="outputContainer" class="hidden space-y-4">
                        <div class="bg-slate-50 p-4 rounded-xl border border-slate-200">
                            <p id="generatedScript" class="text-sm text-slate-700 whitespace-pre-line leading-relaxed"></p>
                        </div>
                        <button onclick="copyToClipboard()" class="inline-flex items-center text-xs font-medium text-indigo-600 hover:text-indigo-800 cursor-pointer">
                            <svg class="w-4 h-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 5H6a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2v-1M8 5a2 2 0 002 2h2a2 2 0 002-2M8 5a2 2 0 012-2h2a2 2 0 012 2m0 0h2a2 2 0 012 2v3m2 4H10m0 0l3-3m-3 3l3 3"></path></svg>
                            Salin ke Papan Klip
                        </button>
                    </div>

                    <div id="placeholderText" class="text-center py-12 text-slate-400">
                        <svg class="w-12 h-12 mx-auto mb-2 text-slate-300" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path></svg>
                        <p class="text-sm">Isi form di samping untuk membuat script.</p>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <footer class="bg-white border-t border-slate-200 py-4 text-center text-xs text-slate-500">
        &copy; 2026 AffiliateScriptGen. All rights reserved.
    </footer>

    <script>
        function generateScript() {
            // Ambil data dari input
            const product = document.getElementById('productName').value.trim();
            const audiens = document.getElementById('targetAudience').value.trim();
            const features = document.getElementById('features').value.trim();
            const cta = document.getElementById('cta').value.trim();

            // Validasi sederhana
            if (!product || !features || !cta) {
                alert('Mohon isi minimal Nama Produk, Kelebihan, dan CTA!');
                return;
            }

            // Template Script AIDA (Attention, Interest, Desire, Action)
            const script = `🎥 [0-3 detik - HOOK ATTENTION]
"Spesial buat kalian para ${audiens || 'Netizen'} yang lagi nyari solusi praktis! Sering gak sih ngerasa ribet atau kurang sreg sama produk yang biasa aja?"

📦 [3-15 detik - INTRODUCE PRODUCT & INTEREST]
"Nah, kenalin nih: *${product}*! Produk yang lagi viral banget karena emang se-berguna itu."

💡 [15-45 detik - DESIRE / BENEFITS]
"Kenapa kalian harus punya? Ini dia kelebihannya:
${features.split(',').map(f => `• ${f.trim()}`).join('\n')}
Bener-bener ngebantu banget buat rutinitas harian kita."

🛒 [45-60 detik - CALL TO ACTION]
"Jangan sampai kehabisan promonya ya. ${cta} ✨"`;

            // Tampilkan hasil
            document.getElementById('generatedScript').innerText = script;
            document.getElementById('placeholderText').classList.add('hidden');
            document.getElementById('outputContainer').classList.remove('hidden');
        }

        function copyToClipboard() {
            const textText = document.getElementById('generatedScript').innerText;
            navigator.clipboard.writeText(textText).then(() => {
                alert('Script berhasil disalin!');
            }).catch(err => {
                alert('Gagal menyalin teks: ', err);
            });
        }
    </script>
</body>
</html>
