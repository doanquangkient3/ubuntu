# 🍎 Giao Diện macOS cho Ubuntu 24.04 — File Tham Chiếu

> **Mục đích:** File này được tạo ra để một **Agent** trên thiết bị Ubuntu 24.04 khác đọc và thực hiện, sao chép chính xác giao diện macOS đã thiết lập trên thiết bị tham chiếu (HP 340S G7).
>
> **Ngày tạo:** 2026-08-07
>
> **Thiết bị tham chiếu:** HP 340S G7, Ubuntu 24.04 LTS, GNOME 46, Wayland

---

## 📋 Kết Quả Cuối Cùng (Target State)

Sau khi hoàn tất tất cả các bước, giao diện sẽ có:

| Thành phần | Giá trị |
|---|---|
| **GTK Theme** | `WhiteSur-Dark` |
| **WM Theme** | `WhiteSur-Dark` |
| **Shell Theme (top bar)** | `WhiteSur-Dark` |
| **Icon Theme** | `WhiteSur-dark` |
| **Cursor Theme** | `WhiteSur-cursors` |
| **System Font** | `Manrope 10` |
| **Document Font** | `Manrope 11` |
| **Monospace Font** | `Manrope Medium 10` |
| **Font Antialiasing** | `rgba` |
| **Font Hinting** | `slight` |
| **Font RGBA Order** | `rgb` |
| **Animations** | `true` |
| **Window Buttons** | `close,minimize,maximize:` (bên phải) |
| **Dock Position** | `BOTTOM` |
| **Dock Icon Size** | `48` |
| **Dock Centered** | `true` |
| **Dock Extended** | `false` |
| **Dock Trash** | `false` |
| **Dock Opacity** | `0.3` |
| **Desktop Home Icon** | `true` |
| **Desktop Trash Icon** | `false` |

---

## 🤖 Agent: Hướng Dẫn Từng Bước

> Thực hiện **tuần tự** từng bước. Mỗi bước đều có lệnh copy-paste.

---

### Bước 1: Kiểm tra hệ thống

```bash
echo "=== System ==="
lsb_release -rs
gnome-shell --version
echo "XDG: $XDG_SESSION_TYPE"

echo "=== GPU ==="
lspci | grep -i vga
```

> ⚠️ **Quan trọng:** Kiểm tra `$XDG_SESSION_TYPE`. Nếu là **wayland** → đọc note ở Bước 8 (Dock). Nếu là **x11** → có thể dùng Plank.

---

### Bước 2: Cập nhật hệ thống

```bash
sudo apt update && sudo apt upgrade -y
```

---

### Bước 3: Cài các gói cần thiết

```bash
# Cài GNOME Tweaks, Shell Extensions, và các công cụ build
sudo apt install -y \
  gnome-tweaks \
  gnome-shell-extensions \
  git \
  curl \
  wget \
  sassc \
  optipng \
  inkscape \
  libglib2.0-dev-bin

# Cài font Manrope (thay thế SF Pro của macOS)
sudo apt install -y fonts-manrope

# Kiểm tra font
fc-list | grep Manrope
```

---

### Bước 4: Cài WhiteSur GTK Theme

```bash
# Clone và cài theme (cả Light và Dark)
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git /tmp/WhiteSur-gtk-theme
/tmp/WhiteSur-gtk-theme/install.sh -c Dark -c Light -i ubuntu -m
rm -rf /tmp/WhiteSur-gtk-theme

# Xác nhận
ls ~/.themes/ | grep WhiteSur
```

**Giải thích flags:**
- `-c Dark -c Light`: Cài cả 2 theme
- `-i ubuntu`: Tự áp dụng cho Ubuntu
- `-m`: Độ phân giải tiêu chuẩn (Full HD)

---

### Bước 5: Cài WhiteSur Icon Theme

```bash
git clone https://github.com/vinceliuice/WhiteSur-icon-theme.git /tmp/WhiteSur-icon-theme
/tmp/WhiteSur-icon-theme/install.sh -t all
rm -rf /tmp/WhiteSur-icon-theme

# Xác nhận
ls ~/.local/share/icons/ | grep WhiteSur
```

---

### Bước 6: Cài WhiteSur Cursors

```bash
git clone https://github.com/vinceliuice/WhiteSur-cursors.git /tmp/WhiteSur-cursors
/tmp/WhiteSur-cursors/install.sh
rm -rf /tmp/WhiteSur-cursors

# Xác nhận
ls ~/.local/share/icons/ | grep WhiteSur-cursors
```

---

### Bước 7: Bật User Themes Extension

```bash
# Bật extension cho phép đổi GNOME Shell theme (top bar)
gnome-extensions enable user-theme@gnome-shell-extensions.gcampax.github.com 2>/dev/null

# Kiểm tra
gnome-extensions info user-theme@gnome-shell-extensions.gcampax.github.com | grep State
# Phải ra: State: ENABLED
```

---

### Bước 8: Cấu hình Dock

> ⚠️ **Đọc kỹ trước khi thực hiện!**

#### Nếu đang dùng **Wayland** (phổ biến trên Ubuntu 24.04):

**Plank KHÔNG hỗ trợ Wayland** — sẽ crash với lỗi `Only X11 environments are supported`.  
→ Dùng **Ubuntu Dock** (dash-to-dock) có sẵn, cấu hình macOS-style:

```bash
# Đảm bảo Ubuntu Dock được bật
gnome-extensions enable ubuntu-dock@ubuntu.com 2>/dev/null

# Cấu hình macOS-style
gsettings set org.gnome.shell.extensions.dash-to-dock dash-max-icon-size 48
gsettings set org.gnome.shell.extensions.dash-to-dock dock-position 'BOTTOM'
gsettings set org.gnome.shell.extensions.dash-to-dock always-center-icons true
gsettings set org.gnome.shell.extensions.dash-to-dock extend-height false
gsettings set org.gnome.shell.extensions.dash-to-dock dock-fixed true
gsettings set org.gnome.shell.extensions.dash-to-dock autohide false
gsettings set org.gnome.shell.extensions.dash-to-dock show-trash false
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts-network false
gsettings set org.gnome.shell.extensions.dash-to-dock background-opacity 0.3
gsettings set org.gnome.shell.extensions.dash-to-dock transparency-mode 'FIXED'
gsettings set org.gnome.shell.extensions.dash-to-dock running-indicator-style 'DOTS'
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
gsettings set org.gnome.shell.extensions.dash-to-dock scroll-action 'switch-workspace'
gsettings set org.gnome.shell.extensions.dash-to-dock show-show-apps-button true
gsettings set org.gnome.shell.extensions.dash-to-dock show-apps-always-in-the-edge true
```

#### Nếu đang dùng **X11** (hoặc đã switch sang X11):

Có thể dùng **Plank** (dock giống macOS hơn):

```bash
# Cài Plank
sudo apt install -y plank

# Tắt Ubuntu Dock
gnome-extensions disable ubuntu-dock@ubuntu.com

# Tạo autostart
mkdir -p ~/.config/autostart
cat > ~/.config/autostart/plank.desktop << 'EOF'
[Desktop Entry]
Type=Application
Name=Plank
Exec=plank
StartupNotify=false
X-GNOME-Autostart-enabled=true
EOF

# Cấu hình Plank macOS-style
gsettings set net.launchpad.plank enabled-docks "['dock1']"
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ alignment 'center'
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ auto-pinning true
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ hide-mode 'intelligent'
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ hide-delay 0
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ unhide-delay 0
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ icon-size 48
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ items-alignment 'center'
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ position 'bottom'
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ theme 'Default'
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ zoom-enabled false
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ tooltips-enabled true
gsettings set net.launchpad.plank.dock.settings:/net/launchpad/plank/docks/dock1/ current-workspace-only false

# Chạy Plank
nohup plank > /dev/null 2>&1 &
```

---

### Bước 9: Áp dụng toàn bộ theme

```bash
# === GTK Theme (cửa sổ, nút, panel) ===
gsettings set org.gnome.desktop.interface gtk-theme 'WhiteSur-Dark'
gsettings set org.gnome.desktop.wm.preferences theme 'WhiteSur-Dark'

# === GNOME Shell Theme (top bar) ===
gsettings set org.gnome.shell.extensions.user-theme name 'WhiteSur-Dark'

# === Icon Theme ===
gsettings set org.gnome.desktop.interface icon-theme 'WhiteSur-dark'

# === Cursor Theme ===
gsettings set org.gnome.desktop.interface cursor-theme 'WhiteSur-cursors'

# === Font hệ thống ===
gsettings set org.gnome.desktop.interface font-name 'Manrope 10'
gsettings set org.gnome.desktop.interface document-font-name 'Manrope 11'
gsettings set org.gnome.desktop.interface monospace-font-name 'Manrope Medium 10'

# === Font rendering (sắc nét) ===
gsettings set org.gnome.desktop.interface font-antialiasing 'rgba'
gsettings set org.gnome.desktop.interface font-hinting 'slight'
gsettings set org.gnome.desktop.interface font-rgba-order 'rgb'

# === Window buttons (bên phải) ===
gsettings set org.gnome.desktop.wm.preferences button-layout 'close,minimize,maximize:'

# === Animations (mượt, giống macOS) ===
gsettings set org.gnome.desktop.interface enable-animations true

# === Desktop icons ===
gsettings set org.gnome.shell.extensions.ding show-home true
gsettings set org.gnome.shell.extensions.ding show-trash false
```

> 🔄 **Chuyển đổi Light ↔ Dark:** Thay `WhiteSur-Dark` → `WhiteSur-Light` và `WhiteSur-dark` → `WhiteSur-light`.

---

### Bước 10: Khởi động lại GNOME Shell

Nhấn tổ hợp phím:
```
Alt + F2 → gõ "r" → Enter
```

Hoặc nếu không được (trên Wayland một số phiên bản), **logout và login lại**.

---

### Bước 11: Kiểm tra kết quả

```bash
echo "╔════════════════════════════════════════╗"
echo "║     THEME VERIFICATION                ║"
echo "╚════════════════════════════════════════╝"
echo ""
echo "=== System ==="
echo "Ubuntu: $(lsb_release -rs)"
echo "GNOME:  $(gnome-shell --version 2>/dev/null)"
echo "Server: $XDG_SESSION_TYPE"
echo ""
echo "=== GTK Theme ==="
echo "GTK:           $(gsettings get org.gnome.desktop.interface gtk-theme)"
echo "WM:            $(gsettings get org.gnome.desktop.wm.preferences theme)"
echo "Shell:         $(gsettings get org.gnome.shell.extensions.user-theme name)"
echo ""
echo "=== Icons & Cursor ==="
echo "Icons:         $(gsettings get org.gnome.desktop.interface icon-theme)"
echo "Cursor:        $(gsettings get org.gnome.desktop.interface cursor-theme)"
echo ""
echo "=== Font ==="
echo "Interface:     $(gsettings get org.gnome.desktop.interface font-name)"
echo "Document:      $(gsettings get org.gnome.desktop.interface document-font-name)"
echo "Monospace:     $(gsettings get org.gnome.desktop.interface monospace-font-name)"
echo "Antialiasing:  $(gsettings get org.gnome.desktop.interface font-antialiasing)"
echo "Hinting:       $(gsettings get org.gnome.desktop.interface font-hinting)"
echo ""
echo "=== Window ==="
echo "Buttons:       $(gsettings get org.gnome.desktop.wm.preferences button-layout)"
echo "Animations:    $(gsettings get org.gnome.desktop.interface enable-animations)"
echo ""
echo "=== Dock ==="
echo "Position:      $(gsettings get org.gnome.shell.extensions.dash-to-dock dock-position)"
echo "Icon size:     $(gsettings get org.gnome.shell.extensions.dash-to-dock dash-max-icon-size)"
echo "Centered:      $(gsettings get org.gnome.shell.extensions.dash-to-dock always-center-icons)"
echo "Extend:        $(gsettings get org.gnome.shell.extensions.dash-to-dock extend-height)"
echo "Trash on dock: $(gsettings get org.gnome.shell.extensions.dash-to-dock show-trash)"
echo "Opacity:       $(gsettings get org.gnome.shell.extensions.dash-to-dock background-opacity)"
echo ""
echo "=== Desktop Icons ==="
echo "Home:          $(gsettings get org.gnome.shell.extensions.ding show-home)"
echo "Trash:         $(gsettings get org.gnome.shell.extensions.ding show-trash)"
echo ""
echo "=== Installed Themes ==="
echo "GTK themes:    $(ls ~/.themes/ 2>/dev/null | grep WhiteSur | tr '\n' ' ')"
echo "Icon themes:   $(ls ~/.local/share/icons/ 2>/dev/null | grep WhiteSur | tr '\n' ' ')"
```

**Kết quả mong đợi:**

```
GTK:           'WhiteSur-Dark'
WM:            'WhiteSur-Dark'
Shell:         'WhiteSur-Dark'
Icons:         'WhiteSur-dark'
Cursor:        'WhiteSur-cursors'
Font:          'Manrope 10'
Buttons:       'close,minimize,maximize:'
Dock Position: 'BOTTOM'
Icon size:     48
Centered:      true
Extend:        false
Trash on dock: false
Opacity:       0.29999999999999999
```

---

## 🔧 Xử Lý Sự Cố

| Vấn đề | Cách khắc phục |
|---|---|
| **Theme không áp dụng** | Mở GNOME Tweaks → Appearance → chọn thủ công |
| **Top bar không đổi** | `gnome-extensions enable user-theme@gnome-shell-extensions.gcampax.github.com` |
| **Plank crash "Only X11"** | Đây là giới hạn của Plank trên Wayland. Chuyển sang dùng Ubuntu Dock (xem Bước 8). |
| **Icon không đổi hết** | Snap app dùng icon riêng — giới hạn của Snap sandbox |
| **Font bị vỡ/lỗi** | `sudo fc-cache -fv` |
| **Muốn nút window bên trái (chuẩn macOS)** | `gsettings set org.gnome.desktop.wm.preferences button-layout 'close,minimize,maximize:appmenu'` |
| **Muốn chuyển sang X11 để dùng Plank** | Logout → click biểu tượng bánh răng ở màn hình login → chọn "Ubuntu on Xorg" |

---

## 📦 Tổng Kết Gói Cần Cài

| Gói | Nguồn | Mục đích |
|---|---|---|
| `gnome-tweaks` | apt | Công cụ chuyển đổi theme |
| `gnome-shell-extensions` | apt | User Themes extension |
| `git` | apt | Clone repo theme |
| `sassc` | apt | Build WhiteSur theme |
| `optipng` | apt | Tối ưu icon |
| `inkscape` | apt | Xử lý SVG icon |
| `libglib2.0-dev-bin` | apt | Build theme settings |
| `fonts-manrope` | apt | Font hệ thống |
| `plank` | apt | Dock (chỉ X11) |
| WhiteSur GTK Theme | GitHub: `vinceliuice/WhiteSur-gtk-theme` | GTK theme |
| WhiteSur Icon Theme | GitHub: `vinceliuice/WhiteSur-icon-theme` | Icon theme |
| WhiteSur Cursors | GitHub: `vinceliuice/WhiteSur-cursors` | Cursor theme |

---

---

## 📂 Phần 2: Tổ Chức Thư Mục — Chuẩn Hóa Không Gian Làm Việc

> 🤖 **Agent:** Sau khi hoàn tất phần giao diện macOS ở trên, tiếp tục tổ chức lại cây thư mục Home cho gọn gàng, khoa học. Mục tiêu: **project-based**, không dùng các thư mục mặc định của Ubuntu (Documents, Music, Videos...).

### Cấu trúc đích

```
/home/<user>/
├── Projects/                 ← TẤT CẢ code & dự án để ở đây
│   └── <tên-dự-án>/          ← Mỗi dự án một thư mục riêng
│       ├── README.md         ← Luôn có file mô tả dự án
│       └── ...
│
├── Scripts/                  ← Script tiện ích cá nhân
│   └── *.sh                  ← Script bash (chmod +x)
│
├── Tools/                    ← Tool portable, AppImage, binary
│   └── ...
│
├── Downloads/                ← Giữ nguyên, dọn dẹp định kỳ
├── Pictures/
│   └── Screenshots/          ← Ảnh chụp màn hình
├── Desktop/                  ← Để trống (sạch sẽ)
│
├── Documents/                ← KHÔNG dùng (code để trong Projects)
├── Music/                    ← KHÔNG dùng
├── Videos/                   ← KHÔNG dùng
├── Templates/                ← KHÔNG dùng
└── Public/                   ← KHÔNG dùng
```

### Bước 1: Tạo cấu trúc thư mục

```bash
# Tạo thư mục chính
mkdir -p ~/Projects ~/Scripts ~/Tools ~/Pictures/Screenshots

# Đảm bảo Desktop trống
rm -f ~/Desktop/* 2>/dev/null

echo "✅ Cấu trúc thư mục đã tạo"
```

### Bước 2: Thiết lập GNOME Shortcuts (thư mục yêu thích)

```bash
# Đặt Projects, Scripts, Tools vào sidebar Files (Nautilus)
# Sửa bookmarks: giữ lại Projects, Downloads, Pictures; bỏ Documents, Music, Videos...

# Tạo symlink cho nhanh (tùy chọn)
# Không cần — Nautilus tự hiển thị các thư mục gốc của Home
```

### Bước 3: Dọn dẹp các thư mục mặc định

> ⚠️ **Không xóa** các thư mục mặc định (có thể gây lỗi với một số ứng dụng). Chỉ cần **không sử dụng** chúng.

```bash
# Xác nhận tất cả thư mục mặc định đều trống
echo "=== Kiểm tra thư mục trống ==="
for dir in Documents Music Videos Templates Public Desktop; do
    count=$(ls -A ~/$dir 2>/dev/null | wc -l)
    if [ "$count" -eq 0 ]; then
        echo "  ~/$dir → TRỐNG ✓"
    else
        echo "  ~/$dir → có $count file/thư mục"
    fi
done
```

### Bước 4: Ghi chú cho người dùng

Sau khi tổ chức xong, nguyên tắc làm việc:

| Quy tắc | Mô tả |
|---|---|
| **Code → Projects** | Mọi dự án (code, tài liệu thiết kế, research) để trong `~/Projects/<tên>/` |
| **Script → Scripts** | Script bash, python tiện ích cá nhân để trong `~/Scripts/` |
| **Tool → Tools** | AppImage, binary portable, công cụ không cài qua apt/snap để trong `~/Tools/` |
| **Desktop sạch** | Không để file nào trên Desktop |
| **Downloads tạm** | Dọn `~/Downloads/` định kỳ — không lưu trữ lâu dài ở đây |

### Bước 5: Kiểm tra kết quả

```bash
echo "╔════════════════════════════════════════╗"
echo "║     DIRECTORY STRUCTURE CHECK         ║"
echo "╚════════════════════════════════════════╝"
echo ""
echo "Home: $(du -sh ~/ 2>/dev/null | cut -f1)"
echo ""
echo "=== Thư mục chính ==="
for dir in Projects Scripts Tools Downloads Pictures Desktop; do
    size=$(du -sh ~/$dir 2>/dev/null | cut -f1)
    items=$(ls -A ~/$dir 2>/dev/null | wc -l)
    echo "  ~/$dir/  ($size, $items items)"
done
echo ""
echo "=== Thư mục mặc định (nên trống) ==="
for dir in Documents Music Videos Templates Public; do
    items=$(ls -A ~/$dir 2>/dev/null | wc -l)
    [ "$items" -eq 0 ] && echo "  ~/$dir/  TRỐNG ✓" || echo "  ~/$dir/  $items items ⚠️"
done
```

**Kết quả mong đợi:**

```
~/Projects/   (có 1+ dự án)
~/Scripts/    (có script .sh)
~/Tools/      (có thể trống)
~/Downloads/  (tạm, ít file)
~/Pictures/   (chủ yếu Screenshots/)
~/Desktop/    TRỐNG
~/Documents/  TRỐNG
~/Music/      TRỐNG
~/Videos/     TRỐNG
```

---

> ✅ **Đã xác nhận hoạt động trên:** HP 340S G7, Ubuntu 24.04 LTS, GNOME 46, Wayland.
>
> 📅 **Ngày xác nhận cuối:** 2026-08-07
