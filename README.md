html_content = """<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Sana Özel</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@600&family=Plus+Jakarta+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #faf7f5;
            --card-bg: #ffffff;
            --text-main: #2c2c2c;
            --text-muted: #666666;
            --accent-color: #d4a373;
            --accent-light: #f4ece1;
            --border-color: #eee4dc;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.04);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.7;
            overflow-x: hidden;
        }

        .section {
            min-height: 100vh;
            min-height: 100dvh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 40px 24px;
            position: relative;
        }

        .card {
            background: var(--card-bg);
            border-radius: 24px;
            padding: 36px 28px;
            width: 100%;
            max-width: 480px;
            box-shadow: var(--shadow);
            border: 1px solid var(--border-color);
            position: relative;
        }

        /* Section 1 Styling */
        .section-1 .intro-title {
            font-family: 'Caveat', cursive;
            font-size: 2.2rem;
            color: var(--accent-color);
            text-align: center;
            margin-bottom: 24px;
            line-height: 1.2;
        }

        .p-main {
            font-size: 1.05rem;
            color: var(--text-main);
            margin-bottom: 18px;
            font-weight: 400;
        }

        .p-highlight {
            font-size: 1.05rem;
            color: var(--text-main);
            margin-bottom: 18px;
            font-weight: 500;
        }

        .note-box {
            margin-top: 28px;
            padding: 20px;
            background-color: var(--accent-light);
            border-left: 4px solid var(--accent-color);
            border-radius: 12px;
            font-size: 0.95rem;
            color: #5a4a42;
            font-style: italic;
            line-height: 1.6;
        }

        /* Navigation Buttons */
        .btn-container {
            margin-top: 32px;
            display: flex;
            justify-content: center;
        }

        .next-btn {
            background-color: var(--accent-color);
            color: white;
            border: none;
            padding: 14px 28px;
            border-radius: 30px;
            font-size: 0.95rem;
            font-weight: 500;
            letter-spacing: 0.5px;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 4px 15px rgba(212, 163, 115, 0.3);
            transition: all 0.3s ease;
            text-decoration: none;
        }

        .next-btn:active {
            transform: scale(0.97);
        }

        .next-btn svg {
            width: 18px;
            height: 18px;
            fill: currentColor;
            transition: transform 0.3s ease;
        }

        .next-btn:hover svg {
            transform: translateY(3px);
        }

        /* Section Titles */
        .section-title {
            font-size: 1.5rem;
            font-weight: 600;
            color: var(--text-main);
            margin-bottom: 24px;
            position: relative;
            padding-bottom: 12px;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 40px;
            height: 3px;
            background-color: var(--accent-color);
            border-radius: 2px;
        }

        /* Interactive Collapsible / Accordion */
        .collapsible-container {
            margin-top: 24px;
        }

        .collapsible-trigger {
            width: 100%;
            background-color: var(--accent-light);
            color: var(--text-main);
            border: 1px solid var(--border-color);
            padding: 16px 20px;
            border-radius: 16px;
            font-size: 0.95rem;
            font-weight: 600;
            text-align: left;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.3s ease;
        }

        .collapsible-trigger .icon {
            width: 20px;
            height: 20px;
            transition: transform 0.3s ease;
        }

        .collapsible-trigger.active .icon {
            transform: rotate(180deg);
        }

        .collapsible-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s cubic-bezier(0, 1, 0, 1);
            background: #ffffff;
            border-radius: 0 0 16px 16px;
        }

        .collapsible-content.open {
            max-height: 500px;
            transition: max-height 0.4s ease-in-out;
            border: 1px solid var(--border-color);
            border-top: none;
            padding: 20px;
        }

        .collapsible-text {
            font-size: 0.95rem;
            color: var(--text-muted);
            line-height: 1.7;
        }

        /* Indicator Dots */
        .nav-dots {
            position: fixed;
            right: 16px;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            flex-direction: column;
            gap: 12px;
            z-index: 100;
        }

        .dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background-color: rgba(0,0,0,0.15);
            transition: all 0.3s ease;
        }

        .dot.active {
            background-color: var(--accent-color);
            transform: scale(1.4);
        }
    </style>
</head>
<body>

    <!-- Indicator Dots -->
    <div class="nav-dots">
        <div class="dot active" id="dot-1"></div>
        <div class="dot" id="dot-2"></div>
        <div class="dot" id="dot-3"></div>
    </div>

    <!-- Section 1 -->
    <section class="section section-1" id="sec-1">
        <div class="card">
            <h1 class="intro-title">Sana Söylemek İstediklerim</h1>
            
            <p class="p-main">Sana eskisi kadar ilgi göstermediğimi, seni yeterince önemsemediğimi düşündürdüm. Belki içimde olanı yeterince gösteremedim ama bunun sende bıraktığı his gerçekti. Bunun için gerçekten özür dilerim.</p>
            
            <p class="p-main">Seni çok özlüyorum. Ama bu özlemimi sana yükleyip seni bir karar vermeye zorlamak istemiyorum. Benden uzak kalmak ve biraz nefes almak istemene saygı duyuyorum.</p>
            
            <p class="p-main">Benim yapmak istediğim şey sadece “özür dilerim” deyip geçmek değil. Sana nasıl daha iyi gelebileceğimi, sevgimi ve ilgimi sana nasıl daha doğru gösterebileceğimi öğrenmak istiyorum. Bunu tek başıma kusursuz yapamayacağımı da biliyorum.</p>
            
            <p class="p-highlight">Sana nasıl daha iyi gelebileceğimi, nerede eksik kaldığımı ve sana sevgimi nasıl hissettirebileceğimi elimden tutup göstermeni istiyorum.</p>
            
            <p class="p-main">Senden hemen bir cevap, bir söz ya da bir karar beklemiyorum. Hazır olduğunda konuşuruz. Hazır değilsen, buna da saygı duyarım.</p>
            
            <p class="p-main">Çünkü sadece seni kaybetmekten korktuğum için değil, seni kırdığım için üzgünüm. Ve eğer bir gün yeniden konuşursak, aynı hataları tekrarlamak yerine bunu davranışlarımla göstermek istiyorum.</p>
            
            <div class="note-box">
                Bu site senden bir cevap almak için değil. Sadece sana söyleyemediğim birkaç şeyi sakin ve dürüst bir şekilde bırakmak için.
            </div>

            <div class="btn-container">
                <button class="next-btn" onclick="scrollToSection('sec-2')">
                    Devam Et
                    <svg viewBox="0 0 24 24"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6z"/></svg>
                </button>
            </div>
        </div>
    </section>

    <!-- Section 2 -->
    <section class="section" id="sec-2">
        <div class="card">
            <h2 class="section-title">Nerede hata yaptığımı biliyorum</h2>
            
            <p class="p-main">Mesele sadece ne söylediğim ya da ne yapmadığım değildi. Sana olan ilgimi yeterince göstermedim. Bazen seni önemsediğimi içimde bilmekle, bunu sana hissettirmek arasındaki farkı kaçırdım.</p>
            
            <p class="p-main">Sana “ben seni seviyorum” demek yetmedi; bunu günlük davranışlarımla da hissettirmen gerekiyordu. Ben bunu yeterince yapamadım. Bu yüzden kendini geri planda, yalnız veya önemsenmiyormuş gibi hissettirdiysem, bunun sorumluluğunu alıyorum.</p>
            
            <p class="p-main">Bundan sonra senden beklediğim şey kusursuz olmanı istemek değil. Benim de nerede eksik kaldığımı bana söylemene izin vermek. Çünkü seni anlamayı gerçekten öğrenmek istiyorum.</p>

            <div class="btn-container">
                <button class="next-btn" onclick="scrollToSection('sec-3')">
                    Devam Et
                    <svg viewBox="0 0 24 24"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6z"/></svg>
                </button>
            </div>
        </div>
    </section>

    <!-- Section 3 -->
    <section class="section" id="sec-3">
        <div class="card">
            <h2 class="section-title">Senden beklediğim tek şey</h2>
            
            <p class="p-highlight">Hiçbir şey yapmak zorunda değilsin.</p>
            
            <p class="p-main">Bu siteye cevap vermek, geri dönmek ya da bir karar vermek zorunda değilsin. İstersen sadece oku ve kapat.</p>
            
            <p class="p-main">Hazır olduğunda konuşuruz. Hazır değilsen, seni sıkıştırmadan beklemek yerine kararına và alanına saygı duymayı seçerim.</p>

            <!-- Tıklanarak açılan interaktif metin -->
            <div class="collapsible-container">
                <button class="collapsible-trigger" id="col-btn" onclick="toggleCollapsible()">
                    <span>Bir şey daha var...</span>
                    <svg class="icon" viewBox="0 0 24 24"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6z"/></svg>
                </button>
                <div class="collapsible-content" id="col-content">
                    <p class="collapsible-text">
                        Sana nasıl daha iyi gelebileceğimi, seni nasıl daha doğru anlayabileceğimi ve sevgimi sana nasıl daha iyi hissettirebileceğimi öğrenmek istiyorum. Elimden tutup bana göstermen gereken yerler varsa, bunu dinlemek istiyorum.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <script>
        function scrollToSection(id) {
            document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
        }

        function toggleCollapsible() {
            const trigger = document.getElementById('col-btn');
            const content = document.getElementById('col-content');
            
            trigger.classList.toggle('active');
            content.classList.toggle('open');
        }

        // Active Dot Observer
        const sections = document.querySelectorAll('.section');
        const dots = {
            'sec-1': document.getElementById('dot-1'),
            'sec-2': document.getElementById('dot-2'),
            'sec-3': document.getElementById('dot-3')
        };

        const observerOptions = {
            root: null,
            rootMargin: '0px',
            threshold: 0.6
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    Object.values(dots).forEach(d => d.classList.remove('active'));
                    if (dots[entry.target.id]) {
                        dots[entry.target.id].classList.add('active');
                    }
                }
            });
        }, observerOptions);

        sections.forEach(sec => observer.observe(sec));
    </script>
</body>
</html>
"""

with open("index.html", "w", encoding="utf-8") as f:
    f.write(html_content)

print("HTML file created successfully.")
