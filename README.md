import tkinter as tk
import random

# -----------------------------
# RENKLER
# -----------------------------

ARKA_PLAN = "#FFF4F8"
PEMBE = "#FF6B9A"
KOYU_PEMBE = "#E84A7A"
BEYAZ = "#FFFFFF"
YAZI = "#333333"
YESIL = "#65C18C"
KIRMIZI = "#F06C6C"
MOR = "#9B7EDE"

# -----------------------------
# SORULAR
# -----------------------------

sorular = [
    {
        "soru": "Nisa'nin en sevdigi yemek hangisidir?",
        "secenekler": ["Pizza", "Manti", "Tavuklu pilav", "Hamburger"],
        "cevap": 2
    },
    {
        "soru": "Nisa'nin sevmedigi bir yemek var mi?",
        "secenekler": ["Evet, bir suru var", "Sadece sebze",
                       "Sadece balik", "Yok"],
        "cevap": 3
    },
    {
        "soru": "Nisa bos zamaninda en cok ne yapmayi sever?",
        "secenekler": ["Kitap okumak", "Yeni filmler izlemek",
                       "Spor yapmak", "Yemek yapmak"],
        "cevap": 1
    },
    {
        "soru": "Nisa'nin en sevdigi renk hangisidir?",
        "secenekler": ["Siyah", "Pembe", "Mavi", "Beyaz"],
        "cevap": 3
    },
    {
        "soru": "Nisa'nin en sevdigi sarkici kimdir?",
        "secenekler": ["Ahmet Kaya", "Tarkan",
                       "Sezen Aksu", "Mabel Matiz"],
        "cevap": 0
    },
    {
        "soru": "Nisa'nin en sevdigi sarki hangisidir?",
        "secenekler": ["Kumralim", "Dardayim",
                       "Ben Seni Cok Sevdim", "Resimdeki Gozyaslari"],
        "cevap": 1
    },
    {
        "soru": "Nisa'nin en sevdigi dizi hangisidir?",
        "secenekler": ["Yargi", "Medcezir", "Sonyaz", "Kiralik Ask"],
        "cevap": 2
    },
    {
        "soru": "Nisa hangi ulkeye gitmek ister?",
        "secenekler": ["Italya", "Fransa", "Amerika", "Ispanya"],
        "cevap": 3
    },
    {
        "soru": "Nisa sabah insani mi gece insani mi?",
        "secenekler": ["Sabah insani", "Gece insani",
                       "Ikisi de", "Hicbiri"],
        "cevap": 1
    },
    {
        "soru": "Nisa sinirlendiginde genellikle ne yapar?",
        "secenekler": ["Susup bekler", "Uyur",
                       "Bazen sinirini sucsuz insanlardan cikarir",
                       "Hemen ortamdan gider"],
        "cevap": 2
    },
    {
        "soru": "Nisa en cok neye guler?",
        "secenekler": ["Sadece komik videolara",
                       "Sadece esprilere", "Hicbir seye", "Her seye"],
        "cevap": 3
    },
    {
        "soru": "Nisa insanlarda en sevmedigi ozellik nedir?",
        "secenekler": ["Sessiz olmak",
                       "Insanlari kucuk dusurmek",
                       "Cok konusmak", "Utangac olmak"],
        "cevap": 1
    },
    {
        "soru": "Nisa insanlarda en cok hangi ozelligi sever?",
        "secenekler": ["Kibirli olmak",
                       "Cok konusmak",
                       "Mutevazi olmak",
                       "Cok ciddi olmak"],
        "cevap": 2
    },
    {
        "soru": "Nisa'ya yapilabilecek en guzel surpriz nedir?",
        "secenekler": ["Sadece pahali hediyeler",
                       "Tatile goturmek",
                       "Her sey",
                       "Sadece cicek"],
        "cevap": 2
    },
    {
        "soru": "Nisa alisveris yaparken en cok ne alir?",
        "secenekler": ["Kitap", "Makyaj malzemesi",
                       "Ayakkabi", "Teknolojik urun"],
        "cevap": 1
    },
    {
        "soru": "Nisa telefonda en cok hangi uygulamayi kullanir?",
        "secenekler": ["Instagram", "YouTube", "TikTok", "WhatsApp"],
        "cevap": 2
    },
    {
        "soru": "Nisa'nin en buyuk hayallerinden biri nedir?",
        "secenekler": ["Guzellik merkezi acmak",
                       "Futbolcu olmak", "Yazar olmak",
                       "Ogretmen olmak"],
        "cevap": 0
    },
    {
        "soru": "Nisa'nin bir diger buyuk hayali nedir?",
        "secenekler": ["Bir ada satin almak",
                       "Butun dunyayi gezmek",
                       "Uzaya gitmek", "Yarismaya katilmak"],
        "cevap": 1
    },
    {
        "soru": "Nisa'yi en hizli ne mutlu eder?",
        "secenekler": ["Sadece pahali hediyeler",
                       "Sadece tatil",
                       "Ufacik bir hediye bile", "Para"],
        "cevap": 2
    },
    {
        "soru": "Nisa'nin en belirgin huyu nedir?",
        "secenekler": ["Kiskanc olmasi",
                       "Merhametli olmasi",
                       "Sinirli olmasi",
                       "Cok ciddi olmasi"],
        "cevap": 1
    }
]

# -----------------------------
# ANA PENCERE
# -----------------------------

pencere = tk.Tk()
pencere.title("Nisa'yi Ne Kadar Taniyorsun?")
pencere.geometry("700x650")
pencere.configure(bg=ARKA_PLAN)
pencere.resizable(False, False)

puan = 0
soru_no = 0


# -----------------------------
# BASLANGIC EKRANI
# -----------------------------

def baslangic():

    temizle()

    baslik = tk.Label(
        pencere,
        text="NISA'YI NE KADAR TANIYORSUN?",
        font=("Arial", 27, "bold"),
        bg=ARKA_PLAN,
        fg=KOYU_PEMBE
    )
    baslik.pack(pady=(80, 20))

    alt = tk.Label(
        pencere,
        text="Bakalım Nisa'yi gercekten taniyor musun? 💗",
        font=("Arial", 14),
        bg=ARKA_PLAN,
        fg=YAZI
    )
    alt.pack(pady=10)

    bilgi = tk.Label(
        pencere,
        text="20 soru • Her dogru cevap 1 puan",
        font=("Arial", 12),
        bg=ARKA_PLAN,
        fg=MOR
    )
    bilgi.pack(pady=10)

    basla = tk.Button(
        pencere,
        text="OYUNA BASLA",
        font=("Arial", 16, "bold"),
        bg=PEMBE,
        fg=BEYAZ,
        activebackground=KOYU_PEMBE,
        activeforeground=BEYAZ,
        relief="flat",
        cursor="hand2",
        padx=45,
        pady=15,
        command=oyunu_baslat
    )
    basla.pack(pady=40)


# -----------------------------
# OYUNU BASLAT
# -----------------------------

def oyunu_baslat():

    global puan, soru_no

    puan = 0
    soru_no = 0

    soru_goster()


# -----------------------------
# SORU EKRANI
# -----------------------------

def soru_goster():

    temizle()

    soru = sorular[soru_no]

    # Ust kisim
    ust = tk.Frame(pencere, bg=ARKA_PLAN)
    ust.pack(fill="x", padx=35, pady=(25, 10))

    soru_sayisi = tk.Label(
        ust,
        text=f"SORU {soru_no + 1} / 20",
        font=("Arial", 13, "bold"),
        bg=ARKA_PLAN,
        fg=KOYU_PEMBE
    )
    soru_sayisi.pack(side="left")

    skor = tk.Label(
        ust,
        text=f"SKOR: {puan}",
        font=("Arial", 13, "bold"),
        bg=ARKA_PLAN,
        fg=MOR
    )
    skor.pack(side="right")

    # Ilerleme cubugu
    ilerleme = tk.Canvas(
        pencere,
        width=620,
        height=12,
        bg="#F0DDE4",
        highlightthickness=0
    )
    ilerleme.pack(pady=10)

    doluluk = (soru_no + 1) / 20 * 620

    ilerleme.create_rectangle(
        0, 0, doluluk, 12,
        fill=PEMBE,
        outline=""
    )

    # Soru kutusu
    soru_kutusu = tk.Frame(
        pencere,
        bg=BEYAZ,
        padx=25,
        pady=25
    )
    soru_kutusu.pack(
        padx=40,
        pady=25,
        fill="x"
    )

    soru_metni = tk.Label(
        soru_kutusu,
        text=soru["soru"],
        font=("Arial", 18, "bold"),
        bg=BEYAZ,
        fg=YAZI,
        wraplength=560,
        justify="center"
    )
    soru_metni.pack()

    # Secenekler
    harfler = ["A", "B", "C", "D"]

    for i in range(4):

        buton = tk.Button(
            pencere,
            text=f"{harfler[i]}) {soru['secenekler'][i]}",
            font=("Arial", 13, "bold"),
            bg=BEYAZ,
            fg=YAZI,
            activebackground=PEMBE,
            activeforeground=BEYAZ,
            relief="flat",
            cursor="hand2",
            width=52,
            pady=10,
            command=lambda x=i: cevap_kontrol(x)
        )

        buton.pack(pady=6)


# -----------------------------
# CEVAP KONTROL
# -----------------------------

def cevap_kontrol(secim):

    global puan

    dogru = sorular[soru_no]["cevap"]

    if secim == dogru:
        puan += 1
        mesaj = "DOGRU! 🎉"
        renk = YESIL
    else:
        mesaj = "YANLIS! 😭"
        renk = KIRMIZI

    sonuc = tk.Label(
        pencere,
        text=mesaj,
        font=("Arial", 16, "bold"),
        bg=ARKA_PLAN,
        fg=renk
    )
    sonuc.pack(pady=8)

    pencere.after(800, sonraki_soru)


# -----------------------------
# SONRAKI SORU
# -----------------------------

def sonraki_soru():

    global soru_no

    soru_no += 1

    if soru_no >= 20:
        final_ekrani()
    else:
        soru_goster()


# -----------------------------
# FINAL EKRANI
# -----------------------------

def final_ekrani():

    temizle()

    yuzde = int((puan / 20) * 100)

    baslik = tk.Label(
        pencere,
        text="OYUN BITTI! 🎉",
        font=("Arial", 30, "bold"),
        bg=ARKA_PLAN,
        fg=KOYU_PEMBE
    )
    baslik.pack(pady=(70, 25))

    skor = tk.Label(
        pencere,
        text=f"{puan} / 20",
        font=("Arial", 45, "bold"),
        bg=ARKA_PLAN,
        fg=MOR
    )
    skor.pack()

    oran = tk.Label(
        pencere,
        text=f"Basari: %{yuzde}",
        font=("Arial", 16),
        bg=ARKA_PLAN,
        fg=YAZI
    )
    oran.pack(pady=10)

    if puan == 20:
        mesaj = "🏆 EFSANE!\nNisa'yi senden iyi taniyan yok!"
    elif puan >= 17:
        mesaj = "🥇 MUKEMMEL!\nNisa hakkinda baya bilgi sahibisin."
    elif puan >= 14:
        mesaj = "🥈 COK IYI!\nNisa seni sever."
    elif puan >= 10:
        mesaj = "🥉 ORTA!\nBiraz daha Nisa bilgisi lazim."
    elif puan >= 5:
        mesaj = "😅 ZAYIF!\nNisa'yi biraz daha taniman lazim."
    else:
        mesaj = "💀 FELAKET!\nSen bu teste nasil girdin?"

    sonuc = tk.Label(
        pencere,
        text=mesaj,
        font=("Arial", 17, "bold"),
        bg=ARKA_PLAN,
        fg=YAZI,
        justify="center"
    )
    sonuc.pack(pady=30)

    tekrar = tk.Button(
        pencere,
        text="TEKRAR OYNA",
        font=("Arial", 14, "bold"),
        bg=PEMBE,
        fg=BEYAZ,
        relief="flat",
        cursor="hand2",
        padx=35,
        pady=12,
        command=baslangic
    )
    tekrar.pack(pady=10)

    cikis = tk.Button(
        pencere,
        text="CIKIS",
        font=("Arial", 12),
        bg=ARKA_PLAN,
        fg=KOYU_PEMBE,
        relief="flat",
        cursor="hand2",
        command=pencere.destroy
    )
    cikis.pack()


# -----------------------------
# EKRANI TEMIZLE
# -----------------------------

def temizle():

    for widget in pencere.winfo_children():
        widget.destroy()


# -----------------------------
# PROGRAMI BASLAT
# -----------------------------

baslangic()

pencere.mainloop()
