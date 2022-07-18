# Báo cáo tuần 1 và 2

## Người viết: Trần Bảo Thịnh
## Thông tin liên lạc:

  - Số điện thoại:0362993732
  - Gmail:tranbaothinh.2001@gmail.com
  - Github: https://github.com/Baothinh20

### I. Công việc được giao:

  - Tìm hiểu về Python Framework.
    - Cài đặt Python.
    - Cài đặt Pycharm
  - Tìm hiểu về Django:
    - Cài đặt Django theo hướng dẫn trên web https://docs.djangoproject.com/en/4.0/intro/install/.
    - Tìm hiểu về cách tạo 1 app cơ bản và có các tính năng (tạo poll để vote).
  - Tìm hiểu về Netbox:
    - Đọc sơ qua tài liệu trên git https://github.com/netbox-community/netbox.
  
### II. Tiến trình công việc:

  1. Tổng quan:
    - Python Framework là các đoạn code đã được viết sẵn, một bộ khung và các thư viện lập trình được đóng gói.
    - Django là Python Back-end framework tốt nhất vào những năm 2021 tới hiện tại.
    - Điểm nổi bật chính:
      - Rất nhiều thư viện có sẵn.
      - Hệ thống xác nhận thông tin người dùng có sẵn.
      - Cơ sở dữ liệu hướng đối tượng giúp lưu trữ và phục hồi dữ liệu.
      - Trình quản lý admin tự động giúp sửa, thêm và xóa các tính năng.
      - Hệ thống cache mạnh mẽ.
    - Sơ qua về Netbox:
      - NetBox là một công cụ mô hình hóa tài nguyên cơ sở hạ tầng (IRM) được thiết kế để trao quyền tự động hóa mạng, được sử dụng bởi hàng nghìn tổ chức trên khắp           thế giới.
      - Vô số thành phần cơ sở hạ tầng có thể được mô hình hóa trong NetBox.
      - Ngoài các mô hình và chức năng tích hợp sẵn, NetBox có thể được tùy chỉnh và mở rộng theo nhiều cách.
      - NetBox cũng có API REST hoàn chỉnh cũng như API GraphQL.
      - NetBox là một ứng dụng web dựa trên Django Python với cơ sở dữ liệu PostgreSQL. 
  2. Cài đặt và thiết lập app Django cơ bản: (Step-by-step)
   - Cài đặt Pycharm theo web https://niithanoi.edu.vn/huong-dan-cai-dat-va-su-dung-pycharm-ide-trong-lap-trinh-python.html
   - Cài đặt Python 3.10 theo web https://www.python.org/downloads/release/python-3105/
   - Kiểm tra version để xem có chạy ổn định không:
    
    >py -m django --version

   - Tạo project:
      
    >django-admin startproject mysite
      
   - Các file đã đc tạo:

   ```bash
   mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
   ```
   - Ghi chú:
      - Thư mục gốc mysite/ ngoài cùng là container của project.
      - Thư mục mysite/ bên trong là package Python thực tế cho project
      - mysite/ __ init __ .py: là một file rỗng để đánh dấu đây là package của Python.
      - mysite/settings.py: Cài đặt/ cấu hình cho project này.
      - mysite/urls.py: Các khai báo URL cho project này, đóng vai trò làm router để hướng dẫn các request đến file xử lý phù hợp.
      - mysite/asgi.py và mysite/wsgi.py: file cấu hình cho server

    >py manage.py runserver
   
   - Tạo Poll app:
   
    >py manage.py startapp polls

   - Các file đã được tạo:
   
   ```bash
   mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
   ```
   
   - Tạo view cơ bản như web https://docs.djangoproject.com/en/4.0/intro/tutorial01/#writing-your-first-django-app-part-1
   - Ta cần điều hướng để có thể gọi view này -> chỉnh url
   - Để load được poll/urls.py vào trong mysite/urls.py thì ta phải thông qua lệnh “include“, muốn sử dụng được lệnh include thì bạn phải import nó từ packages “urls”
   
   - Thư mục mysite/urls.py hiện tại:
   ```bash
   from django.contrib import admin
   from django.urls import include, path

   urlpatterns = [
   path('polls/', include('polls.urls')),
   path('admin/', admin.site.urls),
   ]
   ```
   
   - Thiết lập cơ sở dữ liệu
      - Mở file mysite/settings.py.
      - Theo mặc định, cấu hình sử dụng SQLite.

         ```bash
          DATABASES = {
             'default': {
                 'ENGINE': 'django.db.backends.sqlite3',
                'NAME': BASE_DIR / 'db.sqlite3',
             }
          }
          ```
     
      - Nếu muốn sử dụng cơ sở dữ liệu khác, thay đổi từ khóa:
       - ENGINE -> 'django.db.backends.sqlite3', 'django.db.backends.postgresql', 'django.db.backends.mysql', or 'django.db.backends.oracle' etc.
       - NAME : Tên cơ sở dữ liệu

   - Nếu không sử dụng SQLite làm cơ sở dữ liệu của mình, các cài đặt bổ sung như USER, PASSWORDvà HOST phải được thêm vào.
   - INSTALLED_APPS chứa tên của tất cả các ứng dụng Django được kích hoạt trong phiên bản Django này.
       - django.contrib.admin- Trang web quản trị.
       - django.contrib.auth- Một hệ thống xác thực.
       - django.contrib.contenttypes- Một khung cho các loại nội dung.
       - django.contrib.sessions- Một khung phiên.
       - django.contrib.messages- Một khung nhắn tin.
       - django.contrib.staticfiles- Một khung để quản lý các tệp tĩnh.
   - Lệnh migrate sẽ tạo các cơ sở dữ liệu cần thiết dựa trên co sở dữ liệu ở mysite/settings.py
   - Tạo model:
       - Tạo model trong polls/models.py
       - Với poll app chỉ cần 2 model Question and Choice
       - Thư mục sau khi sửa
          ```bash
          from django.db import models

          class Question(models.Model):
              question_text = models.CharField(max_length=200)
              pub_date = models.DateTimeField('date published')


          class Choice(models.Model):
              question = models.ForeignKey(Question, on_delete=models.CASCADE)
              choice_text = models.CharField(max_length=200)
              votes = models.IntegerField(default=0)
          ```
       - Mỗi mô hình được đại diện bởi một lớp phân lớp con django.db.models.Model. Mỗi mô hình có một số biến lớp, mỗi biến đại diện cho một trường cơ sở dữ liệu            trong mô hình.
       - Mỗi trường được đại diện bởi một thể hiện của một lớp Field
      
   - Kích hoạt model:
       - Thêm 'polls.apps.PollsConfig' vào mysite/settings.py để đưa ứng dụng vào project
       - Thư mục sau khi sửa
          ```bash
          INSTALLED_APPS = [
              'polls.apps.PollsConfig',
              'django.contrib.admin',
              'django.contrib.auth',
              'django.contrib.contenttypes',
              'django.contrib.sessions',
              'django.contrib.messages',
              'django.contrib.staticfiles',
          ]
          ```
        - Chạy lệnh:
          ```bash
          python manage.py makemigrations polls
          ```
        - Xuất hiện những dòng lệnh:
          ```bash
          Migrations for 'polls':
          polls/migrations/0001_initial.py
              - Create model Question
              - Create model Choice
          ```
    
  3. Bổ sung:

   - Hiện tại em đang tìm hiểu về việc cài netbox trên ubuntu (20.04).
    
### III.Tài liệu tham khảo
  - https://topdev.vn/blog/framework-la-gi/.
  - https://niithanoi.edu.vn/huong-dan-cai-dat-va-su-dung-pycharm-ide-trong-lap-trinh-python.html
  - https://www.jetbrains.com/help/pycharm/installation-guide.html#silent
  - https://t3h.edu.vn/tin-tuc/top-framework-python-hoan-hao-danh-cho-lap-trinh-vien.
  - https://www.python.org/downloads/release/python-3105/
  - https://vn.got-it.ai/blog/python-back-end-framework#:~:text=Python%20Back%2Dend%20framework%20l%C3%A0,v%C3%A0%20c%C3%B4ng%20d%E1%BB%A5ng%20kh%C3%A1c%20nhau.
  - https://docs.djangoproject.com/en/4.0/intro/install/.
  - https://docs.djangoproject.com/en/4.0/intro/tutorial01/#writing-your-first-django-app-part-1 to part 7.
  - https://docs.djangoproject.com/en/4.0/intro/reusable-apps/.
  - https://github.com/netbox-community/netbox.
  - https://docs.netbox.dev/en/stable/
  - https://computingforgeeks.com/install-and-configure-netbox-ipam-dcim-tool-on-ubuntu/.
  - https://computingforgeeks.com/installing-postgresql-database-server-on-ubuntu/.
  - Extra:
    - https://howkteam.vn/course/upload-file-trong-lap-trinh-website-voi-python/tao-mot-web-app-va-xu-ly-khi-nguoi-dung-yeu-cau-truy-cap-trong-python-django-1517.
  - Demo:
    - https://demo.netbox.dev/.
