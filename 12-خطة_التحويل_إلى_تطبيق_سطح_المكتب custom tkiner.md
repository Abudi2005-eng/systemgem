# خطة التحويل من تطبيق ويب Flask إلى تطبيق سطح مكتب CustomTkinter

## 🎯 نظرة عامة

يقدم هذا المستند خطة شاملة لتحويل نظام إدارة النادي الرياضي من تطبيق ويب مبني على Flask إلى تطبيق سطح مكتب باستخدام CustomTkinter. الهدف هو الاحتفاظ بجميع الوظائف والخصائص الحالية مع تكييفها لبيئة سطح المكتب، مما يسمح بتشغيل النظام بدون الحاجة إلى اتصال بالإنترنت وبشكل أكثر كفاءة.

## 📋 مقارنة بين البيئتين

| الجانب | تطبيق ويب Flask | تطبيق سطح مكتب CustomTkinter |
|--------|----------------|-----------------------------|
| **واجهة المستخدم** | HTML/CSS/JavaScript | CustomTkinter (Python) |
| **قاعدة البيانات** | SQLite/PostgreSQL (خادم) | SQLite (محلي) |
| **المصادقة** | جلسات الويب، رموز JWT | مصادقة محلية |
| **التوزيع** | نشر على خادم ويب | تطبيق قائم بذاته |
| **التحديثات** | مركزية (تحديث الخادم) | تحديثات للعميل |
| **الاتصال** | يتطلب اتصال بالإنترنت | يعمل بدون اتصال |
| **الأداء** | يعتمد على سرعة الاتصال | أداء محلي أسرع |

## 🏗️ الهيكل العام للتطبيق الجديد

```
gymawy-desktop/
├── app/
│   ├── controllers/        # منطق التحكم في التطبيق
│   ├── models/             # نماذج البيانات
│   ├── views/              # واجهات المستخدم CustomTkinter
│   ├── services/           # خدمات النظام المختلفة
│   ├── utils/              # أدوات مساعدة
│   └── assets/             # الصور والأيقونات والموارد
├── config/                 # ملفات الإعدادات
├── database/               # ملفات قاعدة البيانات
├── docs/                   # توثيق المشروع
└── main.py                 # نقطة الدخول الرئيسية للتطبيق
```

## 💻 استراتيجية التحويل

### 1. إعادة استخدام المكونات

يمكن إعادة استخدام العديد من المكونات الحالية مع تعديلات طفيفة:

- **النماذج (Models)**: يمكن إعادة استخدام نماذج البيانات مع تعديل طريقة الاتصال بقاعدة البيانات.
- **الخدمات (Services)**: يمكن إعادة استخدام معظم خدمات المنطق التجاري.
- **الوظائف المساعدة (Utils)**: يمكن إعادة استخدام معظم الوظائف المساعدة.

### 2. تحويل واجهات المستخدم

يجب إعادة بناء واجهات المستخدم باستخدام CustomTkinter:

- **تحويل القوالب HTML**: تحويل كل قالب HTML إلى نافذة أو إطار CustomTkinter.
- **تحويل النماذج**: تحويل نماذج HTML إلى نماذج CustomTkinter.
- **تحويل الجداول**: استخدام مكتبات مثل Treeview لعرض البيانات الجدولية.

### 3. تكييف نمط MVC

- **النماذج (Models)**: الاحتفاظ بنفس بنية النماذج مع تعديل طريقة الاتصال بقاعدة البيانات.
- **العروض (Views)**: استبدال قوالب Jinja2 بفئات CustomTkinter.
- **وحدات التحكم (Controllers)**: تعديل وحدات التحكم للعمل مع واجهات CustomTkinter بدلاً من طلبات HTTP.

## 🔄 خطة التنفيذ المرحلية

### المرحلة 1: الإعداد والتحليل (1-2 أسبوع)

1. **إعداد بيئة التطوير**:
   - تثبيت CustomTkinter وجميع المكتبات اللازمة.
   - إنشاء هيكل المشروع الجديد.

2. **تحليل التطبيق الحالي**:
   - تحديد جميع الصفحات والوظائف.
   - تحديد تدفقات البيانات والعمليات.
   - تحديد المكونات القابلة لإعادة الاستخدام.

3. **تصميم واجهة المستخدم**:
   - إنشاء نماذج أولية لواجهات المستخدم الرئيسية.
   - تحديد أسلوب وسمة التصميم.

### المرحلة 2: تحويل النماذج والخدمات (2-3 أسابيع)

1. **تحويل نماذج البيانات**:
   - نقل تعريفات النماذج مع تعديل ORM إذا لزم الأمر.
   - تكييف العلاقات بين النماذج.

2. **تحويل الخدمات**:
   - نقل خدمات المنطق التجاري مع التعديلات اللازمة.
   - تكييف خدمات التقارير والإحصائيات.

3. **إعداد قاعدة البيانات المحلية**:
   - إنشاء هيكل قاعدة البيانات.
   - كتابة وظائف الترحيل والتهيئة.

### المرحلة 3: بناء واجهات المستخدم الأساسية (3-4 أسابيع)

1. **إنشاء القالب الرئيسي**:
   - بناء النافذة الرئيسية مع القائمة الجانبية والشريط العلوي.
   - تنفيذ نظام التنقل بين الشاشات.

2. **تحويل الشاشات الرئيسية**:
   - لوحة التحكم (Dashboard).
   - شاشة تسجيل الدخول.
   - شاشات إدارة الأعضاء الأساسية.

3. **تنفيذ المكونات المشتركة**:
   - مربعات الحوار المشتركة.
   - عناصر النماذج المخصصة.
   - مكونات عرض البيانات.

### المرحلة 4: تحويل وحدات النظام (4-6 أسابيع)

1. **نظام إدارة الأعضاء**:
   - شاشات عرض وإضافة وتعديل الأعضاء.
   - بطاقات العضوية وإدارة الصور.

2. **نظام الاشتراكات وخطط العضوية**:
   - شاشات إدارة خطط العضوية.
   - شاشات إدارة الاشتراكات والتجديد.

3. **نظام الحضور والانصراف**:
   - واجهة تسجيل الحضور والانصراف.
   - سجلات الحضور والتقارير.

4. **نظام المدفوعات والفواتير**:
   - شاشات إدارة المدفوعات.
   - إنشاء وطباعة الفواتير.

5. **نظام التقارير**:
   - شاشات إنشاء وعرض التقارير.
   - تصدير التقارير بتنسيقات مختلفة.

6. **نظام المخزون والمبيعات**:
   - شاشات إدارة المنتجات والمخزون.
   - شاشات المبيعات والخدمات.

7. **نظام الإعدادات**:
   - شاشات إعدادات النظام.
   - إدارة المستخدمين والصلاحيات.

### المرحلة 5: الاختبار والتحسين (2-3 أسابيع)

1. **اختبار الوظائف**:
   - اختبار جميع وظائف النظام.
   - التأكد من تطابق السلوك مع النظام الأصلي.

2. **تحسين الأداء**:
   - تحسين استجابة واجهة المستخدم.
   - تحسين أداء قاعدة البيانات.

3. **تحسين تجربة المستخدم**:
   - تنفيذ اختصارات لوحة المفاتيح.
   - تحسين تدفق العمل وسهولة الاستخدام.

### المرحلة 6: التوزيع والتوثيق (1-2 أسبوع)

1. **إعداد حزمة التوزيع**:
   - إنشاء ملف تنفيذي قائم بذاته.
   - إعداد برنامج التثبيت.

2. **إكمال التوثيق**:
   - توثيق واجهة المستخدم الجديدة.
   - تحديث دليل المستخدم.

## 🧩 تفاصيل تنفيذ المكونات الرئيسية

### 1. نظام الفصل بين الجنسين

يعتبر الفصل بين الجنسين من المتطلبات الأساسية في النظام، حيث يجب تنفيذه بشكل دقيق في تطبيق سطح المكتب كما هو في تطبيق الويب. فيما يلي تفاصيل تنفيذ هذه الميزة:

#### 1.1 نموذج البيانات والتعريفات

```python
# app/utils/time_period_utils.py
from enum import Enum

class TimePeriod(Enum):
    MEN = "men"
    WOMEN = "women"
    BOTH = "both"

def get_current_time_period(user=None, session=None):
    """الحصول على الفترة الزمنية الحالية (رجال/سيدات) بناءً على المستخدم الحالي أو الجلسة"""
    if user:
        return user.time_period
    elif session and "time_period" in session:
        return session["time_period"]
    return None

def get_allowed_time_periods_for_user(user):
    """تحديد الفترات الزمنية المسموح بها للمستخدم بناءً على دوره وجنسه"""
    allowed_periods = [TimePeriod.BOTH.value]
    
    if user.is_admin:
        # المدير لديه وصول كامل لجميع الفترات
        allowed_periods.extend([TimePeriod.MEN.value, TimePeriod.WOMEN.value])
    elif user.gender == "female":
        # الموظفات لديهن وصول لفترة السيدات فقط
        allowed_periods.append(TimePeriod.WOMEN.value)
    elif user.gender == "male":
        # الموظفون لديهم وصول لفترة الرجال فقط
        allowed_periods.append(TimePeriod.MEN.value)
    
    return allowed_periods

def validate_time_period_access(user, requested_period):
    """التحقق من صلاحية المستخدم للوصول إلى فترة زمنية محددة"""
    allowed_periods = get_allowed_time_periods_for_user(user)
    return requested_period in allowed_periods
```

#### 1.2 تعديل نظام المصادقة

```python
# app/controllers/auth_controller.py
class AuthController:
    def __init__(self, db_service, security_service):
        self.db_service = db_service
        self.security_service = security_service
    
    def login(self, username, password, time_period):
        user = self.db_service.get_user_by_username(username)
        if user and self.security_service.verify_password(password, user.password_hash):
            # التحقق من صلاحية الوصول للفترة المطلوبة
            from app.utils.time_period_utils import validate_time_period_access
            if validate_time_period_access(user, time_period):
                # تحديث آخر تسجيل دخول والفترة الزمنية
                user.last_login = datetime.now()
                user.time_period = time_period
                self.db_service.update_user(user)
                return user
        return None
```

#### 1.3 تعديل واجهة تسجيل الدخول

```python
# app/views/auth_view.py
class LoginWindow(ctk.CTkToplevel):
    def __init__(self, parent, auth_controller):
        super().__init__(parent)
        self.auth_controller = auth_controller
        self.title("تسجيل الدخول")
        self.geometry("400x400")
        
        # إنشاء عناصر واجهة المستخدم
        self.username_label = ctk.CTkLabel(self, text="اسم المستخدم:")
        self.username_label.pack(pady=10)
        
        self.username_entry = ctk.CTkEntry(self, width=200)
        self.username_entry.pack(pady=5)
        
        self.password_label = ctk.CTkLabel(self, text="كلمة المرور:")
        self.password_label.pack(pady=10)
        
        self.password_entry = ctk.CTkEntry(self, width=200, show="*")
        self.password_entry.pack(pady=5)
        
        # إضافة اختيار الفترة الزمنية
        self.period_label = ctk.CTkLabel(self, text="الفترة الزمنية:")
        self.period_label.pack(pady=10)
        
        self.period_var = ctk.StringVar(value="men")
        self.period_men = ctk.CTkRadioButton(self, text="فترة الرجال", variable=self.period_var, value="men")
        self.period_men.pack(pady=5)
        
        self.period_women = ctk.CTkRadioButton(self, text="فترة السيدات", variable=self.period_var, value="women")
        self.period_women.pack(pady=5)
        
        # إضافة ملاحظة حول الفترات
        self.note_label = ctk.CTkLabel(self, text="ملاحظة: يمكن للموظفين الذكور العمل في فترة الرجال فقط،\nويمكن للموظفات العمل في فترة السيدات فقط.", text_color="gray70")
        self.note_label.pack(pady=10)
        
        self.login_button = ctk.CTkButton(self, text="تسجيل الدخول", command=self.login)
        self.login_button.pack(pady=20)
        
        self.error_label = ctk.CTkLabel(self, text="", text_color="red")
        self.error_label.pack(pady=10)
    
    def login(self):
        username = self.username_entry.get()
        password = self.password_entry.get()
        time_period = self.period_var.get()
        
        user = self.auth_controller.login(username, password, time_period)
        if user:
            self.destroy()  # إغلاق نافذة تسجيل الدخول
            self.master.show_main_window(user)  # عرض النافذة الرئيسية
        else:
            self.error_label.configure(text="اسم المستخدم أو كلمة المرور غير صحيحة\nأو ليس لديك صلاحية للوصول إلى الفترة المحددة")
```

#### 1.4 تعديل النافذة الرئيسية لعرض الفترة الحالية

```python
# app/views/main_window.py
class MainWindow(ctk.CTk):
    def __init__(self, auth_controller):
        super().__init__()
        self.auth_controller = auth_controller
        self.current_user = None
        
        # ... الكود الحالي ...
        
    def show_main_window(self, user):
        self.current_user = user
        
        # إنشاء الشريط العلوي مع معلومات المستخدم والفترة
        self.header_frame = ctk.CTkFrame(self)
        self.header_frame.pack(fill="x", padx=10, pady=5)
        
        # عرض اسم المستخدم والفترة الحالية
        period_text = "فترة الرجال" if user.time_period == "men" else "فترة السيدات" if user.time_period == "women" else "جميع الفترات"
        self.user_label = ctk.CTkLabel(self.header_frame, text=f"مرحباً {user.name} | {period_text}")
        self.user_label.pack(side="right", padx=10)
        
        # ... باقي الكود ...
```

#### 1.5 تعديل وحدات التحكم للتحقق من صلاحيات الوصول

```python
# app/controllers/member_controller.py
class MemberController:
    def __init__(self, db_service, current_user):
        self.db_service = db_service
        self.current_user = current_user
    
    def get_all_members(self):
        # الحصول على الأعضاء مع مراعاة الفترة الزمنية للمستخدم
        if self.current_user.is_admin:
            # المدير يمكنه رؤية جميع الأعضاء
            return self.db_service.get_all_members()
        else:
            # الموظفون يرون فقط الأعضاء في فترتهم
            time_period = self.current_user.time_period
            if time_period == "men":
                return self.db_service.get_members_by_gender("male")
            elif time_period == "women":
                return self.db_service.get_members_by_gender("female")
            else:
                return self.db_service.get_all_members()
```

#### 1.6 تعديل نماذج البيانات للتحقق من صلاحيات الوصول

```python
# app/models/user.py
class User:
    def __init__(self, id, username, password_hash, name, role, gender, time_period=None, last_login=None):
        self.id = id
        self.username = username
        self.password_hash = password_hash
        self.name = name
        self.role = role
        self.gender = gender  # "male" أو "female"
        self.time_period = time_period  # "men" أو "women" أو "both"
        self.last_login = last_login
        
    @property
    def is_admin(self):
        return self.role == "admin"
    
    def has_time_period_access(self, member):
        """التحقق من صلاحية المستخدم للوصول إلى بيانات عضو معين بناءً على الجنس والفترة"""
        if self.is_admin:
            # المدير لديه وصول كامل
            return True
        
        if self.time_period == "both":
            # فترة مشتركة تسمح بالوصول إلى جميع الأعضاء
            return True
        
        if self.time_period == "men" and member.gender == "male":
            # فترة الرجال تسمح بالوصول إلى الأعضاء الذكور فقط
            return True
        
        if self.time_period == "women" and member.gender == "female":
            # فترة السيدات تسمح بالوصول إلى الأعضاء الإناث فقط
            return True
        
        return False
```

#### 1.7 تعديل نظام الحضور والانصراف

```python
# app/controllers/attendance_controller.py
class AttendanceController:
    def __init__(self, db_service, current_user):
        self.db_service = db_service
        self.current_user = current_user
    
    def check_in_member(self, member_id):
        # التحقق من صلاحية الوصول قبل تسجيل الحضور
        member = self.db_service.get_member_by_id(member_id)
        if not member or not self.current_user.has_time_period_access(member):
            return {"success": False, "error": "ليس لديك صلاحية للوصول إلى هذا العضو"}
        
        # التحقق من عدم وجود تسجيل حضور مفتوح
        if self.db_service.has_open_attendance(member_id):
            return {"success": False, "error": "العضو مسجل حضور بالفعل"}
        
        # تسجيل الحضور

### 2. نظام إعدادات الجيم

يعتبر نظام إعدادات الجيم من المكونات الأساسية في النظام، حيث يتيح تخصيص معلومات النادي الرياضي وعرضها في جميع أنحاء التطبيق. فيما يلي تفاصيل تنفيذ هذه الميزة في تطبيق سطح المكتب:

#### 2.1 نموذج البيانات والتعريفات

```python
# app/models/gym_settings.py
class GymSettings:
    def __init__(self, id=None, gym_name="نادي اللياقة البدنية", gym_logo=None, address=None, 
                 phone=None, email=None, website=None, working_hours=None, 
                 male_hours=None, female_hours=None, currency="EGP", 
                 invoice_header=None, invoice_footer=None, 
                 primary_color="#4e73df", secondary_color="#1cc88a"):
        self.id = id
        self.gym_name = gym_name
        self.gym_logo = gym_logo  # مسار ملف اللوجو
        self.address = address
        self.phone = phone
        self.email = email
        self.website = website
        self.working_hours = working_hours
        self.male_hours = male_hours
        self.female_hours = female_hours
        self.currency = currency
        self.invoice_header = invoice_header
        self.invoice_footer = invoice_footer
        self.primary_color = primary_color
        self.secondary_color = secondary_color
        self.created_at = None
        self.updated_at = None
    
    @property
    def has_logo(self):
        """التحقق من وجود لوجو"""
        return self.gym_logo is not None and self.gym_logo.strip() != ''
    
    @property
    def logo_path(self):
        """الحصول على المسار الكامل للوجو"""
        if self.has_logo:
            return os.path.join("assets", "logos", self.gym_logo)
        return None
```

#### 2.2 خدمة إعدادات الجيم

```python
# app/services/gym_settings_service.py
import os
import shutil
from datetime import datetime
from PIL import Image

class GymSettingsService:
    def __init__(self, db_service):
        self.db_service = db_service
        self.settings = None
        self._load_settings()
    
    def _load_settings(self):
        """تحميل إعدادات الجيم من قاعدة البيانات"""
        self.settings = self.db_service.get_gym_settings()
        if not self.settings:
            # إنشاء إعدادات افتراضية إذا لم تكن موجودة
            self.settings = self.db_service.create_gym_settings()
    
    def get_settings(self):
        """الحصول على إعدادات الجيم"""
        return self.settings
    
    def update_settings(self, **kwargs):
        """تحديث إعدادات الجيم"""
        for key, value in kwargs.items():
            if hasattr(self.settings, key):
                setattr(self.settings, key, value)
        
        self.settings.updated_at = datetime.now()
        self.db_service.update_gym_settings(self.settings)
        return self.settings
    
    def upload_logo(self, logo_path):
        """تحميل شعار الجيم"""
        if not logo_path or not os.path.exists(logo_path):
            return False
        
        # إنشاء مجلد اللوجو إذا لم يكن موجودًا
        logos_dir = os.path.join("assets", "logos")
        os.makedirs(logos_dir, exist_ok=True)
        
        # توليد اسم ملف فريد للوجو
        file_ext = os.path.splitext(logo_path)[1]
        new_logo_name = f"gym_logo_{datetime.now().strftime('%Y%m%d%H%M%S')}{file_ext}"
        new_logo_path = os.path.join(logos_dir, new_logo_name)
        
        try:
            # نسخ الملف إلى مجلد اللوجو
            shutil.copy2(logo_path, new_logo_path)
            
            # تحديث مسار اللوجو في الإعدادات
            self.update_settings(gym_logo=new_logo_name)
            return True
        except Exception as e:
            print(f"خطأ في تحميل اللوجو: {e}")
            return False
    
    def remove_logo(self):
        """إزالة شعار الجيم"""
        if self.settings.has_logo:
            logo_path = self.settings.logo_path
            if os.path.exists(logo_path):
                try:
                    os.remove(logo_path)
                except Exception as e:
                    print(f"خطأ في حذف ملف اللوجو: {e}")
            
            # تحديث الإعدادات لإزالة مسار اللوجو
            self.update_settings(gym_logo=None)
            return True
        return False
```

#### 2.3 واجهة إعدادات الجيم

```python
# app/views/settings/gym_settings_window.py
import customtkinter as ctk
from tkinter import filedialog, messagebox
from PIL import Image, ImageTk
import os

class GymSettingsWindow(ctk.CTkToplevel):
    def __init__(self, parent, gym_settings_service):
        super().__init__(parent)
        self.gym_settings_service = gym_settings_service
        self.settings = gym_settings_service.get_settings()
        
        self.title("إعدادات النادي الرياضي")
        self.geometry("800x600")
        self.resizable(True, True)
        
        # إنشاء الإطار الرئيسي
        self.main_frame = ctk.CTkFrame(self)
        self.main_frame.pack(fill="both", expand=True, padx=20, pady=20)
        
        # إنشاء عناصر واجهة المستخدم
        self._create_widgets()
        
        # تحميل البيانات الحالية
        self._load_current_settings()
    
    def _create_widgets(self):
        """إنشاء عناصر واجهة المستخدم"""
        # إنشاء إطار المعلومات الأساسية
        self.basic_info_frame = ctk.CTkFrame(self.main_frame)
        self.basic_info_frame.pack(fill="x", padx=10, pady=10)
        
        # عنوان القسم
        self.basic_info_label = ctk.CTkLabel(self.basic_info_frame, text="معلومات النادي الأساسية", font=ctk.CTkFont(size=16, weight="bold"))
        self.basic_info_label.pack(pady=10)
        
        # اسم النادي
        self.gym_name_label = ctk.CTkLabel(self.basic_info_frame, text="اسم النادي:")
        self.gym_name_label.pack(anchor="w", padx=10, pady=(10, 5))
        
        self.gym_name_entry = ctk.CTkEntry(self.basic_info_frame, width=400)
        self.gym_name_entry.pack(anchor="w", padx=10, pady=(0, 10))
        
        # العنوان
        self.address_label = ctk.CTkLabel(self.basic_info_frame, text="العنوان:")
        self.address_label.pack(anchor="w", padx=10, pady=(10, 5))
        
        self.address_entry = ctk.CTkTextbox(self.basic_info_frame, width=400, height=60)
        self.address_entry.pack(anchor="w", padx=10, pady=(0, 10))
        
        # رقم الهاتف
        self.phone_label = ctk.CTkLabel(self.basic_info_frame, text="رقم الهاتف:")
        self.phone_label.pack(anchor="w", padx=10, pady=(10, 5))
        
        self.phone_entry = ctk.CTkEntry(self.basic_info_frame, width=400)
        self.phone_entry.pack(anchor="w", padx=10, pady=(0, 10))
        
        # البريد الإلكتروني
        self.email_label = ctk.CTkLabel(self.basic_info_frame, text="البريد الإلكتروني:")
        self.email_label.pack(anchor="w", padx=10, pady=(10, 5))
        
        self.email_entry = ctk.CTkEntry(self.basic_info_frame, width=400)
        self.email_entry.pack(anchor="w", padx=10, pady=(0, 10))
        
        # الموقع الإلكتروني
        self.website_label = ctk.CTkLabel(self.basic_info_frame, text="الموقع الإلكتروني:")
        self.website_label.pack(anchor="w", padx=10, pady=(10, 5))
        
        self.website_entry = ctk.CTkEntry(self.basic_info_frame, width=400)
        self.website_entry.pack(anchor="w", padx=10, pady=(0, 10))
        
        # إنشاء إطار اللوجو
        self.logo_frame = ctk.CTkFrame(self.main_frame)
        self.logo_frame.pack(fill="x", padx=10, pady=10)
        
        # عنوان قسم اللوجو
        self.logo_label = ctk.CTkLabel(self.logo_frame, text="شعار النادي", font=ctk.CTkFont(size=16, weight="bold"))
        self.logo_label.pack(pady=10)
        
        # عرض اللوجو الحالي
        self.logo_preview_frame = ctk.CTkFrame(self.logo_frame, width=200, height=200)
        self.logo_preview_frame.pack(pady=10)
        
        self.logo_preview = ctk.CTkLabel(self.logo_preview_frame, text="لا يوجد شعار")
        self.logo_preview.pack(expand=True, fill="both")
        
        # أزرار تحميل وحذف اللوجو
        self.logo_buttons_frame = ctk.CTkFrame(self.logo_frame)
        self.logo_buttons_frame.pack(pady=10)
        
        self.upload_logo_button = ctk.CTkButton(self.logo_buttons_frame, text="تحميل شعار", command=self._upload_logo)
        self.upload_logo_button.pack(side="left", padx=5)
        
        self.remove_logo_button = ctk.CTkButton(self.logo_buttons_frame, text="حذف الشعار", command=self._remove_logo, fg_color="#E74A3B")
        self.remove_logo_button.pack(side="left", padx=5)
        
        # إنشاء إطار أزرار الحفظ والإلغاء
        self.buttons_frame = ctk.CTkFrame(self.main_frame)
        self.buttons_frame.pack(fill="x", padx=10, pady=20)
        
        self.save_button = ctk.CTkButton(self.buttons_frame, text="حفظ التغييرات", command=self._save_settings)
        self.save_button.pack(side="right", padx=10)
        
        self.cancel_button = ctk.CTkButton(self.buttons_frame, text="إلغاء", command=self.destroy, fg_color="#858796")
        self.cancel_button.pack(side="right", padx=10)
    
    def _load_current_settings(self):
        """تحميل الإعدادات الحالية"""
        if self.settings:
            self.gym_name_entry.insert(0, self.settings.gym_name or "")
            if self.settings.address:
                self.address_entry.insert("1.0", self.settings.address)
            self.phone_entry.insert(0, self.settings.phone or "")
            self.email_entry.insert(0, self.settings.email or "")
            self.website_entry.insert(0, self.settings.website or "")
            
            # عرض اللوجو إذا كان موجودًا
            self._display_logo()
    
    def _display_logo(self):
        """عرض اللوجو الحالي"""
        if self.settings.has_logo and os.path.exists(self.settings.logo_path):
            try:
                # فتح وتغيير حجم الصورة
                logo_img = Image.open(self.settings.logo_path)
                logo_img = logo_img.resize((180, 180), Image.LANCZOS)
                
                # تحويل الصورة إلى صيغة متوافقة مع Tkinter
                self.logo_tk_img = ImageTk.PhotoImage(logo_img)
                
                # عرض الصورة
                self.logo_preview.configure(image=self.logo_tk_img, text="")
            except Exception as e:
                print(f"خطأ في عرض اللوجو: {e}")
                self.logo_preview.configure(text="خطأ في عرض الشعار")
        else:
            self.logo_preview.configure(text="لا يوجد شعار", image=None)
    
    def _upload_logo(self):
        """تحميل شعار جديد"""
        file_path = filedialog.askopenfilename(
            title="اختر شعار النادي",
            filetypes=[("صور", "*.png *.jpg *.jpeg *.gif *.bmp")]
        )
        
        if file_path:
            success = self.gym_settings_service.upload_logo(file_path)
            if success:
                messagebox.showinfo("تم", "تم تحميل الشعار بنجاح")
                # تحديث الإعدادات وعرض اللوجو الجديد
                self.settings = self.gym_settings_service.get_settings()
                self._display_logo()
            else:
                messagebox.showerror("خطأ", "حدث خطأ أثناء تحميل الشعار")
    
    def _remove_logo(self):
        """حذف الشعار الحالي"""
        if not self.settings.has_logo:
            messagebox.showinfo("تنبيه", "لا يوجد شعار لحذفه")
            return
        
        if messagebox.askyesno("تأكيد", "هل أنت متأكد من حذف الشعار الحالي؟"):
            success = self.gym_settings_service.remove_logo()
            if success:
                messagebox.showinfo("تم", "تم حذف الشعار بنجاح")
                # تحديث الإعدادات وعرض حالة عدم وجود لوجو
                self.settings = self.gym_settings_service.get_settings()
                self._display_logo()
            else:
                messagebox.showerror("خطأ", "حدث خطأ أثناء حذف الشعار")
    
    def _save_settings(self):
        """حفظ التغييرات"""
        # جمع البيانات من حقول الإدخال
        gym_name = self.gym_name_entry.get()
        address = self.address_entry.get("1.0", "end-1c")
        phone = self.phone_entry.get()
        email = self.email_entry.get()
        website = self.website_entry.get()
        
        # التحقق من صحة البيانات
        if not gym_name:
            messagebox.showerror("خطأ", "يجب إدخال اسم النادي")
            return
        
        # تحديث الإعدادات
        self.gym_settings_service.update_settings(
            gym_name=gym_name,
            address=address,
            phone=phone,
            email=email,
            website=website
        )
        
        messagebox.showinfo("تم", "تم حفظ الإعدادات بنجاح")
        self.destroy()
```

#### 2.4 تكامل إعدادات الجيم مع النظام

##### 2.4.1 عرض معلومات الجيم في النافذة الرئيسية

```python
# app/views/main_window.py
class MainWindow(ctk.CTk):
    def __init__(self, auth_controller, gym_settings_service):
        super().__init__()
        self.auth_controller = auth_controller
        self.gym_settings_service = gym_settings_service
        self.current_user = None
        self.settings = gym_settings_service.get_settings()
        
        # ... الكود الحالي ...
        
    def show_main_window(self, user):
        self.current_user = user
        
        # إنشاء الشريط العلوي مع معلومات المستخدم والفترة ومعلومات الجيم
        self.header_frame = ctk.CTkFrame(self)
        self.header_frame.pack(fill="x", padx=10, pady=5)
        
        # عرض شعار الجيم إذا كان موجودًا
        if self.settings.has_logo and os.path.exists(self.settings.logo_path):
            try:
                logo_img = Image.open(self.settings.logo_path)
                logo_img = logo_img.resize((40, 40), Image.LANCZOS)
                self.logo_tk_img = ImageTk.PhotoImage(logo_img)
                
                self.logo_label = ctk.CTkLabel(self.header_frame, image=self.logo_tk_img, text="")
                self.logo_label.pack(side="left", padx=10)
            except Exception as e:
                print(f"خطأ في عرض اللوجو: {e}")
        
        # عرض اسم الجيم
        self.gym_name_label = ctk.CTkLabel(self.header_frame, text=self.settings.gym_name, font=ctk.CTkFont(size=16, weight="bold"))
        self.gym_name_label.pack(side="left", padx=10)
        
        # عرض اسم المستخدم والفترة الحالية
        period_text = "فترة الرجال" if user.time_period == "men" else "فترة السيدات" if user.time_period == "women" else "جميع الفترات"
        self.user_label = ctk.CTkLabel(self.header_frame, text=f"مرحباً {user.name} | {period_text}")
        self.user_label.pack(side="right", padx=10)
        
        # ... باقي الكود ...
```

##### 2.4.2 استخدام إعدادات الجيم في الفواتير

```python
# app/services/invoice_service.py
class InvoiceService:
    def __init__(self, db_service, gym_settings_service):
        self.db_service = db_service
        self.gym_settings_service = gym_settings_service
    
    def generate_invoice(self, payment_id):
        """إنشاء فاتورة PDF"""
        payment = self.db_service.get_payment_by_id(payment_id)
        if not payment:
            return None
        
        # الحصول على إعدادات الجيم
        gym_settings = self.gym_settings_service.get_settings()
        
        # إنشاء ملف PDF
        buffer = BytesIO()
        doc = SimpleDocTemplate(buffer, pagesize=A4, rightMargin=30, leftMargin=30, topMargin=30, bottomMargin=30)
        story = []
        
        # إضافة رأس الفاتورة مع معلومات الجيم
        self._add_invoice_header(story, gym_settings, payment)
        
        # ... باقي كود إنشاء الفاتورة ...
        
        return buffer
    
    def _add_invoice_header(self, story, gym_settings, payment):
        """إضافة رأس الفاتورة مع معلومات الجيم"""
        # إضافة شعار الجيم إذا كان موجودًا
        if gym_settings.has_logo and os.path.exists(gym_settings.logo_path):
            logo_img = Image(gym_settings.logo_path, width=100, height=100)
            story.append(logo_img)
        
        # إضافة اسم الجيم
        styles = getSampleStyleSheet()
        gym_name_style = ParagraphStyle(
            'GymName',
            parent=styles['Title'],
            fontSize=20,
            alignment=1,  # وسط
            spaceAfter=10
        )
        story.append(Paragraph(gym_settings.gym_name, gym_name_style))
        
        # إضافة معلومات الاتصال
        contact_info = []
        if gym_settings.address:
            contact_info.append(gym_settings.address)
        if gym_settings.phone:
            contact_info.append(f"هاتف: {gym_settings.phone}")
        if gym_settings.email:
            contact_info.append(f"بريد إلكتروني: {gym_settings.email}")
        
        contact_style = ParagraphStyle(
            'ContactInfo',
            parent=styles['Normal'],
            fontSize=10,
            alignment=1,  # وسط
            spaceAfter=20
        )
        
        for info in contact_info:
            story.append(Paragraph(info, contact_style))
        
        # إضافة عنوان الفاتورة
        invoice_title_style = ParagraphStyle(
            'InvoiceTitle',
            parent=styles['Heading1'],
            fontSize=16,
            alignment=1,  # وسط
            spaceAfter=20
        )
        story.append(Paragraph("فاتورة دفع", invoice_title_style))
        
        # ... باقي كود رأس الفاتورة ...
```

##### 2.4.3 استخدام إعدادات الجيم في بطاقات العضوية

```python
# app/services/membership_card_service.py
class MembershipCardService:
    def __init__(self, db_service, gym_settings_service):
        self.db_service = db_service
        self.gym_settings_service = gym_settings_service
    
    def generate_membership_card(self, member_id):
        """إنشاء بطاقة عضوية"""
        member = self.db_service.get_member_by_id(member_id)
        if not member:
            return None
        
        # الحصول على إعدادات الجيم
        gym_settings = self.gym_settings_service.get_settings()
        
        # إنشاء صورة البطاقة
        card_img = Image.new('RGB', (600, 350), color='white')
        draw = ImageDraw.Draw(card_img)
        
        # إضافة شعار الجيم إذا كان موجودًا
        if gym_settings.has_logo and os.path.exists(gym_settings.logo_path):
            try:
                logo_img = Image.open(gym_settings.logo_path)
                logo_img = logo_img.resize((80, 80), Image.LANCZOS)
                card_img.paste(logo_img, (20, 20))
            except Exception as e:
                print(f"خطأ في إضافة اللوجو للبطاقة: {e}")
        
        # إضافة اسم الجيم ومعلومات الاتصال
        font_path = os.path.join("assets", "fonts", "Cairo-Bold.ttf")
        title_font = ImageFont.truetype(font_path, 24)
        info_font = ImageFont.truetype(font_path, 14)
        
        draw.text((120, 30), gym_settings.gym_name, font=title_font, fill='#000000')
        
        y_pos = 60
        if gym_settings.address:
            draw.text((120, y_pos), gym_settings.address, font=info_font, fill='#444444')
            y_pos += 20
        if gym_settings.phone:
            draw.text((120, y_pos), f"هاتف: {gym_settings.phone}", font=info_font, fill='#444444')
            y_pos += 20
        
        # ... باقي كود إنشاء البطاقة ...
        
        return card_img
```

##### 2.4.4 استخدام إعدادات الجيم في التقارير

```python
# app/services/report_service.py
class ReportService:
    def __init__(self, db_service, gym_settings_service):
        self.db_service = db_service
        self.gym_settings_service = gym_settings_service
    
    def generate_members_report(self, filters=None):
        """إنشاء تقرير الأعضاء"""
        members = self.db_service.get_members(filters)
        
        # الحصول على إعدادات الجيم
        gym_settings = self.gym_settings_service.get_settings()
        
        # إنشاء ملف PDF
        buffer = BytesIO()
        doc = SimpleDocTemplate(buffer, pagesize=A4, rightMargin=30, leftMargin=30, topMargin=30, bottomMargin=30)
        story = []
        
        # إضافة رأس التقرير مع معلومات الجيم
        self._add_report_header(story, gym_settings, "تقرير الأعضاء")
        
        # ... باقي كود إنشاء التقرير ...
        
        return buffer
    
    def _add_report_header(self, story, gym_settings, report_title):
        """إضافة رأس التقرير مع معلومات الجيم"""
        # إضافة شعار الجيم إذا كان موجودًا
        if gym_settings.has_logo and os.path.exists(gym_settings.logo_path):
            logo_img = Image(gym_settings.logo_path, width=100, height=100)
            story.append(logo_img)
        
        # إضافة اسم الجيم
        styles = getSampleStyleSheet()
        gym_name_style = ParagraphStyle(
            'GymName',
            parent=styles['Title'],
            fontSize=20,
            alignment=1,  # وسط
            spaceAfter=10
        )
        story.append(Paragraph(gym_settings.gym_name, gym_name_style))
        
        # إضافة عنوان التقرير
        report_title_style = ParagraphStyle(
            'ReportTitle',
            parent=styles['Heading1'],
            fontSize=16,
            alignment=1,  # وسط
            spaceAfter=20
        )
        story.append(Paragraph(report_title, report_title_style))
        
        # إضافة تاريخ التقرير
        date_style = ParagraphStyle(
            'ReportDate',
            parent=styles['Normal'],
            fontSize=10,
            alignment=1,  # وسط
            spaceAfter=20
        )
        report_date = datetime.now().strftime("%Y-%m-%d %H:%M")
        story.append(Paragraph(f"تاريخ التقرير: {report_date}", date_style))
        
        # ... باقي كود رأس التقرير ...
```

#### 2.5 إضافة إعدادات الجيم إلى قائمة الإعدادات

```python
# app/views/settings/settings_menu.py
class SettingsMenu(ctk.CTkFrame):
    def __init__(self, parent, controllers):
        super().__init__(parent)
        self.parent = parent
        self.controllers = controllers
        
        # إنشاء عناصر واجهة المستخدم
        self._create_widgets()
    
    def _create_widgets(self):
        """إنشاء عناصر واجهة المستخدم"""
        # عنوان القسم
        self.title_label = ctk.CTkLabel(self, text="إعدادات النظام", font=ctk.CTkFont(size=20, weight="bold"))
        self.title_label.pack(pady=20)
        
        # إنشاء أزرار الإعدادات
        self.buttons_frame = ctk.CTkFrame(self)
        self.buttons_frame.pack(fill="both", expand=True, padx=20, pady=10)
        
        # زر إعدادات الجيم
        self.gym_settings_button = ctk.CTkButton(
            self.buttons_frame,
            text="إعدادات النادي الرياضي",
            command=self._open_gym_settings,
            height=50,
            font=ctk.CTkFont(size=14)
        )
        self.gym_settings_button.pack(fill="x", pady=10)
        
        # زر إدارة المستخدمين
        self.users_button = ctk.CTkButton(
            self.buttons_frame,
            text="إدارة المستخدمين",
            command=self._open_users_settings,
            height=50,
            font=ctk.CTkFont(size=14)
        )
        self.users_button.pack(fill="x", pady=10)
        
        # ... أزرار إعدادات أخرى ...
    
    def _open_gym_settings(self):
        """فتح نافذة إعدادات الجيم"""
        from app.views.settings.gym_settings_window import GymSettingsWindow
        gym_settings_window = GymSettingsWindow(self.parent, self.controllers["gym_settings_service"])
        gym_settings_window.grab_set()  # جعل النافذة مركز الاهتمام
    
    def _open_users_settings(self):
        """فتح نافذة إدارة المستخدمين"""
        # ... كود فتح نافذة إدارة المستخدمين ...
```

#### 2.6 ملخص تنفيذ نظام إعدادات الجيم

يتم تنفيذ نظام إعدادات الجيم في تطبيق سطح المكتب بالطريقة التالية:

1. **نموذج البيانات**: تم إنشاء نموذج `GymSettings` لتخزين معلومات الجيم الأساسية مثل الاسم واللوجو ومعلومات الاتصال.

2. **خدمة إعدادات الجيم**: تم إنشاء خدمة `GymSettingsService` للتعامل مع إعدادات الجيم، بما في ذلك تحميل الإعدادات وتحديثها وإدارة شعار الجيم.

3. **واجهة إعدادات الجيم**: تم إنشاء نافذة `GymSettingsWindow` لتمكين المستخدمين من تعديل إعدادات الجيم بسهولة.

4. **تكامل مع النظام**: تم دمج إعدادات الجيم في جميع أنحاء النظام، بما في ذلك:
   - عرض معلومات الجيم في النافذة الرئيسية
   - استخدام معلومات الجيم في الفواتير
   - استخدام معلومات الجيم في بطاقات العضوية
   - استخدام معلومات الجيم في التقارير

5. **إضافة إلى قائمة الإعدادات**: تم إضافة خيار إعدادات الجيم إلى قائمة الإعدادات العامة للنظام.

هذا التنفيذ يضمن أن معلومات الجيم تظهر بشكل متسق في جميع أنحاء التطبيق، مما يعزز الهوية البصرية للنادي الرياضي ويوفر تجربة مستخدم متكاملة.
        attendance = Attendance(
            member_id=member_id,
            check_in_time=datetime.now(),
            check_in_by=self.current_user.id,
            time_period=self.current_user.time_period
        )
        
        self.db_service.add_attendance(attendance)
        return {"success": True, "attendance": attendance}
```

#### 1.8 تعديل نظام التقارير

```python
# app/controllers/report_controller.py
class ReportController:
    def __init__(self, db_service, current_user):
        self.db_service = db_service
        self.current_user = current_user
    
    def generate_financial_report(self, start_date, end_date, detail_level="summary"):
        # التحقق من صلاحيات المستخدم
        if not self.current_user.is_admin and not self.current_user.role == "accountant":
            return {"success": False, "error": "ليس لديك صلاحية للوصول إلى التقارير المالية"}
        
        # تحديد الفترة الزمنية للتقرير
        time_period = self.current_user.time_period
        
        # جمع البيانات المالية مع مراعاة الفترة الزمنية
        if time_period == "men":
            # تقارير مالية لفترة الرجال فقط
            income = self.db_service.get_income_by_period(start_date, end_date, "men")
            expenses = self.db_service.get_expenses_by_period(start_date, end_date, "men")
        elif time_period == "women":
            # تقارير مالية لفترة السيدات فقط
            income = self.db_service.get_income_by_period(start_date, end_date, "women")
            expenses = self.db_service.get_expenses_by_period(start_date, end_date, "women")
        else:
            # تقارير مالية لجميع الفترات (للمدير)
            income = self.db_service.get_income(start_date, end_date)
            expenses = self.db_service.get_expenses(start_date, end_date)
        
        # حساب الإجماليات
        total_income = sum(item.amount for item in income)
        total_expenses = sum(item.amount for item in expenses)
        net_profit = total_income - total_expenses
        
        # إعداد التقرير
        report = {
            "success": True,
            "start_date": start_date,
            "end_date": end_date,
            "time_period": time_period,
            "total_income": total_income,
            "total_expenses": total_expenses,
            "net_profit": net_profit
        }
        
        # إضافة تفاصيل إضافية حسب مستوى التفصيل المطلوب
        if detail_level == "detailed":
            report["income_by_category"] = self._group_by_category(income)
            report["expenses_by_category"] = self._group_by_category(expenses)
        
        return report
    
    def generate_member_report(self, start_date, end_date):
        # التحقق من صلاحيات المستخدم
        if not self.current_user.is_admin and not self.current_user.role in ["manager", "receptionist"]:
            return {"success": False, "error": "ليس لديك صلاحية للوصول إلى تقارير الأعضاء"}
        
        # تحديد الفترة الزمنية للتقرير
        time_period = self.current_user.time_period
        
        # جمع بيانات الأعضاء مع مراعاة الفترة الزمنية
        if time_period == "men":
            # تقارير الأعضاء لفترة الرجال فقط
            members = self.db_service.get_members_by_gender("male")
            new_members = self.db_service.get_new_members_by_period(start_date, end_date, "male")
            active_subscriptions = self.db_service.get_active_subscriptions_by_gender("male")
        elif time_period == "women":
            # تقارير الأعضاء لفترة السيدات فقط
            members = self.db_service.get_members_by_gender("female")
            new_members = self.db_service.get_new_members_by_period(start_date, end_date, "female")
            active_subscriptions = self.db_service.get_active_subscriptions_by_gender("female")
        else:
            # تقارير الأعضاء لجميع الفترات (للمدير)
            members = self.db_service.get_all_members()
            new_members = self.db_service.get_new_members(start_date, end_date)
            active_subscriptions = self.db_service.get_active_subscriptions()
        
        # إعداد التقرير
        report = {
            "success": True,
            "start_date": start_date,
            "end_date": end_date,
            "time_period": time_period,
            "total_members": len(members),
            "active_members": len([m for m in members if m.status == "active"]),
            "new_members": len(new_members),
            "active_subscriptions": len(active_subscriptions)
        }
        
        return report
```

#### 1.9 تعديل نظام المبيعات والمخزون

```python
# app/controllers/inventory_controller.py
class InventoryController:
    def __init__(self, db_service, current_user):
        self.db_service = db_service
        self.current_user = current_user
    
    def sell_product(self, product_id, quantity, member_id=None):
        # التحقق من صلاحيات المستخدم
        if not self.current_user.role in ["admin", "sales", "receptionist"]:
            return {"success": False, "error": "ليس لديك صلاحية لإجراء عمليات البيع"}
        
        # التحقق من صلاحية الوصول للعضو إذا تم تحديده
        if member_id:
            member = self.db_service.get_member_by_id(member_id)
            if not member or not self.current_user.has_time_period_access(member):
                return {"success": False, "error": "ليس لديك صلاحية للوصول إلى هذا العضو"}
        
        # التحقق من توفر المنتج
        product = self.db_service.get_product_by_id(product_id)
        if not product or product.quantity < quantity:
            return {"success": False, "error": "المنتج غير متوفر بالكمية المطلوبة"}
        
        # إنشاء عملية البيع
        sale = Sale(
            product_id=product_id,
            quantity=quantity,
            price=product.price,
            total=product.price * quantity,
            member_id=member_id,
            sold_by=self.current_user.id,
            sale_date=datetime.now(),
            time_period=self.current_user.time_period
        )
        
        # تحديث المخزون
        product.quantity -= quantity
        
        # حفظ التغييرات
        self.db_service.add_sale(sale)
        self.db_service.update_product(product)
        
        return {"success": True, "sale": sale}
```

#### 1.10 تعديل واجهة إضافة الأعضاء

```python
# app/views/member_form_view.py
class MemberFormWindow(ctk.CTkToplevel):
    def __init__(self, parent, member_controller, member=None):
        super().__init__(parent)
        self.member_controller = member_controller
        self.member = member
        self.is_edit_mode = member is not None
        
        self.title("تعديل بيانات عضو" if self.is_edit_mode else "إضافة عضو جديد")
        self.geometry("600x700")
        
        # إنشاء عناصر واجهة المستخدم
        self.title_label = ctk.CTkLabel(self, text=self.title(), font=ctk.CTkFont(size=20, weight="bold"))
        self.title_label.pack(pady=10)
        
        # إطار النموذج
        self.form_frame = ctk.CTkScrollableFrame(self)
        self.form_frame.pack(fill="both", expand=True, padx=20, pady=10)
        
        # البيانات الشخصية
        self.personal_info_label = ctk.CTkLabel(self.form_frame, text="البيانات الشخصية", font=ctk.CTkFont(weight="bold"))
        self.personal_info_label.pack(anchor="w", pady=(10, 5))
        
        # الاسم الأول
        self.first_name_label = ctk.CTkLabel(self.form_frame, text="الاسم الأول:")
        self.first_name_label.pack(anchor="w")
        self.first_name_entry = ctk.CTkEntry(self.form_frame, width=250)
        self.first_name_entry.pack(anchor="w", pady=(0, 10))
        
        # الاسم الأخير
        self.last_name_label = ctk.CTkLabel(self.form_frame, text="الاسم الأخير:")
        self.last_name_label.pack(anchor="w")
        self.last_name_entry = ctk.CTkEntry(self.form_frame, width=250)
        self.last_name_entry.pack(anchor="w", pady=(0, 10))
        
        # رقم الهاتف
        self.phone_label = ctk.CTkLabel(self.form_frame, text="رقم الهاتف:")
        self.phone_label.pack(anchor="w")
        self.phone_entry = ctk.CTkEntry(self.form_frame, width=250)
        self.phone_entry.pack(anchor="w", pady=(0, 10))
        
        # البريد الإلكتروني
        self.email_label = ctk.CTkLabel(self.form_frame, text="البريد الإلكتروني:")
        self.email_label.pack(anchor="w")
        self.email_entry = ctk.CTkEntry(self.form_frame, width=250)
        self.email_entry.pack(anchor="w", pady=(0, 10))
        
        # تاريخ الميلاد
        self.birth_date_label = ctk.CTkLabel(self.form_frame, text="تاريخ الميلاد:")
        self.birth_date_label.pack(anchor="w")
        
        self.birth_date_frame = ctk.CTkFrame(self.form_frame)
        self.birth_date_frame.pack(anchor="w", pady=(0, 10))
        
        # اختيار اليوم والشهر والسنة
        self.birth_day = ctk.CTkComboBox(self.birth_date_frame, values=[str(i) for i in range(1, 32)])
        self.birth_day.pack(side="left", padx=5)
        
        self.birth_month = ctk.CTkComboBox(self.birth_date_frame, values=[str(i) for i in range(1, 13)])
        self.birth_month.pack(side="left", padx=5)
        
        self.birth_year = ctk.CTkComboBox(self.birth_date_frame, values=[str(i) for i in range(1950, 2020)])
        self.birth_year.pack(side="left", padx=5)
        
        # الجنس
        self.gender_label = ctk.CTkLabel(self.form_frame, text="الجنس:")
        self.gender_label.pack(anchor="w")
        
        self.gender_var = ctk.StringVar(value="male")
        self.gender_frame = ctk.CTkFrame(self.form_frame)
        self.gender_frame.pack(anchor="w", pady=(0, 10))
        
        self.gender_male = ctk.CTkRadioButton(self.gender_frame, text="ذكر", variable=self.gender_var, value="male", command=self.update_time_period)
        self.gender_male.pack(side="left", padx=10)
        
        self.gender_female = ctk.CTkRadioButton(self.gender_frame, text="أنثى", variable=self.gender_var, value="female", command=self.update_time_period)
        self.gender_female.pack(side="left", padx=10)
        
        # الفترة المفضلة (يتم تحديدها تلقائيًا بناءً على الجنس)
        self.time_period_label = ctk.CTkLabel(self.form_frame, text="الفترة المفضلة:")
        self.time_period_label.pack(anchor="w")
        
        self.time_period_var = ctk.StringVar(value="men")
        self.time_period_frame = ctk.CTkFrame(self.form_frame)
        self.time_period_frame.pack(anchor="w", pady=(0, 10))
        
        self.time_period_men = ctk.CTkRadioButton(self.time_period_frame, text="فترة الرجال", variable=self.time_period_var, value="men")
        self.time_period_men.pack(side="left", padx=10)
        
        self.time_period_women = ctk.CTkRadioButton(self.time_period_frame, text="فترة السيدات", variable=self.time_period_var, value="women")
        self.time_period_women.pack(side="left", padx=10)
        
        # ملاحظة حول الفترات
        self.note_label = ctk.CTkLabel(self.form_frame, text="ملاحظة: يتم تحديد الفترة تلقائيًا بناءً على الجنس", text_color="gray70")
        self.note_label.pack(anchor="w", pady=(0, 10))
        
        # أزرار الحفظ والإلغاء
        self.buttons_frame = ctk.CTkFrame(self)
        self.buttons_frame.pack(fill="x", padx=20, pady=10)
        
        self.cancel_button = ctk.CTkButton(self.buttons_frame, text="إلغاء", command=self.destroy)
        self.cancel_button.pack(side="left", padx=5)
        
        self.save_button = ctk.CTkButton(self.buttons_frame, text="حفظ", command=self.save_member)
        self.save_button.pack(side="right", padx=5)
        
        # تحميل بيانات العضو في حالة التعديل
        if self.is_edit_mode:
            self.load_member_data()
        
        # تحديث الفترة المفضلة بناءً على الجنس المحدد
        self.update_time_period()
    
    def update_time_period(self, event=None):
        """تحديث الفترة المفضلة تلقائيًا بناءً على الجنس المحدد"""
        gender = self.gender_var.get()
        if gender == "male":
            self.time_period_var.set("men")
            self.time_period_men.configure(state="normal")
            self.time_period_women.configure(state="disabled")
        else:  # female
            self.time_period_var.set("women")
            self.time_period_men.configure(state="disabled")
            self.time_period_women.configure(state="normal")
    
    def load_member_data(self):
        """تحميل بيانات العضو في حالة التعديل"""
        if not self.member:
            return
        
        self.first_name_entry.insert(0, self.member.first_name)
        self.last_name_entry.insert(0, self.member.last_name)
        self.phone_entry.insert(0, self.member.phone)
        self.email_entry.insert(0, self.member.email if self.member.email else "")
        
        # تحميل تاريخ الميلاد
        if self.member.birth_date:
            self.birth_day.set(str(self.member.birth_date.day))
            self.birth_month.set(str(self.member.birth_date.month))
            self.birth_year.set(str(self.member.birth_date.year))
        
        # تحميل الجنس والفترة المفضلة
        self.gender_var.set(self.member.gender)
        self.time_period_var.set(self.member.preferred_time_period)
        self.update_time_period()
    
    def save_member(self):
        """حفظ بيانات العضو"""
        # جمع البيانات من النموذج
        member_data = {
            "first_name": self.first_name_entry.get(),
            "last_name": self.last_name_entry.get(),
            "phone": self.phone_entry.get(),
            "email": self.email_entry.get(),
            "birth_date": datetime.date(
                int(self.birth_year.get()),
                int(self.birth_month.get()),
                int(self.birth_day.get())
            ),
            "gender": self.gender_var.get(),
            "preferred_time_period": self.time_period_var.get()
        }
        
        # التحقق من صلاحية البيانات
        if not member_data["first_name"] or not member_data["last_name"] or not member_data["phone"]:
            messagebox.showerror("خطأ", "يرجى ملء جميع الحقول الإلزامية")
            return
        
        # حفظ البيانات
        if self.is_edit_mode:
            result = self.member_controller.update_member(self.member.id, member_data)
        else:
            result = self.member_controller.create_member(member_data)
        
        if result["success"]:
            messagebox.showinfo("نجاح", "تم حفظ بيانات العضو بنجاح")
            self.destroy()
        else:
            messagebox.showerror("خطأ", result["error"])
```

#### 1.11 ملخص تنفيذ نظام الفصل بين الجنسين

يتضمن تنفيذ نظام الفصل بين الجنسين في تطبيق سطح المكتب العناصر التالية:

1. **نموذج البيانات والتعريفات**:
   - تعريف فئة `TimePeriod` لتمثيل الفترات الزمنية (رجال، سيدات، مشترك).
   - وظائف مساعدة للتحقق من صلاحيات الوصول بناءً على الفترة والجنس.

2. **تعديل نظام المصادقة**:
   - تعديل عملية تسجيل الدخول لتشمل اختيار الفترة الزمنية.
   - التحقق من صلاحية المستخدم للوصول إلى الفترة المطلوبة.
   - تخزين الفترة المحددة مع بيانات المستخدم.

3. **تعديل واجهات المستخدم**:
   - إضافة اختيار الفترة في شاشة تسجيل الدخول.
   - عرض الفترة الحالية في الشريط العلوي للتطبيق.
   - تعديل نماذج إضافة وتعديل الأعضاء لتحديد الفترة المفضلة تلقائيًا بناءً على الجنس.

4. **تعديل وحدات التحكم**:
   - تعديل جميع وحدات التحكم للتحقق من صلاحيات الوصول قبل عرض أو تعديل البيانات.
   - تصفية البيانات المعروضة بناءً على الفترة الحالية للمستخدم.
   - تسجيل الفترة الزمنية مع العمليات المختلفة (الحضور، المبيعات، إلخ).

5. **تعديل التقارير**:
   - تصفية بيانات التقارير بناءً على الفترة الزمنية للمستخدم.
   - عرض إحصائيات منفصلة لكل فترة للمستخدمين ذوي الصلاحيات الكاملة.

هذا التنفيذ يضمن الفصل الكامل بين بيانات فترة الرجال وفترة السيدات، مع السماح للمدراء بالوصول إلى جميع البيانات عند الحاجة.

### 2. نظام المصادقة

```python
# app/controllers/auth_controller.py
class AuthController:
    def __init__(self, db_service, security_service):
        self.db_service = db_service
        self.security_service = security_service
    
    def login(self, username, password):
        user = self.db_service.get_user_by_username(username)
        if user and self.security_service.verify_password(password, user.password_hash):
            return user
        return None
    
    def get_current_user(self):
        # استرجاع المستخدم الحالي من الجلسة المحلية
        return self.db_service.get_user_by_id(self.security_service.get_current_user_id())

# app/views/auth_view.py
class LoginWindow(ctk.CTkToplevel):
    def __init__(self, parent, auth_controller):
        super().__init__(parent)
        self.auth_controller = auth_controller
        self.title("تسجيل الدخول")
        self.geometry("400x300")
        
        # إنشاء عناصر واجهة المستخدم
        self.username_label = ctk.CTkLabel(self, text="اسم المستخدم:")
        self.username_label.pack(pady=10)
        
        self.username_entry = ctk.CTkEntry(self, width=200)
        self.username_entry.pack(pady=5)
        
        self.password_label = ctk.CTkLabel(self, text="كلمة المرور:")
        self.password_label.pack(pady=10)
        
        self.password_entry = ctk.CTkEntry(self, width=200, show="*")
        self.password_entry.pack(pady=5)
        
        self.login_button = ctk.CTkButton(self, text="تسجيل الدخول", command=self.login)
        self.login_button.pack(pady=20)
        
        self.error_label = ctk.CTkLabel(self, text="", text_color="red")
        self.error_label.pack(pady=10)
    
    def login(self):
        username = self.username_entry.get()
        password = self.password_entry.get()
        
        user = self.auth_controller.login(username, password)
        if user:
            self.destroy()  # إغلاق نافذة تسجيل الدخول
            self.master.show_main_window(user)  # عرض النافذة الرئيسية
        else:
            self.error_label.configure(text="اسم المستخدم أو كلمة المرور غير صحيحة")
```

### 2. نظام إدارة الأعضاء

```python
# app/views/members_view.py
class MembersListFrame(ctk.CTkFrame):
    def __init__(self, parent, member_controller):
        super().__init__(parent)
        self.member_controller = member_controller
        
        # إنشاء عناصر واجهة المستخدم
        self.title_label = ctk.CTkLabel(self, text="قائمة الأعضاء", font=ctk.CTkFont(size=20, weight="bold"))
        self.title_label.pack(pady=10)
        
        # شريط البحث
        self.search_frame = ctk.CTkFrame(self)
        self.search_frame.pack(fill="x", padx=10, pady=10)
        
        self.search_label = ctk.CTkLabel(self.search_frame, text="بحث:")
        self.search_label.pack(side="right", padx=5)
        
        self.search_entry = ctk.CTkEntry(self.search_frame, width=200)
        self.search_entry.pack(side="right", padx=5)
        self.search_entry.bind("<KeyRelease>", self.search_members)
        
        self.add_button = ctk.CTkButton(self.search_frame, text="إضافة عضو", command=self.add_member)
        self.add_button.pack(side="left", padx=5)
        
        # جدول الأعضاء
        self.tree_frame = ctk.CTkFrame(self)
        self.tree_frame.pack(fill="both", expand=True, padx=10, pady=10)
        
        columns = ("member_code", "name", "phone", "status", "join_date")
        self.tree = ttk.Treeview(self.tree_frame, columns=columns, show="headings")
        
        # تعيين عناوين الأعمدة
        self.tree.heading("member_code", text="كود العضو")
        self.tree.heading("name", text="الاسم")
        self.tree.heading("phone", text="الهاتف")
        self.tree.heading("status", text="الحالة")
        self.tree.heading("join_date", text="تاريخ الانضمام")
        
        # تعيين أحجام الأعمدة
        self.tree.column("member_code", width=100)
        self.tree.column("name", width=200)
        self.tree.column("phone", width=150)
        self.tree.column("status", width=100)
        self.tree.column("join_date", width=150)
        
        # إضافة شريط التمرير
        scrollbar = ttk.Scrollbar(self.tree_frame, orient="vertical", command=self.tree.yview)
        self.tree.configure(yscrollcommand=scrollbar.set)
        scrollbar.pack(side="right", fill="y")
        self.tree.pack(side="left", fill="both", expand=True)
        
        # ربط حدث النقر المزدوج لعرض تفاصيل العضو
        self.tree.bind("<Double-1>", self.view_member)
        
        # تحميل بيانات الأعضاء
        self.load_members()
    
    def load_members(self):
        # مسح البيانات الحالية
        for item in self.tree.get_children():
            self.tree.delete(item)
        
        # تحميل بيانات الأعضاء من وحدة التحكم
        members = self.member_controller.get_all_members()
        for member in members:
            self.tree.insert("", "end", values=(
                member.member_code,
                f"{member.first_name} {member.last_name}",
                member.phone,
                member.status,
                member.join_date.strftime("%Y-%m-%d")
            ))
    
    def search_members(self, event):
        search_text = self.search_entry.get()
        # مسح البيانات الحالية
        for item in self.tree.get_children():
            self.tree.delete(item)
        
        # البحث عن الأعضاء
        members = self.member_controller.search_members(search_text)
        for member in members:
            self.tree.insert("", "end", values=(
                member.member_code,
                f"{member.first_name} {member.last_name}",
                member.phone,
                member.status,
                member.join_date.strftime("%Y-%m-%d")
            ))
    
    def add_member(self):
        # فتح نافذة إضافة عضو جديد
        add_window = MemberFormWindow(self.winfo_toplevel(), self.member_controller)
        add_window.wait_window()  # انتظار إغلاق النافذة
        self.load_members()  # إعادة تحميل البيانات
    
    def view_member(self, event):
        # الحصول على العنصر المحدد
        selected_item = self.tree.selection()[0]
        member_code = self.tree.item(selected_item, "values")[0]
        
        # فتح نافذة عرض تفاصيل العضو
        member = self.member_controller.get_member_by_code(member_code)
        view_window = MemberDetailsWindow(self.winfo_toplevel(), self.member_controller, member)
        view_window.wait_window()  # انتظار إغلاق النافذة
        self.load_members()  # إعادة تحميل البيانات
```

### 3. نظام الاشتراكات

```python
# app/controllers/subscription_controller.py
class SubscriptionController:
    def __init__(self, db_service, subscription_service):
        self.db_service = db_service
        self.subscription_service = subscription_service
    
    def get_member_subscriptions(self, member_id):
        return self.db_service.get_subscriptions_by_member(member_id)
    
    def create_subscription(self, subscription_data):
        # إنشاء اشتراك جديد
        try:
            # حساب تاريخ البداية والنهاية
            plan = self.db_service.get_plan_by_id(subscription_data['plan_id'])
            start_date = subscription_data.get('start_date', datetime.date.today())
            end_date = self.subscription_service.calculate_end_date(start_date, plan.duration_days)
            
            # حساب السعر النهائي بعد الخصم
            price = plan.price
            discount = subscription_data.get('discount', 0)
            final_price = price - discount
            
            # إنشاء الاشتراك
            subscription = Subscription(
                member_id=subscription_data['member_id'],
                plan_id=subscription_data['plan_id'],
                start_date=start_date,
                end_date=end_date,
                status='active',
                total_sessions=plan.sessions_count,
                remaining_sessions=plan.sessions_count,
                price=price,
                discount=discount,
                final_price=final_price,
                paid_amount=subscription_data.get('paid_amount', 0),
                payment_status='unpaid' if final_price > subscription_data.get('paid_amount', 0) else 'paid'
            )
            
            # حفظ الاشتراك في قاعدة البيانات
            self.db_service.add_subscription(subscription)
            
            # إنشاء فاتورة للاشتراك
            if subscription_data.get('create_invoice', True):
                self.create_subscription_invoice(subscription)
            
            return {'success': True, 'subscription': subscription}
        except Exception as e:
            return {'success': False, 'error': str(e)}

# app/views/subscription_view.py
class SubscriptionFormWindow(ctk.CTkToplevel):
    def __init__(self, parent, subscription_controller, member=None):
        super().__init__(parent)
        self.subscription_controller = subscription_controller
        self.member = member
        
        self.title("إضافة اشتراك جديد")
        self.geometry("600x500")
        
        # إنشاء عناصر واجهة المستخدم
        self.title_label = ctk.CTkLabel(self, text="إضافة اشتراك جديد", font=ctk.CTkFont(size=20, weight="bold"))
        self.title_label.pack(pady=10)
        
        # إطار النموذج
        self.form_frame = ctk.CTkFrame(self)
        self.form_frame.pack(fill="both", expand=True, padx=20, pady=10)
        
        # العضو
        self.member_label = ctk.CTkLabel(self.form_frame, text="العضو:")
        self.member_label.grid(row=0, column=0, padx=10, pady=10, sticky="e")
        
        if member:
            self.member_value = ctk.CTkLabel(self.form_frame, text=f"{member.first_name} {member.last_name}")
            self.member_value.grid(row=0, column=1, padx=10, pady=10, sticky="w")
        else:
            self.member_button = ctk.CTkButton(self.form_frame, text="اختيار عضو", command=self.select_member)
            self.member_button.grid(row=0, column=1, padx=10, pady=10, sticky="w")
            self.selected_member = None
        
        # خطة العضوية
        self.plan_label = ctk.CTkLabel(self.form_frame, text="خطة العضوية:")
        self.plan_label.grid(row=1, column=0, padx=10, pady=10, sticky="e")
        
        # الحصول على خطط العضوية المتاحة
        self.plans = self.subscription_controller.db_service.get_all_plans()
        plan_names = [plan.name for plan in self.plans]
        
        self.plan_combobox = ctk.CTkComboBox(self.form_frame, values=plan_names, width=200)
        self.plan_combobox.grid(row=1, column=1, padx=10, pady=10, sticky="w")
        self.plan_combobox.bind("<<ComboboxSelected>>", self.update_price)
        
        # تاريخ البداية
        self.start_date_label = ctk.CTkLabel(self.form_frame, text="تاريخ البداية:")
        self.start_date_label.grid(row=2, column=0, padx=10, pady=10, sticky="e")
        
        self.start_date_frame = ctk.CTkFrame(self.form_frame)
        self.start_date_frame.grid(row=2, column=1, padx=10, pady=10, sticky="w")
        
        today = datetime.date.today()
        
        self.start_day = ctk.CTkComboBox(self.start_date_frame, values=[str(i) for i in range(1, 32)], width=60)
        self.start_day.set(str(today.day))
        self.start_day.pack(side="right", padx=2)
        
        self.start_month = ctk.CTkComboBox(self.start_date_frame, values=[str(i) for i in range(1, 13)], width=60)
        self.start_month.set(str(today.month))
        self.start_month.pack(side="right", padx=2)
        
        self.start_year = ctk.CTkComboBox(self.start_date_frame, values=[str(i) for i in range(today.year - 5, today.year + 6)], width=80)
        self.start_year.set(str(today.year))
        self.start_year.pack(side="right", padx=2)
        
        # السعر
        self.price_label = ctk.CTkLabel(self.form_frame, text="السعر:")
        self.price_label.grid(row=3, column=0, padx=10, pady=10, sticky="e")
        
        self.price_value = ctk.CTkLabel(self.form_frame, text="0")
        self.price_value.grid(row=3, column=1, padx=10, pady=10, sticky="w")
        
        # الخصم
        self.discount_label = ctk.CTkLabel(self.form_frame, text="الخصم:")
        self.discount_label.grid(row=4, column=0, padx=10, pady=10, sticky="e")
        
        self.discount_entry = ctk.CTkEntry(self.form_frame, width=100)
        self.discount_entry.insert(0, "0")
        self.discount_entry.grid(row=4, column=1, padx=10, pady=10, sticky="w")
        self.discount_entry.bind("<KeyRelease>", self.update_final_price)
        
        # السعر النهائي
        self.final_price_label = ctk.CTkLabel(self.form_frame, text="السعر النهائي:")
        self.final_price_label.grid(row=5, column=0, padx=10, pady=10, sticky="e")
        
        self.final_price_value = ctk.CTkLabel(self.form_frame, text="0")
        self.final_price_value.grid(row=5, column=1, padx=10, pady=10, sticky="w")
        
        # المبلغ المدفوع
        self.paid_amount_label = ctk.CTkLabel(self.form_frame, text="المبلغ المدفوع:")
        self.paid_amount_label.grid(row=6, column=0, padx=10, pady=10, sticky="e")
        
        self.paid_amount_entry = ctk.CTkEntry(self.form_frame, width=100)
        self.paid_amount_entry.insert(0, "0")
        self.paid_amount_entry.grid(row=6, column=1, padx=10, pady=10, sticky="w")
        
        # إنشاء فاتورة
        self.create_invoice_var = ctk.BooleanVar(value=True)
        self.create_invoice_checkbox = ctk.CTkCheckBox(self.form_frame, text="إنشاء فاتورة", variable=self.create_invoice_var)
        self.create_invoice_checkbox.grid(row=7, column=1, padx=10, pady=10, sticky="w")
        
        # أزرار الإجراءات
        self.buttons_frame = ctk.CTkFrame(self)
        self.buttons_frame.pack(fill="x", padx=20, pady=10)
        
        self.cancel_button = ctk.CTkButton(self.buttons_frame, text="إلغاء", command=self.destroy)
        self.cancel_button.pack(side="right", padx=10)
        
        self.save_button = ctk.CTkButton(self.buttons_frame, text="حفظ", command=self.save_subscription)
        self.save_button.pack(side="right", padx=10)
        
        # تحديث السعر عند اختيار خطة
        if self.plans:
            self.plan_combobox.set(self.plans[0].name)
            self.update_price(None)
    
    def select_member(self):
        # فتح نافذة اختيار عضو
        select_window = MemberSelectorWindow(self, self.subscription_controller.db_service)
        self.wait_window(select_window)
        
        if hasattr(select_window, 'selected_member') and select_window.selected_member:
            self.selected_member = select_window.selected_member
            self.member_button.configure(text=f"{self.selected_member.first_name} {self.selected_member.last_name}")
    
    def update_price(self, event):
        plan_name = self.plan_combobox.get()
        for plan in self.plans:
            if plan.name == plan_name:
                self.price_value.configure(text=str(plan.price))
                self.update_final_price(None)
                break
    
    def update_final_price(self, event):
        try:
            price = float(self.price_value.cget("text"))
            discount = float(self.discount_entry.get() or 0)
            final_price = price - discount
            if final_price < 0:
                final_price = 0
            self.final_price_value.configure(text=str(final_price))
        except ValueError:
            self.final_price_value.configure(text="خطأ في القيم")
    
    def save_subscription(self):
        try:
            # التحقق من اختيار عضو
            member_id = self.member.id if self.member else (self.selected_member.id if self.selected_member else None)
            if not member_id:
                messagebox.showerror("خطأ", "يرجى اختيار عضو")
                return
            
            # الحصول على خطة العضوية المحددة
            plan_name = self.plan_combobox.get()
            plan_id = None
            for plan in self.plans:
                if plan.name == plan_name:
                    plan_id = plan.id
                    break
            
            if not plan_id:
                messagebox.showerror("خطأ", "يرجى اختيار خطة عضوية صالحة")
                return
            
            # تحويل تاريخ البداية
            try:
                start_date = datetime.date(
                    int(self.start_year.get()),
                    int(self.start_month.get()),
                    int(self.start_day.get())
                )
            except ValueError:
                messagebox.showerror("خطأ", "تاريخ البداية غير صالح")
                return
            
            # الحصول على قيم النموذج
            discount = float(self.discount_entry.get() or 0)
            paid_amount = float(self.paid_amount_entry.get() or 0)
            create_invoice = self.create_invoice_var.get()
            
            # إنشاء بيانات الاشتراك
            subscription_data = {
                'member_id': member_id,
                'plan_id': plan_id,
                'start_date': start_date,
                'discount': discount,
                'paid_amount': paid_amount,
                'create_invoice': create_invoice
            }
            
            # حفظ الاشتراك
            result = self.subscription_controller.create_subscription(subscription_data)
            
            if result['success']:
                messagebox.showinfo("نجاح", "تم إنشاء الاشتراك بنجاح")
                self.destroy()
            else:
                messagebox.showerror("خطأ", f"حدث خطأ: {result['error']}")
        
        except Exception as e:
            messagebox.showerror("خطأ", f"حدث خطأ غير متوقع: {str(e)}")
```

## 🔄 تحويل تدفقات العمل الرئيسية

### 1. تسجيل الحضور والانصراف

```python
# app/views/attendance_view.py
class AttendanceFrame(ctk.CTkFrame):
    def __init__(self, parent, attendance_controller):
        super().__init__(parent)
        self.attendance_controller = attendance_controller
        
        # إنشاء عناصر واجهة المستخدم
        self.title_label = ctk.CTkLabel(self, text="تسجيل الحضور والانصراف", font=ctk.CTkFont(size=20, weight="bold"))
        self.title_label.pack(pady=10)
        
        # إطار البحث
        self.search_frame = ctk.CTkFrame(self)
        self.search_frame.pack(fill="x", padx=20, pady=10)
        
        self.search_label = ctk.CTkLabel(self.search_frame, text="كود العضو:")
        self.search_label.pack(side="right", padx=5)
        
        self.search_entry = ctk.CTkEntry(self.search_frame, width=200)
        self.search_entry.pack(side="right", padx=5)
        self.search_entry.bind("<Return>", self.search_member)
        
        self.search_button = ctk.CTkButton(self.search_frame, text="بحث", command=lambda: self.search_member(None))
        self.search_button.pack(side="right", padx=5)
        
        # إطار معلومات العضو
        self.member_frame = ctk.CTkFrame(self)
        self.member_frame.pack(fill="x", padx=20, pady=10)
        
        self.member_info_label = ctk.CTkLabel(self.member_frame, text="معلومات العضو", font=ctk.CTkFont(weight="bold"))
        self.member_info_label.pack(pady=5)
        
        self.member_name_label = ctk.CTkLabel(self.member_frame, text="الاسم: ")
        self.member_name_label.pack(pady=2)
        
        self.member_code_label = ctk.CTkLabel(self.member_frame, text="كود العضو: ")
        self.member_code_label.pack(pady=2)
        
        self.subscription_status_label = ctk.CTkLabel(self.member_frame, text="حالة الاشتراك: ")
        self.subscription_status_label.pack(pady=2)
        
        self.remaining_sessions_label = ctk.CTkLabel(self.member_frame, text="الحصص المتبقية: ")
        self.remaining_sessions_label.pack(pady=2)
        
        # إطار الإجراءات
        self.actions_frame = ctk.CTkFrame(self)
        self.actions_frame.pack(fill="x", padx=20, pady=10)
        
        self.check_in_button = ctk.CTkButton(self.actions_frame, text="تسجيل الحضور", command=self.check_in)
        self.check_in_button.pack(side="right", padx=10, pady=10)
        
        self.check_out_button = ctk.CTkButton(self.actions_frame, text="تسجيل الانصراف", command=self.check_out)
        self.check_out_button.pack(side="right", padx=10, pady=10)
        
        # تعطيل الأزرار في البداية
        self.check_in_button.configure(state="disabled")
        self.check_out_button.configure(state="disabled")
        
        # حالة العضو الحالي
        self.current_member = None
        self.current_attendance = None
    
    def search_member(self, event):
        member_code = self.search_entry.get()
        if not member_code:
            messagebox.showwarning("تنبيه", "يرجى إدخال كود العضو")
            return
        
        # البحث عن العضو
        member = self.attendance_controller.get_member_by_code(member_code)
        if not member:
            messagebox.showerror("خطأ", "لم يتم العثور على العضو")
            return
        
        # عرض معلومات العضو
        self.current_member = member
        self.member_name_label.configure(text=f"الاسم: {member.first_name} {member.last_name}")
        self.member_code_label.configure(text=f"كود العضو: {member.member_code}")
        
        # التحقق من حالة الاشتراك
        subscription = self.attendance_controller.get_active_subscription(member.id)
        if subscription:
            self.subscription_status_label.configure(text=f"حالة الاشتراك: {subscription.status}")
            self.remaining_sessions_label.configure(text=f"الحصص المتبقية: {subscription.remaining_sessions}")
            
            # التحقق من صلاحية الاشتراك
            validity_check = self.attendance_controller.check_subscription_validity(subscription.id)
            if validity_check['valid']:
                # التحقق من وجود حضور مفتوح
                attendance = self.attendance_controller.get_open_attendance(member.id)
                if attendance:
                    self.current_attendance = attendance
                    self.check_in_button.configure(state="disabled")
                    self.check_out_button.configure(state="normal")
                else:
                    self.current_attendance = None
                    self.check_in_button.configure(state="normal")
                    self.check_out_button.configure(state="disabled")
            else:
                messagebox.showwarning("تنبيه", f"الاشتراك غير صالح: {validity_check['reason']}")
                self.check_in_button.configure(state="disabled")
                self.check_out_button.configure(state="disabled")
        else:
            self.subscription_status_label.configure(text="حالة الاشتراك: لا يوجد اشتراك نشط")
            self.remaining_sessions_label.configure(text="الحصص المتبقية: 0")
            messagebox.showwarning("تنبيه", "لا يوجد اشتراك نشط لهذا العضو")
            self.check_in_button.configure(state="disabled")
            self.check_out_button.configure(state="disabled")
    
    def check_in(self):
        if not self.current_member:
            return
        
        # تسجيل الحضور
        result = self.attendance_controller.check_in(self.current_member.id)
        if result['success']:
            messagebox.showinfo("نجاح", "تم تسجيل الحضور بنجاح")
            self.current_attendance = result['attendance']
            self.check_in_button.configure(state="disabled")
            self.check_out_button.configure(state="normal")
            
            # تحديث عدد الحصص المتبقية
            subscription = self.attendance_controller.get_active_subscription(self.current_member.id)
            if subscription:
                self.remaining_sessions_label.configure(text=f"الحصص المتبقية: {subscription.remaining_sessions}")
        else:
            messagebox.showerror("خطأ", f"حدث خطأ: {result['error']}")
    
    def check_out(self):
        if not self.current_attendance:
            return
        
        # تسجيل الانصراف
        result = self.attendance_controller.check_out(self.current_attendance.id)
        if result['success']:
            messagebox.showinfo("نجاح", "تم تسجيل الانصراف بنجاح")
            self.current_attendance = None
            self.check_in_button.configure(state="normal")
            self.check_out_button.configure(state="disabled")
        else:
            messagebox.showerror("خطأ", f"حدث خطأ: {result['error']}")
```

### 2. إنشاء وطباعة الفواتير

```python
# app/controllers/invoice_controller.py
class InvoiceController:
    def __init__(self, db_service, invoice_service):
        self.db_service = db_service
        self.invoice_service = invoice_service
    
    def create_invoice(self, invoice_data):
        try:
            # إنشاء فاتورة جديدة
            invoice = Invoice(
                member_id=invoice_data['member_id'],
                invoice_date=datetime.date.today(),
                invoice_number=self.invoice_service.generate_invoice_number(),
                total_amount=invoice_data['total_amount'],
                paid_amount=invoice_data.get('paid_amount', 0),
                payment_status='unpaid' if invoice_data['total_amount'] > invoice_data.get('paid_amount', 0) else 'paid',
                notes=invoice_data.get('notes', '')
            )
            
            # إضافة عناصر الفاتورة
            invoice_items = []
            for item_data in invoice_data['items']:
                item = InvoiceItem(
                    description=item_data['description'],
                    quantity=item_data['quantity'],
                    unit_price=item_data['unit_price'],
                    total_price=item_data['quantity'] * item_data['unit_price']
                )
                invoice_items.append(item)
            
            # حفظ الفاتورة وعناصرها في قاعدة البيانات
            self.db_service.add_invoice(invoice, invoice_items)
            
            return {'success': True, 'invoice': invoice}
        except Exception as e:
            return {'success': False, 'error': str(e)}
    
    def generate_invoice_pdf(self, invoice_id):
        try:
            # الحصول على الفاتورة وعناصرها
            invoice = self.db_service.get_invoice_by_id(invoice_id)
            if not invoice:
                return {'success': False, 'error': 'الفاتورة غير موجودة'}
            
            # إنشاء ملف PDF
            pdf_path = self.invoice_service.generate_invoice_pdf(invoice)
            
            return {'success': True, 'pdf_path': pdf_path}
        except Exception as e:
            return {'success': False, 'error': str(e)}

# app/views/invoice_view.py
class InvoiceFormWindow(ctk.CTkToplevel):
    def __init__(self, parent, invoice_controller, member=None):
        super().__init__(parent)
        self.invoice_controller = invoice_controller
        self.member = member
        
        self.title("إنشاء فاتورة جديدة")
        self.geometry("800x600")
        
        # إنشاء عناصر واجهة المستخدم
        self.title_label = ctk.CTkLabel(self, text="إنشاء فاتورة جديدة", font=ctk.CTkFont(size=20, weight="bold"))
        self.title_label.pack(pady=10)
        
        # إطار معلومات الفاتورة
        self.info_frame = ctk.CTkFrame(self)
        self.info_frame.pack(fill="x", padx=20, pady=10)
        
        # العضو
        self.member_label = ctk.CTkLabel(self.info_frame, text="العضو:")
        self.member_label.grid(row=0, column=0, padx=10, pady=10, sticky="e")
        
        if member:
            self.member_value = ctk.CTkLabel(self.info_frame, text=f"{member.first_name} {member.last_name}")
            self.member_value.grid(row=0, column=1, padx=10, pady=10, sticky="w")
        else:
            self.member_button = ctk.CTkButton(self.info_frame, text="اختيار عضو", command=self.select_member)
            self.member_button.grid(row=0, column=1, padx=10, pady=10, sticky="w")
            self.selected_member = None
        
        # التاريخ
        self.date_label = ctk.CTkLabel(self.info_frame, text="التاريخ:")
        self.date_label.grid(row=0, column=2, padx=10, pady=10, sticky="e")
        
        today = datetime.date.today()
        self.date_value = ctk.CTkLabel(self.info_frame, text=today.strftime("%Y-%m-%d"))
        self.date_value.grid(row=0, column=3, padx=10, pady=10, sticky="w")
        
        # الملاحظات
        self.notes_label = ctk.CTkLabel(self.info_frame, text="ملاحظات:")
        self.notes_label.grid(row=1, column=0, padx=10, pady=10, sticky="e")
        
        self.notes_entry = ctk.CTkEntry(self.info_frame, width=300)
        self.notes_entry.grid(row=1, column=1, columnspan=3, padx=10, pady=10, sticky="w")
        
        # إطار عناصر الفاتورة
        self.items_frame = ctk.CTkFrame(self)
        self.items_frame.pack(fill="both", expand=True, padx=20, pady=10)
        
        self.items_label = ctk.CTkLabel(self.items_frame, text="عناصر الفاتورة", font=ctk.CTkFont(weight="bold"))
        self.items_label.pack(pady=5)
        
        # جدول العناصر
        self.tree_frame = ctk.CTkFrame(self.items_frame)
        self.tree_frame.pack(fill="both", expand=True, padx=10, pady=5)
        
        columns = ("description", "quantity", "unit_price", "total_price")
        self.tree = ttk.Treeview(self.tree_frame, columns=columns, show="headings")
        
        # تعيين عناوين الأعمدة
        self.tree.heading("description", text="الوصف")
        self.tree.heading("quantity", text="الكمية")
        self.tree.heading("unit_price", text="سعر الوحدة")
        self.tree.heading("total_price", text="السعر الإجمالي")
        
        # تعيين أحجام الأعمدة
        self.tree.column("description", width=300)
        self.tree.column("quantity", width=100)
        self.tree.column("unit_price", width=100)
        self.tree.column("total_price", width=100)
        
        # إضافة شريط التمرير
        scrollbar = ttk.Scrollbar(self.tree_frame, orient="vertical", command=self.tree.yview)
        self.tree.configure(yscrollcommand=scrollbar.set)
        scrollbar.pack(side="right", fill="y")
        self.tree.pack(side="left", fill="both", expand=True)
        
        # أزرار إدارة العناصر
        self.item_buttons_frame = ctk.CTkFrame(self.items_frame)
        self.item_buttons_frame.pack(fill="x", padx=10, pady=5)
        
        self.add_item_button = ctk.CTkButton(self.item_buttons_frame, text="إضافة عنصر", command=self.add_item)
        self.add_item_button.pack(side="left", padx=5)
        
        self.edit_item_button = ctk.CTkButton(self.item_buttons_frame, text="تعديل عنصر", command=self.edit_item)
        self.edit_item_button.pack(side="left", padx=5)
        
        self.remove_item_button = ctk.CTkButton(self.item_buttons_frame, text="حذف عنصر", command=self.remove_item)
        self.remove_item_button.pack(side="left", padx=5)
        
        # إطار المجاميع
        self.totals_frame = ctk.CTkFrame(self)
        self.totals_frame.pack(fill="x", padx=20, pady=10)
        
        # المجموع
        self.total_label = ctk.CTkLabel(self.totals_frame, text="المجموع:")
        self.total_label.grid(row=0, column=0, padx=10, pady=5, sticky="e")
        
        self.total_value = ctk.CTkLabel(self.totals_frame, text="0")
        self.total_value.grid(row=0, column=1, padx=10, pady=5, sticky="w")
        
        # المبلغ المدفوع
        self.paid_amount_label = ctk.CTkLabel(self.totals_frame, text="المبلغ المدفوع:")
        self.paid_amount_label.grid(row=1, column=0, padx=10, pady=5, sticky="e")
        
        self.paid_amount_entry = ctk.CTkEntry(self.totals_frame, width=100)
        self.paid_amount_entry.insert(0, "0")
        self.paid_amount_entry.grid(row=1, column=1, padx=10, pady=5, sticky="w")
        
        # أزرار الإجراءات
        self.buttons_frame = ctk.CTkFrame(self)
        self.buttons_frame.pack(fill="x", padx=20, pady=10)
        
        self.cancel_button = ctk.CTkButton(self.buttons_frame, text="إلغاء", command=self.destroy)
        self.cancel_button.pack(side="right", padx=10)
        
        self.save_button = ctk.CTkButton(self.buttons_frame, text="حفظ", command=self.save_invoice)
        self.save_button.pack(side="right", padx=10)
        
        self.save_print_button = ctk.CTkButton(self.buttons_frame, text="حفظ وطباعة", command=self.save_and_print)
        self.save_print_button.pack(side="right", padx=10)
        
        # قائمة العناصر
        self.invoice_items = []
    
    def select_member(self):
        # فتح نافذة اختيار عضو
        select_window = MemberSelectorWindow(self, self.invoice_controller.db_service)
        self.wait_window(select_window)
        
        if hasattr(select_window, 'selected_member') and select_window.selected_member:
            self.selected_member = select_window.selected_member
            self.member_button.configure(text=f"{self.selected_member.first_name} {self.selected_member.last_name}")
    
    def add_item(self):
        # فتح نافذة إضافة عنصر
        item_window = InvoiceItemWindow(self)
        self.wait_window(item_window)
        
        if hasattr(item_window, 'item_data') and item_window.item_data:
            # إضافة العنصر إلى القائمة
            self.invoice_items.append(item_window.item_data)
            
            # إضافة العنصر إلى الجدول
            self.tree.insert("", "end", values=(
                item_window.item_data['description'],
                item_window.item_data['quantity'],
                item_window.item_data['unit_price'],
                item_window.item_data['quantity'] * item_window.item_data['unit_price']
            ))
            
            # تحديث المجموع
            self.update_total()
    
    def edit_item(self):
        # التحقق من تحديد عنصر
        selected_items = self.tree.selection()
        if not selected_items:
            messagebox.showwarning("تنبيه", "يرجى تحديد عنصر للتعديل")
            return
        
        # الحصول على العنصر المحدد
        selected_item = selected_items[0]
        item_index = self.tree.index(selected_item)
        item_data = self.invoice_items[item_index]
        
        # فتح نافذة تعديل العنصر
        item_window = InvoiceItemWindow(self, item_data)
        self.wait_window(item_window)
        
        if hasattr(item_window, 'item_data') and item_window.item_data:
            # تحديث العنصر في القائمة
            self.invoice_items[item_index] = item_window.item_data
            
            # تحديث العنصر في الجدول
            self.tree.item(selected_item, values=(
                item_window.item_data['description'],
                item_window.item_data['quantity'],
                item_window.item_data['unit_price'],
                item_window.item_data['quantity'] * item_window.item_data['unit_price']
            ))
            
            # تحديث المجموع
            self.update_total()
    
    def remove_item(self):
        # التحقق من تحديد عنصر
        selected_items = self.tree.selection()
        if not selected_items:
            messagebox.showwarning("تنبيه", "يرجى تحديد عنصر للحذف")
            return
        
        # الحصول على العنصر المحدد
        selected_item = selected_items[0]
        item_index = self.tree.index(selected_item)
        
        # حذف العنصر من القائمة
        self.invoice_items.pop(item_index)
        
        # حذف العنصر من الجدول
        self.tree.delete(selected_item)
        
        # تحديث المجموع
        self.update_total()
    
    def update_total(self):
        # حساب المجموع
        total = sum(item['quantity'] * item['unit_price'] for item in self.invoice_items)
        self.total_value.configure(text=str(total))
    
    def save_invoice(self):
        try:
            # التحقق من اختيار عضو
            member_id = self.member.id if self.member else (self.selected_member.id if self.selected_member else None)
            if not member_id:
                messagebox.showerror("خطأ", "يرجى اختيار عضو")
                return
            
            # التحقق من وجود عناصر
            if not self.invoice_items:
                messagebox.showwarning("تنبيه", "يرجى إضافة عناصر للفاتورة")
                return
            
            # الحصول على قيم النموذج
            total_amount = float(self.total_value.cget("text"))
            paid_amount = float(self.paid_amount_entry.get() or 0)
            notes = self.notes_entry.get()
            
            # إنشاء بيانات الفاتورة
            invoice_data = {
                'member_id': member_id,
                'total_amount': total_amount,
                'paid_amount': paid_amount,
                'notes': notes,
                'items': self.invoice_items
            }
            
            # حفظ الفاتورة
            result = self.invoice_controller.create_invoice(invoice_data)
            
            if result['success']:
                messagebox.showinfo("نجاح", "تم إنشاء الفاتورة بنجاح")
                self.destroy()
                return result['invoice']
            else:
                messagebox.showerror("خطأ", f"حدث خطأ: {result['error']}")
                return None
        
        except Exception as e:
            messagebox.showerror("خطأ", f"حدث خطأ غير متوقع: {str(e)}")
            return None
    
    def save_and_print(self):
        # حفظ الفاتورة
        invoice = self.save_invoice()
        if not invoice:
            return
        
        # إنشاء ملف PDF
        result = self.invoice_controller.generate_invoice_pdf(invoice.id)
        if result['success']:
            # فتح ملف PDF
            os.startfile(result['pdf_path'])
        else:
            messagebox.showerror("خطأ", f"حدث خطأ أثناء إنشاء ملف PDF: {result['error']}")
```

### 3. عرض وإنشاء التقارير

```python
# app/controllers/report_controller.py
class ReportController:
    def __init__(self, db_service, report_service):
        self.db_service = db_service
        self.report_service = report_service
    
    def generate_financial_report(self, start_date, end_date, report_type='summary'):
        try:
            # الحصول على البيانات المالية
            invoices = self.db_service.get_invoices_by_date_range(start_date, end_date)
            payments = self.db_service.get_payments_by_date_range(start_date, end_date)
            expenses = self.db_service.get_expenses_by_date_range(start_date, end_date)
            
            # إنشاء التقرير
            report_data = self.report_service.generate_financial_report(
                invoices, payments, expenses, report_type
            )
            
            return {'success': True, 'report_data': report_data}
        except Exception as e:
            return {'success': False, 'error': str(e)}
    
    def generate_member_report(self, start_date, end_date, report_type='summary'):
        try:
            # الحصول على بيانات الأعضاء
            members = self.db_service.get_members_by_date_range(start_date, end_date)
            subscriptions = self.db_service.get_subscriptions_by_date_range(start_date, end_date)
            attendance = self.db_service.get_attendance_by_date_range(start_date, end_date)
            
            # إنشاء التقرير
            report_data = self.report_service.generate_member_report(
                members, subscriptions, attendance, report_type
            )
            
            return {'success': True, 'report_data': report_data}
        except Exception as e:
            return {'success': False, 'error': str(e)}
    
    def export_report_to_excel(self, report_data, file_path):
        try:
            # تصدير التقرير إلى ملف Excel
            self.report_service.export_to_excel(report_data, file_path)
            return {'success': True, 'file_path': file_path}
        except Exception as e:
            return {'success': False, 'error': str(e)}

# app/views/report_view.py
class ReportFrame(ctk.CTkFrame):
    def __init__(self, parent, report_controller):
        super().__init__(parent)
        self.report_controller = report_controller
        
        # إنشاء عناصر واجهة المستخدم
        self.title_label = ctk.CTkLabel(self, text="التقارير", font=ctk.CTkFont(size=20, weight="bold"))
        self.title_label.pack(pady=10)
        
        # إطار معايير التقرير
        self.criteria_frame = ctk.CTkFrame(self)
        self.criteria_frame.pack(fill="x", padx=20, pady=10)
        
        # نوع التقرير
        self.report_type_label = ctk.CTkLabel(self.criteria_frame, text="نوع التقرير:")
        self.report_type_label.grid(row=0, column=0, padx=10, pady=10, sticky="e")
        
        self.report_type_var = ctk.StringVar(value="financial")
        self.report_type_financial = ctk.CTkRadioButton(self.criteria_frame, text="تقرير مالي", variable=self.report_type_var, value="financial")
        self.report_type_financial.grid(row=0, column=1, padx=10, pady=10, sticky="w")
        
        self.report_type_member = ctk.CTkRadioButton(self.criteria_frame, text="تقرير الأعضاء", variable=self.report_type_var, value="member")
        self.report_type_member.grid(row=0, column=2, padx=10, pady=10, sticky="w")
        
        # مستوى التفاصيل
        self.detail_level_label = ctk.CTkLabel(self.criteria_frame, text="مستوى التفاصيل:")
        self.detail_level_label.grid(row=1, column=0, padx=10, pady=10, sticky="e")
        
        self.detail_level_var = ctk.StringVar(value="summary")
        self.detail_level_summary = ctk.CTkRadioButton(self.criteria_frame, text="ملخص", variable=self.detail_level_var, value="summary")
        self.detail_level_summary.grid(row=1, column=1, padx=10, pady=10, sticky="w")
        
        self.detail_level_detailed = ctk.CTkRadioButton(self.criteria_frame, text="تفصيلي", variable=self.detail_level_var, value="detailed")
        self.detail_level_detailed.grid(row=1, column=2, padx=10, pady=10, sticky="w")
        
        # الفترة الزمنية
        self.date_range_label = ctk.CTkLabel(self.criteria_frame, text="الفترة الزمنية:")
        self.date_range_label.grid(row=2, column=0, padx=10, pady=10, sticky="e")
        
        self.date_range_var = ctk.StringVar(value="month")
        self.date_range_month = ctk.CTkRadioButton(self.criteria_frame, text="الشهر الحالي", variable=self.date_range_var, value="month")
        self.date_range_month.grid(row=2, column=1, padx=10, pady=10, sticky="w")
        
        self.date_range_quarter = ctk.CTkRadioButton(self.criteria_frame, text="الربع الحالي", variable=self.date_range_var, value="quarter")
        self.date_range_quarter.grid(row=2, column=2, padx=10, pady=10, sticky="w")
        
        self.date_range_year = ctk.CTkRadioButton(self.criteria_frame, text="السنة الحالية", variable=self.date_range_var, value="year")
        self.date_range_year.grid(row=2, column=3, padx=10, pady=10, sticky="w")
        
        self.date_range_custom = ctk.CTkRadioButton(self.criteria_frame, text="مخصص", variable=self.date_range_var, value="custom")
        self.date_range_custom.grid(row=2, column=4, padx=10, pady=10, sticky="w")
        
        # تواريخ مخصصة
        self.custom_dates_frame = ctk.CTkFrame(self.criteria_frame)
        self.custom_dates_frame.grid(row=3, column=1, columnspan=4, padx=10, pady=10, sticky="w")
        
        self.start_date_label = ctk.CTkLabel(self.custom_dates_frame, text="من:")
        self.start_date_label.pack(side="left", padx=5)
        
        today = datetime.date.today()
        
        self.start_date_frame = ctk.CTkFrame(self.custom_dates_frame)
        self.start_date_frame.pack(side="left", padx=5)
        
        self.start_day = ctk.CTkComboBox(self.start_date_frame, values=[str(i) for i in range(1, 32)], width=60)
        self.start_day.set("1")
        self.start_day.pack(side="right", padx=2)
        
        self.start_month = ctk.CTkComboBox(self.start_date_frame, values=[str(i) for i in range(1, 13)], width=60)
        self.start_month.set(str(today.month))
        self.start_month.pack(side="right", padx=2)
        
        self.start_year = ctk.CTkComboBox(self.start_date_frame, values=[str(i) for i in range(today.year - 5, today.year + 1)], width=80)
        self.start_year.set(str(today.year))
        self.start_year.pack(side="right", padx=2)
        
        self.end_date_label = ctk.CTkLabel(self.custom_dates_frame, text="إلى:")
        self.end_date_label.pack(side="left", padx=5)
        
        self.end_date_frame = ctk.CTkFrame(self.custom_dates_frame)
        self.end_date_frame.pack(side="left", padx=5)
        
        self.end_day = ctk.CTkComboBox(self.end_date_frame, values=[str(i) for i in range(1, 32)], width=60)
        self.end_day.set(str(today.day))
        self.end_day.pack(side="right", padx=2)
        
        self.end_month = ctk.CTkComboBox(self.end_date_frame, values=[str(i) for i in range(1, 13)], width=60)
        self.end_month.set(str(today.month))
        self.end_month.pack(side="right", padx=2)
        
        self.end_year = ctk.CTkComboBox(self.end_date_frame, values=[str(i) for i in range(today.year - 5, today.year + 1)], width=80)
        self.end_year.set(str(today.year))
        self.end_year.pack(side="right", padx=2)
        
        # أزرار الإجراءات
        self.actions_frame = ctk.CTkFrame(self)
        self.actions_frame.pack(fill="x", padx=20, pady=10)
        
        self.generate_button = ctk.CTkButton(self.actions_frame, text="إنشاء التقرير", command=self.generate_report)
        self.generate_button.pack(side="left", padx=10)
        
        self.export_excel_button = ctk.CTkButton(self.actions_frame, text="تصدير إلى Excel", command=self.export_to_excel)
        self.export_excel_button.pack(side="left", padx=10)
        self.export_excel_button.configure(state="disabled")
        
        self.export_pdf_button = ctk.CTkButton(self.actions_frame, text="تصدير إلى PDF", command=self.export_to_pdf)
        self.export_pdf_button.pack(side="left", padx=10)
        self.export_pdf_button.configure(state="disabled")
        
        # إطار عرض التقرير
        self.report_frame = ctk.CTkFrame(self)
        self.report_frame.pack(fill="both", expand=True, padx=20, pady=10)
        
        self.report_label = ctk.CTkLabel(self.report_frame, text="نتائج التقرير", font=ctk.CTkFont(weight="bold"))
        self.report_label.pack(pady=5)
        
        # مساحة عرض التقرير (تختلف حسب نوع التقرير)
        self.report_content_frame = ctk.CTkFrame(self.report_frame)
        self.report_content_frame.pack(fill="both", expand=True, padx=10, pady=5)
        
        # حالة التقرير الحالي
        self.current_report_data = None
    
    def generate_report(self):
        try:
            # الحصول على معايير التقرير
            report_type = self.report_type_var.get()
            detail_level = self.detail_level_var.get()
            date_range = self.date_range_var.get()
            
            # تحديد تاريخ البداية والنهاية
            today = datetime.date.today()
            start_date = None
            end_date = today
            
            if date_range == "month":
                start_date = datetime.date(today.year, today.month, 1)
            elif date_range == "quarter":
                quarter_month = ((today.month - 1) // 3) * 3 + 1
                start_date = datetime.date(today.year, quarter_month, 1)
            elif date_range == "year":
                start_date = datetime.date(today.year, 1, 1)
            elif date_range == "custom":
                try:
                    start_date = datetime.date(
                        int(self.start_year.get()),
                        int(self.start_month.get()),
                        int(self.start_day.get())
                    )
                    end_date = datetime.date(
                        int(self.end_year.get()),
                        int(self.end_month.get()),
                        int(self.end_day.get())
                    )
                except ValueError:
                    messagebox.showerror("خطأ", "تاريخ غير صالح")
                    return
            
            # إنشاء التقرير
            if report_type == "financial":
                result = self.report_controller.generate_financial_report(start_date, end_date, detail_level)
            else:  # member
                result = self.report_controller.generate_member_report(start_date, end_date, detail_level)
            
            if result['success']:
                self.current_report_data = result['report_data']
                self.display_report(self.current_report_data, report_type)
                self.export_excel_button.configure(state="normal")
                self.export_pdf_button.configure(state="normal")
            else:
                messagebox.showerror("خطأ", f"حدث خطأ أثناء إنشاء التقرير: {result['error']}")
        
        except Exception as e:
            messagebox.showerror("خطأ", f"حدث خطأ غير متوقع: {str(e)}")
    
    def display_report(self, report_data, report_type):
        # مسح المحتوى الحالي
        for widget in self.report_content_frame.winfo_children():
            widget.destroy()
        
        # عرض التقرير حسب النوع
        if report_type == "financial":
            self.display_financial_report(report_data)
        else:  # member
            self.display_member_report(report_data)
    
    def display_financial_report(self, report_data):
        # إنشاء جدول لعرض البيانات المالية
        columns = ("category", "amount")
        tree = ttk.Treeview(self.report_content_frame, columns=columns, show="headings")
        
        # تعيين عناوين الأعمدة
        tree.heading("category", text="الفئة")
        tree.heading("amount", text="المبلغ")
        
        # تعيين أحجام الأعمدة
        tree.column("category", width=200)
        tree.column("amount", width=150)
        
        # إضافة البيانات
        tree.insert("", "end", values=("إجمالي الإيرادات", report_data['total_income']))
        tree.insert("", "end", values=("إجمالي المصروفات", report_data['total_expenses']))
        tree.insert("", "end", values=("صافي الربح", report_data['net_profit']))
        
        # إضافة تفاصيل الإيرادات
        income_parent = tree.insert("", "end", values=("تفاصيل الإيرادات", ""))
        for category, amount in report_data['income_by_category'].items():
            tree.insert(income_parent, "end", values=(category, amount))
        
        # إضافة تفاصيل المصروفات
        expenses_parent = tree.insert("", "end", values=("تفاصيل المصروفات", ""))
        for category, amount in report_data['expenses_by_category'].items():
            tree.insert(expenses_parent, "end", values=(category, amount))
        
        # إضافة شريط التمرير
        scrollbar = ttk.Scrollbar(self.report_content_frame, orient="vertical", command=tree.yview)
        tree.configure(yscrollcommand=scrollbar.set)
        scrollbar.pack(side="right", fill="y")
        tree.pack(side="left", fill="both", expand=True)
    
    def display_member_report(self, report_data):
        # إنشاء جدول لعرض بيانات الأعضاء
        columns = ("category", "value")
        tree = ttk.Treeview(self.report_content_frame, columns=columns, show="headings")
        
        # تعيين عناوين الأعمدة
        tree.heading("category", text="الفئة")
        tree.heading("value", text="القيمة")
        
        # تعيين أحجام الأعمدة
        tree.column("category", width=200)
        tree.column("value", width=150)
        
        # إضافة البيانات
        tree.insert("", "end", values=("إجمالي الأعضاء", report_data['total_members']))
        tree.insert("", "end", values=("الأعضاء النشطين", report_data['active_members']))
        tree.insert("", "end", values=("الأعضاء الجدد", report_data['new_members']))
        tree.insert("", "end", values=("الاشتراكات النشطة", report_data['active_subscriptions']))
        tree.insert("", "end", values=("متوسط مدة الحضور", f"{report_data['avg_attendance_duration']} دقيقة"))
        
        # إضافة تفاصيل الاشتراكات
        subscriptions_parent = tree.insert("", "end", values=("الاشتراكات حسب الخطة", ""))
        for plan, count in report_data['subscriptions_by_plan'].items():
            tree.insert(subscriptions_parent, "end", values=(plan, count))
        
        # إضافة شريط التمرير
        scrollbar = ttk.Scrollbar(self.report_content_frame, orient="vertical", command=tree.yview)
        tree.configure(yscrollcommand=scrollbar.set)
        scrollbar.pack(side="right", fill="y")
        tree.pack(side="left", fill="both", expand=True)
    
    def export_to_excel(self):
        if not self.current_report_data:
            messagebox.showwarning("تنبيه", "يرجى إنشاء تقرير أولاً")
            return
        
        # اختيار مسار الملف
        file_path = filedialog.asksaveasfilename(
            defaultextension=".xlsx",
            filetypes=[("Excel files", "*.xlsx")],
            title="حفظ التقرير كملف Excel"
        )
        
        if not file_path:
            return
        
        # تصدير التقرير
        result = self.report_controller.export_report_to_excel(self.current_report_data, file_path)
        
        if result['success']:
            messagebox.showinfo("نجاح", f"تم تصدير التقرير بنجاح إلى {result['file_path']}")
            # فتح الملف
            os.startfile(result['file_path'])
        else:
            messagebox.showerror("خطأ", f"حدث خطأ أثناء تصدير التقرير: {result['error']}")
    
    def export_to_pdf(self):
        # مماثل لتصدير Excel ولكن باستخدام PDF
        pass
```

## 🔄 تكييف قاعدة البيانات

### 1. إعداد قاعدة البيانات المحلية

```python
# app/services/db_service.py
class DatabaseService:
    def __init__(self, db_path):
        self.db_path = db_path
        self.engine = create_engine(f'sqlite:///{db_path}')
        self.Session = sessionmaker(bind=self.engine)
        self.session = self.Session()
    
    def init_db(self):
        # إنشاء جميع الجداول
        Base.metadata.create_all(self.engine)
    
    def migrate_db(self, old_db_path):
        # ترحيل البيانات من قاعدة البيانات القديمة إلى الجديدة
        old_engine = create_engine(f'sqlite:///{old_db_path}')
        old_session = sessionmaker(bind=old_engine)()
        
        # ترحيل الأعضاء
        old_members = old_session.query(Member).all()
        for member in old_members:
            self.session.add(member)
        
        # ترحيل خطط العضوية
        old_plans = old_session.query(MembershipPlan).all()
        for plan in old_plans:
            self.session.add(plan)
        
        # ترحيل الاشتراكات
        old_subscriptions = old_session.query(Subscription).all()
        for subscription in old_subscriptions:
            self.session.add(subscription)
        
        # ترحيل سجلات الحضور
        old_attendance = old_session.query(Attendance).all()
        for attendance in old_attendance:
            self.session.add(attendance)
        
        # ترحيل الفواتير
        old_invoices = old_session.query(Invoice).all()
        for invoice in old_invoices:
            self.session.add(invoice)
        
        # ترحيل عناصر الفواتير
        old_invoice_items = old_session.query(InvoiceItem).all()
        for item in old_invoice_items:
            self.session.add(item)
        
        # ترحيل المدفوعات
        old_payments = old_session.query(Payment).all()
        for payment in old_payments:
            self.session.add(payment)
        
        # ترحيل المصروفات
        old_expenses = old_session.query(Expense).all()
        for expense in old_expenses:
            self.session.add(expense)
        
        # ترحيل المنتجات
        old_products = old_session.query(Product).all()
        for product in old_products:
            self.session.add(product)
        
        # ترحيل المبيعات
        old_sales = old_session.query(Sale).all()
        for sale in old_sales:
            self.session.add(sale)
        
        # ترحيل عناصر المبيعات
        old_sale_items = old_session.query(SaleItem).all()
        for item in old_sale_items:
            self.session.add(item)
        
        # ترحيل المستخدمين
        old_users = old_session.query(User).all()
        for user in old_users:
            self.session.add(user)
        
        # ترحيل الإعدادات
        old_settings = old_session.query(GymSettings).all()
        for setting in old_settings:
            self.session.add(setting)
        
        # حفظ التغييرات
        self.session.commit()
        
        old_session.close()
```

## 🔄 تكييف واجهة المستخدم الرئيسية

### 1. النافذة الرئيسية

```python
# app/views/main_window.py
class MainWindow(ctk.CTk):
    def __init__(self, app_controller):
        super().__init__()
        self.app_controller = app_controller
        
        # إعداد النافذة الرئيسية
        self.title("نظام إدارة النادي الرياضي")
        self.geometry("1200x800")
        
        # تعيين السمة
        ctk.set_appearance_mode("dark")  # الوضع: "light" أو "dark"
        ctk.set_default_color_theme("blue")  # السمة: "blue", "green", "dark-blue"
        
        # إنشاء الإطار الرئيسي
        self.main_frame = ctk.CTkFrame(self)
        self.main_frame.pack(fill="both", expand=True)
        
        # إنشاء الشريط الجانبي
        self.sidebar_frame = ctk.CTkFrame(self.main_frame, width=200)
        self.sidebar_frame.pack(side="right", fill="y")
        
        # شعار النادي
        self.logo_label = ctk.CTkLabel(self.sidebar_frame, text="النادي الرياضي", font=ctk.CTkFont(size=20, weight="bold"))
        self.logo_label.pack(pady=20)
        
        # أزرار القائمة
        self.dashboard_button = ctk.CTkButton(self.sidebar_frame, text="لوحة التحكم", command=lambda: self.show_frame("dashboard"))
        self.dashboard_button.pack(pady=10, padx=20, fill="x")
        
        self.members_button = ctk.CTkButton(self.sidebar_frame, text="الأعضاء", command=lambda: self.show_frame("members"))
        self.members_button.pack(pady=10, padx=20, fill="x")
        
        self.subscriptions_button = ctk.CTkButton(self.sidebar_frame, text="الاشتراكات", command=lambda: self.show_frame("subscriptions"))
        self.subscriptions_button.pack(pady=10, padx=20, fill="x")
        
        self.attendance_button = ctk.CTkButton(self.sidebar_frame, text="الحضور والانصراف", command=lambda: self.show_frame("attendance"))
        self.attendance_button.pack(pady=10, padx=20, fill="x")
        
        self.invoices_button = ctk.CTkButton(self.sidebar_frame, text="الفواتير", command=lambda: self.show_frame("invoices"))
        self.invoices_button.pack(pady=10, padx=20, fill="x")
        
        self.reports_button = ctk.CTkButton(self.sidebar_frame, text="التقارير", command=lambda: self.show_frame("reports"))
        self.reports_button.pack(pady=10, padx=20, fill="x")
        
        self.inventory_button = ctk.CTkButton(self.sidebar_frame, text="المخزون والمبيعات", command=lambda: self.show_frame("inventory"))
        self.inventory_button.pack(pady=10, padx=20, fill="x")
        
        self.settings_button = ctk.CTkButton(self.sidebar_frame, text="الإعدادات", command=lambda: self.show_frame("settings"))
        self.settings_button.pack(pady=10, padx=20, fill="x")
        
        # معلومات المستخدم
        self.user_frame = ctk.CTkFrame(self.sidebar_frame)
        self.user_frame.pack(side="bottom", fill="x", padx=20, pady=20)
        
        self.user_label = ctk.CTkLabel(self.user_frame, text="مرحباً، المستخدم")
        self.user_label.pack(pady=5)
        
        self.logout_button = ctk.CTkButton(self.user_frame, text="تسجيل الخروج", command=self.logout)
        self.logout_button.pack(pady=5)
        
        # إنشاء إطار المحتوى
        self.content_frame = ctk.CTkFrame(self.main_frame)
        self.content_frame.pack(side="left", fill="both", expand=True)
        
        # إنشاء الإطارات المختلفة
        self.frames = {}
        
        # تحميل الإطار الافتراضي (لوحة التحكم)
        self.current_frame = None
        self.load_frames()
        self.show_frame("dashboard")
    
    def load_frames(self):
        # إنشاء وحدات التحكم للإطارات المختلفة
        member_controller = self.app_controller.get_member_controller()
        subscription_controller = self.app_controller.get_subscription_controller()
        attendance_controller = self.app_controller.get_attendance_controller()
        invoice_controller = self.app_controller.get_invoice_controller()
        report_controller = self.app_controller.get_report_controller()
        inventory_controller = self.app_controller.get_inventory_controller()
        settings_controller = self.app_controller.get_settings_controller()
        
        # إنشاء الإطارات
        from app.views.dashboard_view import DashboardFrame
        from app.views.members_view import MembersListFrame
        from app.views.subscription_view import SubscriptionsListFrame
        from app.views.attendance_view import AttendanceFrame
        from app.views.invoice_view import InvoicesListFrame
        from app.views.report_view import ReportFrame
        from app.views.inventory_view import InventoryFrame
        from app.views.settings_view import SettingsFrame
        
        self.frames["dashboard"] = DashboardFrame(self.content_frame, self.app_controller)
        self.frames["members"] = MembersListFrame(self.content_frame, member_controller)
        self.frames["subscriptions"] = SubscriptionsListFrame(self.content_frame, subscription_controller)
        self.frames["attendance"] = AttendanceFrame(self.content_frame, attendance_controller)
        self.frames["invoices"] = InvoicesListFrame(self.content_frame, invoice_controller)
        self.frames["reports"] = ReportFrame(self.content_frame, report_controller)
        self.frames["inventory"] = InventoryFrame(self.content_frame, inventory_controller)
        self.frames["settings"] = SettingsFrame(self.content_frame, settings_controller)
    
    def show_frame(self, frame_name):
        # إخفاء الإطار الحالي
        if self.current_frame:
            self.frames[self.current_frame].pack_forget()
        
        # عرض الإطار الجديد
        self.frames[frame_name].pack(fill="both", expand=True)
        self.current_frame = frame_name
    
    def logout(self):
        # تسجيل الخروج
        self.app_controller.logout()
        self.destroy()
        
        # فتح نافذة تسجيل الدخول
        from app.views.auth_view import LoginWindow
        login_window = LoginWindow(None, self.app_controller.get_auth_controller())
        login_window.mainloop()
```

## 📊 نقطة الدخول الرئيسية للتطبيق

```python
# main.py
import os
import customtkinter as ctk
from app.controllers.app_controller import AppController
from app.views.auth_view import LoginWindow
from app.views.main_window import MainWindow

def main():
    # إنشاء مسارات التطبيق إذا لم تكن موجودة
    os.makedirs("database", exist_ok=True)
    os.makedirs("logs", exist_ok=True)
    os.makedirs("exports", exist_ok=True)
    os.makedirs("temp", exist_ok=True)
    
    # إنشاء وحدة التحكم الرئيسية للتطبيق
    app_controller = AppController()
    
    # تهيئة قاعدة البيانات
    app_controller.init_database()
    
    # إنشاء نافذة تسجيل الدخول
    login_window = LoginWindow(None, app_controller.get_auth_controller())
    login_window.mainloop()

if __name__ == "__main__":
    main()
```

## 🔄 تحديات التحويل والحلول

### 1. تحويل نماذج HTML إلى CustomTkinter

| نوع العنصر في HTML | المكافئ في CustomTkinter |
|-------------------|---------------------------|
| `<input type="text">` | `ctk.CTkEntry()` |
| `<input type="password">` | `ctk.CTkEntry(show="*")` |
| `<input type="checkbox">` | `ctk.CTkCheckBox()` |
| `<input type="radio">` | `ctk.CTkRadioButton()` |
| `<select>` | `ctk.CTkComboBox()` |
| `<textarea>` | `ctk.CTkTextbox()` |
| `<button>` | `ctk.CTkButton()` |
| `<table>` | `ttk.Treeview()` |
| `<div>` | `ctk.CTkFrame()` |
| `<label>` | `ctk.CTkLabel()` |

### 2. تحويل طلبات HTTP إلى استدعاءات مباشرة

| نمط Flask | نمط CustomTkinter |
|-----------|-------------------|
| `@app.route('/members')` | `def show_members_frame(self):` |
| `request.form.get('name')` | `self.name_entry.get()` |
| `return render_template('members.html', members=members)` | `self.display_members(members)` |
| `redirect(url_for('members'))` | `self.show_frame('members')` |
| `flash('تم الحفظ بنجاح')` | `messagebox.showinfo('نجاح', 'تم الحفظ بنجاح')` |

### 3. تحويل المصادقة والجلسات

| آلية Flask | آلية CustomTkinter |
|------------|--------------------|
| `flask_login` | مصادقة محلية وتخزين المستخدم الحالي في الذاكرة |
| `session['user_id']` | `self.current_user` |
| `@login_required` | فحص `self.current_user` قبل تنفيذ العمليات |

## 🔍 اختبار وضمان الجودة

### 1. استراتيجية الاختبار

1. **اختبار الوحدات**: اختبار كل وحدة تحكم ونموذج بشكل منفصل.
2. **اختبار التكامل**: اختبار تفاعل المكونات المختلفة مع بعضها البعض.
3. **اختبار واجهة المستخدم**: اختبار سهولة استخدام واجهة المستخدم وتجربة المستخدم.
4. **اختبار الأداء**: قياس أداء التطبيق وتحسينه.

### 2. قائمة التحقق للاختبار

- [ ] تسجيل الدخول والخروج
- [ ] إدارة الأعضاء (إضافة، تعديل، حذف، بحث)
- [ ] إدارة الاشتراكات (إضافة، تعديل، تجديد)
- [ ] تسجيل الحضور والانصراف
- [ ] إنشاء وطباعة الفواتير
- [ ] إنشاء وتصدير التقارير
- [ ] إدارة المخزون والمبيعات
- [ ] إعدادات النظام

## 📦 التوزيع والتثبيت

### 1. إنشاء حزمة قابلة للتنفيذ

```python
# setup.py
from setuptools import setup, find_packages

setup(
    name="gymawy-desktop",
    version="1.0.0",
    packages=find_packages(),
    install_requires=[
        "customtkinter>=5.0.0",
        "sqlalchemy>=2.0.0",
        "pillow>=9.0.0",
        "reportlab>=3.6.0",
        "openpyxl>=3.0.0",
        "bcrypt>=4.0.0"
    ],
    entry_points={
        'console_scripts': [
            'gymawy-desktop=main:main',
        ],
    },
)
```

### 2. إنشاء ملف تنفيذي باستخدام PyInstaller

```bash
pyinstaller --name="Gymawy" --windowed --icon=app/assets/icon.ico --add-data="app/assets;app/assets" main.py
```

## 🏁 الخلاصة

تحويل تطبيق ويب Flask إلى تطبيق سطح مكتب CustomTkinter هو عملية منهجية تتطلب تخطيطًا دقيقًا وتنفيذًا مرحليًا. باتباع الخطة المقترحة، يمكن الاحتفاظ بمعظم المنطق التجاري والوظائف الحالية مع تكييف واجهة المستخدم لبيئة سطح المكتب. النتيجة النهائية ستكون تطبيقًا قائمًا بذاته يعمل بدون الحاجة إلى اتصال بالإنترنت ويوفر تجربة مستخدم سلسة وفعالة.

المفتاح لنجاح هذا التحويل هو الحفاظ على نمط MVC وإعادة استخدام النماذج والخدمات قدر الإمكان، مع التركيز على إعادة بناء واجهات المستخدم باستخدام CustomTkinter وتكييف آليات التحكم للعمل في بيئة سطح المكتب.