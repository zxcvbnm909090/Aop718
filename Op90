import zipfile
import os

# إنشاء ملف ZIP
with zipfile.ZipFile('islamic_bot.zip', 'w', zipfile.ZIP_DEFLATED) as zipf:
    
    # إضافة ملف requirements.txt (تصحيح اسم المكتبة)
    requirements = """python-telegram-bot==20.7
apscheduler==3.10.4
python-dotenv==1.0.0
"""
    zipf.writestr('requirements.txt', requirements)
    
    # إضافة ملف .env (تصحيح التنسيق)
    env_file = """# Bot Token from @BotFather - قم بتغييره إلى التوكن الخاص بك
BOT_TOKEN=YOUR_BOT_TOKEN_HERE

# Admin User IDs (comma-separated) - أيدي المشرفين
ADMIN_IDS=123456789,987654321
"""
    zipf.writestr('.env', env_file)
    
    # إضافة ملف config.py
    config = '''import os
from dotenv import load_dotenv

load_dotenv()

# Bot Configuration
BOT_TOKEN = os.getenv('BOT_TOKEN', '8269653015:AAGybShdzQSmYMRcL860_iXyg4NSSKupYqg')
ADMIN_IDS = [int(id) for id in os.getenv('ADMIN_IDS', '').split(',') if id]

# Time Configuration
MORNING_ADHKAR_TIME = "06:00"
EVENING_ADHKAR_TIME = "18:00"

# Database Configuration
DATABASE_NAME = "islamic_bot.db"
'''
    zipf.writestr('config.py', config)
    
    # إضافة ملف constants.py
    constants = '''# Welcome Message
WELCOME_MESSAGE = """
<b>🌸 بسم الله الرحمن الرحيم 🌸</b>

أهلاً وسهلاً بك في بوت الأذكار والأدعية الإسلامي 🕌

هذا البوت يساعدك على:
• أذكار الصباح والمساء
• أذكار ما بعد الصلاة
• أذكار النوم
• أدعية من القرآن الكريم
• التسبيح الرقمي
• معرفة فضائل الذكر

اختر من القائمة أدناه ما تريد 👇
"""

# Adhkar Data
MORNING_ADHKAR = [
    {
        "title": "آية الكرسي",
        "arabic": "اللَّهُ لَا إِلَٰهَ إِلَّا هُوَ الْحَيُّ الْقَيُّومُ ۚ لَا تَأْخُذُهُ سِنَةٌ وَلَا نَوْمٌ ۚ لَّهُ مَا فِي السَّمَاوَاتِ وَمَا فِي الْأَرْضِ ۗ مَن ذَا الَّذِي يَشْفَعُ عِندَهُ إِلَّا بِإِذْنِهِ ۚ يَعْلَمُ مَا بَيْنَ أَيْدِيهِمْ وَمَا خَلْفَهُمْ ۖ وَلَا يُحِيطُونَ بِشَيْءٍ مِّنْ عِلْمِهِ إِلَّا بِمَا شَاءَ ۚ وَسِعَ كُرْسِيُّهُ السَّمَاوَاتِ وَالْأَرْضَ ۖ وَلَا يَئُودُهُ حِفْظُهُمَا ۚ وَهُوَ الْعَلِيُّ الْعَظِيمُ",
        "translation": "الله لا إله إلا هو الحي القيوم...",
        "count": 1,
        "virtue": "من قرأها حين يصبح أجير من الشياطين حتى يمسي"
    },
    {
        "title": "سورة الإخلاص",
        "arabic": "قُلْ هُوَ اللَّهُ أَحَدٌ • اللَّهُ الصَّمَدُ • لَمْ يَلِدْ وَلَمْ يُولَدْ • وَلَمْ يَكُن لَّهُ كُفُوًا أَحَدٌ",
        "translation": "قل هو الله أحد...",
        "count": 3,
        "virtue": "تعدل ثلث القرآن"
    },
    {
        "title": "سورة الفلق",
        "arabic": "قُلْ أَعُوذُ بِرَبِّ الْفَلَقِ • مِن شَرِّ مَا خَلَقَ • وَمِن شَرِّ غَاسِقٍ إِذَا وَقَبَ • وَمِن شَرِّ النَّفَّاثَاتِ فِي الْعُقَدِ • وَمِن شَرِّ حَاسِدٍ إِذَا حَسَدَ",
        "translation": "قل أعوذ برب الفلق...",
        "count": 3,
        "virtue": "تحصنك من كل شر"
    },
    {
        "title": "سورة الناس",
        "arabic": "قُلْ أَعُوذُ بِرَبِّ النَّاسِ • مَلِكِ النَّاسِ • إِلَٰهِ النَّاسِ • مِن شَرِّ الْوَسْوَاسِ الْخَنَّاسِ • الَّذِي يُوَسْوِسُ فِي صُدُورِ النَّاسِ • مِنَ الْجِنَّةِ وَالنَّاسِ",
        "translation": "قل أعوذ برب الناس...",
        "count": 3,
        "virtue": "تحصنك من الوسواس"
    },
    {
        "title": "أصبحنا وأصبح الملك لله",
        "arabic": "أَصْبَحْنَا وَأَصْبَحَ الْمُلْكُ لِلَّهِ، وَالْحَمْدُ لِلَّهِ، لا إِلَهَ إِلاَّ اللَّهُ وَحْدَهُ لا شَرِيكَ لَهُ، لَهُ الْمُلْكُ وَلَهُ الْحَمْدُ وَهُوَ عَلَى كُلِّ شَيْءٍ قَدِيرٌ",
        "translation": "أصبحنا وأصبح الملك لله...",
        "count": 1,
        "virtue": "من قالها حين يصبح كان عليه عهد من الله أن يعتقده من النار"
    },
    {
        "title": "اللهم بك أصبحنا",
        "arabic": "اللَّهُمَّ بِكَ أَصْبَحْنَا، وَبِكَ أَمْسَيْنَا، وَبِكَ نَحْيَا، وَبِكَ نَمُوتُ، وَإِلَيْكَ النُّشُورُ",
        "translation": "اللهم بك أصبحنا...",
        "count": 1,
        "virtue": "ذكر الصباح"
    }
]

EVENING_ADHKAR = [
    {
        "title": "آية الكرسي",
        "arabic": "اللَّهُ لَا إِلَٰهَ إِلَّا هُوَ الْحَيُّ الْقَيُّومُ ۚ لَا تَأْخُذُهُ سِنَةٌ وَلَا نَوْمٌ ۚ لَّهُ مَا فِي السَّمَاوَاتِ وَمَا فِي الْأَرْضِ ۗ مَن ذَا الَّذِي يَشْفَعُ عِندَهُ إِلَّا بِإِذْنِهِ ۚ يَعْلَمُ مَا بَيْنَ أَيْدِيهِمْ وَمَا خَلْفَهُمْ ۖ وَلَا يُحِيطُونَ بِشَيْءٍ مِّنْ عِلْمِهِ إِلَّا بِمَا شَاءَ ۚ وَسِعَ كُرْسِيُّهُ السَّمَاوَاتِ وَالْأَرْضَ ۖ وَلَا يَئُودُهُ حِفْظُهُمَا ۚ وَهُوَ الْعَلِيُّ الْعَظِيمُ",
        "translation": "الله لا إله إلا هو الحي القيوم...",
        "count": 1,
        "virtue": "من قرأها حين يمسي أجير من الشياطين حتى يصبح"
    },
    {
        "title": "المعوذات",
        "arabic": "قُلْ هُوَ اللَّهُ أَحَدٌ • قُلْ أَعُوذُ بِرَبِّ الْفَلَقِ • قُلْ أَعُوذُ بِرَبِّ النَّاسِ",
        "translation": "الإخلاص والفلق والناس",
        "count": 3,
        "virtue": "من قالها حين يمسي كفته من كل شيء"
    },
    {
        "title": "أمسينا وأمسى الملك لله",
        "arabic": "أَمْسَيْنَا وَأَمْسَى الْمُلْكُ لِلَّهِ، وَالْحَمْدُ لِلَّهِ، لا إِلَهَ إِلاَّ اللَّهُ وَحْدَهُ لا شَرِيكَ لَهُ",
        "translation": "أمسينا وأمسى الملك لله...",
        "count": 1,
        "virtue": "ذكر المساء"
    }
]

AFTER_PRAYER_ADHKAR = [
    {
        "title": "أستغفر الله",
        "arabic": "أَسْتَغْفِرُ اللَّهَ (ثلاثاً) اللَّهُمَّ أَنْتَ السَّلاَمُ وَمِنْكَ السَّلاَمُ، تَبَارَكْتَ يَا ذَا الْجَلاَلِ وَالإِكْرَامِ",
        "translation": "أستغفر الله...",
        "count": 3,
        "virtue": "يستغفر الله ثلاثاً بعد كل صلاة"
    },
    {
        "title": "آية الكرسي",
        "arabic": "اللَّهُ لَا إِلَٰهَ إِلَّا هُوَ الْحَيُّ الْقَيُّومُ...",
        "translation": "آية الكرسي",
        "count": 1,
        "virtue": "من قرأها دبر كل صلاة لم يمنعه من دخول الجنة إلا الموت"
    },
    {
        "title": "سبحان الله",
        "arabic": "سُبْحَانَ اللَّهِ (33 مرة) • الْحَمْدُ لِلَّهِ (33 مرة) • اللَّهُ أَكْبَرُ (33 مرة)",
        "translation": "سبحان الله، الحمد لله، الله أكبر",
        "count": 33,
        "virtue": "من قالها دبر كل صلاة غفرت له خطاياه وإن كانت مثل زبد البحر"
    }
]

SLEEP_ADHKAR = [
    {
        "title": "آية الكرسي",
        "arabic": "اللَّهُ لَا إِلَٰهَ إِلَّا هُوَ الْحَيُّ الْقَيُّومُ...",
        "translation": "آية الكرسي",
        "count": 1,
        "virtue": "من قرأها عند النوم لم يزل عليه من الله حافظ"
    },
    {
        "title": "المعوذات",
        "arabic": "قُلْ هُوَ اللَّهُ أَحَدٌ • قُلْ أَعُوذُ بِرَبِّ الْفَلَقِ • قُلْ أَعُوذُ بِرَبِّ النَّاسِ",
        "translation": "المعوذات",
        "count": 3,
        "virtue": "ينفث في كفيه ثم يمسح بهما جسده"
    },
    {
        "title": "اللهم باسمك أموت وأحيا",
        "arabic": "اللَّهُمَّ بِاسْمِكَ أَمُوتُ وَأَحْيَا",
        "translation": "اللهم باسمك أموت وأحيا",
        "count": 1,
        "virtue": "من قالها ثم نام قبض روحه ثم ردها إذا استيقظ"
    }
]

QURAN_DUAS = [
    {
        "title": "دعاء سورة البقرة",
        "arabic": "رَبَّنَا آتِنَا فِي الدُّنْيَا حَسَنَةً وَفِي الْآخِرَةِ حَسَنَةً وَقِنَا عَذَابَ النَّارِ",
        "translation": "ربنا آتنا في الدنيا حسنة...",
        "reference": "البقرة 201"
    },
    {
        "title": "دعاء سورة آل عمران",
        "arabic": "رَبَّنَا لَا تُزِغْ قُلُوبَنَا بَعْدَ إِذْ هَدَيْتَنَا وَهَبْ لَنَا مِن لَّدُنكَ رَحْمَةً ۚ إِنَّكَ أَنتَ الْوَهَّابُ",
        "translation": "ربنا لا تزغ قلوبنا بعد إذ هديتنا...",
        "reference": "آل عمران 8"
    },
    {
        "title": "دعاء سورة إبراهيم",
        "arabic": "رَبَّنَا اغْفِرْ لِي وَلِوَالِدَيَّ وَلِلْمُؤْمِنِينَ يَوْمَ يَقُومُ الْحِسَابُ",
        "translation": "ربنا اغفر لي ولوالدي...",
        "reference": "إبراهيم 41"
    }
]

VIRTUES = [
    {
        "title": "فضل ذكر الله",
        "content": "قال الله تعالى: {فَاذْكُرُونِي أَذْكُرْكُمْ وَاشْكُرُوا لِي وَلَا تَكْفُرُونِ} [البقرة:152]",
        "explanation": "من ذكر الله ذكره الله في الملأ الأعلى"
    },
    {
        "title": "فضل التسبيح",
        "content": "قال رسول الله ﷺ: 'كَلِمَتَانِ خَفِيفَتَانِ عَلَى اللِّسَانِ، ثَقِيلَتَانِ فِي الْمِيزَانِ، حَبِيبَتَانِ إِلَى الرَّحْمَنِ: سُبْحَانَ اللَّهِ وَبِحَمْدِهِ، سُبْحَانَ اللَّهِ الْعَظِيمِ'",
        "explanation": "كلمتان خفيفتان على اللسان ثقيلتان في الميزان"
    }
]

# Callback Data Constants
class CallbackData:
    # Main Menu
    MAIN_MENU = "main_menu"
    
    # Sections
    MORNING = "morning"
    EVENING = "evening"
    AFTER_PRAYER = "after_prayer"
    SLEEP = "sleep"
    QURAN_DUA = "quran_dua"
    TASBEEH = "tasbeeh"
    VIRTUES = "virtues"
    
    # Navigation
    NEXT = "next"
    PREVIOUS = "previous"
    BACK = "back"
    
    # Tasbeeh
    SUBHANALLAH = "subhanallah"
    ALHAMDULILLAH = "alhamdulillah"
    ALLAHU_AKBAR = "allahu_akbar"
    RESET_TASBEEH = "reset_tasbeeh"
'''
    zipf.writestr('constants.py', constants)
    
    # إضافة ملف database.py
    database = '''import sqlite3
import logging
from datetime import datetime
from config import DATABASE_NAME

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

class Database:
    def __init__(self):
        self.conn = None
        self.cursor = None
        self.init_database()
    
    def connect(self):
        """Create database connection"""
        self.conn = sqlite3.connect(DATABASE_NAME, check_same_thread=False)
        self.cursor = self.conn.cursor()
    
    def close(self):
        """Close database connection"""
        if self.conn:
            self.conn.close()
    
    def init_database(self):
        """Initialize database tables"""
        try:
            self.connect()
            
            # Users table
            self.cursor.execute('''
                CREATE TABLE IF NOT EXISTS users (
                    user_id INTEGER PRIMARY KEY,
                    username TEXT,
                    first_name TEXT,
                    last_name TEXT,
                    language_code TEXT,
                    is_active INTEGER DEFAULT 1,
                    joined_date TEXT,
                    last_active TEXT
                )
            ''')
            
            # Tasbeeh counts table
            self.cursor.execute('''
                CREATE TABLE IF NOT EXISTS tasbeeh_counts (
                    user_id INTEGER PRIMARY KEY,
                    subhanallah INTEGER DEFAULT 0,
                    alhamdulillah INTEGER DEFAULT 0,
                    allahu_akbar INTEGER DEFAULT 0,
                    total INTEGER DEFAULT 0,
                    last_updated TEXT,
                    FOREIGN KEY (user_id) REFERENCES users(user_id)
                )
            ''')
            
            # User settings table
            self.cursor.execute('''
                CREATE TABLE IF NOT EXISTS user_settings (
                    user_id INTEGER PRIMARY KEY,
                    receive_notifications INTEGER DEFAULT 1,
                    notification_time_morning TEXT DEFAULT '06:00',
                    notification_time_evening TEXT DEFAULT '18:00',
                    language TEXT DEFAULT 'ar',
                    FOREIGN KEY (user_id) REFERENCES users(user_id)
                )
            ''')
            
            # Broadcast messages table
            self.cursor.execute('''
                CREATE TABLE IF NOT EXISTS broadcast_messages (
                    id INTEGER PRIMARY KEY AUTOINCREMENT,
                    message_text TEXT,
                    sent_date TEXT,
                    total_sent INTEGER,
                    successful INTEGER,
                    failed INTEGER
                )
            ''')
            
            self.conn.commit()
            logger.info("Database initialized successfully")
            
        except Exception as e:
            logger.error(f"Database initialization error: {e}")
        finally:
            self.close()
    
    def add_user(self, user_id, username, first_name, last_name, language_code):
        """Add new user to database"""
        try:
            self.connect()
            now = datetime.now().isoformat()
            
            # Insert or ignore user
            self.cursor.execute('''
                INSERT OR IGNORE INTO users 
                (user_id, username, first_name, last_name, language_code, joined_date, last_active)
                VALUES (?, ?, ?, ?, ?, ?, ?)
            ''', (user_id, username, first_name, last_name, language_code, now, now))
            
            # Initialize tasbeeh counts
            self.cursor.execute('''
                INSERT OR IGNORE INTO tasbeeh_counts (user_id, last_updated)
                VALUES (?, ?)
            ''', (user_id, now))
            
            # Initialize user settings
            self.cursor.execute('''
                INSERT OR IGNORE INTO user_settings (user_id)
                VALUES (?)
            ''', (user_id,))
            
            self.conn.commit()
            logger.info(f"User {user_id} added successfully")
            
        except Exception as e:
            logger.error(f"Error adding user {user_id}: {e}")
        finally:
            self.close()
    
    def update_user_activity(self, user_id):
        """Update user's last active time"""
        try:
            self.connect()
            now = datetime.now().isoformat()
            self.cursor.execute('''
                UPDATE users SET last_active = ? WHERE user_id = ?
            ''', (now, user_id))
            self.conn.commit()
        except Exception as e:
            logger.error(f"Error updating user activity: {e}")
        finally:
            self.close()
    
    def get_tasbeeh_counts(self, user_id):
        """Get user's tasbeeh counts"""
        try:
            self.connect()
            self.cursor.execute('''
                SELECT subhanallah, alhamdulillah, allahu_akbar, total 
                FROM tasbeeh_counts WHERE user_id = ?
            ''', (user_id,))
            result = self.cursor.fetchone()
            
            if result:
                return {
                    'subhanallah': result[0],
                    'alhamdulillah': result[1],
                    'allahu_akbar': result[2],
                    'total': result[3]
                }
            return None
        except Exception as e:
            logger.error(f"Error getting tasbeeh counts: {e}")
            return None
        finally:
            self.close()
    
    def update_tasbeeh_count(self, user_id, tasbeeh_type):
        """Update specific tasbeeh count"""
        try:
            self.connect()
            now = datetime.now().isoformat()
            
            # Update specific count and total
            self.cursor.execute(f'''
                UPDATE tasbeeh_counts 
                SET {tasbeeh_type} = {tasbeeh_type} + 1,
                    total = total + 1,
                    last_updated = ?
                WHERE user_id = ?
            ''', (now, user_id))
            
            self.conn.commit()
            
            # Get updated counts
            return self.get_tasbeeh_counts(user_id)
            
        except Exception as e:
            logger.error(f"Error updating tasbeeh count: {e}")
            return None
        finally:
            self.close()
    
    def reset_tasbeeh(self, user_id):
        """Reset user's tasbeeh counts"""
        try:
            self.connect()
            now = datetime.now().isoformat()
            self.cursor.execute('''
                UPDATE tasbeeh_counts 
                SET subhanallah = 0,
                    alhamdulillah = 0,
                    allahu_akbar = 0,
                    total = 0,
                    last_updated = ?
                WHERE user_id = ?
            ''', (now, user_id))
            self.conn.commit()
            return True
        except Exception as e:
            logger.error(f"Error resetting tasbeeh: {e}")
            return False
        finally:
            self.close()
    
    def get_all_users(self):
        """Get all active users"""
        try:
            self.connect()
            self.cursor.execute('SELECT user_id FROM users WHERE is_active = 1')
            return [row[0] for row in self.cursor.fetchall()]
        except Exception as e:
            logger.error(f"Error getting all users: {e}")
            return []
        finally:
            self.close()
    
    def get_user_count(self):
        """Get total number of users"""
        try:
            self.connect()
            self.cursor.execute('SELECT COUNT(*) FROM users')
            return self.cursor.fetchone()[0]
        except Exception as e:
            logger.error(f"Error getting user count: {e}")
            return 0
        finally:
            self.close()
    
    def get_user_settings(self, user_id):
        """Get user notification settings"""
        try:
            self.connect()
            self.cursor.execute('''
                SELECT receive_notifications, notification_time_morning, 
                       notification_time_evening, language
                FROM user_settings WHERE user_id = ?
            ''', (user_id,))
            result = self.cursor.fetchone()
            
            if result:
                return {
                    'receive_notifications': bool(result[0]),
                    'morning_time': result[1],
                    'evening_time': result[2],
                    'language': result[3]
                }
            return None
        except Exception as e:
            logger.error(f"Error getting user settings: {e}")
            return None
        finally:
            self.close()
    
    def update_notification_setting(self, user_id, setting, value):
        """Update user notification setting"""
        try:
            self.connect()
            self.cursor.execute(f'''
                UPDATE user_settings SET {setting} = ? WHERE user_id = ?
            ''', (value, user_id))
            self.conn.commit()
            return True
        except Exception as e:
            logger.error(f"Error updating notification setting: {e}")
            return False
        finally:
            self.close()
    
    def log_broadcast(self, message_text, total_sent, successful, failed):
        """Log broadcast message"""
        try:
            self.connect()
            now = datetime.now().isoformat()
            self.cursor.execute('''
                INSERT INTO broadcast_messages 
                (message_text, sent_date, total_sent, successful, failed)
                VALUES (?, ?, ?, ?, ?)
            ''', (message_text, now, total_sent, successful, failed))
            self.conn.commit()
        except Exception as e:
            logger.error(f"Error logging broadcast: {e}")
        finally:
            self.close()

# Global database instance
db = Database()
'''
    zipf.writestr('database.py', database)
    
    # إضافة ملف keyboards.py
    keyboards = '''from telegram import InlineKeyboardButton, InlineKeyboardMarkup
from constants import CallbackData

class Keyboards:
    
    @staticmethod
    def main_menu():
        """Main menu keyboard"""
        keyboard = [
            [
                InlineKeyboardButton("أذكار الصباح 🌅", callback_data=CallbackData.MORNING),
                InlineKeyboardButton("أذكار المساء 🌙", callback_data=CallbackData.EVENING)
            ],
            [
                InlineKeyboardButton("أذكار بعد الصلاة 🕌", callback_data=CallbackData.AFTER_PRAYER),
                InlineKeyboardButton("أذكار النوم 😴", callback_data=CallbackData.SLEEP)
            ],
            [
                InlineKeyboardButton("أدعية من القرآن 📖", callback_data=CallbackData.QURAN_DUA),
                InlineKeyboardButton("المسبحة الرقمية 📿", callback_data=CallbackData.TASBEEH)
            ],
            [
                InlineKeyboardButton("فضائل الذكر ⭐", callback_data=CallbackData.VIRTUES)
            ]
        ]
        return InlineKeyboardMarkup(keyboard)
    
    @staticmethod
    def navigation_keyboard(current_index, total_items, section):
        """Navigation keyboard for Adhkar sections"""
        keyboard = []
        nav_buttons = []
        
        if current_index > 0:
            nav_buttons.append(InlineKeyboardButton("السابق ▶️", callback_data=f"{section}_{CallbackData.PREVIOUS}_{current_index}"))
        
        if current_index < total_items - 1:
            nav_buttons.append(InlineKeyboardButton("التالي ◀️", callback_data=f"{section}_{CallbackData.NEXT}_{current_index}"))
        
        if nav_buttons:
            keyboard.append(nav_buttons)
        
        # Back button
        keyboard.append([
            InlineKeyboardButton("🔙 العودة للقائمة الرئيسية", callback_data=CallbackData.MAIN_MENU)
        ])
        
        return InlineKeyboardMarkup(keyboard)
    
    @staticmethod
    def tasbeeh_keyboard():
        """Tasbeeh counter keyboard"""
        keyboard = [
            [
                InlineKeyboardButton("سبحان الله 🤲", callback_data=CallbackData.SUBHANALLAH),
                InlineKeyboardButton("الحمد لله 🤲", callback_data=CallbackData.ALHAMDULILLAH)
            ],
            [
                InlineKeyboardButton("الله أكبر 🤲", callback_data=CallbackData.ALLAHU_AKBAR),
                InlineKeyboardButton("🔄 إعادة تعيين", callback_data=CallbackData.RESET_TASBEEH)
            ],
            [
                InlineKeyboardButton("🔙 العودة", callback_data=CallbackData.MAIN_MENU)
            ]
        ]
        return InlineKeyboardMarkup(keyboard)
    
    @staticmethod
    def back_keyboard():
        """Simple back keyboard"""
        keyboard = [
            [InlineKeyboardButton("🔙 العودة للقائمة الرئيسية", callback_data=CallbackData.MAIN_MENU)]
        ]
        return InlineKeyboardMarkup(keyboard)
'''
    zipf.writestr('keyboards.py', keyboards)
    
    # إضافة ملف handlers.py
    handlers = '''import logging
from telegram import Update, ParseMode
from telegram.ext import ContextTypes
from database import db
from keyboards import Keyboards
from constants import *
import random

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

class Handlers:
    
    @staticmethod
    async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
        """Handle /start command"""
        user = update.effective_user
        
        # Add user to database
        db.add_user(
            user_id=user.id,
            username=user.username,
            first_name=user.first_name,
            last_name=user.last_name,
            language_code=user.language_code
        )
        
        # Send welcome message
        await update.message.reply_text(
            WELCOME_MESSAGE,
            parse_mode=ParseMode.HTML,
            reply_markup=Keyboards.main_menu()
        )
        
        logger.info(f"User {user.id} started the bot")
    
    @staticmethod
    async def button_handler(update: Update, context: ContextTypes.DEFAULT_TYPE):
        """Handle button callbacks"""
        query = update.callback_query
        await query.answer()
        
        user_id = update.effective_user.id
        data = query.data
        
        # Update user activity
        db.update_user_activity(user_id)
        
        # Main menu
        if data == CallbackData.MAIN_MENU:
            await query.edit_message_text(
                WELCOME_MESSAGE,
                parse_mode=ParseMode.HTML,
                reply_markup=Keyboards.main_menu()
            )
        
        # Morning Adhkar
        elif data == CallbackData.MORNING:
            context.user_data['current_section'] = 'morning'
            context.user_data['current_index'] = 0
            await Handlers.show_adhkar(query, MORNING_ADHKAR, 0, 'morning')
        
        # Evening Adhkar
        elif data == CallbackData.EVENING:
            context.user_data['current_section'] = 'evening'
            context.user_data['current_index'] = 0
            await Handlers.show_adhkar(query, EVENING_ADHKAR, 0, 'evening')
        
        # After Prayer Adhkar
        elif data == CallbackData.AFTER_PRAYER:
            context.user_data['current_section'] = 'after_prayer'
            context.user_data['current_index'] = 0
            await Handlers.show_adhkar(query, AFTER_PRAYER_ADHKAR, 0, 'after_prayer')
        
        # Sleep Adhkar
        elif data == CallbackData.SLEEP:
            context.user_data['current_section'] = 'sleep'
            context.user_data['current_index'] = 0
            await Handlers.show_adhkar(query, SLEEP_ADHKAR, 0, 'sleep')
        
        # Quran Duas
        elif data == CallbackData.QURAN_DUA:
            context.user_data['current_section'] = 'quran_dua'
            context.user_data['current_index'] = 0
            await Handlers.show_dua(query, QURAN_DUAS, 0)
        
        # Virtues
        elif data == CallbackData.VIRTUES:
            await Handlers.show_virtues(query)
        
        # Tasbeeh
        elif data == CallbackData.TASBEEH:
            await Handlers.show_tasbeeh(query, user_id)
        
        # Tasbeeh actions
        elif data in [CallbackData.SUBHANALLAH, CallbackData.ALHAMDULILLAH, CallbackData.ALLAHU_AKBAR]:
            await Handlers.update_tasbeeh(query, user_id, data)
        
        elif data == CallbackData.RESET_TASBEEH:
            await Handlers.reset_tasbeeh(query, user_id)
        
        # Navigation
        elif data.startswith(('morning_', 'evening_', 'after_prayer_', 'sleep_', 'quran_dua_')):
            await Handlers.handle_navigation(query, data, context)
    
    @staticmethod
    async def show_adhkar(query, adhkar_list, index, section):
        """Show Adhkar with navigation"""
        adhkar = adhkar_list[index]
        
        text = f"""
<b>{adhkar['title']}</b>

{adhkar['arabic']}

📖 <i>{adhkar['translation']}</i>

📌 <b>مرات القراءة:</b> {adhkar['count']} مرات
✨ <b>الفضل:</b> {adhkar['virtue']}
        """
        
        await query.edit_message_text(
            text,
            parse_mode=ParseMode.HTML,
            reply_markup=Keyboards.navigation_keyboard(index, len(adhkar_list), section)
        )
    
    @staticmethod
    async def show_dua(query, dua_list, index):
        """Show Quran Duas"""
        dua = dua_list[index]
        
        text = f"""
<b>{dua['title']}</b>

{dua['arabic']}

📖 <i>{dua['translation']}</i>

📚 <b>المرجع:</b> {dua['reference']}
        """
        
        await query.edit_message_text(
            text,
            parse_mode=ParseMode.HTML,
            reply_markup=Keyboards.navigation_keyboard(index, len(dua_list), 'quran_dua')
        )
    
    @staticmethod
    async def show_virtues(query):
        """Show random virtue"""
        virtue = random.choice(VIRTUES)
        
        text = f"""
<b>⭐ {virtue['title']} ⭐</b>

{virtue['content']}

💫 <i>{virtue['explanation']}</i>
        """
        
        await query.edit_message_text(
            text,
            parse_mode=ParseMode.HTML,
            reply_markup=Keyboards.back_keyboard()
        )
    
    @staticmethod
    async def show_tasbeeh(query, user_id):
        """Show tasbeeh counter"""
        counts = db.get_tasbeeh_counts(user_id)
        
        if counts:
            text = f"""
<b>📿 المسبحة الرقمية 📿</b>

سبحان الله: {counts['subhanallah']}
الحمد لله: {counts['alhamdulillah']}
الله أكبر: {counts['allahu_akbar']}

<b>المجموع الكلي: {counts['total']}</b>

اضغط على الأزرار للتسبيح:
            """
        else:
            text = "حدث خطأ في تحميل المسبحة"
        
        await query.edit_message_text(
            text,
            parse_mode=ParseMode.HTML,
            reply_markup=Keyboards.tasbeeh_keyboard()
        )
    
    @staticmethod
    async def update_tasbeeh(query, user_id, tasbeeh_type):
        """Update tasbeeh count"""
        # Map callback to database field
        type_map = {
            CallbackData.SUBHANALLAH: 'subhanallah',
            CallbackData.ALHAMDULILLAH: 'alhamdulillah',
            CallbackData.ALLAHU_AKBAR: 'allahu_akbar'
        }
        
        db_field = type_map.get(tasbeeh_type)
        if db_field:
            counts = db.update_tasbeeh_count(user_id, db_field)
            
            if counts:
                text = f"""
<b>📿 المسبحة الرقمية 📿</b>

سبحان الله: {counts['subhanallah']}
الحمد لله: {counts['alhamdulillah']}
الله أكبر: {counts['allahu_akbar']}

<b>المجموع الكلي: {counts['total']}</b>

✅ تم التحديث!
اضغط على الأزرار للمزيد:
                """
            else:
                text = "حدث خطأ في التحديث"
            
            await query.edit_message_text(
                text,
                parse_mode=ParseMode.HTML,
                reply_markup=Keyboards.tasbeeh_keyboard()
            )
    
    @staticmethod
    async def reset_tasbeeh(query, user_id):
        """Reset tasbeeh counter"""
        if db.reset_tasbeeh(user_id):
            text = """
<b>📿 المسبحة الرقمية 📿</b>

سبحان الله: 0
الحمد لله: 0
الله أكبر: 0

<b>المجموع الكلي: 0</b>

✅ تم إعادة تعيين المسبحة
اضغط على الأزرار للبدء من جديد:
            """
        else:
            text = "حدث خطأ في إعادة التعيين"
        
        await query.edit_message_text(
            text,
            parse_mode=ParseMode.HTML,
            reply_markup=Keyboards.tasbeeh_keyboard()
        )
    
    @staticmethod
    async def handle_navigation(query, data, context):
        """Handle navigation between Adhkar"""
        parts = data.split('_')
        section = parts[0]
        action = parts[1]
        current_index = int(parts[2])
        
        if action == CallbackData.NEXT:
            new_index = current_index + 1
        elif action == CallbackData.PREVIOUS:
            new_index = current_index - 1
        else:
            return
        
        context.user_data['current_index'] = new_index
        
        # Select appropriate list
        if section == 'morning':
            await Handlers.show_adhkar(query, MORNING_ADHKAR, new_index, section)
        elif section == 'evening':
            await Handlers.show_adhkar(query, EVENING_ADHKAR, new_index, section)
        elif section == 'after_prayer':
            await Handlers.show_adhkar(query, AFTER_PRAYER_ADHKAR, new_index, section)
        elif section == 'sleep':
            await Handlers.show_adhkar(query, SLEEP_ADHKAR, new_index, section)
        elif section == 'quran_dua':
            await Handlers.show_dua(query, QURAN_DUAS, new_index)
'''
    zipf.writestr('handlers.py', handlers)
    
    # إضافة ملف admin.py
    admin = '''import logging
from telegram import Update, ParseMode
from telegram.ext import ContextTypes
from database import db
from config import ADMIN_IDS

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

class AdminHandlers:
    
    @staticmethod
    async def is_admin(user_id):
        """Check if user is admin"""
        return user_id in ADMIN_IDS
    
    @staticmethod
    async def admin_panel(update: Update, context: ContextTypes.DEFAULT_TYPE):
        """Show admin panel"""
        user = update.effective_user
        
        if not await AdminHandlers.is_admin(user.id):
            await update.message.reply_text("⛔ هذا الأمر مخصص للمشرفين فقط")
            return
        
        text = """
<b>🔐 لوحة تحكم المشرف</b>

الأوامر المتاحة:
/panel - عرض لوحة التحكم
/stats - إحصائيات البوت
/broadcast - إرسال رسالة لجميع المستخدمين
/notify_on - تفعيل الإشعارات لجميع المستخدمين
/notify_off - تعطيل الإشعارات لجميع المستخدمين

اختر الأمر المناسب:
        """
        
        await update.message.reply_text(text, parse_mode=ParseMode.HTML)
    
    @staticmethod
    async def stats(update: Update, context: ContextTypes.DEFAULT_TYPE):
        """Show bot statistics"""
        user = update.effective_user
        
        if not await AdminHandlers.is_admin(user.id):
            await update.message.reply_text("⛔ هذا الأمر مخصص للمشرفين فقط")
            return
        
        total_users = db.get_user_count()
        
        text = f"""
<b>📊 إحصائيات البوت</b>

👥 إجمالي المستخدمين: {total_users}
📅 آخر تحديث: {__import__('datetime').datetime.now().strftime('%Y-%m-%d %H:%M:%S')}
        """
        
        await update.message.reply_text(text, parse_mode=ParseMode.HTML)
    
    @staticmethod
    async def broadcast_start(update: Update, context: ContextTypes.DEFAULT_TYPE):
        """Start broadcast process"""
        user = update.effective_user
        
        if not await AdminHandlers.is_admin(user.id):
            await update.message.reply_text("⛔ هذا الأمر مخصص للمشرفين فقط")
            return
        
        context.user_data['broadcast_mode'] = True
        await update.message.reply_text(
            "📝 أرسل الرسالة التي تريد نشرها لجميع المستخدمين:\n"
            "(يمكنك استخدام HTML للتنسيق)"
        )
    
    @staticmethod
    async def handle_broadcast_message(update: Update, context: ContextTypes.DEFAULT_TYPE):
        """Handle broadcast message"""
        user = update.effective_user
        
        if not context.user_data.get('broadcast_mode'):
            return
        
        if not await AdminHandlers.is_admin(user.id):
            context.user_data['broadcast_mode'] = False
            return
        
        message_text = update.message.text_html or update.message.text
        
        # Get all users
        users = db.get_all_users()
        total_users = len(users)
        
        status_message = await update.message.reply_text(
            f"📨 جاري إرسال الرسالة إلى {total_users} مستخدم...\n"
            "قد يستغرق هذا بعض الوقت"
        )
        
        successful = 0
        failed = 0
        
        for user_id in users:
            try:
                await context.bot.send_message(
                    chat_id=user_id,
                    text=message_text,
                    parse_mode=ParseMode.HTML
                )
                successful += 1
                
                # Add small delay to avoid rate limiting
                await __import__('asyncio').sleep(0.05)
                
            except Exception as e:
                logger.error(f"Failed to send to {user_id}: {e}")
                failed += 1
        
        # Log broadcast
        db.log_broadcast(message_text, total_users, successful, failed)
        
        # Send final report
        await status_message.edit_text(
            f"✅ تم إرسال الرسالة\n\n"
            f"إجمالي المستخدمين: {total_users}\n"
            f"نجح: {successful}\n"
            f"فشل: {failed}"
        )
        
        context.user_data['broadcast_mode'] = False
    
    @staticmethod
    async def notify_all(update: Update, context: ContextTypes.DEFAULT_TYPE, enable: bool):
        """Enable/disable notifications for all users"""
        user = update.effective_user
        
        if not await AdminHandlers.is_admin(user.id):
            await update.message.reply_text("⛔ هذا الأمر مخصص للمشرفين فقط")
            return
        
        users = db.get_all_users()
        status = "تفعيل" if enable else "تعطيل"
        
        status_message = await update.message.reply_text(
            f"📨 جاري {status} الإشعارات لجميع المستخدمين..."
        )
        
        successful = 0
        failed = 0
        
        for user_id in users:
            try:
                # Update user settings
                db.update_notification_setting(
                    user_id, 
                    'receive_notifications', 
                    1 if enable else 0
                )
                successful += 1
            except Exception as e:
                logger.error(f"Failed to update {user_id}: {e}")
                failed += 1
        
        await status_message.edit_text(
            f"✅ تم {status} الإشعارات\n\n"
            f"نجح: {successful}\n"
            f"فشل: {failed}"
        )
'''
    zipf.writestr('admin.py', admin)
    
    # إضافة ملف scheduler.py
    scheduler = '''import logging
from apscheduler.schedulers.asyncio import AsyncIOScheduler
from apscheduler.triggers.cron import CronTrigger
from telegram import Bot
from database import db
from constants import MORNING_ADHKAR, EVENING_ADHKAR
import random

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

class AdhkarScheduler:
    
    def __init__(self, bot: Bot):
        self.bot = bot
        self.scheduler = AsyncIOScheduler()
    
    def start(self):
        """Start the scheduler"""
        # Schedule morning Adhkar at 6:00 AM
        self.scheduler.add_job(
            self.send_morning_adhkar,
            CronTrigger(hour=6, minute=0),
            id='morning_adhkar'
        )
        
        # Schedule evening Adhkar at 6:00 PM
        self.scheduler.add_job(
            self.send_evening_adhkar,
            CronTrigger(hour=18, minute=0),
            id='evening_adhkar'
        )
        
        self.scheduler.start()
        logger.info("Scheduler started successfully")
    
    async def send_morning_adhkar(self):
        """Send morning Adhkar to all users"""
        await self.send_adhkar_to_all(MORNING_ADHKAR, "صباح")
    
    async def send_evening_adhkar(self):
        """Send evening Adhkar to all users"""
        await self.send_adhkar_to_all(EVENING_ADHKAR, "مساء")
    
    async def send_adhkar_to_all(self, adhkar_list, time_of_day):
        """Send Adhkar to all users who have notifications enabled"""
        users = db.get_all_users()
        
        # Select random Adhkar
        adhkar = random.choice(adhkar_list)
        
        text = f"""
<b>🌙 أذكار {time_of_day} - تذكير تلقائي 🌙</b>

<b>{adhkar['title']}</b>

{adhkar['arabic']}

📖 <i>{adhkar['translation']}</i>

📌 <b>مرات القراءة:</b> {adhkar['count']} مرات
✨ <b>الفضل:</b> {adhkar['virtue']}

لا تنسى ذكر الله في هذا اليوم المبارك 🤲
        """
        
        successful = 0
        failed = 0
        
        for user_id in users:
            try:
                # Check if user wants notifications
                settings = db.get_user_settings(user_id)
                if settings and settings['receive_notifications']:
                    await self.bot.send_message(
                        chat_id=user_id,
                        text=text,
                        parse_mode='HTML'
                    )
                    successful += 1
                    
                    # Small delay to avoid rate limiting
                    await __import__('asyncio').sleep(0.05)
            except Exception as e:
                logger.error(f"Failed to send to {user_id}: {e}")
                failed += 1
        
        logger.info(f"Sent {time_of_day} Adhkar to {successful} users, failed: {failed}")
'''
    zipf.writestr('scheduler.py', scheduler)
    
    # إضافة ملف main.py
    main = '''#!/usr/bin/env python3
"""
Islamic Adhkar and Duas Telegram Bot
Main entry point for the bot
"""

import logging
from telegram.ext import Application, CommandHandler, CallbackQueryHandler, MessageHandler, filters
from config import BOT_TOKEN, ADMIN_IDS
from handlers import Handlers
from admin import AdminHandlers
from database import db
from scheduler import AdhkarScheduler

# Configure logging
logging.basicConfig(
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    level=logging.INFO
)
logger = logging.getLogger(__name__)

class IslamicBot:
    def __init__(self):
        self.application = None
        self.scheduler = None
    
    def setup_handlers(self):
        """Setup all bot handlers"""
        # Command handlers
        self.application.add_handler(CommandHandler("start", Handlers.start))
        self.application.add_handler(CommandHandler("panel", AdminHandlers.admin_panel))
        self.application.add_handler(CommandHandler("stats", AdminHandlers.stats))
        self.application.add_handler(CommandHandler("broadcast", AdminHandlers.broadcast_start))
        self.application.add_handler(CommandHandler("notify_on", 
            lambda u, c: AdminHandlers.notify_all(u, c, True)))
        self.application.add_handler(CommandHandler("notify_off", 
            lambda u, c: AdminHandlers.notify_all(u, c, False)))
        
        # Callback query handler
        self.application.add_handler(CallbackQueryHandler(Handlers.button_handler))
        
        # Message handler for broadcasts
        self.application.add_handler(MessageHandler(
            filters.TEXT & ~filters.COMMAND, 
            AdminHandlers.handle_broadcast_message
        ))
        
        logger.info("Handlers setup completed")
    
    def setup_scheduler(self):
        """Setup the adhkar scheduler"""
        self.scheduler = AdhkarScheduler(self.application.bot)
        self.scheduler.start()
        logger.info("Scheduler setup completed")
    
    async def error_handler(self, update, context):
        """Handle errors"""
        logger.error(f"Update {update} caused error {context.error}")
        
        # Notify admin of critical errors
        if context.error:
            try:
                error_msg = f"⚠️ خطأ في البوت:\n{str(context.error)[:200]}"
                for admin_id in ADMIN_IDS:
                    await context.bot.send_message(chat_id=admin_id, text=error_msg)
            except:
                pass
    
    def run(self):
        """Run the bot"""
        try:
            # Create application
            self.application = Application.builder().token(BOT_TOKEN).build()
            
            # Setup handlers
            self.setup_handlers()
            
            # Add error handler
            self.application.add_error_handler(self.error_handler)
            
            # Setup scheduler after application is built
            self.setup_scheduler()
            
            logger.info("Bot started successfully")
            
            # Run the bot
            self.application.run_polling()
            
        except Exception as e:
            logger.error(f"Failed to start bot: {e}")
        finally:
            # Close database connection
            db.close()
            logger.info("Bot stopped")

def main():
    """Main function"""
    # Check if token exists
    if not BOT_TOKEN or BOT_TOKEN == "YOUR_BOT_TOKEN_HERE":
        logger.error("Please set your BOT_TOKEN in .env file")
        return
    
    # Create and run bot
    bot = IslamicBot()
    bot.run()

if __name__ == '__main__':
    main()
'''
    zipf.writestr('main.py', main)
    
    # إضافة ملف README.md
    readme = '''# بوت الأذكار والأدعية الإسلامي 🤲

بوت تليجرام إسلامي متكامل للأذكار والأدعية مع واجهة عربية سهلة الاستخدام.

## المميزات 🌟

- ✅ أذكار الصباح والمساء
- ✅ أذكار ما بعد الصلاة
- ✅ أذكار النوم
- ✅ أدعية من القرآن الكريم
- ✅ المسبحة الرقمية (تسبيح)
- ✅ فضائل الذكر
- ✅ أزرار تنقل بين الأذكار
- ✅ تذكير تلقائي يومي (6 صباحاً - 6 مساءً)
- ✅ لوحة تحكم للمشرفين
- ✅ قاعدة بيانات SQLite
- ✅ دعم النشر على VPS و Railway و Render

## التثبيت والتشغيل 🚀

1. قم بتثبيت المتطلبات:
```bash
pip install -r requirements.txt
