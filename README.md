<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Home Recipes - สร้างความสุขในทุกมื้ออาหารของครอบครัว</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Sarabun', 'Prompt', sans-serif;
            background: linear-gradient(135deg, #FFE5F1 0%, #FFF0F5 50%, #E6E6FA 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.98);
            border-radius: 25px;
            padding: 40px;
            box-shadow: 0 15px 35px rgba(255, 182, 193, 0.2);
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            padding-bottom: 30px;
            border-bottom: 3px solid #FFE0EC;
        }

        .header h1 {
            color: #D8627D;
            font-size: 2.8em;
            margin-bottom: 15px;
            font-weight: bold;
            text-shadow: 2px 2px 4px rgba(255, 182, 193, 0.3);
        }
        
        .header .subtitle {
            color: #F9A8D4;
            font-size: 1.4em;
            margin-bottom: 10px;
            font-weight: 600;
        }

        .header .tagline {
            color: #A78BFA;
            font-size: 1.1em;
            line-height: 1.6;
            max-width: 700px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .input-section {
            background: linear-gradient(135deg, #FFEDF0, #F0F4FD);
            padding: 35px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 8px 20px rgba(255, 182, 193, 0.15);
        }

        .input-section h2 {
            color: #D8627D;
            margin-bottom: 25px;
            font-size: 1.6em;
            text-align: center;
        }

        .ingredients-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }

        .ingredient-input {
            position: relative;
        }

        .ingredient-input input {
            width: 100%;
            padding: 14px 15px 14px 45px;
            border: 2px solid #FFD4E5;
            border-radius: 15px;
            font-size: 1.1em;
            transition: all 0.3s;
            background: linear-gradient(to right, #FFFBFC, #FFF9FC);
        }

        .ingredient-input input:focus {
            outline: none;
            border-color: #F9A8D4;
            box-shadow: 0 0 15px rgba(249, 168, 212, 0.2);
            background: white;
        }

        .ingredient-number {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            width: 24px;
            height: 24px;
            background: linear-gradient(135deg, #FEC8D8, #FFDFD8);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: #D8627D;
            font-size: 0.9em;
        }

        .btn-generate {
            background: linear-gradient(135deg, #F9A8D4, #C084FC);
            color: white;
            border: none;
            padding: 18px 50px;
            font-size: 1.3em;
            border-radius: 35px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 8px 20px rgba(249, 168, 212, 0.3);
            display: block;
            margin: 35px auto;
            font-weight: bold;
            letter-spacing: 0.5px;
        }

        .btn-generate:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 25px rgba(249, 168, 212, 0.4);
            background: linear-gradient(135deg, #FBB6CE, #DDA5FF);
        }

        .btn-generate:active {
            transform: translateY(-1px);
        }

        .menu-results {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .menu-card {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(255, 182, 193, 0.15);
            transition: transform 0.3s;
            border: 2px solid #FFE8F1;
        }

        .menu-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(255, 182, 193, 0.25);
        }

        .menu-card-header {
            padding: 20px;
            color: white;
            font-weight: bold;
            font-size: 1.3em;
            text-align: center;
        }

        .menu-card.soup .menu-card-header {
            background: linear-gradient(135deg, #B4E7F8, #A8DADC);
        }

        .menu-card.dry .menu-card-header {
            background: linear-gradient(135deg, #FFD4BA, #FFDAB9);
        }

        .menu-card-body {
            padding: 25px;
        }

        .menu-name {
            font-size: 1.6em;
            color: #D8627D;
            margin-bottom: 12px;
            font-weight: bold;
        }

        .price-estimate {
            display: inline-block;
            background: linear-gradient(135deg, #FFE5F1, #FCE4EC);
            padding: 8px 16px;
            border-radius: 20px;
            color: #C2185B;
            font-weight: bold;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        .menu-description {
            color: #666;
            line-height: 1.6;
            margin-bottom: 20px;
            font-size: 1.05em;
        }

        .menu-ingredients {
            background: linear-gradient(135deg, #FFF9FC, #FFF5F9);
            padding: 18px;
            border-radius: 15px;
            margin-bottom: 20px;
            border: 1px solid #FFE8F1;
        }

        .menu-ingredients h4 {
            color: #D8627D;
            margin-bottom: 12px;
            font-size: 1.1em;
        }

        .menu-ingredients ul {
            list-style: none;
            padding-left: 0;
        }

        .menu-ingredients li {
            padding: 6px 0;
            color: #666;
            display: flex;
            align-items: center;
        }

        .menu-ingredients li::before {
            content: '✨';
            margin-right: 10px;
        }

        .cooking-method {
            background: linear-gradient(135deg, #F0F9FF, #F8F0FF);
            padding: 18px;
            border-radius: 15px;
            margin-bottom: 20px;
            border: 1px solid #E8D6FF;
        }

        .cooking-method h4 {
            color: #9F7AEA;
            margin-bottom: 12px;
            font-size: 1.1em;
        }

        .cooking-method ol {
            padding-left: 20px;
            color: #666;
            line-height: 1.8;
        }

        .cooking-method li {
            margin-bottom: 8px;
        }

        .nutrition-info {
            display: flex;
            justify-content: space-around;
            padding: 15px;
            background: linear-gradient(135deg, #FFF0F5, #F5F0FF);
            border-radius: 15px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .nutrition-item {
            text-align: center;
            flex: 1;
            min-width: 80px;
        }

        .nutrition-item .label {
            color: #A78BFA;
            font-size: 0.9em;
            margin-bottom: 5px;
        }

        .nutrition-item .value {
            color: #7C3AED;
            font-weight: bold;
            font-size: 1.1em;
        }

        .taste-indicator {
            display: inline-block;
            padding: 6px 18px;
            border-radius: 25px;
            color: white;
            font-weight: bold;
            margin: 10px 5px;
            font-size: 0.95em;
        }

        .taste-mild {
            background: linear-gradient(135deg, #C7F2E3, #B2E1D4);
            color: #059669;
        }

        .taste-strong {
            background: linear-gradient(135deg, #FECACA, #FCA5A5);
            color: #DC2626;
        }

        .loading {
            display: none;
            text-align: center;
            padding: 50px;
        }

        .loading.active {
            display: block;
        }

        .spinner {
            border: 4px solid #FFE8F1;
            border-top: 4px solid #F9A8D4;
            border-radius: 50%;
            width: 60px;
            height: 60px;
            animation: spin 1s linear infinite;
            margin: 0 auto 25px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .tips-section {
            background: linear-gradient(135deg, #FFEDF0, #F0F4FD);
            padding: 30px;
            border-radius: 20px;
            margin-top: 35px;
            border: 2px solid #FFE0EC;
        }

        .tips-section h3 {
            color: #D8627D;
            margin-bottom: 18px;
            font-size: 1.4em;
        }

        .tips-section ul {
            list-style: none;
            padding: 0;
        }

        .tips-section li {
            padding: 10px 0;
            color: #666;
            line-height: 1.6;
        }

        .tips-section li::before {
            content: '🌸 ';
            margin-right: 10px;
        }

        .footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 30px;
            border-top: 2px solid #FFE0EC;
            color: #A78BFA;
            font-size: 0.95em;
        }

        .health-warning-section {
            margin-top: 30px;
            padding: 30px;
            background: linear-gradient(135deg, #FFF9FC, #FFF5F9);
            border-radius: 20px;
            border: 2px solid #FFE0EC;
        }

        .health-warning-section h3 {
            color: #E91E63;
            margin-bottom: 25px;
            font-size: 1.4em;
            text-align: center;
        }

        .disease-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
        }

        .disease-card {
            background: white;
            padding: 20px;
            border-radius: 15px;
            border-left: 5px solid;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }

        .disease-card.diabetes {
            border-left-color: #FFB6C1;
            background: linear-gradient(to right, #FFF5F7, white);
        }

        .disease-card.hypertension {
            border-left-color: #87CEEB;
            background: linear-gradient(to right, #F0F8FF, white);
        }

        .disease-card.cholesterol {
            border-left-color: #FFE4B5;
            background: linear-gradient(to right, #FFFAF0, white);
        }

        .disease-card.gout {
            border-left-color: #DDA0DD;
            background: linear-gradient(to right, #FAF0FF, white);
        }

        .disease-card h4 {
            color: #D8627D;
            margin-bottom: 15px;
            font-size: 1.2em;
        }

        .avoid-list {
            margin-bottom: 15px;
        }

        .avoid-list strong {
            color: #E91E63;
            display: block;
            margin-bottom: 8px;
        }

        .avoid-list ul {
            list-style: none;
            padding: 0;
        }

        .avoid-list li {
            padding: 4px 0;
            color: #666;
            font-size: 0.95em;
        }

        .avoid-list li::before {
            content: '❌ ';
            margin-right: 8px;
        }

        .recommend {
            padding: 12px;
            background: linear-gradient(135deg, #E8F5E9, #F1F8E9);
            border-radius: 10px;
            font-size: 0.95em;
        }

        .recommend strong {
            color: #4CAF50;
            display: block;
            margin-bottom: 5px;
        }

        .calories-badge {
            display: inline-block;
            background: linear-gradient(135deg, #FFE0B2, #FFCC80);
            padding: 5px 12px;
            border-radius: 15px;
            color: #E65100;
            font-weight: bold;
            margin-left: 10px;
            font-size: 0.9em;
        }

        .menu-warnings {
            background: linear-gradient(135deg, #FFF9E7, #FFECB3);
            padding: 15px;
            border-radius: 12px;
            margin-top: 15px;
            border-left: 4px solid #FFA726;
        }

        .menu-warnings h4 {
            color: #E65100;
            margin-bottom: 10px;
            font-size: 1.05em;
        }

        .menu-warnings ul {
            list-style: none;
            padding: 0;
        }

        .menu-warnings li {
            padding: 5px 0;
            color: #666;
            font-size: 0.95em;
            line-height: 1.5;
        }

        .menu-warnings strong {
            color: #E65100;
        }

        @media (max-width: 768px) {
            .container {
                padding: 20px;
            }

            .header h1 {
                font-size: 2em;
            }

            .header .subtitle {
                font-size: 1.2em;
            }

            .header .tagline {
                font-size: 1em;
            }

            .menu-results {
                grid-template-columns: 1fr;
            }

            .ingredients-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🏡 Happy Home Recipes</h1>
            <div class="subtitle">สร้างความสุขในทุกมื้ออาหารของครอบครัว</div>
            <p class="tagline">เพียงแค่บอก 'วัตถุดิบที่คุณมี' เราพร้อมออกแบบสูตรอาหารโฮมเมดง่าย ๆ<br>ที่เติมเต็มความอบอุ่น และกลายเป็นจานโปรดที่เหมาะสมกับทุกวัยในครอบครัว</p>
        </div>

        <div class="input-section">
            <h2>🛒 วัตถุดิบที่คุณมีในครัว (กรอก 5 รายการ)</h2>
            <div class="ingredients-grid">
                <div class="ingredient-input">
                    <span class="ingredient-number">1</span>
                    <input type="text" id="ingredient1" placeholder="เช่น ไก่, หมู, ปลา" />
                </div>
                <div class="ingredient-input">
                    <span class="ingredient-number">2</span>
                    <input type="text" id="ingredient2" placeholder="เช่น ผักบุ้ง, คะน้า" />
                </div>
                <div class="ingredient-input">
                    <span class="ingredient-number">3</span>
                    <input type="text" id="ingredient3" placeholder="เช่น มะเขือเทศ, หอม" />
                </div>
                <div class="ingredient-input">
                    <span class="ingredient-number">4</span>
                    <input type="text" id="ingredient4" placeholder="เช่น ไข่, เต้าหู้" />
                </div>
                <div class="ingredient-input">
                    <span class="ingredient-number">5</span>
                    <input type="text" id="ingredient5" placeholder="เช่น เห็ด, ถั่วฝักยาว" />
                </div>
            </div>
            <button class="btn-generate" onclick="generateMenu()">✨ สร้างเมนูอาหาร</button>
        </div>

        <div class="loading" id="loading">
            <div class="spinner"></div>
            <p style="color: #F9A8D4; font-size: 1.2em; font-weight: bold;">กำลังสร้างสรรค์เมนูอาหารแสนอร่อย...</p>
        </div>

        <div class="menu-results" id="menuResults"></div>

        <div class="health-warning-section" id="healthWarning" style="display: none;">
            <h3>⚠️ ข้อควรระวังสำหรับผู้ป่วยโรคเรื้อรัง</h3>
            <div class="disease-cards">
                <div class="disease-card diabetes">
                    <h4>🩺 โรคเบาหวาน</h4>
                    <div class="avoid-list">
                        <strong>อาหารที่ควรหลีกเลี่ยง:</strong>
                        <ul>
                            <li>น้ำตาล น้ำผึ้ง น้ำเชื่อม</li>
                            <li>ข้าวเหนียว ขนมหวาน</li>
                            <li>ผลไม้หวานจัด (ทุเรียน ลำไย องุ่น)</li>
                            <li>เครื่องดื่มที่มีน้ำตาล</li>
                        </ul>
                    </div>
                    <div class="recommend">
                        <strong>แนะนำ:</strong> เลือกคาร์โบไฮเดรตเชิงซ้อน ผักใบเขียว โปรตีนไม่ติดมัน
                    </div>
                </div>

                <div class="disease-card hypertension">
                    <h4>💓 ความดันโลหิตสูง</h4>
                    <div class="avoid-list">
                        <strong>อาหารที่ควรหลีกเลี่ยง:</strong>
                        <ul>
                            <li>อาหารเค็มจัด (ปลาเค็ม ไข่เค็ม)</li>
                            <li>อาหารหมักดอง กะปิ น้ำปลา</li>
                            <li>อาหารสำเร็จรูป บะหมี่กึ่งสำเร็จรูป</li>
                            <li>เนื้อสัตว์แปรรูป (ไส้กรอก แฮม เบคอน)</li>
                        </ul>
                    </div>
                    <div class="recommend">
                        <strong>แนะนำ:</strong> ลดเกลือเหลือไม่เกิน 1 ช้อนชาต่อวัน เพิ่มผักผลไม้ที่มีโพแทสเซียม
                    </div>
                </div>

                <div class="disease-card cholesterol">
                    <h4>🧈 ไขมันในเลือดสูง</h4>
                    <div class="avoid-list">
                        <strong>อาหารที่ควรหลีกเลี่ยง:</strong>
                        <ul>
                            <li>อาหารทอดน้ำมันท่วม</li>
                            <li>เนื้อติดมัน หนังสัตว์</li>
                            <li>เครื่องในสัตว์ ไข่แดง (เกิน 3 ฟอง/สัปดาห์)</li>
                            <li>กะทิ ครีม เนย ชีส</li>
                        </ul>
                    </div>
                    <div class="recommend">
                        <strong>แนะนำ:</strong> เลือกเนื้อไม่ติดมัน ใช้น้ำมันพืช ปรุงด้วยการต้ม นึ่ง ย่าง
                    </div>
                </div>

                <div class="disease-card gout">
                    <h4>🦴 โรคเก๊าท์</h4>
                    <div class="avoid-list">
                        <strong>อาหารที่ควรหลีกเลี่ยง:</strong>
                        <ul>
                            <li>เครื่องในสัตว์ (ตับ ไต หัวใจ)</li>
                            <li>อาหารทะเล (กุ้ง หอย ปู ปลาทูน่า)</li>
                            <li>เนื้อแดง เป็ด ห่าน</li>
                            <li>ถั่วเมล็ดแห้ง เห็ดหอม หน่อไม้</li>
                            <li>เครื่องดื่มแอลกอฮอล์</li>
                        </ul>
                    </div>
                    <div class="recommend">
                        <strong>แนะนำ:</strong> ดื่มน้ำมากๆ วันละ 2-3 ลิตร เลือกโปรตีนจากไข่ นม เต้าหู้
                    </div>
                </div>
            </div>
        </div>

        <div class="tips-section">
            <h3>💝 เคล็ดลับการทำอาหารให้ครอบครัว</h3>
            <ul>
                <li>เลือกวัตถุดิบสดใหม่ เพื่อคุณค่าทางโภชนาการที่ดีที่สุด</li>
                <li>ปรุงรสพอดี ไม่เค็มหรือหวานจัด เพื่อสุขภาพที่ดีของทุกคน</li>
                <li>ใส่ผักหลากสีในทุกมื้อ เพื่อวิตามินและแร่ธาตุที่หลากหลาย</li>
                <li>ทำอาหารด้วยความรัก อาหารจะอร่อยและอบอุ่นยิ่งขึ้น</li>
                <li>ชวนทุกคนมาช่วยทำอาหาร สร้างความสุขและความผูกพันในครอบครัว</li>
            </ul>
        </div>

        <div class="footer">
            <p>Made with 💕 for Happy Families | อาหารดี ชีวิตดี ครอบครัวมีความสุข</p>
        </div>
    </div>

    <script>
        // ฐานข้อมูลเมนูจริงที่มีอยู่ในอาหารไทย
        const realMenuDatabase = {
            // เมนูที่ใช้ไก่เป็นหลัก
            'ไก่': {
                soup: [
                    {name: 'ต้มยำไก่บ้าน', spicy: true},
                    {name: 'ต้มข่าไก่', spicy: false},
                    {name: 'ต้มจืดไก่สับผักกาด', spicy: false},
                    {name: 'แกงจืดไก่สับใส่เต้าหู้', spicy: false}
                ],
                dry: [
                    {name: 'ไก่ผัดเม็ดมะม่วงหิมพานต์', spicy: false},
                    {name: 'ผัดกะเพราไก่', spicy: true},
                    {name: 'ไก่ผัดขิง', spicy: false},
                    {name: 'ไก่ผัดน้ำมันหอย', spicy: false}
                ]
            },
            // เมนูที่ใช้หมูเป็นหลัก
            'หมู': {
                soup: [
                    {name: 'ต้มจืดหมูสับใส่เต้าหู้', spicy: false},
                    {name: 'แกงจืดหมูบดใส่แตงกวา', spicy: false},
                    {name: 'ต้มยำหมู', spicy: true}
                ],
                dry: [
                    {name: 'หมูผัดพริกแกงใต้', spicy: true},
                    {name: 'ผัดกะเพราหมูสับ', spicy: true},
                    {name: 'หมูผัดน้ำมันหอย', spicy: false},
                    {name: 'หมูผัดขิง', spicy: false}
                ],
                warning: 'cholesterol' // ระวังไขมัน
            },
            // เมนูที่ใช้ปลาเป็นหลัก
            'ปลา': {
                soup: [
                    {name: 'ต้มยำปลากระพง', spicy: true},
                    {name: 'แกงส้มปลาชะอม', spicy: true},
                    {name: 'ต้มจืดปลากรายใส่ผักกาด', spicy: false}
                ],
                dry: [
                    {name: 'ปลาผัดฉ่า', spicy: true},
                    {name: 'ปลาผัดขิง', spicy: false},
                    {name: 'ปลานึ่งซีอิ๊ว', spicy: false},
                    {name: 'ปลาทอดราดพริกสามรส', spicy: true}
                ]
            },
            // เมนูที่ใช้กุ้งเป็นหลัก
            'กุ้ง': {
                soup: [
                    {name: 'ต้มยำกุ้งน้ำใส', spicy: true},
                    {name: 'แกงส้มกุ้งผักรวม', spicy: true}
                ],
                dry: [
                    {name: 'กุ้งผัดพริกเผา', spicy: true},
                    {name: 'กุ้งผัดซอสมะขาม', spicy: false},
                    {name: 'กุ้งผัดสะตอ', spicy: true}
                ],
                warning: 'gout,cholesterol' // ระวังเก๊าท์และคอเลสเตอรอล
            },
            // เมนูที่ใช้หอยเป็นหลัก
            'หอย': {
                soup: [
                    {name: 'ต้มยำทะเล', spicy: true},
                    {name: 'แกงจืดหอยลายใส่ตะไคร้', spicy: false}
                ],
                dry: [
                    {name: 'หอยลายผัดพริกเผา', spicy: true},
                    {name: 'หอยลายผัดฉ่า', spicy: true}
                ],
                warning: 'gout,cholesterol'
            },
            // เมนูที่ใช้เต้าหู้เป็นหลัก
            'เต้าหู้': {
                soup: [
                    {name: 'แกงจืดเต้าหู้อ่อนใส่หมูสับ', spicy: false},
                    {name: 'ต้มจืดเต้าหู้ใส่สาหร่าย', spicy: false}
                ],
                dry: [
                    {name: 'เต้าหู้ทอดราดซอสเห็ดหอม', spicy: false},
                    {name: 'เต้าหู้ผัดซอสมะเขือเทศ', spicy: false},
                    {name: 'ผัดเต้าหู้ใส่ผักรวม', spicy: false}
                ]
            },
            // เมนูที่ใช้ไข่เป็นหลัก
            'ไข่': {
                soup: [
                    {name: 'แกงจืดไข่น้ำ', spicy: false},
                    {name: 'ต้มจืดไข่หวานใส่หมูสับ', spicy: false}
                ],
                dry: [
                    {name: 'ไข่เจียวหมูสับ', spicy: false},
                    {name: 'ไข่ดาว', spicy: false},
                    {name: 'ไข่ต้มยำ', spicy: true},
                    {name: 'ไข่พะโล้', spicy: false}
                ],
                warning: 'cholesterol' // ระวังไขมันในไข่แดง
            },
            // ผักต่างๆ
            'ผักบุ้ง': {
                dry: [
                    {name: 'ผักบุ้งไฟแดง', spicy: false},
                    {name: 'ผักบุ้งผัดน้ำมันหอย', spicy: false}
                ]
            },
            'คะน้า': {
                dry: [
                    {name: 'คะน้าผัดน้ำมันหอย', spicy: false},
                    {name: 'คะน้าหมูกรอบ', spicy: false}
                ],
                warning: 'cholesterol' // ถ้ามีหมูกรอบ
            },
            'กะหล่ำปลี': {
                soup: [{name: 'แกงจืดกะหล่ำปลีใส่หมูสับ', spicy: false}],
                dry: [
                    {name: 'กะหล่ำปลีผัดน้ำปลา', spicy: false},
                    {name: 'กะหล่ำปลีผัดไข่', spicy: false}
                ]
            },
            'ผักกาด': {
                soup: [
                    {name: 'แกงจืดผักกาดขาวหมูสับ', spicy: false},
                    {name: 'แกงเลียงผักกาด', spicy: false}
                ],
                dry: [{name: 'ผักกาดขาวผัดน้ำมันหอย', spicy: false}]
            },
            'ฟักทอง': {
                soup: [
                    {name: 'แกงจืดฟักทอง', spicy: false},
                    {name: 'แกงเลียงฟักทอง', spicy: false}
                ],
                dry: [{name: 'ฟักทองผัดไข่', spicy: false}]
            },
            'มะเขือเทศ': {
                soup: [{name: 'แกงจืดมะเขือเทศยัดไส้', spicy: false}],
                dry: [{name: 'ไข่ผัดมะเขือเทศ', spicy: false}]
            },
            'ถั่วฝักยาว': {
                dry: [
                    {name: 'ถั่วฝักยาวผัดพริกแกง', spicy: true},
                    {name: 'ถั่วฝักยาวผัดไข่', spicy: false}
                ]
            },
            'เห็ด': {
                soup: [
                    {name: 'ต้มยำเห็ดรวม', spicy: true},
                    {name: 'แกงจืดเห็ดหอม', spicy: false}
                ],
                dry: [
                    {name: 'ผัดเห็ดน้ำมันหอย', spicy: false},
                    {name: 'ลาบเห็ด', spicy: true}
                ],
                warning: 'gout' // เห็ดหอมมีพิวรีนสูง
            },
            'หน่อไม้': {
                soup: [{name: 'แกงหน่อไม้ดอง', spicy: true}],
                dry: [{name: 'หน่อไม้ผัดน้ำพริกเผา', spicy: true}],
                warning: 'gout'
            }
        };

        // สูตรอาหารที่ถูกต้อง
        const correctRecipes = {
            'ต้มยำไก่': {
                calories: '150-180',
                price: '60-80',
                time: '25 นาที',
                tasteClass: 'taste-strong',
                tasteText: '🌶️ รสเปรี้ยวเผ็ดนำ',
                mainIngredients: [
                    'ไก่หั่นชิ้นพอคำ - 300 กรัม',
                    'เห็ดฟางผ่าครึ่ง - 150 กรัม',
                    'มะเขือเทศผ่า 4 - 3 ลูก',
                    'หอมแดงผ่าครึ่ง - 4 หัว',
                    'ผักชีฝรั่งหั่นท่อน - 2 ต้น'
                ],
                seasonings: [
                    'น้ำซุปไก่ - 3 ถ้วย',
                    'ตะไคร้ทุบหั่นท่อน - 3 ต้น',
                    'ข่าอ่อนหั่นบางๆ - 6-7 แว่น',
                    'ใบมะกรูดฉีก - 5 ใบ',
                    'พริกขี้หนูสดทุบพอแตก - 10-15 เม็ด',
                    'น้ำปลา - 3 ช้อนโต๊ะ',
                    'น้ำมะนาวสด - 4-5 ช้อนโต๊ะ',
                    'น้ำพริกเผา - 2 ช้อนโต๊ะ (ไม่จำเป็น)'
                ],
                steps: [
                    'ต้มน้ำซุปไก่ให้เดือด',
                    'ใส่ตะไคร้ ข่า รากผักชี ต้มให้หอม 3-5 นาที',
                    'ใส่ไก่ลงต้ม รอให้ไก่สุก ประมาณ 8-10 นาที',
                    'ใส่เห็ดฟาง ต้มต่อ 2 นาที',
                    'ใส่ใบมะกรูด มะเขือเทศ หอมแดง ผักชีฝรั่ง',
                    'ปิดไฟ รอให้อุณหภูมิลดลงเล็กน้อย',
                    'ใส่พริกขี้หนูทุบ น้ำปลา น้ำมะนาว',
                    'ชิมรสให้ได้รสเปรี้ยวนำ ตามด้วยเค็มและเผ็ด',
                    'ตักใส่ถ้วย โรยผักชีเสิร์ฟขณะร้อน'
                ],
                warnings: {
                    diabetes: '✅ เหมาะสม - ไม่มีน้ำตาล แต่ระวังน้ำพริกเผาถ้าใส่',
                    hypertension: '⚠️ ลดน้ำปลาเหลือ 1-2 ช้อนโต๊ะ ไม่ใส่น้ำพริกเผา',
                    cholesterol: '⚠️ เลือกเนื้ออกไก่ ลอกหนังออก',
                    gout: '✅ ปลอดภัย - ไก่มีพิวรีนต่ำ'
                }
            },
            'ต้มข่าไก่': {
                calories: '200-250',
                price: '80-100',
                time: '30 นาที',
                tasteClass: 'taste-mild',
                tasteText: '😊 รสกลมกล่อม เผ็ดอ่อนๆ',
                mainIngredients: [
                    'ไก่หั่นชิ้นกลาง - 400 กรัม',
                    'เห็ดฟางผ่าครึ่ง - 150 กรัม',
                    'มะเขือพวง - 5-6 ลูก',
                    'กะทิ - 2 ถ้วย',
                    'น้ำซุป - 1 ถ้วย'
                ],
                seasonings: [
                    'ข่าอ่อนหั่นบางๆ - 1 ห่อเล็ก',
                    'ตะไคร้ทุบหั่นท่อน - 3 ต้น',
                    'หอมแดงทุบ - 5 หัว',
                    'ใบมะกรูดฉีก - 5-6 ใบ',
                    'พริกชี้ฟ้าทุบเบาๆ - 5 เม็ด',
                    'น้ำปลา - 2-3 ช้อนโต๊ะ',
                    'น้ำมะนาว - 2 ช้อนโต๊ะ',
                    'น้ำตาลมะพร้าว - 1 ช้อนชา'
                ],
                steps: [
                    'แยกหัวกะทิ 1/2 ถ้วย พักไว้',
                    'เคี่ยวหัวกะทิที่เหลือกับน้ำซุปให้เดือด',
                    'ใส่ข่า ตะไคร้ หอมแดง ต้มให้หอม 5 นาที',
                    'ใส่ไก่ ต้มไฟกลางจนไก่สุก 10-12 นาที',
                    'ใส่เห็ดฟาง มะเขือพวง ใบมะกรูด',
                    'เติมหางกะทิ ต้มให้เดือดอีกครั้ง',
                    'ปรุงรสด้วยน้ำปลา น้ำตาลมะพร้าว',
                    'ปิดไฟ ใส่พริกชี้ฟ้า น้ำมะนาว',
                    'เติมหัวกะทิที่พักไว้ คนเบาๆ เสิร์ฟ'
                ],
                warnings: {
                    diabetes: '⚠️ ระวังน้ำตาลมะพร้าว ใส่น้อยหรืองด',
                    hypertension: '⚠️ ลดน้ำปลา ใช้กะทิไขมันต่ำ',
                    cholesterol: '❌ หลีกเลี่ยง - กะทิมีไขมันอิ่มตัวสูง',
                    gout: '✅ ปลอดภัย - ถ้าใช้ไก่และเห็ดฟาง'
                }
            },
            'แกงจืดเต้าหู้หมูสับ': {
                calories: '120-150',
                price: '40-50',
                time: '20 นาที',
                tasteClass: 'taste-mild',
                tasteText: '😊 รสชาติอ่อนโยน กลมกล่อม',
                mainIngredients: [
                    'หมูสับ - 200 กรัม',
                    'เต้าหู้ขาวหั่นก้อน - 1 หลอด',
                    'ผักกาดขาวหั่นท่อน - 100 กรัม',
                    'เห็ดหอมแช่น้ำ - 5 ดอก',
                    'วุ้นเส้น - 1 กำเล็ก'
                ],
                seasonings: [
                    'น้ำซุปกระดูกหมู - 3 ถ้วย',
                    'กระเทียมสับ - 1 ช้อนโต๊ะ',
                    'รากผักชีทุบ - 3 ราก',
                    'พริกไทยป่น - 1 ช้อนชา',
                    'ซีอิ๊วขาว - 2 ช้อนโต๊ะ',
                    'น้ำมันหอย - 1 ช้อนโต๊ะ',
                    'เกลือป่น - 1/4 ช้อนชา'
                ],
                steps: [
                    'ผสมหมูสับกับกระเทียม พริกไทย ซีอิ๊วขาว 1 ช้อนโต๊ะ',
                    'นวดให้เข้ากัน หมักไว้ 10 นาที',
                    'ต้มน้ำซุปให้เดือด',
                    'ปั้นหมูสับเป็นก้อนกลม ใส่ลงต้มทีละลูก',
                    'รอให้ลูกชิ้นลอยขึ้น ต้มต่อ 3 นาที',
                    'ใส่เห็ดหอม เต้าหู้ วุ้นเส้น',
                    'ใส่ผักกาดขาว ต้มจนผักสุก',
                    'ปรุงรสด้วยซีอิ๊วขาว น้ำมันหอย เกลือ',
                    'โรยต้นหอม ผักชี กระเทียมเจียว เสิร์ฟ'
                ],
                warnings: {
                    diabetes: '✅ เหมาะสม - ไม่มีน้ำตาล คาร์บต่ำ',
                    hypertension: '⚠️ ลดซีอิ๊วขาวและน้ำมันหอย',
                    cholesterol: '⚠️ ใช้หมูสับเนื้อแดง ไม่ใส่มันหมู',
                    gout: '⚠️ ระวังเห็ดหอม อาจใช้เห็ดฟางแทน'
                }
            },
            'ผัดกะเพราหมูสับ': {
                calories: '280-350',
                price: '45-60',
                time: '10 นาที',
                tasteClass: 'taste-strong',
                tasteText: '🌶️ รสจัดจ้าน เผ็ดร้อน',
                mainIngredients: [
                    'หมูสับ - 250 กรัม',
                    'ใบกะเพราแดง - 2 กำมือ',
                    'ถั่วฝักยาวหั่น - 100 กรัม',
                    'พริกชี้ฟ้าหั่น - 2 เม็ด (สำหรับสีสัน)'
                ],
                seasonings: [
                    'น้ำมันพืช - 3 ช้อนโต๊ะ',
                    'กระเทียมสับหยาบ - 6 กลีบ',
                    'พริกขี้หนูสดสับหยาบ - 5-15 เม็ด (ตามชอบ)',
                    'น้ำปลา - 1.5 ช้อนโต๊ะ',
                    'ซีอิ๊วดำหวาน - 1 ช้อนโต๊ะ',
                    'ซีอิ๊วขาว - 1/2 ช้อนโต๊ะ',
                    'น้ำตาลทราย - 1 ช้อนชา',
                    'น้ำสะอาด - 3 ช้อนโต๊ะ'
                ],
                steps: [
                    'ตั้งกระทะไฟแรงมาก รอให้ร้อนจัด',
                    'ใส่น้ำมัน รอให้ร้อนจนเห็นควัน',
                    'ใส่กระเทียมและพริก ผัดเร็วๆ 10 วินาที',
                    'ใส่หมูสับ ใช้ตะหลิวกดแบนๆ ผัดให้สุกและกรอบ',
                    'ใส่ถั่วฝักยาว ผัดให้สุก',
                    'เขยกระทะ ใส่เครื่องปรุงทั้งหมด',
                    'ใส่น้ำ ผัดให้ซอสเคลือบเนื้อหมู',
                    'ใส่พริกชี้ฟ้า ผัดแป๊บเดียว',
                    'ปิดไฟ ใส่ใบกะเพรา คลุกเร็วๆ เสิร์ฟทันที'
                ],
                warnings: {
                    diabetes: '⚠️ ลดน้ำตาล ระวังกินกับข้าวมาก',
                    hypertension: '❌ ไม่เหมาะ - เค็มและมันมาก',
                    cholesterol: '⚠️ ใช้หมูเนื้อแดง ลดน้ำมัน',
                    gout: '⚠️ หมูมีพิวรีนปานกลาง กินแต่พอดี'
                }
            },
            'ไก่ผัดเม็ดมะม่วงหิมพานต์': {
                calories: '320-380',
                price: '100-120',
                time: '20 นาที',
                tasteClass: 'taste-mild',
                tasteText: '😊 รสหวานนัว กลมกล่อม',
                mainIngredients: [
                    'เนื้ออกไก่หั่นสี่เหลี่ยม - 300 กรัม',
                    'เม็ดมะม่วงหิมพานต์คั่ว - 150 กรัม',
                    'พริกหยวก 3 สี หั่น - 100 กรัม',
                    'หอมใหญ่หั่นชิ้น - 1/2 หัว',
                    'ต้นหอมหั่นท่อน - 2 ต้น'
                ],
                seasonings: [
                    'สำหรับหมักไก่:',
                    '- ไข่ขาว - 1 ฟอง',
                    '- แป้งข้าวโพด - 2 ช้อนโต๊ะ',
                    '- เกลือ - 1/2 ช้อนชา',
                    'สำหรับผัด:',
                    '- น้ำมันพืช - 3 ช้อนโต๊ะ',
                    '- กระเทียมสับ - 3 กลีบ',
                    '- น้ำพริกเผา - 2 ช้อนโต๊ะ',
                    '- ซอสหอยนางรม - 1.5 ช้อนโต๊ะ',
                    '- ซีอิ๊วขาว - 1 ช้อนโต๊ะ',
                    '- น้ำตาลทราย - 2 ช้อนชา',
                    '- น้ำซุปไก่ - 4 ช้อนโต๊ะ'
                ],
                steps: [
                    'หมักไก่กับไข่ขาว แป้ง เกลือ 15 นาที',
                    'คั่วเม็ดมะม่วงในกระทะแห้งจนหอม พักไว้',
                    'ตั้งกระทะใส่น้ำมัน 2 ช้อนโต๊ะ',
                    'ผัดไก่จนสุกและเหลือง ตักขึ้นพัก',
                    'ใส่น้ำมันที่เหลือ ผัดกระเทียมให้หอม',
                    'ใส่น้ำพริกเผา ผัดจนหอม',
                    'ใส่ไก่กลับลง ใส่หอมใหญ่ พริกหยวก',
                    'ใส่เครื่องปรุง ผัดให้เข้ากัน',
                    'ใส่น้ำซุป ผัดจนข้นเหนียว',
                    'ใส่เม็ดมะม่วง ต้นหอม คลุกเบาๆ เสิร์ฟ'
                ],
                warnings: {
                    diabetes: '❌ ไม่เหมาะ - น้ำตาลสูง แป้งเยอะ',
                    hypertension: '⚠️ ลดซอสหอยนางรม ไม่ใส่เกลือ',
                    cholesterol: '⚠️ เม็ดมะม่วงมีไขมันดีแต่แคลอรี่สูง',
                    gout: '✅ ปลอดภัย - ไก่และถั่วพิวรีนต่ำ'
                }
            },
            'ต้มยำกุ้งน้ำข้น': {
                calories: '180-220',
                price: '100-150',
                time: '20 นาที',
                tasteClass: 'taste-strong',
                tasteText: '🌶️ รสเข้มข้น เปรี้ยวเผ็ดมัน',
                mainIngredients: [
                    'กุ้งแม่น้ำขนาดกลาง - 300 กรัม',
                    'เห็ดฟางผ่าครึ่ง - 150 กรัม',
                    'นมสดข้นจืด - 3 ช้อนโต๊ะ',
                    'มะเขือเทศราชินี - 5 ลูก'
                ],
                seasonings: [
                    'น้ำซุป - 2 ถ้วย',
                    'ตะไคร้ทุบหั่น - 2 ต้น',
                    'ข่าหั่นบาง - 5 แว่น',
                    'ใบมะกรูด - 4 ใบ',
                    'พริกขี้หนูสดทุบ - 10 เม็ด',
                    'น้ำพริกเผา - 3 ช้อนโต๊ะ',
                    'น้ำปลา - 2 ช้อนโต๊ะ',
                    'น้ำมะนาว - 3 ช้อนโต๊ะ'
                ],
                steps: [
                    'ล้างกุ้ง ผ่าหลังดึงเส้นดำออก',
                    'ต้มน้ำใส่ตะไคร้ ข่า ใบมะกรูด',
                    'ใส่เห็ดฟาง ต้ม 2 นาที',
                    'ใส่น้ำพริกเผา คนให้ละลาย',
                    'ใส่กุ้ง ต้มจนกุ้งสุกพอดี',
                    'ใส่มะเขือเทศ ต้มอีก 1 นาที',
                    'ปิดไฟ ใส่นมข้นจืด คนเบาๆ',
                    'ใส่พริกขี้หนูทุบ น้ำปลา น้ำมะนาว',
                    'ชิมรส โรยผักชี เสิร์ฟร้อนๆ'
                ],
                warnings: {
                    diabetes: '⚠️ ระวังน้ำพริกเผาที่มีน้ำตาล',
                    hypertension: '⚠️ เค็มมาก ลดน้ำปลาและน้ำพริกเผา',
                    cholesterol: '❌ กุ้งมีคอเลสเตอรอลสูงมาก',
                    gout: '❌ ห้ามเด็ดขาด - กุ้งมีพิวรีนสูงมาก'
                }
            },
            'ผักบุ้งไฟแดง': {
                calories: '90-120',
                price: '30-40',
                time: '5 นาที',
                tasteClass: 'taste-mild',
                tasteText: '😊 รสกลมกล่อม เค็มหวานนิดๆ',
                mainIngredients: [
                    'ผักบุ้งไทยเด็ดเป็นท่อน - 300 กรัม',
                    'พริกแดงหั่นเฉียง - 2 เม็ด'
                ],
                seasonings: [
                    'น้ำมันพืช - 2-3 ช้อนโต๊ะ',
                    'กระเทียมทุบ - 4 กลีบ',
                    'เต้าเจี้ยว - 1.5 ช้อนโต๊ะ',
                    'ซีอิ๊วขาว - 1 ช้อนชา',
                    'น้ำตาลทราย - 1 ช้อนชา',
                    'น้ำเปล่า - 2 ช้อนโต๊ะ'
                ],
                steps: [
                    'เตรียมเครื่องปรุงทั้งหมดให้พร้อม',
                    'ตั้งกระทะไฟแรงสุด รอจนร้อนจัด',
                    'ใส่น้ำมัน รอจนเห็นควัน',
                    'ใส่กระเทียม ผัด 3 วินาที',
                    'ใส่ผักบุ้งทั้งหมด ผัดเร็วๆ',
                    'ใส่เต้าเจี้ยว ซีอิ๊ว น้ำตาล',
                    'ใส่น้ำ ผัดให้ทั่วไม่เกิน 30 วินาที',
                    'ใส่พริกแดง ผัดอีก 10 วินาที',
                    'ตักใส่จาน เสิร์ฟร้อนๆ ทันที'
                ],
                warnings: {
                    diabetes: '✅ ดีมาก - ผักมีไฟเบอร์สูง คาร์บต่ำ',
                    hypertension: '⚠️ ลดเต้าเจี้ยวและซีอิ๊ว',
                    cholesterol: '✅ ดี - ไม่มีคอเลสเตอรอล',
                    gout: '✅ ปลอดภัย - ผักมีพิวรีนต่ำมาก'
                }
            },
            'ไข่เจียวหมูสับ': {
                calories: '250-300',
                price: '35-45',
                time: '10 นาที',
                tasteClass: 'taste-mild',
                tasteText: '😊 รสเค็มนิดๆ หอมมัน',
                mainIngredients: [
                    'ไข่ไก่ - 3 ฟอง',
                    'หมูสับ - 100 กรัม',
                    'หอมแดงซอย - 2 หัว',
                    'ต้นหอมซอย - 1 ต้น'
                ],
                seasonings: [
                    'น้ำมันพืชสำหรับทอด - 1/2 ถ้วย',
                    'ซีอิ๊วขาว - 1 ช้อนโต๊ะ',
                    'น้ำปลา - 1 ช้อนชา',
                    'พริกไทยป่น - 1/4 ช้อนชา',
                    'น้ำมะนาว - 1 ช้อนโต๊ะ (ใส่ตอนตี)'
                ],
                steps: [
                    'ผัดหมูสับในน้ำมันเล็กน้อยจนสุก พักไว้',
                    'ตีไข่ในชาม ใส่ซีอิ๊ว น้ำปลา พริกไทย',
                    'ใส่น้ำมะนาว ตีให้ฟูเบาๆ',
                    'ใส่หมูสับ หอมแดง ต้นหอม คนเบาๆ',
                    'ตั้งกระทะใส่น้ำมัน รอให้ร้อนจัด',
                    'เทไข่ลงทอด รอให้ด้านล่างเซ็ต',
                    'ใช้ตะหลิวรูดไข่จากขอบเข้าตรงกลาง',
                    'พลิกไข่เจียว ทอดอีกด้านจนเหลืองกรอบ',
                    'ตักขึ้นพักให้สะเด็ดน้ำมัน เสิร์ฟร้อนๆ'
                ],
                warnings: {
                    diabetes: '⚠️ มีน้ำมันมาก ควรซับน้ำมันก่อนกิน',
                    hypertension: '⚠️ ลดเกลือ กินแต่พอดี',
                    cholesterol: '❌ ไข่แดงมีคอเลสเตอรอลสูง',
                    gout: '✅ ปลอดภัย - ไข่มีพิวรีนต่ำ'
                }
            },
            'แกงจืดผักกาดขาวหมูสับ': {
                calories: '100-130',
                price: '35-45',
                time: '15 นาที',
                tasteClass: 'taste-mild',
                tasteText: '😊 รสชาติใสๆ อร่อยธรรมชาติ',
                mainIngredients: [
                    'หมูสับ - 150 กรัม',
                    'ผักกาดขาวหั่นท่อน - 200 กรัม',
                    'เต้าหู้ขาว - 4 ชิ้น',
                    'ขึ้นฉ่ายหั่น - 2 ต้น'
                ],
                seasonings: [
                    'น้ำซุป - 3 ถ้วย',
                    'กระเทียมทุบ - 3 กลีบ',
                    'รากผักชีทุบ - 2 ราก',
                    'พริกไทยเม็ด - 1 ช้อนชา',
                    'ซีอิ๊วขาว - 1 ช้อนโต๊ะ',
                    'เกลือ - 1/2 ช้อนชา'
                ],
                steps: [
                    'โขลกกระเทียม รากผักชี พริกไทยรวมกัน',
                    'ผสมเครื่องที่โขลกกับหมูสับ',
                    'ใส่ซีอิ๊วขาว 1 ช้อนชา นวดให้เข้ากัน',
                    'ต้มน้ำซุปให้เดือด',
                    'ปั้นหมูสับเป็นก้อน ใส่ลงต้มทีละลูก',
                    'รอจนลูกชิ้นลอยขึ้นหมด',
                    'ใส่เต้าหู้ ต้มอีก 2 นาที',
                    'ใส่ผักกาดขาว ขึ้นฉ่าย ต้มจนผักสุก',
                    'ปรุงรสด้วยซีอิ๊ว เกลือ เสิร์ฟร้อนๆ'
                ],
                warnings: {
                    diabetes: '✅ ดีมาก - คาร์บต่ำ ไฟเบอร์สูง',
                    hypertension: '⚠️ ลดเกลือและซีอิ๊ว',
                    cholesterol: '✅ ดี - ใช้หมูเนื้อแดง',
                    gout: '✅ ปลอดภัย - ผักพิวรีนต่ำ'
                }
            }
        };

        function generateMenu() {
            // เก็บค่าวัตถุดิบ
            const ingredients = [];
            for (let i = 1; i <= 5; i++) {
                const ingredient = document.getElementById(`ingredient${i}`).value.trim();
                if (ingredient) {
                    ingredients.push(ingredient);
                }
            }

            if (ingredients.length < 2) {
                alert('กรุณากรอกวัตถุดิบอย่างน้อย 2 รายการค่ะ 😊');
                return;
            }

            // แสดง loading
            document.getElementById('loading').classList.add('active');
            document.getElementById('menuResults').innerHTML = '';
            document.getElementById('healthWarning').style.display = 'none';

            // จำลองการประมวลผล
            setTimeout(() => {
                // สร้างเมนูตามวัตถุดิบที่กรอก
                const menus = createRealMenus(ingredients);
                
                // แสดงผล
                document.getElementById('loading').classList.remove('active');
                document.getElementById('menuResults').innerHTML = menus.html;
                
                // แสดงข้อควรระวังถ้ามี
                document.getElementById('healthWarning').style.display = 'block';
            }, 2000);
        }

        function createRealMenus(ingredients) {
            let possibleMenus = { soup: [], dry: [] };
            let warnings = new Set();
            
            // หาเมนูที่เป็นไปได้จากวัตถุดิบ
            ingredients.forEach(ingredient => {
                const key = findIngredientKey(ingredient);
                if (key && realMenuDatabase[key]) {
                    if (realMenuDatabase[key].soup) {
                        realMenuDatabase[key].soup.forEach(menu => {
                            possibleMenus.soup.push({
                                ...menu,
                                mainIngredient: ingredient,
                                key: key
                            });
                        });
                    }
                    if (realMenuDatabase[key].dry) {
                        realMenuDatabase[key].dry.forEach(menu => {
                            possibleMenus.dry.push({
                                ...menu,
                                mainIngredient: ingredient,
                                key: key
                            });
                        });
                    }
                    if (realMenuDatabase[key].warning) {
                        realMenuDatabase[key].warning.split(',').forEach(w => warnings.add(w));
                    }
                }
            });

            // ถ้าไม่มีเมนูในฐานข้อมูล สร้างเมนูทั่วไป
            if (possibleMenus.soup.length === 0) {
                possibleMenus.soup.push({
                    name: `ต้มจืด${ingredients[0]}ใส่${ingredients[1] || 'ผัก'}`,
                    mainIngredient: ingredients[0],
                    spicy: false
                });
            }
            if (possibleMenus.dry.length === 0) {
                possibleMenus.dry.push({
                    name: `${ingredients[0]}ผัด${ingredients[1] || 'น้ำมันหอย'}`,
                    mainIngredient: ingredients[0],
                    spicy: false
                });
            }

            // เลือกเมนูที่ผสมระหว่างรสจืดและรสจัด
            let selectedSoup, selectedDry;
            
            const spicySoups = possibleMenus.soup.filter(m => m.spicy);
            const mildSoups = possibleMenus.soup.filter(m => !m.spicy);
            const spicyDrys = possibleMenus.dry.filter(m => m.spicy);
            const mildDrys = possibleMenus.dry.filter(m => !m.spicy);

            // พยายามเลือก 1 จืด 1 จัด
            if (Math.random() > 0.5) {
                selectedSoup = spicySoups.length > 0 ? 
                    spicySoups[Math.floor(Math.random() * spicySoups.length)] :
                    possibleMenus.soup[Math.floor(Math.random() * possibleMenus.soup.length)];
                selectedDry = mildDrys.length > 0 ?
                    mildDrys[Math.floor(Math.random() * mildDrys.length)] :
                    possibleMenus.dry[Math.floor(Math.random() * possibleMenus.dry.length)];
            } else {
                selectedSoup = mildSoups.length > 0 ?
                    mildSoups[Math.floor(Math.random() * mildSoups.length)] :
                    possibleMenus.soup[Math.floor(Math.random() * possibleMenus.soup.length)];
                selectedDry = spicyDrys.length > 0 ?
                    spicyDrys[Math.floor(Math.random() * spicyDrys.length)] :
                    possibleMenus.dry[Math.floor(Math.random() * possibleMenus.dry.length)];
            }

            // สร้าง HTML
            const menuCards = [];
            menuCards.push(createRealMenuCard(selectedSoup, 'soup', ingredients));
            menuCards.push(createRealMenuCard(selectedDry, 'dry', ingredients));

            return {
                html: menuCards.join(''),
                hasWarning: true // แสดงข้อควรระวังเสมอ
            };
        }

        function findIngredientKey(ingredient) {
            const normalized = ingredient.toLowerCase();
            for (let key in realMenuDatabase) {
                if (normalized.includes(key.toLowerCase()) || key.toLowerCase().includes(normalized)) {
                    return key;
                }
            }
            return null;
        }

        function createRealMenuCard(menuData, type, allIngredients) {
            const typeText = type === 'soup' ? '🍲 อาหารประเภทน้ำ' : '🍳 อาหารประเภทแห้ง';
            
            // ดึงสูตรที่ถูกต้องจากฐานข้อมูล
            let recipe = correctRecipes[menuData.name];
            
            // ถ้าไม่มีสูตรในฐานข้อมูล ใช้สูตรพื้นฐาน
            if (!recipe) {
                recipe = getBasicRecipe(menuData.name, allIngredients);
            }
            
            // สร้างส่วนข้อควรระวังสำหรับแต่ละโรค
            let warningsHtml = '';
            if (recipe.warnings) {
                warningsHtml = `
                    <div class="menu-warnings">
                        <h4>⚠️ ข้อควรระวังสำหรับผู้ป่วย</h4>
                        <ul>
                            ${recipe.warnings.diabetes ? `<li><strong>🩺 เบาหวาน:</strong> ${recipe.warnings.diabetes}</li>` : ''}
                            ${recipe.warnings.hypertension ? `<li><strong>💓 ความดันสูง:</strong> ${recipe.warnings.hypertension}</li>` : ''}
                            ${recipe.warnings.cholesterol ? `<li><strong>🧈 ไขมันสูง:</strong> ${recipe.warnings.cholesterol}</li>` : ''}
                            ${recipe.warnings.gout ? `<li><strong>🦴 เก๊าท์:</strong> ${recipe.warnings.gout}</li>` : ''}
                        </ul>
                    </div>
                `;
            }
            
            return `
                <div class="menu-card ${type}">
                    <div class="menu-card-header">
                        ${typeText}
                    </div>
                    <div class="menu-card-body">
                        <div class="menu-name">
                            ${menuData.name}
                            <span class="calories-badge">🔥 ${recipe.calories} แคลอรี่</span>
                        </div>
                        <span class="taste-indicator ${recipe.tasteClass}">${recipe.tasteText}</span>
                        <div class="price-estimate">💰 ประมาณ ${recipe.price} บาท</div>
                        
                        <div class="menu-ingredients">
                            <h4>📝 วัตถุดิบหลัก (สำหรับ 2-3 ที่)</h4>
                            <ul>
                                ${recipe.mainIngredients.map(ing => `<li>${ing}</li>`).join('')}
                            </ul>
                        </div>

                        <div class="menu-ingredients" style="background: linear-gradient(135deg, #FFF0F5, #FFF5F9);">
                            <h4>🥄 เครื่องปรุง</h4>
                            <ul>
                                ${recipe.seasonings.map(s => `<li>${s}</li>`).join('')}
                            </ul>
                        </div>

                        <div class="cooking-method">
                            <h4>👩‍🍳 วิธีทำ</h4>
                            <ol>
                                ${recipe.steps.map(step => `<li>${step}</li>`).join('')}
                            </ol>
                        </div>

                        ${warningsHtml}

                        <div class="nutrition-info">
                            <div class="nutrition-item">
                                <div class="label">⏰ เวลา</div>
                                <div class="value">${recipe.time}</div>
                            </div>
                            <div class="nutrition-item">
                                <div class="label">👥 สำหรับ</div>
                                <div class="value">2-3 คน</div>
                            </div>
                            <div class="nutrition-item">
                                <div class="label">🔥 ระดับ</div>
                                <div class="value">ง่าย</div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        function getBasicRecipe(menuName, ingredients) {
            // สูตรพื้นฐานสำหรับเมนูที่ไม่มีในฐานข้อมูล
            return {
                calories: '150-200',
                price: '50-70',
                time: '15-20 นาที',
                tasteClass: 'taste-mild',
                tasteText: '😊 รสกลมกล่อม',
                mainIngredients: ingredients.slice(0, 3).map((ing, idx) => 
                    `${ing} - ${idx === 0 ? '200 กรัม' : '100 กรัม'}`
                ),
                seasonings: [
                    'น้ำมัน - 2 ช้อนโต๊ะ',
                    'กระเทียมสับ - 3 กลีบ',
                    'ซีอิ๊วขาว - 1 ช้อนโต๊ะ',
                    'น้ำมันหอย - 1 ช้อนโต๊ะ',
                    'น้ำตาล - 1/2 ช้อนชา'
                ],
                steps: [
                    'เตรียมวัตถุดิบให้พร้อม',
                    'ตั้งกระทะใส่น้ำมัน',
                    'ผัดกระเทียมให้หอม',
                    `ใส่${ingredients[0]} ผัดจนสุก`,
                    'ใส่ผักหรือวัตถุดิบอื่นๆ',
                    'ปรุงรสตามชอบ',
                    'ผัดให้เข้ากัน เสิร์ฟ'
                ],
                warnings: {
                    diabetes: 'ควรลดน้ำตาล',
                    hypertension: 'ลดเครื่องปรุงรสเค็ม',
                    cholesterol: 'ใช้น้ำมันพืชที่ดีต่อสุขภาพ',
                    gout: 'ตรวจสอบวัตถุดิบที่ใช้'
                }
            };
        }

        // ฟังก์ชันสำหรับ Enter key
        document.addEventListener('DOMContentLoaded', function() {
            const inputs = document.querySelectorAll('.ingredient-input input');
            inputs.forEach(input => {
                input.addEventListener('keypress', function(e) {
                    if (e.key === 'Enter') {
                        generateMenu();
                    }
                });
            });
        });
    </script>
</body>
</html>
