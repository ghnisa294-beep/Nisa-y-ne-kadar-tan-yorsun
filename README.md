# yaz-l-m-oyunu
# Sorumluluk Sınavı Oyunu 🎮

Bu proje, öğrencilerin sorumluluk sınavlarına hazırlanmasına yardımcı olmak amacıyla hazırlanmış eğlenceli bir soru-cevap oyunudur.

## 🎯 Özellikler

- Çoktan seçmeli sorular
- Doğru ve yanlış cevap kontrolü
- Puan sistemi
- Sınav sonunda sonuç gösterme
- Basit ve kullanışlı arayüz

## 💻 Kullanılan Teknolojiler

- HTML
- CSS
- JavaScript

## 🚀 Nasıl Çalıştırılır?

1. Projeyi GitHub'dan indirin.
2. `index.html` dosyasını açın.
3. Oyun tarayıcıda çalışacaktır.

## 📁 Dosyalar

- `index.html` → Ana sayfa
- `style.css` → Tasarım ve görünüm
- `script.js` → Oyunun kodları
- `README.md` → Proje hakkında bilgiler
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yazılım Sorumluluk Sınavı Oyunu</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #1e1e2e;
            color: #cdd6f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .quiz-container {
            background-color: #313244;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 8px 24px rgba(0,0,0,0.3);
            width: 450px;
            max-width: 90%;
            text-align: center;
        }
        .badge {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
            margin-bottom: 15px;
            text-transform: uppercase;
        }
        .easy { background-color: #a6e3a1; color: #11111b; }
        .medium { background-color: #f9e2af; color: #11111b; }
        .hard { background-color: #f38ba8; color: #11111b; }
        
        h2 { font-size: 18px; margin-bottom: 20px; height: 50px; }
        .btn-grid { display: grid; gap: 10px; }
        button {
            background-color: #45475a;
            color: #cdd6f4;
            border: 2px solid transparent;
            padding: 12px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.2s;
        }
        button:hover { background-color: #585b70; }
        .correct { background-color: #a6e3a1 !important; color: #11111b; font-weight: bold; }
        .wrong { background-color: #f38ba8 !important; color: #11111b; font-weight: bold; }
        .score { font-size: 14px; color: #a6adc8; margin-top: 15px; }
    </style>
</head>
<body>

<div class="quiz-container" id="quiz">
    <div id="badge" class="badge easy">Kolay Seviye</div>
    <h2 id="question">Soru yükleniyor...</h2>
    <div class="btn-grid" id="answer-buttons"></div>
    <div class="score" id="score">Puan: 0</div>
</div>

<script>
const questions = [
    // Kolay Sorular
    { level: "easy", label: "Kolay", q: "Web sayfalarının temel iskeletini oluşturmak için hangi dil kullanılır?", options: ["CSS", "HTML", "Python", "SQL"], answer: 1 },
    { level: "easy", label: "Kolay", q: "Aşağıdakilerden hangi veri tipi metinsel ifadeleri tutar?", options: ["Integer", "Boolean", "String", "Float"], answer: 2 },
    { level: "easy", label: "Kolay", q: "Bir döngüyü tamamen sonlandırmak için hangi anahtar kelime kullanılır?", options: ["continue", "exit", "stop", "break"], answer: 3 },
    
    // Orta Sorular
    { level: "medium", label: "Orta", q: "Nesne Yönelimli Programlamada (OOP) sınıf şablonundan türetilen yapılara ne denir?", options: ["Object (Nesne)", "Function (Fonksiyon)", "Variable (Değişken)", "Array (Dizi)"], answer: 0 },
    { level: "medium", label: "Orta", q: "İki durumu (True/False) kontrol eden mantıksal veri tipi hangisidir?", options: ["Char", "Boolean", "Double", "String"], answer: 1 },
    { level: "medium", label: "Orta", q: "Veritabanından veri çekmek için kullanılan temel SQL komutu hangisidir?", options: ["INSERT", "UPDATE", "SELECT", "DELETE"], answer: 2 },
    
    // Zor Sorular
    { level: "hard", label: "Zor", q: "Hangisi 'FIFO' (First In First Out - İlk Giren İlk Çıkar) prensibiyle çalışır?", options: ["Stack (Yığın)", "Queue (Kuyruk)", "Tree (Ağaç)", "Graph (Graf)"], answer: 1 },
    { level: "hard", label: "Zor", q: "OOP'de bir sınıfın başka bir sınıftan özellik mirası almasına ne ad verilir?", options: ["Polymorphism", "Encapsulation", "Inheritance", "Abstraction"], answer: 2 },
    { level: "hard", label: "Zor", q: "Zaman karmaşıklığı O(1) olan bir işlem ne anlama gelir?", options: ["Girdi boyutu artsa da işlem süresi sabittir", "Her adımda işlem süresi ikiye katlanır", "Girdi boyutuyla orantılı artar", "En yavaş algoritma türüdür"], answer: 0 }
];

let currentQ = 0;
let score = 0;

const questionEl = document.getElementById("question");
const badgeEl = document.getElementById("badge");
const buttonsEl = document.getElementById("answer-buttons");
const scoreEl = document.getElementById("score");

function loadQuestion() {
    buttonsEl.innerHTML = "";
    const q = questions[currentQ];
    
    questionEl.innerText = q.q;
    badgeEl.innerText = `${q.label} Seviye (${currentQ + 1}/${questions.length})`;
    badgeEl.className = `badge ${q.level}`;

    q.options.forEach((opt, index) => {
        const btn = document.createElement("button");
        btn.innerText = opt;
        btn.onclick = () => checkAnswer(index, q.answer);
        buttonsEl.appendChild(btn);
    });
}

function checkAnswer(selected, correct) {
    const btns = buttonsEl.getElementsByTagName("button");
    if (selected === correct) {
        btns[selected].classList.add("correct");
        score += 10;
    } else {
        btns[selected].classList.add("wrong");
        btns[correct].classList.add("correct");
    }

    scoreEl.innerText = `Puan: ${score}`;

    Array.from(btns).forEach(b => b.disabled = true);

    setTimeout(() => {
        currentQ++;
        if (currentQ < questions.length) {
            loadQuestion();
        } else {
            showResult();
        }
    }, 1500);
}

function showResult() {
    let resultMsg = score >= 60 ? "Tebrikler! Sorumluluk sınavını geçtin ve üniversite yolun açık! 🎓" : "Biraz daha çalışman gerekiyor, tekrar dene! 📚";
    document.getElementById("quiz").innerHTML = `
        <h2>Sınav Bitti!</h2>
        <p style="font-size: 20px; font-weight: bold;">Toplam Puan: ${score} / 90</p>
        <p>${resultMsg}</p>
        <button onclick="location.reload()" style="margin-top:15px; width:100%;">Tekrar Oyna</button>
    `;
}

loadQuestion();
</script>

</body>
</html>

## 👩‍💻 Geliştirici

Nisa

## 📌 Proje

Bu proje eğitim amacıyla hazırlanmıştır.