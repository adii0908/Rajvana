<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Rajvana -- Journey Through Heritage & Spirituality</title>
<style>
  :root{
    --saffron:#cc6600;
    --cream:#fff9f0;
    --dark-bg:#1e1e1e;
    --dark-text:#eaeaea;
  }
  *{box-sizing:border-box}
  body{
    margin:0;
    font-family: "Segoe UI", Arial, sans-serif;
    background:var(--cream);
    color:#111;
    scroll-behavior:smooth;
    transition: background .25s, color .25s;
  }
  header{
    position:fixed; left:0; right:0; top:0;
    height:70px; background:var(--saffron);
    display:flex; align-items:center; gap:20px;
    padding:8px 18px; z-index:1200;
    box-shadow:0 4px 14px rgba(0,0,0,0.15);
  }
  #logo{
    height:54px; width:54px; border-radius:8px; cursor:pointer;
    object-fit:cover;
  }
  header nav{ display:flex; gap:12px; align-items:center; margin-left:6px;}
  header nav a{ color:#000; font-weight:700; text-decoration:none; }
  header .controls{ margin-left:auto; display:flex; gap:10px; align-items:center;}
  select, button{ padding:6px 8px; border-radius:6px; border:1px solid rgba(0,0,0,0.12); background:#fff; cursor:pointer; }
  button:hover{ opacity:.95; }

  main{ max-width:1100px; margin:90px auto 60px; padding:0 18px; }

  .hero{
    height:64vh; border-radius:10px; overflow:hidden;
    background-image:url('https://upload.wikimedia.org/wikipedia/commons/0/0f/Varanasi_Ghat.jpg');
    background-size:cover; background-position:center;
    display:flex; align-items:center; justify-content:center; text-align:center;
    color:#fff; box-shadow: inset 0 0 0 1000px rgba(0,0,0,0.25);
  }
  .hero h1{ margin:0; font-family:Georgia,serif; font-size:2.1rem; text-shadow:0 2px 6px rgba(0,0,0,0.4);}
  .hero p{ margin-top:10px; font-weight:600; }

  /* Floating right-side place quick menu */
  .places-menu{
    position:fixed; right:12px; top:90px; z-index:1100;
    display:flex; flex-direction:column; gap:10px;
  }
  .place-btn{
    width:72px; height:72px; border-radius:50%; overflow:hidden; border:4px solid var(--saffron);
    background:#fff; cursor:pointer; box-shadow:0 6px 12px rgba(0,0,0,0.14); display:block;
  }
  .place-btn img{ width:100%; height:100%; object-fit:cover; display:block; }

  section.place{
    margin-top:32px; padding:26px; background:#fff; border-radius:10px;
    box-shadow:0 6px 18px rgba(0,0,0,0.06); margin-bottom:28px;
  }
  section.place h2{ margin-top:0; color:#000; }
  .place-grid{ display:flex; gap:22px; flex-wrap:wrap; align-items:flex-start; }
  .place-grid img{ width:420px; max-width:100%; border-radius:10px; }
  .place-text{ flex:1; min-width:300px; }
  .price-box{ margin-top:14px; background:rgba(255,160,80,0.12); padding:10px; border-radius:8px; font-weight:700; color:#000; display:inline-block; }

  /* small screens */
  @media (max-width:900px){
    header{ padding:8px 12px; }
    .place-grid{ flex-direction:column; }
    .places-menu{ right:8px; top:120px; }
  }

  /* dark mode */
  body.dark{
    background:var(--dark-bg); color:var(--dark-text);
  }
  body.dark .hero{ box-shadow: inset 0 0 0 1000px rgba(0,0,0,0.5); }
  body.dark section.place{ background:#242424; box-shadow: none; }
  body.dark .price-box{ background: rgba(204,102,0,0.12); color:var(--dark-text); }

  footer{ text-align:center; padding:20px; margin-top:18px; background:var(--saffron); color:#000; font-weight:700; border-top:4px solid rgba(0,0,0,0.06); }

  /* small niceties */
  .back-top{ margin-top:14px; padding:8px 12px; border-radius:6px; background:var(--saffron); border:none; cursor:pointer; color:#000; font-weight:700; }
</style>
</head>
<body>

<header>
  <!-- Logo (fixed top-left). Clicking returns to top/home -->
  <img id="logo" src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/fd/Lotus_flower_icon.svg/512px-Lotus_flower_icon.svg.png" alt=Rajvana  Logo" onclick="window.scrollTo({top:0,behavior:'smooth'})">
  <nav>
    <a href="#home" onclick="scrollToId('home')">Home</a>
    <a href="#about" onclick="scrollToId('about')">About</a>
    <a href="#contact" onclick="scrollToId('contact')">Contact</a>
  </nav>

  <div class="controls" style="margin-left:auto; display:flex; gap:8px; align-items:center;">
    <select id="lang" onchange="setLanguage(this.value)" title="Choose language">
      <option value="en">English</option>
      <option value="hi">हिन्दी</option>
      <option value="ta">தமிழ்</option>
    </select>
    <button id="themeBtn" onclick="toggleTheme()" title="Toggle dark / light">🌓</button>
  </div>
</header>

<main id="main">
  <section class="hero" id="home">
    <div>
      <h1>Rajvana -- Journey Through Heritage & Spirituality</h1>
      <p>Explore the sacred, historical and cultural heart of Uttar Pradesh with guided tours and curated experiences.</p>
    </div>
  </section>

  <!-- Floating image buttons for quick navigation -->
  <div class="places-menu" aria-hidden="false">
    <a class="place-btn" title="Varanasi" onclick="scrollToId('varanasi')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/3/37/Ganga_Aarti_at_Dashashwamedh_Ghat.jpg" alt="Varanasi">
    </a>
    <a class="place-btn" title="Ayodhya" onclick="scrollToId('ayodhya')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/4/49/Ram_Janmabhoomi_Mandir_Ayodhya.jpg" alt="Ayodhya">
    </a>
    <a class="place-btn" title="Sarnath" onclick="scrollToId('sarnath')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/2/28/Dhamekh_Stupa.jpg" alt="Sarnath">
    </a>
    <a class="place-btn" title="Bodh Gaya" onclick="scrollToId('bodhgaya')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/0/02/Mahabodhi_Temple_1.jpg" alt="Bodh Gaya">
    </a>
    <a class="place-btn" title="Agra" onclick="scrollToId('agra')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/d/da/Taj-Mahal.jpg" alt="Agra">
    </a>
    <a class="place-btn" title="Mathura" onclick="scrollToId('mathura')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/9/9d/Mathura_Temple_%282%29.jpg" alt="Mathura">
    </a>
    <a class="place-btn" title="Vrindavan" onclick="scrollToId('vrindavan')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/8/8e/Govinddev_temple_-_Vrindavan.jpg" alt="Vrindavan">
    </a>
    <a class="place-btn" title="Prayagraj" onclick="scrollToId('prayagraj')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/8/85/Prayagraj_Ganga.jpg" alt="Prayagraj">
    </a>
    <a class="place-btn" title="Lucknow" onclick="scrollToId('lucknow')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/5/5c/RumiDarwaza_Lucknow_2013.jpg" alt="Lucknow">
    </a>
    <a class="place-btn" title="Chitrakoot" onclick="scrollToId('chitrakoot')">
      <img src="https://upload.wikimedia.org/wikipedia/commons/6/6a/Chitrakoot_River.jpg" alt="Chitrakoot">
    </a>
  </div>

  <!-- 1. Varanasi -->
  <section id="varanasi" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/5/5a/Varanasi_City.jpg" alt="Varanasi">
      <div class="place-text">
        <h2>Varanasi</h2>
        <p data-lang="en">
          Varanasi (Kashi) is one of the world's oldest continuously inhabited cities and the spiritual heart of India. Its famous ghats line the sacred Ganges where pilgrims come to bathe, perform last rites, and partake in daily rituals. The city pulses with devotional music, temple bells, sari weavers, and street food that has been perfected over generations. Don't miss the magical Ganga Aarti at dusk -- a spectacle of lamps, chants, and incense. Historical alleys lead to small temples and workshops where age-old traditions continue, making Varanasi an immersive cultural and spiritual experience.
        </p>
        <p data-lang="hi" style="display:none;">
          वाराणसी (काशी) दुनिया के सबसे पुराने लगातार बसे हुए शहरों में से एक है और भारत का आध्यात्मिक केंद्र माना जाता है। इसकी प्रसिद्ध घाट पवित्र गंगा के किनारे हैं जहां श्रद्धालु स्नान करने, अंत्य संस्कार करने और दैनिक अनुष्ठानों में भाग लेने आते हैं। शहर भक्ति संगीत, मंदिरों की घंटियों, साड़ी बुनाई करने वालों और पीढ़ियों से परिपक्व स्ट्रीट फूड से परिपूर्ण है। शाम की गंगा आरती दीपों, मंत्रों और धूप-दीप की एक अनूठी झलक प्रस्तुत करती है। ऐतिहासिक गलियाँ छोटे मंदिरों और पारंपरिक कार्यशालाओं तक जाती हैं, जो वाराणसी को एक जीवंत सांस्कृतिक और आध्यात्मिक अनुभव बनाती हैं।
        </p>
        <p data-lang="ta" style="display:none;">
          வரணாசி (காஷி) உலகின் பழமைமிக்க நகரங்களில் ஒன்றாகும் மற்றும் இந்தியாவின் ஆன்மிக மையமாகும். புனித கண்கேஸ் ஆற்றின் கரையில் உள்ள புகழ்பெற்ற "காட்ஸ்" மத பரம்பரை நிகழ்ச்சிகளுக்கு அறியப்படுகின்றன. மாலை நேரத்தில் நடைபெறும் கங்கா ஆர்த்தி மிகவும் பிரம்மாண்டமான அனுபவமாகும்.
        </p>
        <div class="price-box">Price (basic): Adults ₹1,500 • Children ₹800 • Foreigners ₹3,000</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 2. Ayodhya -->
  <section id="ayodhya" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/a/ab/Ayodhya_river.jpg" alt="Ayodhya">
      <div class="place-text">
        <h2>Ayodhya</h2>
        <p data-lang="en">
          Ayodhya is the ancient city associated with the epic Ramayana and believed to be the birthplace of Lord Rama. The city's spiritual aura draws pilgrims who visit temples, ghats and sacred sites like Ram Janmabhoomi, Hanuman Garhi and Kanak Bhawan. Recent restoration and development have improved pilgrim facilities while preserving religious traditions and festivals that enliven the city year-round. Walking through Ayodhya allows visitors to connect with mythic stories, temple architecture, and the devotional rhythms of daily life. A focused pilgrimage or a cultural exploration both reveal deep layers of heritage here.
        </p>
        <p data-lang="hi" style="display:none;">
          अयोध्या रामायण से जुड़ा एक प्राचीन शहर है और इसे भगवान राम का जन्मस्थान माना जाता है। शहर की आध्यात्मिक अनुभूति श्रद्धालुओं को आकर्षित करती है, जो राम जन्मभूमि, हनुमान गढ़ी और कनक भवन जैसे पवित्र स्थानों का दर्शन करते हैं। हाल के विकास और पुनरुद्धार कार्यों ने तीर्थयात्रियों की सुविधाओं को बेहतर किया है जबकि धार्मिक परंपराओं और त्योहारों को संरक्षित किया गया है। अयोध्या में चलकर आप पौराणिक कथाओं, मंदिर वास्तुकला और दैनिक भक्ति जीवन की ताल से जुड़ते हैं। यह स्थान आध्यात्मिक और सांस्कृतिक दोनों ही दृष्टियों से समृद्ध है।
        </p>
        <p data-lang="ta" style="display:none;">
          அதிகம் பழமையான நகரமான ஆயோதோ இராமாயண சம்பந்தப்பட்ட இடமாகவும், ராமனின் பிறப்பு இல்லமாகவும் கருதப்படுகிறது. கோயில்கள் மற்றும் புனித தாளங்கள் பக்தர்களை ஈர்க்கின்றன.
        </p>
        <div class="price-box">Price (basic): Adults ₹1,200 • Children ₹700 • Foreigners ₹2,500</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 3. Sarnath -->
  <section id="sarnath" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/2/28/Dhamekh_Stupa.jpg" alt="Sarnath">
      <div class="place-text">
        <h2>Sarnath</h2>
        <p data-lang="en">
          Sarnath is where Lord Buddha gave his first sermon after attaining enlightenment, making it one of the most important Buddhist pilgrimage sites. Located a short drive from Varanasi, Sarnath's serene Deer Park, Dhamekh Stupa, and the Archaeological Museum showcase ancient relics, sculptures and inscriptions from the Mauryan and Gupta periods. Monasteries from different Buddhist traditions create an international atmosphere, with monks and pilgrims meditating under shady trees. It is ideal for a reflective half-day visit to appreciate history, art, and the peaceful spiritual legacy of Buddhism.
        </p>
        <p data-lang="hi" style="display:none;">
          सारनाथ वह स्थान है जहाँ भगवान बुद्ध ने निर्वाण प्राप्ति के बाद अपनी पहली उपदेश दी थी, और यह बौद्ध तीर्थस्थलों में सबसे महत्वपूर्ण स्थानों में से एक है। वाराणसी से थोड़ी दूरी पर स्थित सारनाथ का शांत हिरण उद्यान, धमेख स्तूप और पुरातत्व संग्रहालय मौर्य और गुप्त काल की प्राचीन मूर्तियाँ और शिलालेख दिखाते हैं। विभिन्न बौद्ध परंपराओं के मठ अंतरराष्ट्रीय माहौल बनाते हैं जहाँ भिक्षु और श्रद्धालु पेड़ों की छाया में ध्यान करते हैं। इतिहास, कला और बौद्ध धर्म की शांत विरासत को समझने के लिए यह आधे दिन की यात्रा के लिए उपयुक्त है।
        </p>
        <p data-lang="ta" style="display:none;">
          சார்நாத் புத்தர் தனது முதற்பேச்சை வழங்கிய இடமாகப் பிரபலமானது. மயூரா மற்றும் குப்த காலங்களில் இருந்து மீதிகளைக் காணலாம். அமைதியான மற்றும் சிந்தனை ஊட்டமான இடமாகும்.
        </p>
        <div class="price-box">Price (basic): Adults ₹900 • Children ₹500 • Foreigners ₹1,800</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 4. Bodh Gaya -->
  <section id="bodhgaya" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/0/02/Mahabodhi_Temple_1.jpg" alt="Bodh Gaya">
      <div class="place-text">
        <h2>Bodh Gaya</h2>
        <p data-lang="en">
          Bodh Gaya is the sacred site where Siddhartha Gautama attained enlightenment and became the Buddha. The towering Mahabodhi Temple and the ancient Bodhi Tree draw pilgrims from around the world. The temple complex and nearby monasteries reflect diverse Buddhist architectural styles and rituals, creating a deeply peaceful and international pilgrimage atmosphere. Visitors often spend time in meditation, walking the temple grounds, and learning about Buddhist history in nearby museums. Bodh Gaya is best visited as a short overnight or two-day trip from Varanasi with time for reflection and cultural immersion.
        </p>
        <p data-lang="hi" style="display:none;">
          बोध गया वह पवित्र स्थल है जहां सिद्धार्थ गौतम ने ज्ञान प्राप्त किया और उन्होंने बुद्धत्व प्राप्त किया। विशाल महाबोधि मंदिर और प्राचीन बोधी वृक्ष दुनिया भर के तीर्थयात्रियों को आकर्षित करते हैं। मंदिर परिसर और आसपास के मठ विभिन्न बौद्ध वास्तुशिल्प शैलियों और रीतियों को दर्शाते हैं, जिससे एक शांत और अंतरराष्ट्रीय वातावरण बनता है। यात्री अक्सर ध्यान करते हैं, मंदिर परिसर में टहलते हैं और नज़दीकी संग्रहालयों में बौद्ध इतिहास के बारे में सीखते हैं। बोध गया वाराणसी से एक रात के ठहराव या दो दिनों की यात्रा के रूप में आदर्श है।
        </p>
        <p data-lang="ta" style="display:none;">
          போத் கயா புத்தரானிடம் உண்மை அறிவை அடைந்த இடமாகும். மகாபோதீ கோயிலும், பழமையான போதீ மரமும் உலகம் முழுவதிருந்து பக்தர்களை கொண்டுவருகின்றன.
        </p>
        <div class="price-box">Price (basic): Adults ₹4,000 • Children ₹2,000 • Foreigners ₹8,000 (includes 1-night package)</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 5. Agra -->
  <section id="agra" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/d/da/Taj-Mahal.jpg" alt="Agra - Taj Mahal">
      <div class="place-text">
        <h2>Agra</h2>
        <p data-lang="en">
          Agra is world-famous for the Taj Mahal, the white marble mausoleum built by Emperor Shah Jahan in memory of Mumtaz Mahal. Beyond the Taj, Agra Fort, Fatehpur Sikri (nearby), and Mughal-era architecture reveal the region's royal history. Agra offers photographic sunrise and sunset experiences, bustling markets for marble inlay and handicrafts, and flavorful Mughlai cuisine. A day trip from major nearby cities is common, but staying overnight gives time to explore the fort, bazaars, and lesser-known historic sites at a relaxed pace.
        </p>
        <p data-lang="hi" style="display:none;">
          आगरा विश्वप्रसिद्ध ताज महल के लिए जाना जाता है, जो सम्राट शाहजहां ने मुमताज़ महल की याद में बनवाया था। ताज के अलावा आगरा किला, फतेहपुर सीकरी (नज़दीक) और मुगल कालीन वास्तुकला क्षेत्र के शाही इतिहास को दर्शाते हैं। आगरा में सूर्योदय और सूर्यास्त के शानदार दृश्य मिलते हैं, साथ ही संगमरमर की कारीगरी और हस्तशिल्प के बाजार हैं, और मुगलई व्यंजनों का आनंद लिया जा सकता है। एक दिन की यात्रा आम है, पर रात ठहरने से आप आराम से सभी स्थलों का आनंद ले सकते हैं।
        </p>
        <p data-lang="ta" style="display:none;">
          ஆக்ரா உலகப் புகழ் பெற்ற தாஜ்மஹலுக்காக பிரபலமானது. மேகலா காலத்து மஹால்களும் கோட்டைகளும் இங்கு காணப்படுகின்றன. புகைப்பட ரசிகர்களுக்கு சிறந்த இடமாகும்.
        </p>
        <div class="price-box">Price (basic): Adults ₹1,800 • Children ₹900 • Foreigners ₹4,000</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 6. Mathura -->
  <section id="mathura" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/9/9d/Mathura_Temple_%282%29.jpg" alt="Mathura">
      <div class="place-text">
        <h2>Mathura</h2>
        <p data-lang="en">
          Mathura is celebrated as the birthplace of Lord Krishna and is dotted with temples, ghats, and festivals dedicated to Krishna's life. The town's lively religious calendar -- with Holi, Janmashtami and other festivals -- brings color, music and devotion to its streets. Pilgrims and culture seekers visit sites such as Krishna Janmabhoomi and nearby Brij region spots. Mathura's markets offer traditional sweets, religious items and crafts. A short trip from Agra or Delhi, Mathura provides a deep dive into devotional traditions of northern India and Vrindavan's associated spiritual atmosphere.
        </p>
        <p data-lang="hi" style="display:none;">
          मथुरा को भगवान कृष्ण का जन्मस्थान माना जाता है और यह मंदिरों, घाटों और कृष्ण से जुड़ी त्योहारों से भरा हुआ है। होली, जन्माष्टमी और अन्य उत्सव यहां की गलियों में रंग, संगीत और भक्ति लाते हैं। कृष्ण जन्मभूमि और ब्रज क्षेत्र के नज़दीकी स्थलों के दर्शन के लिए श्रद्धालु आते हैं। मथुरा के बाजार पारंपरिक मिठाइयाँ, धार्मिक सामान और हस्तशिल्प बेचते हैं। आगरा या दिल्ली से छोटी यात्रा पर आने पर मथुरा उत्तर भारत की भक्ति परंपराओं में गहरे अवलोकन का अवसर देती है।
        </p>
        <p data-lang="ta" style="display:none;">
          மாதுரா திரு கிருஷ்ணரின் பிறப்பிடம் எனக் கருதப்படுகிறது. கோயில்கள் மற்றும் திருவிழாக்கள் இங்கு மிக முக்கியம்.
        </p>
        <div class="price-box">Price (basic): Adults ₹900 • Children ₹500 • Foreigners ₹1,800</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 7. Vrindavan -->
  <section id="vrindavan" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/8/8e/Govinddev_temple_-_Vrindavan.jpg" alt="Vrindavan">
      <div class="place-text">
        <h2>Vrindavan</h2>
        <p data-lang="en">
          Vrindavan, close to Mathura, is famed for temples dedicated to Lord Krishna and a rich tradition of bhakti (devotion). The town's serene ashrams and colorful temples such as Banke Bihari and ISKCON attract devotees year-round. Pilgrims perform kirtan (devotional singing), participate in communal feasts and experience the spiritual stories associated with Krishna's childhood. Vrindavan's narrow lanes and fragrant flower markets create an intimate devotional atmosphere perfect for contemplative visitors and those seeking to witness devotional music, dance, and daily rituals.
        </p>
        <p data-lang="hi" style="display:none;">
          वृंदावन, मथुरा के नज़दीक, भगवान कृष्ण को समर्पित मंदिरों और भक्ति परंपरा के लिए प्रसिद्ध है। बैंके बिहारी और इस्कॉन जैसे रंगीन मंदिर साल भर भक्तों को आकर्षित करते हैं। श्रद्धालु कीर्तन करते हैं, सामूहिक भोग में भाग लेते हैं और कृष्ण के बाल्यकाल से जुड़ी कथाओं का अनुभव करते हैं। वृंदावन की संकरी गलियाँ और फूलों के बाजार एक अंतरंग भक्ति वातावरण बनाते हैं जो चिंतनशील यात्रियों के लिए आदर्श है।
        </p>
        <p data-lang="ta" style="display:none;">
          விரிந்தாவன் கிருஷ்ணர் வழிபாட்டிற்காக பிரபலமான இடமாகும். சங்கீதம் மற்றும் பக்தி நிகழ்வுகள் அதிகமாக நடைபெறுகின்றன.
        </p>
        <div class="price-box">Price (basic): Adults ₹900 • Children ₹500 • Foreigners ₹1,800</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 8. Prayagraj (Allahabad) -->
  <section id="prayagraj" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/8/85/Prayagraj_Ganga.jpg" alt="Prayagraj">
      <div class="place-text">
        <h2>Prayagraj (Allahabad)</h2>
        <p data-lang="en">
          Prayagraj, historically called Allahabad, sits at the Sangam -- the confluence of the Ganges, Yamuna and mythical Sarasvati rivers -- and is one of India's most important Hindu pilgrimage sites. The city hosts the Kumbh Mela periodically, attracting millions of pilgrims, and is dotted with historic monuments, colonial architecture, and spiritual ashrams. Visitors can explore Triveni Sangam, Anand Bhavan (Nehru family home), and local markets. Prayagraj offers a powerful mix of ritual, history, and river-based cultural life.
        </p>
        <p data-lang="hi" style="display:none;">
          प्रयागराज (इलाहाबाद) त्रिवेणी संगम -- गंगा, यमुना और पवित्र सरस्वती (कथित) के मिलन बिंदु -- पर स्थित है और यह हिंदुओं के लिए अत्यंत महत्वपूर्ण तीर्थस्थल है। कुम्भ मेला यहाँ आयोजित होता है और लाखों तीर्थयात्री आते हैं। शहर में ऐतिहासिक स्मारक, औपनिवेशिक वास्तुकला और आध्यात्मिक आश्रम हैं। यात्री त्रिवेणी संगम, आनंद भवन और बाजारों का भ्रमण कर सकते हैं। प्रयागराज धार्मिक, ऐतिहासिक और नदियों से जुड़े सांस्कृतिक जीवन का मिश्रण प्रस्तुत करता है।
        </p>
        <p data-lang="ta" style="display:none;">
          பிரயாகிராஜ் (அல்லாஹாபாத்) மூன்று ஆற்களின் சங்கமமாகும். கும்ப்மேளா போன்ற மிகப்பெரிய திருவிழாக்களுக்கு இடம்.
        </p>
        <div class="price-box">Price (basic): Adults ₹1,200 • Children ₹700 • Foreigners ₹2,500</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 9. Lucknow -->
  <section id="lucknow" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/5/5c/RumiDarwaza_Lucknow_2013.jpg" alt="Lucknow">
      <div class="place-text">
        <h2>Lucknow</h2>
        <p data-lang="en">
          Lucknow, the capital of Uttar Pradesh, is renowned for its nawabi culture, elegant Awadhi cuisine, and historical monuments such as the Bara Imambara and Rumi Darwaza. The city blends refined etiquette, music, poetry and culinary heritage, offering rich experiences like kebab tastings, chikan embroidery shopping, and strolls through old bazaars. Lucknow is an appealing destination for travelers who enjoy history, food culture and leisurely exploration of urban heritage with a graceful cultural rhythm.
        </p>
        <p data-lang="hi" style="display:none;">
          लखनऊ, उत्तर प्रदेश की राजधानी, नवाबी संस्कृति, शानदार अवधी व्यंजन और बारा इमामबाड़ा तथा रूमी दरवाज़ा जैसे ऐतिहासिक स्मारकों के लिए प्रसिद्ध है। शहर सभ्य शिष्टाचार, संगीत, कविता और पाकसंस्कृति का समन्वय प्रस्तुत करता है। यहाँ कबाब का स्वाद लेना, चिकन कढ़ाई की खरीदारी और पुराने बाज़ारों में टहलना बहुत पसंद किया जाता है। लखनऊ उन यात्रियों के लिए आकर्षक है जो इतिहास, भोजन और शहरी विरासत का सुखद अन्वेषण चाहते हैं।
        </p>
        <p data-lang="ta" style="display:none;">
          லக்னோ தனது பாரம்பரிய நவாப் கலாச்சாரம் மற்றும் பாரம்பரிய உணவுகள் மூலம் பிரசித்தி பெற்றது. பழைய மார்க்கெட்டுகள் மற்றும் வரலாற்று இடங்கள் சுவாரஸ்யமானவை.
        </p>
        <div class="price-box">Price (basic): Adults ₹1,300 • Children ₹700 • Foreigners ₹2,800</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- 10. Chitrakoot -->
  <section id="chitrakoot" class="place">
    <div class="place-grid">
      <img src="https://upload.wikimedia.org/wikipedia/commons/6/6a/Chitrakoot_River.jpg" alt="Chitrakoot">
      <div class="place-text">
        <h2>Chitrakoot</h2>
        <p data-lang="en">
          Chitrakoot is celebrated in Indian epics as a place of meditation where Lord Rama spent time during exile. The area is filled with scenic ghats, waterfalls, temples, and quiet forests that invite reflection and pilgrimage. Devotees visit places like Ramghat, Bharat Milap, and Kamadgiri Hill to walk sacred paths and engage in devotional practices. Chitrakoot's blend of natural beauty and mythic heritage makes it a peaceful destination for spiritual seekers and nature lovers seeking a quieter retreat from city life.
        </p>
        <p data-lang="hi" style="display:none;">
          चित्रकूट भारतीय महाकाव्यों में उस स्थान के रूप में प्रसिद्ध है जहाँ राम ने वनवास के दौरान समय बिताया था। यहाँ सुंदर घाट, जलप्रपात, मंदिर और शांत वन हैं जो चिंतन और तीर्थयात्रा के लिए उपयुक्त हैं। भक्त रामघाट, भरत मिलाप और कामदगिरि पर्वत जैसे स्थलों पर आते हैं और पवित्र मार्गों पर चलता अनुभव करते हैं। चित्रकूट की प्राकृतिक सुंदरता और पौराणिक विरासत इसे आध्यात्मिक खोजकर्ताओं और प्रकृति-प्रेमियों के लिए एक शांत स्थान बनाती है।
        </p>
        <p data-lang="ta" style="display:none;">
          சித்ரகூட் திருமண களஞ்சியங்களிலும் ராமாயண தொடர்புகளிலும் குறிப்பிடத்தக்க இடமாகும். இயற்கை அழகு மற்றும் ஆன்மீகத் தலங்கள் இங்கு காணப்படுகின்றன.
        </p>
        <div class="price-box">Price (basic): Adults ₹1,000 • Children ₹600 • Foreigners ₹2,000</div>
        <br><button class="back-top" onclick="scrollToId('home')">Back to Top</button>
      </div>
    </div>
  </section>

  <!-- About -->
  <section id="about" class="place" style="background:transparent; box-shadow:none; border-bottom:none;">
    <h2>About Us</h2>
    <div>
      <p data-lang="en">
        I am <strong>Rajnish Mishra</strong>. I have 5 years of experience organizing and guiding tours across Uttar Pradesh. My approach combines authentic local knowledge, comfortable logistics, and an emphasis on cultural respect. Whether you seek spiritual pilgrimage, cultural discovery, or a relaxing picnic with beautiful scenery, I craft trips to match your interests. Connect on Instagram: <strong>@_uk_adii_0908</strong> for updates, sample itineraries, and direct booking inquiries.
      </p>
      <p data-lang="hi" style="display:none;">
        मैं <strong>रजनीश मिश्रा</strong> हूँ। मुझे उत्तर प्रदेश में यात्राओं के आयोजन और मार्गदर्शन का 5 वर्षों का अनुभव है। मेरा तरीका स्थानीय ज्ञान, सुविधाजनक व्यवस्था और सांस्कृतिक सम्मान को जोड़कर यात्रियों के लिए सुविधाजनक और अर्थपूर्ण पर्यटन प्रदान करना है। चाहे आप आध्यात्मिक तीर्थयात्रा चाहते हों, सांस्कृतिक अन्वेषण या खूबसूरत स्थानों पर पिकनिक -- मैं आपकी रुचि के अनुसार यात्रा तैयार करता हूँ। इंस्टाग्राम पर जुड़ें: <strong>@_uk_adii_0908</strong>।
      </p>
      <p data-lang="ta" style="display:none;">
        நான் <strong>ரஜநீஷ் மிஷ்ரா</strong>. நான் உத்தர் பிரதேசில் பயணம் மற்றும் வழிகாட்டுவதில் 5 ஆண்டுகளுக்கு மேற்பட்ட அனுபவம் பெற்றுள்ளேன். எனது பணிப்புரு உள்ளூரியல் அறிவு மற்றும் பயண வசதிகளை கொண்டு வருகிறது.
      </p>
    </div>
  </section>

  <!-- Contact -->
  <section id="contact" class="place" style="border-bottom:none;">
    <h2>Contact</h2>
    <form onsubmit="event.preventDefault(); alert('Thank you! Your message has been received. (This is a demo form.)')">
      <input required placeholder="Your name" style="width:100%; padding:10px; border-radius:6px; border:1px solid #ccc;"><br><br>
      <input required type="email" placeholder="Your email" style="width:100%; padding:10px; border-radius:6px; border:1px solid #ccc;"><br><br>
      <textarea placeholder="Your message" style="width:100%; padding:10px; border-radius:6px; border:1px solid #ccc;" rows="5"></textarea><br><br>
      <button style="padding:10px 16px; background:var(--saffron); border:none; border-radius:6px; font-weight:700; cursor:pointer;">Send Message</button>
    </form>
  </section>
</main>

<footer>
  © 2025 Gokashi -- Rajnish Mishra • Instagram: @_uk_adii_0908
</footer>

<script>
  // Smooth scroll helper
  function scrollToId(id){
    const el = document.getElementById(id);
    if(!el) return;
    el.scrollIntoView({behavior:'smooth', block:'start'});
  }

  // Language switching: show elements with matching data-lang
  function setLanguage(lang){
    const elems = document.querySelectorAll('[data-lang]');
    elems.forEach(el => {
      el.style.display = (el.getAttribute('data-lang') === lang) ? 'block' : 'none';
    });
    // For Tamil: if translations incomplete, fall back to English where needed
    if(lang === 'ta'){
      // if Tamil block not present for some paragraphs, show English as fallback
      document.querySelectorAll('[data-lang="en"]').forEach(en => {
        // if sibling Tamil exists for same content? we rely on explicit blocks above.
      });
    }
    // save preference (session)
    sessionStorage.setItem('gokashi-lang', lang);
  }

  // Theme toggle
  function toggleTheme(){
    document.body.classList.toggle('dark');
    sessionStorage.setItem('gokashi-theme', document.body.classList.contains('dark') ? 'dark' : 'light');
  }

  // Init language & theme from session if available
  (function(){
    const lang = sessionStorage.getItem('gokashi-lang') || 'en';
    document.getElementById('lang').value = lang;
    setLanguage(lang);

    const theme = sessionStorage.getItem('gokashi-theme');
    if(theme === 'dark'){
      document.body.classList.add('dark');
    }
  })();
</script>
</body>
</html>
