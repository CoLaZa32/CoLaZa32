import requests
import os
from datetime import datetime

def get_github_stats(username, token=None):
    """ดึงข้อมูลจาก GitHub API"""
    headers = {}
    if token:
        headers['Authorization'] = f'token {token}'
    
    # ข้อมูลผู้ใช้
    user_url = f"https://api.github.com/users/{username}"
    user_response = requests.get(user_url, headers=headers)
    user_data = user_response.json()
    
    # ข้อมูล repository
    repos_url = f"https://api.github.com/users/{username}/repos?per_page=100"
    repos_response = requests.get(repos_url, headers=headers)
    repos_data = repos_response.json()
    
    return user_data, repos_data

def generate_readme_content(user_data, repos_data):
    """สร้างเนื้อหา README"""
    name = user_data.get('name', user_data.get('login', 'CoLaZa32'))
    bio = user_data.get('bio', 'นักพัฒนาที่สนใจในเทคโนโลยีใหม่ๆ')
    email = user_data.get('email', 'colaza32@email.com')
    avatar_url = user_data.get('avatar_url', '')
    
    # นับ stars และ forks
    total_stars = sum(repo['stargazers_count'] for repo in repos_data)
    total_forks = sum(repo['forks_count'] for repo in repos_data)
    
    # หาภาษาที่ใช้บ่อย
    languages = {}
    for repo in repos_data:
        if repo['language']:
            languages[repo['language']] = languages.get(repo['language'], 0) + 1
    
    top_languages = sorted(languages.items(), key=lambda x: x[1], reverse=True)[:5]
    
    readme_content = f"""# สวัสดี! ผมคือ {name} 👋

{bio}

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