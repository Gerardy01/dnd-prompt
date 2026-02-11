[SYSTEM INSTRUCTION: SAVE GAME SEQUENCE]

Kita akan melakukan migrasi ke sesi baru (New Chat) untuk menyegarkan memori. Saya butuh kamu men-generate **"WORLD STATE CHECKPOINT"**.

**ATURAN PENTING:**
1.  **JANGAN** sertakan data statistik karakter saya (HP, Spell Slot, Inventory Personal, XP) karena saya melacaknya sendiri.
2.  **SERTAKAN** data statistik LENGKAP Companion/Sidekick (HP, AC, Skill) karena AI di sesi baru butuh data ini untuk simulasi combat.
3.  FOKUS sepenuhnya pada **Lingkungan, Narasi, Peta, Companion, dan NPC**.

Tolong output data berikut dalam satu **Code Block** agar mudah saya copy:

---
**[WORLD STATE DATA]**

**1. Narrative Recap:**
(Ringkasan singkat kejadian terakhir dalam 1-2 kalimat).

**2. Current Location & Atmosphere:**
- **Zone Name:** (Nama Area/Ruangan)
- **Sensory Details:** (Apa yang terlihat, terdengar, dan tercium saat ini. *Penting untuk Theater of the Mind di sesi baru*).
- **Lighting:** (Terang/Redup/Gelap).

**3. Tactical Map State:**
(Generate ulang Peta ASCII kondisi DETIK INI juga. Pastikan posisi Player [@], Companion [C], Musuh [E], dan Objek [O] akurat sesuai langkah terakhir).
(Sertakan Legenda Simbol).

**4. Companion / Sidekick Data (CRITICAL):**
(Ulangi blok ini jika ada lebih dari 1 companion. Jika tidak ada, tulis "None").
- **Name:**
- **Race/Class:**
- **HP:** (Current/Max)
- **AC:**
- **Primary Weapon/Attack:** (Contoh: Shortbow +4 hit, 1d6+2 dmg)
- **Key Skills:** (Contoh: Stealth, Survival)
- **Personality/Tactics:** (Contoh: Suka menyerang jarak jauh, penakut, atau agresif).
- **Current Condition:** (Posisi terakhir & status fisik).
- **Current Activity:** (Apa yang sedang mereka lakukan saat sesi berhenti? Contoh: Menjaga pintu, Berlindung, Menyiapkan mantra).

**5. Entity & Object Status:**
- **NPC/Enemy:** Daftar siapa saja yang masih hidup/aktif di area ini & kondisi mereka (Luka Parah/Sehat).
- **Interactive Objects:** Pintu (terbuka/kunci?), Peti (sudah dijarah?), Jebakan (aktif/nonaktif?).

**6. Active Quest/Objective:**
- Apa tujuan terdekat (Immediate Goal) saat ini?

**7. Unclaimed Loot:**
- Daftar item yang masih tergeletak di tanah/ruangan yang BELUM saya masukkan ke inventory (jika ada).

**[END OF WORLD DATA]**
---