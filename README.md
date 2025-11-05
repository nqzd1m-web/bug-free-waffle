<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اختبار كيمياء تفاعلي - الوحدة الثانية</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #8A2BE2, #4B0082);
            color: white;
            min-height: 100vh;
            padding: 20px;
            line-height: 1.6;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        h1, h2, h3 {
            text-align: center;
            margin-bottom: 20px;
            color: #FFD700;
        }
        
        .intro {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }
        
        input, select {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 8px;
            background-color: rgba(255, 255, 255, 0.9);
            font-size: 16px;
        }
        
        button {
            background-color: #FFD700;
            color: #4B0082;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
            display: block;
            margin: 20px auto;
        }
        
        button:hover {
            background-color: #FFC400;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .question-container {
            display: none;
        }
        
        .question {
            background-color: rgba(255, 255, 255, 0.15);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
        }
        
        .options {
            display: grid;
            grid-template-columns: 1fr;
            gap: 10px;
            margin-top: 15px;
        }
        
        .option {
            background-color: rgba(255, 255, 255, 0.2);
            padding: 15px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s ease;
        }
        
        .option:hover {
            background-color: rgba(255, 255, 255, 0.3);
        }
        
        .option.selected {
            background-color: rgba(255, 215, 0, 0.3);
            border: 2px solid #FFD700;
        }
        
        .navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        .result-container, .answers-container {
            display: none;
            text-align: center;
        }
        
        .result {
            font-size: 24px;
            margin: 20px 0;
            color: #FFD700;
        }
        
        .team {
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.3);
        }
        
        .team h3 {
            color: #FFD700;
            margin-bottom: 15px;
        }
        
        .team ul {
            list-style-type: none;
            text-align: right;
        }
        
        .team li {
            margin-bottom: 8px;
            padding-right: 10px;
        }
        
        .error-message {
            color: #FF6B6B;
            text-align: center;
            margin-top: 10px;
            display: none;
        }
        
        .teacher-room {
            background-color: rgba(0, 0, 0, 0.3);
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            display: none;
        }
        
        .teacher-room h3 {
            color: #FFD700;
            margin-bottom: 10px;
        }
        
        .progress-bar {
            height: 10px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 5px;
            margin: 20px 0;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background-color: #FFD700;
            width: 0%;
            transition: width 0.5s ease;
        }
        
        .correct-answer {
            background-color: rgba(0, 255, 0, 0.2);
            border: 1px solid rgba(0, 255, 0, 0.5);
        }
        
        .incorrect-answer {
            background-color: rgba(255, 0, 0, 0.2);
            border: 1px solid rgba(255, 0, 0, 0.5);
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- شاشة البداية -->
        <div id="start-screen">
            <h1>اختبار كيمياء التفاعلي</h1>
            <h2>الوحدة الثانية</h2>
            <div class="intro">
                <p>مرحباً بك في اختبار الكيمياء التفاعلي. يرجى إدخال بياناتك قبل البدء.</p>
            </div>
            
            <div class="form-group">
                <label for="student-name">اسم الطالب:</label>
                <input type="text" id="student-name" placeholder="أدخل اسمك الكامل">
            </div>
            
            <div class="form-group">
                <label for="student-section">الشعبة (من 1 إلى 7):</label>
                <select id="student-section">
                    <option value="">اختر الشعبة</option>
                    <option value="1">الشعبة 1</option>
                    <option value="2">الشعبة 2</option>
                    <option value="3">الشعبة 3</option>
                    <option value="4">الشعبة 4</option>
                    <option value="5">الشعبة 5</option>
                    <option value="6">الشعبة 6</option>
                    <option value="7">الشعبة 7</option>
                </select>
            </div>
            
            <button id="start-btn">بدء الاختبار</button>
            <div class="error-message" id="start-error">يرجى إدخال الاسم واختيار الشعبة!</div>
            
            <!-- غرفة المعلم -->
            <div class="teacher-room" id="teacher-room">
                <h3>غرفة المعلم</h3>
                <p>رقم الغرفة: <strong>13321</strong></p>
                <div id="student-results"></div>
            </div>
        </div>
        
        <!-- شاشة الأسئلة -->
        <div id="questions-screen" class="question-container">
            <h2>اختبار الكيمياء - الوحدة الثانية</h2>
            <div class="progress-bar">
                <div class="progress" id="progress-bar"></div>
            </div>
            <div id="question-number">السؤال 1 من 40</div>
            
            <div class="question" id="question-container">
                <h3 id="question-text"></h3>
                <div class="options" id="options-container"></div>
            </div>
            
            <div class="navigation">
                <button id="prev-btn">السابق</button>
                <button id="next-btn">التالي</button>
            </div>
            
            <button id="submit-btn" style="display: none;">إنهاء الاختبار وعرض النتيجة</button>
            <div class="error-message" id="answer-error">يرجى اختيار إجابة!</div>
        </div>
        
        <!-- شاشة النتائج -->
        <div id="results-screen" class="result-container">
            <h2>نتيجة الاختبار</h2>
            <div class="result" id="score-result"></div>
            <p id="score-message"></p>
            
            <button id="show-answers-btn">عرض الإجابات</button>
            <button id="restart-btn">إعادة الاختبار</button>
        </div>
        
        <!-- شاشة الإجابات -->
        <div id="answers-screen" class="answers-container">
            <h2>الإجابات الصحيحة</h2>
            <div id="answers-list"></div>
            
            <div class="team">
                <h3>فريق العمل</h3>
                <ul>
                    <li>قائد و المشرف: مهدي البطاط</li>
                    <li>المراجع: سالم المحيبس</li>
                    <li>الباحثين عن الأسئلة: عبدالله الدوسري و سامي الشمري</li>
                    <li>المراجع: عماد الرشود</li>
                    <li>المقدم: مهدي البطاط</li>
                </ul>
            </div>
            
            <button id="back-to-results">العودة إلى النتائج</button>
        </div>
    </div>

    <!-- أصوات -->
    <audio id="correct-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-correct-answer-tone-2870.mp3" preload="auto"></audio>
    <audio id="wrong-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-wrong-answer-fail-notification-946.mp3" preload="auto"></audio>

    <script>
        // بيانات الأسئلة
        const questions = [
            {
                question: "ما هي الآفة الرئيسية التي تتسبب بها الأشعة فوق البنفسجية (UVB) للبشر؟",
                options: [
                    "تحسين كثافة العظام.",
                    "التسبب بسرطان الجلد.",
                    "المساعدة على إنتاج فيتامين د.",
                    "تحسين النظر الليلي."
                ],
                correct: 1
            },
            {
                question: "أين تتركز طبقة الأوزون الرئيسية في الغلاف الجوي؟",
                options: [
                    "التروبوسفير.",
                    "الميزوسفير.",
                    "الثيرموسفير.",
                    "الستراتوسفير."
                ],
                correct: 3
            },
            {
                question: "ما هي الصيغة الكيميائية الصحيحة لجزيء الأوزون؟",
                options: [
                    "O₂",
                    "O₃",
                    "O₄",
                    "CO₂"
                ],
                correct: 1
            },
            {
                question: "ما الوحدة المستخدمة لقياس كمية الأوزون في الغلاف الجوي؟",
                options: [
                    "النيوتن.",
                    "دوبسون.",
                    "الباسكال.",
                    "الجول."
                ],
                correct: 1
            },
            {
                question: "ما هي المركبات المسؤولة بشكل رئيسي عن استنزاف طبقة الأوزون؟",
                options: [
                    "ثاني أكسيد الكربون (CO₂).",
                    "مركبات الكلوروفلوروكربون (CFCs).",
                    "الأكسجين (O₂).",
                    "الميثان (CH₄)."
                ],
                correct: 1
            },
            {
                question: "ما الدور الرئيسي الذي تلعبه طبقة الأوزون؟",
                options: [
                    "تنظيم درجة حرارة الأرض.",
                    "امتصاص الأشعة فوق البنفسجية الضارة.",
                    "توفير الأكسجين للتنفس.",
                    "تشكيل السحب."
                ],
                correct: 1
            },
            {
                question: "ما الهدف الرئيسي من بروتوكول مونتريال؟",
                options: [
                    "مكافحة الفقر.",
                    "الحد من انبعاثات ثاني أكسيد الكربون.",
                    "حماية طبقة الأوزون من المواد المستنفدة لها.",
                    "تنظيم التجارة الدولية."
                ],
                correct: 2
            },
            {
                question: "لماذا يكون ثقب الأوزون أكثر وضوحًا فوق القارة القطبية الجنوبية؟",
                options: [
                    "لأنها الأقرب إلى الشمس.",
                    "بسبب الظروف الجوية الخاصة التي تساعد على تجمع المركبات المستنفدة للأوزون.",
                    "لأنها تنتج كميات كبيرة من مركبات الكلوروفلوروكربون.",
                    "بسبب قلة السكان."
                ],
                correct: 1
            },
            {
                question: "ما العامل الرئيسي الذي يؤدي إلى تكوين كميات أكبر من الأوزون فوق خط الاستواء؟",
                options: [
                    "انخفاض درجة الحرارة.",
                    "قلة التلوث.",
                    "شدة وسقوط أشعة الشمس عمودياً طوال العام.",
                    "وجود المحيطات."
                ],
                correct: 2
            },
            {
                question: "أي من هذه الأجهزة يستخدم لقياس الأوزون من الأقمار الصناعية؟",
                options: [
                    "مقياس الحرارة.",
                    "مقياس طيف الأوزون (مثل TOMS).",
                    "الميزان.",
                    "المسطرة."
                ],
                correct: 1
            },
            {
                question: "ما هو التركيز الرئيسي لعلم الكيمياء العضوية؟",
                options: [
                    "دراسة العناصر المعدنية.",
                    "دراسة المركبات التي تحتوي على الكربون.",
                    "دراسة التفاعلات في الكائنات الحية فقط.",
                    "دراسة خواص الماء."
                ],
                correct: 1
            },
            {
                question: "أي من العبارات التالية تميز الكتلة عن الوزن؟",
                options: [
                    "الكتلة تتغير بتغير الجاذبية، بينما الوزن ثابت.",
                    "الكتلة قوة، بينما الوزن كمية المادة.",
                    "الكتلة كمية المادة وثابتة، بينما الوزن قوة ويتغير بالجاذبية.",
                    "الكتلة والوزن مترادفان."
                ],
                correct: 2
            },
            {
                question: "لماذا يهتم الكيميائي بدراسة المادة على المستوى المجهري؟",
                options: [
                    "لأنه أرخص.",
                    "لأن الخصائص المرئية للمادة ناتجة عن سلوكها المجهري.",
                    "لأنه لا يمكن رؤية المادة بالعين المجردة.",
                    "لأنه أسهل."
                ],
                correct: 1
            },
            {
                question: "أي فرع من فروع الكيمياء يهتم بدراسة العمليات الكيميائية داخل جسم الكائن الحي؟",
                options: [
                    "الكيمياء الفيزيائية.",
                    "الكيمياء التحليلية.",
                    "الكيمياء الحيوية.",
                    "الكيمياء غير العضوية."
                ],
                correct: 2
            },
            {
                question: "أي من الخيارات التالية يمثل بيانات كمية؟",
                options: [
                    "لون العينة أزرق.",
                    "العينة لها رائحة كريهة.",
                    "درجة غليان السائل 100 درجة مئوية.",
                    "المادة صلبة."
                ],
                correct: 2
            },
            {
                question: "ما هو التعريف الأنسب للطريقة العلمية؟",
                options: [
                    "مجموعة من المعتقدات.",
                    "عملية منهجية يستخدمها العلماء للتحقق من الظواهر الطبيعية.",
                    "طريقة لكتابة التقارير.",
                    "نظرية غير قابلة للدحض."
                ],
                correct: 1
            },
            {
                question: "ما الفرق الرئيسي بين الفرضية والنظرية؟",
                options: [
                    "الفرضية مثبتة بأدلة كثيرة، بينما النظرية هي مجرد تخمين.",
                    "النظرية هي تفسير أولي، بينما الفرضية مثبتة.",
                    "الفرضية تفسير قابل للاختبار، بينما النظرية تفسير شامل مدعوم بأدلة.",
                    "لا فرق بينهما."
                ],
                correct: 2
            },
            {
                question: "في تجربة لاختبار تأثير درجة الحرارة على ذوبان السكر، ما هو المتغير المستقل؟",
                options: [
                    "كمية الماء المستخدمة.",
                    "نوع السكر.",
                    "درجة حرارة الماء.",
                    "الوقت الذي يستغرقه الذوبان."
                ],
                correct: 2
            },
            {
                question: "ما هو المتغير التابع في التجربة السابقة؟",
                options: [
                    "كمية الماء المستخدمة.",
                    "نوع السكر.",
                    "درجة حرارة الماء.",
                    "الوقت الذي يستغرقه الذوبان."
                ],
                correct: 3
            },
            {
                question: "ما الهدف الأساسي من تحليل نتائج التجربة؟",
                options: [
                    "لإثبات أن الفرضية خاطئة دائمًا.",
                    "لتأكيد الفرضية أو نفيها واستخلاص استنتاجات.",
                    "لتجاهل البيانات غير المتوقعة.",
                    "لإنهاء التقرير بسرعة."
                ],
                correct: 1
            },
            {
                question: "أي نوع من البحوث يهدف مباشرة إلى حل مشكلة عملية؟",
                options: [
                    "البحث النظري.",
                    "البحث التطبيقي.",
                    "البحث التاريخي.",
                    "البحث الفلسفي."
                ],
                correct: 1
            },
            {
                question: "أي من الخيارات التالية يمثل قانونًا علميًا؟",
                options: [
                    "نظرية التطور.",
                    "قانون نيوتن للجاذبية (يصف الجاذبية دون تفسيرها).",
                    "فرضية الوجود.",
                    "نظرية الانفجار العظيم."
                ],
                correct: 1
            },
            {
                question: "ما هو الإجراء الأكثر أهمية للسلامة في المختبر؟",
                options: [
                    "ارتداء المعدات الواقية مثل النظارات والمعطف.",
                    "تناول الطعام والشراب.",
                    "الجري لإنجاز التجربة بسرعة.",
                    "العمل بمفردك دائمًا."
                ],
                correct: 0
            },
            {
                question: "أي من هذه الاكتشافات كان غير مقصود (بالصدفة)؟",
                options: [
                    "اكتشاف البنسلين من قبل ألكسندر فلمنج.",
                    "وضع جدول دوري من قبل مندليف.",
                    "اكتشاف تركيب الحمض النووي من قبل واتسون وكريك.",
                    "جميع ما سبق."
                ],
                correct: 0
            },
            {
                question: "أي من هذه ليس من فوائد علم الكيمياء؟",
                options: [
                    "تطوير أدوية جديدة.",
                    "تلويث البيئة بشكل متعمد.",
                    "إنتاج مواد بناء جديدة.",
                    "تحسين تقنيات تنقية المياه."
                ],
                correct: 1
            },
            {
                question: "عند سكب مادة كيميائية على جلدك، ما أول ما يجب عليك فعله؟",
                options: [
                    "الانتظار لترى ما إذا كان هناك ألم.",
                    "غسل المنطقة بماء جاري بكمية كبيرة.",
                    "تجفيفها بمنشور.",
                    "وضع مرهم دون استشارة."
                ],
                correct: 1
            },
            {
                question: "ما هو الغرض من غطاء الدخان (الشفاط) في المختبر؟",
                options: [
                    "لإضاءة منطقة العمل.",
                    "لتخزين المواد الكيميائية.",
                    "لحماية المستخدم من استنشاق الأبخرة الخطرة.",
                    "لتبريد الأدوات الساخنة."
                ],
                correct: 2
            },
            {
                question: "أي من هذه المواد الكيميائية يعتبر قابلاً للاشتعال في العادة؟",
                options: [
                    "الماء.",
                    "الكحول.",
                    "ملح الطعام.",
                    "الرمل."
                ],
                correct: 1
            },
            {
                question: "اكتشاف مادة السكارين (المحلي الصناعي) هو مثال على:",
                options: [
                    "بحث نظري دقيق.",
                    "اكتشاف غير مقصود.",
                    "تطبيق للكيمياء الحيوية فقط.",
                    "تفاعل مخطّط له بدقة."
                ],
                correct: 1
            },
            {
                question: "أي من هذه المجالات لا يعتبر فرعًا رئيسيًا من فروع الكيمياء؟",
                options: [
                    "الكيمياء العضوية.",
                    "الكيمياء التحليلية.",
                    "كيمياء السحر.",
                    "الكيمياء الفيزيائية."
                ],
                correct: 2
            },
            {
                question: "أي من هذه الخواص تعتبر خاصية كيميائية؟",
                options: [
                    "الكتلة.",
                    "اللون.",
                    "القابلية للاشتعال.",
                    "الكثافة."
                ],
                correct: 2
            },
            {
                question: "عندما يتحول الماء من الحالة السائلة إلى الصلبة، يسمى هذا التغير:",
                options: [
                    "تغير كيميائي.",
                    "انصهار.",
                    "تكثف.",
                    "تجمد."
                ],
                correct: 3
            },
            {
                question: "المادة النقية التي لا يمكن تحليلها إلى مواد أبسط بالوسائل الكيميائية العادية هي:",
                options: [
                    "المركب.",
                    "الخليط.",
                    "العنصر.",
                    "المحلول."
                ],
                correct: 2
            },
            {
                question: "أي من هذه يمثل خليطًا متجانسًا؟",
                options: [
                    "السلطة.",
                    "الماء المالح.",
                    "الرمل والحصى.",
                    "الرغوة."
                ],
                correct: 1
            },
            {
                question: "ما الذي تشير إليه 'الكتلة الذرية' للعنصر؟",
                options: [
                    "عدد الإلكترونات.",
                    "عدد البروتونات.",
                    "متوسط كتلة ذرات العنصر.",
                    "عدد النيوترونات."
                ],
                correct: 2
            },
            {
                question: "كم إلكترونًا يوجد في الغلاف الخارجي للعناصر المستقرة (الغازات النبيلة) عادة؟",
                options: [
                    "2 إلكترونات.",
                    "8 إلكترونات.",
                    "18 إلكترونًا.",
                    "الرقم يعتمد على العنصر."
                ],
                correct: 1
            },
            {
                question: "ما نوع الرابطة التي تتشارك فيها الذرات بالإلكترونات؟",
                options: [
                    "الرابطة الأيونية.",
                    "الرابطة التساهمية.",
                    "الرابطة الهيدروجينية.",
                    "الرابطة المعدنية."
                ],
                correct: 1
            },
            {
                question: "في المعادلة الكيميائية، ماذا يجب أن يكون متساويًا على طرفي السهم؟",
                options: [
                    "عدد الجزيئات فقط.",
                    "عدد الذرات لكل عنصر.",
                    "حجم المواد المتفاعلة.",
                    "كتلة المواد الناتجة فقط."
                ],
                correct: 1
            },
            {
                question: "أي من هذه العوامل لا يؤثر عادة في سرعة التفاعل الكيميائي؟",
                options: [
                    "درجة الحرارة.",
                    "تركيز المواد المتفاعلة.",
                    "وجود عامل حفاز.",
                    "لون المواد المتفاعلة."
                ],
                correct: 3
            },
            {
                question: "عند إذابة حمض في الماء، يجب دائمًا:",
                options: [
                    "إضافة الماء إلى الحمض.",
                    "إضافة الحمض إلى الماء.",
                    "خلطهما في نفس الوقت.",
                    "تسخين الماء أولاً."
                ],
                correct: 1
            }
        ];

        // عناصر DOM
        const startScreen = document.getElementById('start-screen');
        const questionsScreen = document.getElementById('questions-screen');
        const resultsScreen = document.getElementById('results-screen');
        const answersScreen = document.getElementById('answers-screen');
        const teacherRoom = document.getElementById('teacher-room');
        const studentResults = document.getElementById('student-results');
        
        const startBtn = document.getElementById('start-btn');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const submitBtn = document.getElementById('submit-btn');
        const showAnswersBtn = document.getElementById('show-answers-btn');
        const restartBtn = document.getElementById('restart-btn');
        const backToResultsBtn = document.getElementById('back-to-results');
        
        const studentNameInput = document.getElementById('student-name');
        const studentSectionInput = document.getElementById('student-section');
        
        const questionText = document.getElementById('question-text');
        const optionsContainer = document.getElementById('options-container');
        const questionNumber = document.getElementById('question-number');
        const progressBar = document.getElementById('progress-bar');
        
        const scoreResult = document.getElementById('score-result');
        const scoreMessage = document.getElementById('score-message');
        const answersList = document.getElementById('answers-list');
        
        const startError = document.getElementById('start-error');
        const answerError = document.getElementById('answer-error');
        
        const correctSound = document.getElementById('correct-sound');
        const wrongSound = document.getElementById('wrong-sound');
        
        // متغيرات التطبيق
        let currentQuestion = 0;
        let userAnswers = new Array(questions.length).fill(null);
        let testStarted = false;
        
        // تهيئة التطبيق
        function initApp() {
            // إظهار غرفة المعلم إذا كان الرمز صحيحاً
            const urlParams = new URLSearchParams(window.location.search);
            if (urlParams.get('teacher') === '13321') {
                teacherRoom.style.display = 'block';
                loadStudentResults();
            }
            
            // إضافة المستمعين للأحداث
            startBtn.addEventListener('click', startTest);
            prevBtn.addEventListener('click', showPreviousQuestion);
            nextBtn.addEventListener('click', showNextQuestion);
            submitBtn.addEventListener('click', showResults);
            showAnswersBtn.addEventListener('click', showAnswers);
            restartBtn.addEventListener('click', restartTest);
            backToResultsBtn.addEventListener('click', () => {
                answersScreen.style.display = 'none';
                resultsScreen.style.display = 'block';
            });
        }
        
        // بدء الاختبار
        function startTest() {
            const name = studentNameInput.value.trim();
            const section = studentSectionInput.value;
            
            if (!name || !section) {
                startError.style.display = 'block';
                return;
            }
            
            startError.style.display = 'none';
            startScreen.style.display = 'none';
            questionsScreen.style.display = 'block';
            testStarted = true;
            
            // حفظ بيانات الطالب
            const studentData = {
                name: name,
                section: section,
                startTime: new Date().toISOString()
            };
            localStorage.setItem('currentStudent', JSON.stringify(studentData));
            
            showQuestion(currentQuestion);
        }
        
        // عرض السؤال
        function showQuestion(index) {
            const question = questions[index];
            questionText.textContent = question.question;
            questionNumber.textContent = `السؤال ${index + 1} من ${questions.length}`;
            
            // تحديث شريط التقدم
            const progress = ((index + 1) / questions.length) * 100;
            progressBar.style.width = `${progress}%`;
            
            // مسح الخيارات السابقة
            optionsContainer.innerHTML = '';
            
            // إضافة الخيارات
            question.options.forEach((option, i) => {
                const optionElement = document.createElement('div');
                optionElement.className = 'option';
                if (userAnswers[index] === i) {
                    optionElement.classList.add('selected');
                }
                optionElement.textContent = option;
                optionElement.addEventListener('click', () => selectOption(i));
                optionsContainer.appendChild(optionElement);
            });
            
            // تحديث أزرار التنقل
            prevBtn.disabled = index === 0;
            nextBtn.style.display = index === questions.length - 1 ? 'none' : 'block';
            submitBtn.style.display = index === questions.length - 1 ? 'block' : 'none';
            
            // إخفاء رسالة الخطأ
            answerError.style.display = 'none';
        }
        
        // اختيار إجابة
        function selectOption(optionIndex) {
            // إزالة التحديد من جميع الخيارات
            const options = document.querySelectorAll('.option');
            options.forEach(option => option.classList.remove('selected'));
            
            // تحديد الخيار المختار
            options[optionIndex].classList.add('selected');
            userAnswers[currentQuestion] = optionIndex;
            
            // إخفاء رسالة الخطأ
            answerError.style.display = 'none';
        }
        
        // الانتقال للسؤال السابق
        function showPreviousQuestion() {
            if (currentQuestion > 0) {
                currentQuestion--;
                showQuestion(currentQuestion);
            }
        }
        
        // الانتقال للسؤال التالي
        function showNextQuestion() {
            if (userAnswers[currentQuestion] === null) {
                answerError.style.display = 'block';
                return;
            }
            
            if (currentQuestion < questions.length - 1) {
                currentQuestion++;
                showQuestion(currentQuestion);
            }
        }
        
        // عرض النتائج
        function showResults() {
            if (userAnswers[currentQuestion] === null) {
                answerError.style.display = 'block';
                return;
            }
            
            // حساب النتيجة
            let correctCount = 0;
            userAnswers.forEach((answer, index) => {
                if (answer === questions[index].correct) {
                    correctCount++;
                }
            });
            
            const score = (correctCount / questions.length) * 100;
            
            // حفظ النتيجة
            const studentData = JSON.parse(localStorage.getItem('currentStudent'));
            studentData.endTime = new Date().toISOString();
            studentData.score = score;
            studentData.correctAnswers = correctCount;
            studentData.totalQuestions = questions.length;
            
            saveStudentResult(studentData);
            
            // عرض النتيجة
            questionsScreen.style.display = 'none';
            resultsScreen.style.display = 'block';
            
            scoreResult.textContent = `${score.toFixed(1)}%`;
            
            if (score >= 90) {
                scoreMessage.textContent = 'ممتاز! أداء رائع.';
            } else if (score >= 80) {
                scoreMessage.textContent = 'جيد جداً! أداء متميز.';
            } else if (score >= 70) {
                scoreMessage.textContent = 'جيد! يمكنك التحسين أكثر.';
            } else if (score >= 60) {
                scoreMessage.textContent = 'مقبول! تحتاج للمراجعة.';
            } else {
                scoreMessage.textContent = 'ضعيف! يرجى مراجعة المادة جيداً.';
            }
        }
        
        // عرض الإجابات
        function showAnswers() {
            resultsScreen.style.display = 'none';
            answersScreen.style.display = 'block';
            
            answersList.innerHTML = '';
            
            questions.forEach((question, index) => {
                const answerItem = document.createElement('div');
                answerItem.className = 'question';
                
                const userAnswer = userAnswers[index];
                const isCorrect = userAnswer === question.correct;
                
                let answerStatus = '';
                if (isCorrect) {
                    answerStatus = '<span style="color: green;">✓ إجابة صحيحة</span>';
                } else {
                    answerStatus = `<span style="color: red;">✗ إجابة خاطئة - الإجابة الصحيحة: ${question.options[question.correct]}</span>`;
                }
                
                answerItem.innerHTML = `
                    <h3>السؤال ${index + 1}: ${question.question}</h3>
                    <p><strong>إجابتك:</strong> ${userAnswer !== null ? question.options[userAnswer] : 'لم تجب على هذا السؤال'}</p>
                    <p><strong>${answerStatus}</strong></p>
                `;
                
                answersList.appendChild(answerItem);
            });
        }
        
        // إعادة الاختبار
        function restartTest() {
            currentQuestion = 0;
            userAnswers = new Array(questions.length).fill(null);
            
            resultsScreen.style.display = 'none';
            startScreen.style.display = 'block';
            
            studentNameInput.value = '';
            studentSectionInput.value = '';
        }
        
        // حفظ نتيجة الطالب
        function saveStudentResult(studentData) {
            let allResults = JSON.parse(localStorage.getItem('studentResults')) || [];
            allResults.push(studentData);
            localStorage.setItem('studentResults', JSON.stringify(allResults));
            
            // تحديث غرفة المعلم إذا كانت مفتوحة
            if (teacherRoom.style.display === 'block') {
                loadStudentResults();
            }
        }
        
        // تحميل نتائج الطلاب
        function loadStudentResults() {
            const allResults = JSON.parse(localStorage.getItem('studentResults')) || [];
            studentResults.innerHTML = '';
            
            if (allResults.length === 0) {
                studentResults.innerHTML = '<p>لا توجد نتائج حتى الآن.</p>';
                return;
            }
            
            allResults.forEach((result, index) => {
                const resultItem = document.createElement('div');
                resultItem.style.padding = '10px';
                resultItem.style.borderBottom = '1px solid rgba(255,255,255,0.2)';
                resultItem.innerHTML = `
                    <p><strong>${result.name}</strong> - الشعبة ${result.section}</p>
                    <p>النتيجة: ${result.score.toFixed(1)}% (${result.correctAnswers}/${result.totalQuestions})</p>
                    <p>الوقت: ${new Date(result.endTime).toLocaleString('ar-SA')}</p>
                `;
                studentResults.appendChild(resultItem);
            });
        }
        
        // تشغيل الصوت عند الإجابة الصحيحة
        function playCorrectSound() {
            correctSound.currentTime = 0;
            correctSound.play();
        }
        
        // تشغيل الصوت عند الإجابة الخاطئة
        function playWrongSound() {
            wrongSound.currentTime = 0;
            wrongSound.play();
        }
        
        // بدء التطبيق
        window.onload = initApp;
    </script>
</body>
</html>
