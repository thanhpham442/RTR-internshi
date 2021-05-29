# Overview: Báo cáo tuần 1

 ## Intern:  Phạm Phương Thành

 ## 1. Ubuntu
-Về win và Ubuntu
Shell là một layer trên os level tại terminal là user level
Kernel ở trong os level
Win có GUI hướng đến người dùng dễ sử dụng, Ubuntu có cả terminal và GUI. Khác nhau lớn nhất ở bản chất là kernel, win dùng kernel Windows NT còn Ubuntu dùng Linux kernel

Về 20.04 và 18.04
20.04 Ubuntu will try to force you on a Snap version, which có thể xung đột với Debian package hay dùng cho software installation, say, install 2 bản khác nhau của một phần mềm. Và snap tốn nhiều space hơn vì snap install tất cả dependencies 
Kernel của 20.04 là Linux 5.4, của 18.04 là 5.3. There is a chance peripheral devices may not function in this newer version. 
20.04 được update nhiều về UI/UX, và cái đấy không cần thiết lắm. Mình hoàn toàn có thể update kernel lên 5.4 và vẫn dùng 18.04, which saves space nếu deploy trên nhiều máy.

Conclusion: 
-Possible software error with Snap
-Saving space by updating kernel only

Sau khi xin ý kiến anh Khôi, có những phần mềm chạy trên bản này mà không chạy trên bản khác. Do đó để đảm bảo tính ổn định công ty dùng bản Ubuntu 18.04.

## 2.Markdown

Markdown is a lightweight markup language for creating formatted text using a plain-text editor.
Markdown thường được dùng để viết documentation.
Markdown là markup language dùng PERL script để convert Markdown sang valid XHTML hoặc HTML. Do đó nên Markdown hỗ trợ HTML và CSS

## 3.Python 3.8 
Ubuntu 18.04 không có python mặc định nếu gõ python trong terminal. Thay vào đó là bản python 3.6.9 mặc định
Cài đặt python 3.8: sudo apt update -y
                    sudo apt install python3.8
Terminal: $ python3.8
Cài đặt python3.8 làm mặc định
$ sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 1
$ sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 2
$ sudo update-alternatives --config python3

Thông báo như sau sẽ hiện ra
user@ubuntu1804:~$ sudo update-alternatives --config python3
There are 2 choices for the alternative python3 (providing /usr/bin/python3).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/python3.6   1         auto mode
  1            /usr/bin/python3.6   1         manual mode
  2            /usr/bin/python3.8   2         manual mode

Press <enter> to keep the current choice[*], or type selection number:

Nhập 2, ấn enter. Có thể dùng phương pháp tương tự đổi lại sau này.

## 4.OpenCV4
Hướng dẫn cài openCV4 ở trên trang chủ https://docs.opencv.org/4.0.0/d7/d9f/tutorial_linux_install.html. Không dùng pip install opencv-python vì sẽ cài bản opencv-python, là một bản được optimize nên không đảm bảo khả năng tương thích về phần cứng.

Chưa tìm ra cách dùng OpenCV4 trên Python 3.8, đã dùng thành công trên Python 3.6.9.

Khi xảy ra lỗi Import Error: cannot import name 'cv2':
- Tìm đến folder cd /usr/local/lib/python3.6/site-packages
- sudo mv cv2.cpython-36m-x86_64-linux-gnu.so cv2.so
- Trong Python 3.6.9:
import sys
sys.path.append('/usr/local/lib/python3.6/site-packages')
import cv2

OpenCV là một libray hướng tới real-time computer vision được phát triển bởi Intel.
OpenCV Tracker Algorthms:
- __BOOSTING Tracker
- __MIL Tracker
- __KCF Tracker
- __TLD Tracker
- __MEDIANFLOW Tracker
- __MOSSE tracker
- __CSRT tracker







