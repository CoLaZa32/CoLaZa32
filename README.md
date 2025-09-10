
### 👋 สวัสดีครับ ผม CoLaZa32
#### Full-stack Developer | Google Community Developer

ยินดีต้อนรับสู่โปรไฟล์ของผม! ผมเป็นนักพัฒนา Full-stack ที่มีความเชี่ยวชาญในการสร้างเว็บไซต์และแอปพลิเคชันที่ทำงานได้อย่างมีประสิทธิภาพทั้งในแบบ Full-stack และ Hybrid developer

---

### 🚀 ประสบการณ์และความเชี่ยวชาญ

* **Full-stack Development:** ออกแบบและพัฒนาทั้งฝั่ง Front-end และ Back-end
* **Hybrid Development:** สร้างแอปพลิเคชันบนแพลตฟอร์มต่างๆ ด้วยเทคโนโลยีแบบ Hybrid
* **Freelance:** ให้บริการพัฒนาเว็บไซต์และแอปพลิเคชันผ่าน Fastwork Thailand
* **Cybersecurity:** มีความเชี่ยวชาญด้านความมั่นคงปลอดภัยไซเบอร์ (Red Team) จากหลักสูตรขั้นสูงของ สกมช.

---

### 🛠️ ทักษะและเทคโนโลยี

| Front-end | Back-end | Database | Cloud & Tools | Cybersecurity |
|---|---|---|---|---|
| HTML, CSS, JavaScript | Python, Node.js | MySQL, PostgreSQL | Google Cloud, Docker | Network Security, Pentesting |
| React, Vue.js | Express.js, Django | MongoDB | Git, GitHub | Cybersecurity Forensics |

---

### 🏆 ใบรับรองที่ได้รับ

* **หลักสูตร Cybersecurity ขั้นสูง (สกมช.)**
* **หลักสูตร AI Essentials**

---

### 🌐 ติดต่อและติดตามผม

* **LinkedIn:** [ใส่ลิงก์โปรไฟล์ LinkedIn ของคุณ]
* **Fastwork:** [ใส่ลิงก์โปรไฟล์ Fastwork ของคุณ]
* **Email:** [ใส่อีเมลของคุณ]


## 📊 สถิติ GitHub ของผม

![สถิติ GitHub ของ CoLaZa32](https://github-readme-stats.vercel.app/api?username=CoLaZa32&show_icons=true&theme=radical)

![ภาษาโปรแกรมที่ใช้](https://github-readme-stats.vercel.app/api/top-langs/?username=CoLaZa32&layout=compact&theme=radical)

![ข้อมูลเพิ่มเติม](https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=CoLaZa32&theme=radical)

### 🏆 achievement
- ⭐ ได้รับดาวทั้งหมด: {total_stars}
- 🍴 Fork ทั้งหมด: {total_forks}
- 📦 Repository สาธารณะ: {len(repos_data)}

## 🛠️ ทักษะและเทคโนโลยี

- **ภาษาโปรแกรมที่ถนัด:** {', '.join([lang[0] for lang in top_languages])}
- **เว็บ Development:** HTML, CSS, React, Node.js
- **ฐานข้อมูล:** MySQL, MongoDB
- **เครื่องมือ:** Git, Docker, VS Code, Linux

## 📫 ติดต่อผม

- อีเมล: [{email}](mailto:{email})
- LinkedIn: [CoLaZa32](https://linkedin.com/in/colaza32)
- Twitter: [@CoLaZa32](https://twitter.com/colaza32)

## 🌱 สิ่งที่ผมกำลังเรียนรู้อยู่ตอนนี้

- Machine Learning และ AI
- การพัฒนาแอปพลิเคชันบน Cloud
- เทคโนโลยี Blockchain

## ⚡ ข้อเท็จจริงน่าสนใจ

ผมรักการเขียนโค้ดและการแก้ปัญหา นอกจากนี้ยังสนุกกับการเล่นเกมและฟังเพลงในเวลาว่าง!

---

⏳ อัปเดตล่าสุด: {datetime.now().strftime("%Y-%m-%d %H:%M:%S")}

ขอบคุณที่แวะมาเยี่ยมชมโปรไฟล์ของผม! ไม่ว่าจะเป็นเรื่อง collaboration หรือ只是想คุยกัน ทักมาได้เสมอนะครับ 😊
"""
    return readme_content

if __name__ == "__main__":
    username = "CoLaZa32"
    token = os.getenv('GITHUB_TOKEN')
    
    user_data, repos_data = get_github_stats(username, token)
    readme = generate_readme_content(user_data, repos_data)
    
    with open("README.md", "w") as f:
        f.write(readme)
    
    print("README.md created successfully!")
