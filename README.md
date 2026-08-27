import time

def yaz(metin):
    print(metin)
    time.sleep(0.5)

while True:

    print("\n" + "=" * 45)
    print("        NISA'YI NE KADAR TANIYORSUN?")
    print("=" * 45)

    oyuncu = input("\nAdin ne? ")

    print("\nHos geldin", oyuncu + "!")
    print("Bu oyunda Nisa hakkinda 20 soru var.")
    print("Her dogru cevap 1 puan.")
    print("Hazirsan basliyoruz...")
    
    time.sleep(2)

    puan = 0
    seri = 0

    sorular = [

        {
            "soru": "Nisa'nin en sevdigi yemek hangisidir?",
            "secenekler": ["Pizza", "Manti", "Tavuklu pilav", "Hamburger"],
            "cevap": "C"
        },

        {
            "soru": "Nisa'nin sevmedigi bir yemek var mi?",
            "secenekler": ["Evet, bir suru var", "Sadece sebze yemegi",
                           "Sadece balik", "Yok"],
            "cevap": "D"
        },

        {
            "soru": "Nisa bos zamaninda en cok ne yapmayi sever?",
            "secenekler": ["Kitap okumak", "Yeni filmler izlemek",
                           "Spor yapmak", "Yemek yapmak"],
            "cevap": "B"
        },

        {
            "soru": "Nisa'nin en sevdigi renk hangisidir?",
            "secenekler": ["Siyah", "Pembe", "Mavi", "Beyaz"],
            "cevap": "D"
        },

        {
            "soru": "Nisa'nin en sevdigi sarkici kimdir?",
            "secenekler": ["Ahmet Kaya", "Tarkan", "Sezen Aksu", "Mabel Matiz"],
            "cevap": "A"
        },

        {
            "soru": "Nisa'nin en sevdigi sarki hangisidir?",
            "secenekler": ["Kumralim", "Dardayim",
                           "Ben Seni Cok Sevdim", "Resimdeki Gozyaslari"],
            "cevap": "B"
        },

        {
            "soru": "Nisa'nin en sevdigi dizi hangisidir?",
            "secenekler": ["Yargi", "Medcezir", "Sonyaz", "Kiralik Ask"],
            "cevap": "C"
        },

        {
            "soru": "Nisa hangi ulkeye gitmek ister?",
            "secenekler": ["Italya", "Fransa", "Amerika", "Ispanya"],
            "cevap": "D"
        },

        {
            "soru": "Nisa sabah insani mi gece insani mi?",
            "secenekler": ["Sabah insani", "Gece insani",
                           "Ikisi de", "Hicbiri"],
            "cevap": "B"
        },

        {
            "soru": "Nisa sinirlendiginde genellikle ne yapar?",
            "secenekler": ["Susup bekler",
                           "Uyur",
                           "Bazen sinirini sucsuz insanlardan cikarir",
                           "Hemen ortamdan gider"],
            "cevap": "C"
        },

        {
            "soru": "Nisa en cok neye guler?",
            "secenekler": ["Sadece komik videolara",
                           "Sadece esprilere",
                           "Hicbir seye",
                           "Her seye"],
            "cevap": "D"
        },

        {
            "soru": "Nisa insanlarda en sevmedigi ozellik nedir?",
            "secenekler": ["Sessiz olmak",
                           "Insanlari kucuk dusurmek",
                           "Cok konusmak",
                           "Utangac olmak"],
            "cevap": "B"
        },

        {
            "soru": "Nisa insanlarda en cok hangi ozelligi sever?",
            "secenekler": ["Kibirli olmak",
                           "Cok konusmak",
                           "Mutevazi olmak",
                           "Cok ciddi olmak"],
            "cevap": "C"
        },

        {
            "soru": "Nisa'ya yapilabilecek en guzel surpriz nedir?",
            "secenekler": ["Sadece pahali hediyeler",
                           "Tatile goturmek",
                           "Her sey",
                           "Sadece cicek"],
            "cevap": "C"
        },

        {
            "soru": "Nisa alisveris yaparken en cok ne alir?",
            "secenekler": ["Kitap", "Makyaj malzemesi",
                           "Ayakkabi", "Teknolojik urun"],
            "cevap": "B"
        },

        {
            "soru": "Nisa telefonda en cok hangi uygulamayi kullanir?",
            "secenekler": ["Instagram", "YouTube", "TikTok", "WhatsApp"],
            "cevap": "C"
        },

        {
            "soru": "Nisa'nin en buyuk hayallerinden biri nedir?",
            "secenekler": ["Guzellik merkezi acmak",
                           "Futbolcu olmak",
                           "Yazar olmak",
                           "Ogretmen olmak"],
            "cevap": "A"
        },

        {
            "soru": "Nisa'nin bir diger buyuk hayali nedir?",
            "secenekler": ["Bir ada satin almak",
                           "Butun dunyayi gezmek",
                           "Uzaya gitmek",
                           "Yarismaya katilmak"],
            "cevap": "B"
        },

        {
            "soru": "Nisa'yi en hizli ne mutlu eder?",
            "secenekler": ["Sadece pahali hediyeler",
                           "Sadece tatil",
                           "Ufacik bir hediye bile",
                           "Para"],
            "cevap": "C"
        },

        {
            "soru": "Nisa'nin en belirgin huyu nedir?",
            "secenekler": ["Kiskanc olmasi",
                           "Merhametli olmasi",
                           "Sinirli olmasi",
                           "Cok ciddi olmasi"],
            "cevap": "B"
        }
    ]

    for i, soru in enumerate(sorular, 1):

        print("\n" + "-" * 45)
        print("SORU", i, "/ 20")
        print("-" * 45)

        print(soru["soru"])

        harfler = ["A", "B", "C", "D"]

        for harf, secenek in zip(harfler, soru["secenekler"]):
            print(harf + ") " + secenek)

        cevap = input("\nCevabin: ").upper()

        while cevap not in ["A", "B", "C", "D"]:
            print("Lutfen A, B, C veya D gir.")
            cevap = input("Cevabin: ").upper()

        if cevap == soru["cevap"]:
            puan += 1
            seri += 1

            print("\nDOGRU! 🎉")
            print("Seri:", seri)
            print("Skor:", puan, "/", i)

            if seri == 3:
                print("🔥 3'te 3! Nisa'yi baya iyi taniyorsun!")
            elif seri == 5:
                print("🔥🔥 5'te 5! Bu artik supheli...")
            elif seri == 10:
                print("🔥🔥🔥 10'da 10! Nisa'nin biyografisini mi okudun?")

        else:
            seri = 0

            print("\nYANLIS! 😭")
            print("Dogru cevap:", soru["cevap"])
            print("Skor:", puan, "/", i)

        time.sleep(1)

    yuzde = (puan / 20) * 100

    print("\n")
    print("=" * 45)
    print("             OYUN BITTI!")
    print("=" * 45)

    print("\nOyuncu:", oyuncu)
    print("Toplam skor:", puan, "/ 20")
    print("Basari orani: %", int(yuzde))

    print("\nSONUCUN:")

    if puan == 20:
        print("🏆 EFSANE!")
        print("Nisa'yi Nisa'dan bile iyi taniyorsun.")
    elif puan >= 17:
        print("🥇 MUKEMMEL!")
        print("Nisa hakkinda baya saglam bilgiye sahipsin.")
    elif puan >= 14:
        print("🥈 COK IYI!")
        print("Nisa seni sever, bu testten geciyorsun.")
    elif puan >= 10:
        print("🥉 ORTA!")
        print("Biraz daha Nisa bilgisi lazim.")
    elif puan >= 5:
        print("😅 ZAYIF!")
        print("Nisa seni tanisa bile sen Nisa'yi pek tanimiyorsun.")
    else:
        print("💀 FELAKET!")
        print("Sen bu teste nasil girdin amk?")

    print("\n" + "=" * 45)

    tekrar = input("\nTekrar oynamak ister misin? (E/H): ").upper()

    if tekrar != "E":
        print("\nOynadigin icin tesekkurler", oyuncu + "!")
        print("Gorusuruz 👋")
        break
