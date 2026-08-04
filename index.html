# 🐧 Hướng Dẫn Cài Đặt Ubuntu 24.04.4 LTS — Xóa Toàn Bộ, Cài Thuần

> **Thiết bị:** HP 340S G7 Notebook PC  
> **CPU:** Intel Core i5-1035G1 (4 nhân / 8 luồng)  
> **RAM:** 12 GB  
> **SSD:** WD PC SN530 NVMe 256GB  
> **Ngày soạn:** 04/08/2026  

---

## 📋 Mục Lục

1. [Tổng quan](#1-tổng-quan)
2. [Chuẩn bị](#2-chuẩn-bị)
3. [Tải Ubuntu ISO và tạo USB/SD boot](#3-tải-ubuntu-iso-và-tạo-usbsd-boot)
4. [Cấu hình BIOS/UEFI](#4-cấu-hình-biosuefi)
5. [Cài đặt Ubuntu](#5-cài-đặt-ubuntu)
6. [Sau khi cài đặt](#6-sau-khi-cài-đặt)
7. [Xử lý sự cố](#7-xử-lý-sự-cố)

---

## 1. Tổng Quan

### Tại sao chọn Ubuntu 24.04.4 LTS?

| Tiêu chí | Đánh giá |
|---|---|
| **Phiên bản** | 24.04.4 LTS (Noble Numbat) — phát hành 02/2026 |
| **Kernel** | Linux 6.8 — hỗ trợ hoàn hảo CPU Intel Ice Lake thế hệ 10 |
| **Hỗ trợ** | Đến tháng 4/2029 (miễn phí), kéo dài đến 2034 với Ubuntu Pro |
| **Dung lượng** | Cài đặt gốc ~15-20 GB, để lại hơn 200 GB trống cho dữ liệu |
| **Ổ cứng** | NVMe SSD — boot chỉ ~5-7 giây |

### Kết quả sau khi cài

```
Trước:                               Sau:
┌──────────────────────┐             ┌──────────────────────┐
│  Windows 11          │             │  Ubuntu 24.04 LTS    │
│  Ổ C: Windows (128G) │     =>      │  Toàn bộ 256GB SSD   │
│  Ổ D: DATA (125G)    │             │  HĐH duy nhất        │
│  Dữ liệu: mất hết    │             │  Trống: ~220GB       │
└──────────────────────┘             └──────────────────────┘
```

> ⚠️ **CẢNH BÁO CUỐI CÙNG:** Tất cả dữ liệu trên SSD 256GB sẽ bị **xóa vĩnh viễn** — Windows, ổ C, ổ D, file cá nhân, mọi thứ. Hãy sao lưu dữ liệu quan trọng ngay bây giờ trước khi tiếp tục!

---

## 2. Chuẩn Bị

### 2.1 Những thứ bạn cần

| Vật dụng | Mục đích |
|---|---|
| **Thẻ MicroSD 32GB** (đã có) | Chứa bộ cài Ubuntu (~6.2 GB) |
| **Adapter MicroSD → USB** (nếu máy không có khe SD) | Để cắm vào máy |
| **Mạng Internet ổn định** | Tải ISO + cập nhật trong lúc cài |
| **Ổ cứng ngoài / Cloud** | Sao lưu dữ liệu trước khi xóa |

### 2.2 Sao lưu dữ liệu (ĐỪNG BỎ QUA!)

Trước khi làm bất cứ điều gì khác, hãy sao lưu:

- [ ] Documents, Pictures, Downloads từ ổ C (`C:\Users\HP\`)
- [ ] Dữ liệu cá nhân từ ổ D (`D:\`)
- [ ] Mật khẩu đã lưu trên trình duyệt
- [ ] License key các phần mềm đã mua
- [ ] Bookmark trình duyệt
- [ ] File cấu hình phần mềm đặc thù

### 2.3 Kiểm tra BIOS

Khởi động lại máy, nhấn **F10** liên tục để vào BIOS. Ghi lại:

- Phiên bản BIOS hiện tại (đã biết: AMI F.30)
- Boot mode hiện tại (nên là UEFI)
- Secure Boot status (nên là Enabled — Ubuntu hỗ trợ)

---

## 3. Tải Ubuntu ISO Và Tạo USB/SD Boot

### 3.1 Tải Ubuntu 24.04.4 LTS

**Tải từ trang chủ Ubuntu (khuyến nghị):**

```
🔗 https://releases.ubuntu.com/24.04.4/ubuntu-24.04.4-desktop-amd64.iso
```

**Mirror dự phòng (nếu link trên chậm):**

```
🔗 https://mirror.clarkson.edu/ubuntu-releases/24.04.4/ubuntu-24.04.4-desktop-amd64.iso
```

- **Dung lượng:** ~6.2 GB
- **Thời gian tải:** 10-30 phút tùy tốc độ mạng
- **Vị trí lưu:** `C:\Users\HP\Downloads\ubuntu-24.04.4-desktop-amd64.iso`

### 3.2 Cài Rufus (công cụ nạp ISO vào thẻ SD)

**Cách 1: Dùng winget (đã cài sẵn trên Windows 11)**
```powershell
winget install --id Rufus.Rufus
```

**Cách 2: Tải thủ công**
```
🔗 https://rufus.ie/downloads/
```
Tải file `rufus-4.15.exe`, chạy trực tiếp (không cần cài đặt).

### 3.3 Nạp ISO vào thẻ MicroSD

1. **Cắm thẻ MicroSD** 32GB vào máy (qua đầu đọc thẻ hoặc adapter USB)
2. **Mở Rufus** (tìm trong Start Menu hoặc chạy `rufus` trong PowerShell)
3. **Cấu hình trong Rufus:**

| Mục | Chọn |
|---|---|
| **Device** | Multiple Card Reader (32 GB) — thẻ MicroSD của bạn |
| **Boot selection** | Nhấn **SELECT** → chọn file `ubuntu-24.04.4-desktop-amd64.iso` |
| **Partition scheme** | **GPT** (vì máy bạn dùng UEFI) |
| **Target system** | **UEFI (non CSM)** |
| **File system** | FAT32 (mặc định) |
| **Cluster size** | 4096 bytes (mặc định) |

4. Nhấn **START**
5. Hộp thoại hỏi — chọn: **"Write in ISO Image mode"** (Recommended) → OK
6. Xác nhận xóa dữ liệu thẻ SD → OK
7. Chờ quá trình hoàn tất (~5-10 phút)

> 📊 **Thanh trạng thái Rufus:** Khi thanh màu xanh đầy, chữ "READY" hiện lên là xong.

---

## 4. Cấu Hình BIOS/UEFI

> ⚠️ **BƯỚC SỐNG CÒN — ĐỌC KỸ TRƯỚC KHI LÀM**

### 4.1 Vào BIOS

1. **Tắt máy hoàn toàn** (Shutdown, không phải Restart)
2. Cắm thẻ MicroSD đã nạp Ubuntu vào máy
3. **Bật máy** và **nhấn F10 liên tục** (khoảng 2 lần/giây) cho đến khi vào BIOS

### 4.2 Các thiết lập cần chỉnh

#### Trong tab "System Configuration":

| Mục | Thiết lập | Lý do |
|---|---|---|
| **Boot Options → Fast Boot** | **Disable** | Để Ubuntu có thời gian nhận diện phần cứng |
| **Boot Options → UEFI Boot Order** | Đẩy **USB/SD Card** lên đầu | Để boot từ thẻ SD trước |
| **Boot Options → Legacy Support** | **Disable** | Giữ thuần UEFI, tránh xung đột |

#### Trong tab "Security":

| Mục | Thiết lập | Lý do |
|---|---|---|
| **Secure Boot** | Giữ **Enable** | Ubuntu 24.04 hỗ trợ Secure Boot tốt |
| **TPM** | Không cần chỉnh | Không ảnh hưởng đến Ubuntu |

> ℹ️ **Không cần chuyển SATA mode** — ổ NVMe của bạn giao tiếp qua PCIe trực tiếp, không qua SATA controller, nên không bị ảnh hưởng bởi RST/AHCI.

### 4.3 Lưu và thoát

- Nhấn **F10** → chọn **Yes** để lưu và thoát
- Máy sẽ khởi động lại

### 4.4 Chọn boot từ thẻ SD

- Khi màn hình HP hiện lên, nhấn **F9** liên tục
- Chọn thẻ SD/USB của bạn trong danh sách Boot Menu
- Nhấn Enter

> Nếu bạn thấy màn hình đen với logo Ubuntu và menu GRUB, bạn đã thành công!

---

## 5. Cài Đặt Ubuntu

### 5.1 Màn hình GRUB

Khi boot từ SD thành công, bạn sẽ thấy menu đen:

```
┌────────────────────────────────────────────┐
│  *Try or Install Ubuntu                    │  ← Chọn dòng này
│   Ubuntu (safe graphics)                   │
│   OEM install (for manufacturers)          │
│   Test memory                              │
└────────────────────────────────────────────┘
```

Chọn **"Try or Install Ubuntu"** → Enter.

### 5.2 Màn hình chào mừng

- Chọn ngôn ngữ: **Tiếng Việt** hoặc **English**
- Nhấn **"Install Ubuntu"** (không chọn "Try Ubuntu")

### 5.3 Accessibility (Trợ năng)

- Có thể bỏ qua, nhấn **Next**

### 5.4 Bố cục bàn phím

- Chọn **Vietnamese** (nếu dùng Telex/VNI) hoặc **English (US)**
- Nhấn **Next**

### 5.5 Kết nối Internet

- Kết nối Wi-Fi (nếu có) — giúp tải driver và cập nhật khi cài
- Nếu không có mạng, chọn **"I don't want to connect to internet right now"**

### 5.6 Kiểu cài đặt

Chọn **"Interactive installation"** ✓

```
┌──────────────────────────────────────────────┐
│ ○ Interactive installation                   │ ← CHỌN CÁI NÀY
│     Cài đặt từng bước, dễ kiểm soát          │
│                                              │
│ ○ Automated installation                     │
│     Cần file .yaml cấu hình                  │
└──────────────────────────────────────────────┘
```

### 5.7 Ứng dụng mặc định

Chọn một trong hai (tùy nhu cầu):

| Tùy chọn | Gồm những gì |
|---|---|
| **Default selection** | Firefox, Thunderbird, LibreOffice, Files, Settings, ảnh, video... |
| **Extended selection** | Thêm GIMP, Inkscape, VLC, Synaptic... (~3 GB thêm) |

> 💡 Khuyến nghị: **Default selection** — gọn nhẹ, cài thêm sau nếu cần.

### 5.8 Driver và codec

Tích cả hai:

- [x] ✅ **"Install third-party software for graphics and Wi-Fi hardware"**
- [x] ✅ **"Download and install support for additional media formats"**

> Những thứ này cần cho driver Intel UHD Graphics, Wi-Fi, và xem video MP4/MP3.

### 5.9 🔴 PHÂN VÙNG Ổ ĐĨA — BƯỚC QUAN TRỌNG NHẤT

Bạn sẽ thấy 2 tùy chọn:

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  ○ Erase disk and install Ubuntu                        │ ← CHỌN CÁI NÀY
│    ⚠️ This will delete ALL data on the disk              │
│    (Xóa toàn bộ 256GB SSD, chỉ còn Ubuntu)              │
│                                                         │
│  ○ Manual partitioning                                   │
│    (Tự chia phân vùng - chỉ cho người có kinh nghiệm)     │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

Chọn **"Erase disk and install Ubuntu"**.

> 🔴 Đây là điểm không thể quay lại. Sau bước này, Windows và mọi dữ liệu bị xóa **vĩnh viễn**.

Nhấn **Next** → **"Start installing"** để xác nhận.

### 5.10 Tạo tài khoản

| Trường | Nhập |
|---|---|
| **Your name** | Tên hiển thị (VD: "Nguyễn Văn A") |
| **Your computer's name** | Tên máy trên mạng (VD: "hp-laptop") |
| **Pick a username** | Tên đăng nhập (VD: "nguyenvana") |
| **Choose a password** | Mật khẩu (≥8 ký tự, nên có chữ + số) |

- [x] ✅ **"Require my password to login"** (bảo mật hơn)

### 5.11 Múi giờ

- Chọn **Asia/Ho Chi Minh** (GMT+7)

### 5.12 Xác nhận và bắt đầu

- Xem lại tất cả thiết lập
- Nhấn **"Install"**
- Quá trình cài đặt bắt đầu (~10-15 phút)

### 5.13 Trong lúc cài đặt

Thanh trượt hiển thị tiến trình. Khi cài xong sẽ hiện:

```
┌──────────────────────────────────────────┐
│  Installation complete                   │
│                                          │
│  Please remove the installation medium   │
│  and press Enter to restart.             │
└──────────────────────────────────────────┘
```

1. **Rút thẻ MicroSD ra**
2. Nhấn **Enter**
3. Máy sẽ khởi động lại vào **Ubuntu!**

---

## 6. Sau Khi Cài Đặt

### 6.1 Đăng nhập lần đầu

- Nhập mật khẩu bạn đã tạo ở bước 5.10
- Màn hình desktop GNOME sẽ hiện ra

### 6.2 Kết nối Internet

- Click góc trên bên phải → Wi-Fi → chọn mạng → nhập mật khẩu

### 6.3 Cập nhật hệ thống (LÀM NGAY!)

Mở Terminal bằng tổ hợp phím:

```
Ctrl + Alt + T
```

Chạy lần lượt các lệnh sau:

```bash
# 1. Cập nhật danh sách gói
sudo apt update

# 2. Nâng cấp toàn bộ gói đã cài
sudo apt upgrade -y

# 3. Cài driver Intel + codec media
sudo apt install -y intel-media-va-driver ubuntu-restricted-extras

# 4. Dọn dẹp gói thừa
sudo apt autoremove -y

# 5. Khởi động lại
sudo reboot
```

### 6.4 Các phần mềm nên cài

```bash
# Trình duyệt + công cụ web
sudo apt install -y curl wget git

# Media player
sudo apt install -y vlc

# Nén giải nén (RAR, 7zip...)
sudo apt install -y unrar p7zip-full

# GNOME Tweaks (tùy chỉnh giao diện)
sudo apt install -y gnome-tweaks

# Bộ gõ tiếng Việt
sudo apt install -y ibus-unikey
ibus restart
# Sau đó vào Settings → Keyboard → Input Sources → Add → Vietnamese (Unikey)
```

### 6.5 Tùy chỉnh giao diện cơ bản

Mở **Settings** → **Appearance**:
- Chọn **Dark** / **Light** theme
- Bật **Night Light** để bảo vệ mắt buổi tối

Mở **Settings** → **Power**:
- **Screen Blank**: 10 phút
- **Automatic Suspend**: Tắt (khi cắm sạc)

---

## 7. Xử Lý Sự Cố

### 7.1 Không vào được BIOS

- Tắt máy, rút hết USB/SD
- Bật lại, nhấn **F10** trước khi logo HP xuất hiện
- Nếu không được, thử **Esc** rồi chọn **BIOS Setup**

### 7.2 Không thấy thẻ SD trong Boot Menu

- Vào BIOS → **Boot Options** → bật **USB Boot**
- Kiểm tra thẻ SD đã cắm đúng chưa
- Thử tạo lại thẻ SD bằng Rufus (chọn đúng GPT + UEFI)

### 7.3 Ubuntu không nhận diện ổ NVMe

- Vào BIOS → **System Configuration** → kiểm tra **NVMe Controller** đã Enable
- Nếu có tùy chọn **Intel VMD**, tắt nó đi (Disable)

### 7.4 Màn hình đen sau khi boot

- Khởi động lại, vào GRUB, chọn **"Ubuntu (safe graphics)"**
- Sau khi vào được, cài driver đồ họa Intel:
  ```bash
  sudo apt install -y xserver-xorg-video-intel
  sudo reboot
  ```

### 7.5 Wi-Fi không hoạt động

- Cắm mạng dây (Ethernet) nếu có
- Chạy:
  ```bash
  sudo apt update
  sudo apt install -y linux-firmware
  sudo reboot
  ```

### 7.6 Muốn quay lại Windows?

Bạn cần một máy Windows khác để tạo USB cài Windows 11:

```
🔗 https://www.microsoft.com/software-download/windows11
```

> Lưu ý: Không thể khôi phục dữ liệu đã xóa. Chỉ có thể cài lại Windows sạch.

---

## 📞 Tài Nguyên Tham Khảo

| Tài nguyên | Link |
|---|---|
| Ubuntu Official | https://ubuntu.com |
| Ubuntu Forums | https://ubuntuforums.org |
| Ask Ubuntu (Stack Exchange) | https://askubuntu.com |
| HP Support | https://support.hp.com |
| Rufus Official | https://rufus.ie |

---

> 📝 **Ghi chú cuối:** File hướng dẫn này được viết riêng cho máy HP 340S G7 Notebook PC của bạn. Nếu bạn cài cho máy khác, một số bước BIOS có thể khác nhau.

---

**Chúc bạn cài đặt thành công! 🐧**
