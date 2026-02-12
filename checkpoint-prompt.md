***[SYSTEM INSTRUCTION: GAME STATE SERIALIZATION & MERGE]***

Kita akan mengakhiri sesi ini. Tugasmu adalah melakukan **State Persistence** ke dalam format JSON agar game bisa dilanjutkan di sesi baru atau model AI lain.

**ATURAN UTAMA GENERASI DATA:**
1.  **MERGE & UPDATE:** Jika user memberikan JSON lama, gabungkan dengan kejadian sesi ini.
    * *NPC:* Jika bertemu NPC yang sudah ada di list, update status/lokasinya. Jangan buat duplikat.
    * *Quests:* Pindahkan quest yang selesai ke `completed_log` dan **RINGKAS** deskripsinya untuk hemat memori.
2.  **PEMISAHAN DATA:** Jangan masukkan Stat Block/Inventory Player (User memegang data itu sendiri). Fokus pada Dunia, NPC, dan Story.
3.  **OUTPUT:** Berikan **SATU BLOK JSON** valid, dan juga map ASCII nya dalam bentuk md, Tanpa teks pengantar.

**KONDISI A: JIKA ADA SAVE DATA LAMA (Update Mode)**
Jangan buat JSON dari nol! Gunakan JSON lama sebagai basis, lalu lakukan **PATCHING**:
1.  **Overwrite (Timpa):** Update field yang dinamis seperti `current_location`, `time`, `hp`, `active_encounter` dengan kondisi TERAKHIR saat ini.
2.  **Append (Tambah):** Masukkan item/quest/NPC *baru* yang ditemui sesi ini ke dalam list yang sudah ada.
3.  **Preserve (Pertahankan):** JANGAN HAPUS data lama (NPC masa lalu, Quest yang sudah selesai di sesi lampau) meskipun tidak dibahas di sesi ini. Biarkan mereka tetap ada di memori JSON.

**KONDISI B: JIKA NEW GAME (Create Mode)**
Buat JSON baru dari nol menggunakan template standar di bawah.

**TACTICAL MAP STATE**
(Generate ulang Peta ASCII kondisi DETIK INI juga. Pastikan posisi Player [@], Companion [C], Musuh [E], dan Objek [O] akurat sesuai langkah terakhir).
(Sertakan Legenda Simbol).

---

**INSTRUKSI FORMATTING:**
2. Output JSON datanya dan juga Map ASCII nya bila ada

**TEMPLATE STRUKTUR JSON (Gunakan ini sebagai acuan struktur):**
```json
{
    "header": {
        "timestamp": "End of Session [Nomor Sesi]",
        "session_summary": "[1 kalimat rangkuman sesi ini]"
    },
    "campaign_status": {
        "module_name": "[Nama Modul/Dunia]",
        "ruleset": "D&D 5e",
        "narrative_tone": "[Tone cerita saat ini]",
        "players": ["[Nama Karakter]"],
        "time_management": {
            "in_game_date": "[Hari, Bulan, Tahun]",
            "time_of_day": "[Pagi/Siang/Sore/Malam]",
            "last_rest_status": "[Kapan terakhir Long Rest?]"
        }
    },
    "companions_data": [
        // HANYA diisi jika ada Companion/Follower/Pet yang aktif bersama party.
        // {
        //   "name": "[Nama Companion]",
        //   "race_class": "[e.g., Human Paladin]",
        //   "hp": "[Health]",
        //   "ac": "[Armor Class]",
        //   "weapon": "[e.g., Shortbow]",
        //   "key_skills": "[e.g., Stealth, Survival]",
        //   "personality": "[e.g., Suka menyerang jarak jauh, penakut, atau agresif]",
        //   "current_condition": "[Posisi terakhir & status fisik]",
        //   "current_activity": "[Apa yang sedang mereka lakukan saat sesi berhenti]"
        // }
    ],
    "quest_log": {
        "main_objective": "[Tujuan utama campaign/journey]",
        "active_side_quests": [
            "[Quest 1 yang masih aktif]",
            "[Quest 2 yang masih aktif]"
        ],
        "completed_quests": [
            "[Quest yang diselesaikan di sesi INI]"
        ]
    },
    "world_memory": {
        "known_npcs": [
            {
                "name": "[Nama NPC]",
                "role": "[Pekerjaan/Peran, e.g., Bartender, Blacksmith, Bandit Chief]",
                "attitude": "[Friendly/Neutral/Hostile/Unknown]",
                "status": "[Alive/Dead/Missing/Transformed]",
                "last_known_location": "[Kota/Dungeon/Tempat]"
            }
        ],
        "key_events": [
            "[Rangkuman singkat kejadian penting Sesi TERAKHIR ini, 1-3 poin]"
        ],
        "discovered_secrets": [
            "[List rahasia/clue yang sudah diketahui player tapi belum terselesaikan]"
        ]
    },
    "current_session_state": {
        "location_name": "[Lokasi Spesifik]",
        "sensory_details": "[Deskripsi visual, suara, bau]"
    },
    "party_assets": [
        // HANYA diisi jika ada barang yang termasuk ke party assets, dan bukan di dalam Inventory Player.
        // {
        //     "name": "[Nama]",
        //     "description": "[Deskripsi]"
        // }
    ]
}