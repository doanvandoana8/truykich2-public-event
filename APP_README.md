# Truy Kích Event Viewer — Hướng dẫn cài đặt

Công cụ xem sự kiện game Truy Kích. **Ứng dụng miễn phí, phi lợi nhuận.**

---

## Tải về

Vào trang [Releases](https://github.com/doanvandoana8/truykich-app-event/releases/latest) và tải file phù hợp:

| Hệ điều hành | File tải về |
|-------------|-------------|
| **macOS** (M1/M2/M3/M4) | `..._aarch64.dmg` |
| **macOS** (Intel) | `..._x64.dmg` |
| **Windows 64-bit** | `..._x64-setup.exe` hoặc `..._x64_en-US.msi` |
| **Windows 32-bit** | `..._x86-setup.exe` hoặc `..._x86_en-US.msi` |

> **Không biết máy Mac dùng chip gì?** Nhấn vào icon Apple () ở góc trái trên → **About This Mac**. Nếu thấy **Apple M1/M2/M3/M4** thì tải bản `aarch64`. Nếu thấy **Intel** thì tải bản `x64`.

---

## Xác minh file tải về (SHA-256)

Sau khi tải, hãy kiểm tra mã SHA-256 để đảm bảo file đúng nguồn, không bị chỉnh sửa hay nhiễm mã độc.

| File | SHA-256 |
|------|---------|
| `Truy.Kich.Event.Viewer_1.0.0_aarch64.dmg` | `9b9855bbf4a432d9d8e555ad468039dcd41a848f258fbbdb4852e3ccd3bcee75` |
| `Truy.Kich.Event.Viewer_1.0.0_x64.dmg` | `839a4115b2c4cababc937a43f6bc05e9ad353d9381e94b933120ac2b52c7b64a` |
| `Truy.Kich.Event.Viewer_1.0.0_x64-setup.exe` | `4a7a768e8bdef8ddaf97e05f3a74aa430f40391fe5852689bf7a0e21ecdb6d6d` |
| `Truy.Kich.Event.Viewer_1.0.0_x86-setup.exe` | `7aa69aaa62f8512c466e5282c8b3eaf865d4862bf83145c288b15f1d85818fb8` |
| `Truy.Kich.Event.Viewer_1.0.0_x64_en-US.msi` | `ea171ed5c738cc81683a5fd011a555ba976b85c0cf53812cc3b2bcd2feb63c36` |
| `Truy.Kich.Event.Viewer_1.0.0_x86_en-US.msi` | `bc02d46e02bfba8d468e565da4731a2552bc329a87b0304f6b9d307a9f365c38` |

**Cách kiểm tra:**

**macOS** — Mở Terminal và chạy:
```bash
shasum -a 256 ~/Downloads/Truy.Kich.Event.Viewer_1.0.0_aarch64.dmg
```

**Windows** — Mở PowerShell và chạy:
```powershell
Get-FileHash ~\Downloads\Truy.Kich.Event.Viewer_1.0.0_x64-setup.exe -Algorithm SHA256
```

So sánh mã hash hiện ra với bảng trên. Nếu **khớp** → file an toàn. Nếu **không khớp** → xóa file và tải lại từ trang Releases chính thức.

---

## Cài đặt trên macOS

### Bước 1 — Mở file DMG

Mở file `.dmg` vừa tải → kéo app vào thư mục **Applications**.

### Bước 2 — Mở app lần đầu (bị chặn)

Vì app chưa có chữ ký Apple Developer, macOS sẽ chặn và hiện thông báo:

> **"Truy Kich Event Viewer" can't be opened because Apple cannot check it for malicious software.**

**Cách mở:**

1. Mở **System Settings** (Cài đặt hệ thống)
2. Vào **Privacy & Security** (Quyền riêng tư & Bảo mật)
3. Kéo xuống phần **Security**, bạn sẽ thấy dòng:
   > "Truy Kich Event Viewer" was blocked from use because it is not from an identified developer.
4. Nhấn **Open Anyway** (Vẫn mở)
5. Nhập mật khẩu máy nếu được hỏi
6. Nhấn **Open** trong popup xác nhận

> **Chỉ cần làm 1 lần.** Các lần sau mở app bình thường.

### Cách khác (dùng Terminal)

Nếu không thấy nút "Open Anyway", mở **Terminal** và chạy:

```bash
xattr -cr /Applications/Truy\ Kich\ Event\ Viewer.app
```

Sau đó mở app lại bình thường.

---

## Cài đặt trên Windows

### Cách 1 — Dùng file EXE (NSIS Installer)

1. Mở file `..._x64-setup.exe` (hoặc `x86` cho 32-bit)
2. Windows sẽ hiện cảnh báo **"Windows protected your PC"** (Microsoft Defender SmartScreen)

**Cách xử lý:**

1. Nhấn **More info** (Thông tin thêm)
2. Nhấn **Run anyway** (Vẫn chạy)
3. Làm theo hướng dẫn cài đặt

### Cách 2 — Dùng file MSI (Windows Installer)

1. Mở file `..._x64_en-US.msi`
2. Nếu hiện cảnh báo SmartScreen, làm tương tự: **More info** → **Run anyway**
3. Làm theo hướng dẫn cài đặt

### Windows 11 — SmartScreen chặn hoàn toàn

Trên một số máy Windows 11, SmartScreen có thể chặn không cho chạy. Cách tắt tạm:

1. Mở **Windows Security** (Bảo mật Windows)
2. Vào **App & browser control** → **Reputation-based protection settings**
3. Tắt **Check apps and files**
4. Cài đặt app
5. **Bật lại** sau khi cài xong

---

## Gỡ cài đặt

### macOS

Mở **Finder** → **Applications** → kéo **Truy Kich Event Viewer** vào **Trash** (Thùng rác).

Xóa thêm dữ liệu cache (tùy chọn):
```bash
rm -rf ~/Library/Application\ Support/com.truykich.event-viewer
```

### Windows

Mở **Settings** → **Apps** → **Installed apps** → tìm **Truy Kich Event Viewer** → **Uninstall**.

---

## Gặp lỗi khi cài?

| Vấn đề | Giải pháp |
|--------|-----------|
| macOS: "App is damaged" | Chạy `xattr -cr /Applications/Truy\ Kich\ Event\ Viewer.app` trong Terminal |
| macOS: Không thấy "Open Anyway" | Dùng lệnh `xattr -cr` ở trên |
| Windows: SmartScreen chặn | Nhấn **More info** → **Run anyway** |
| Windows: "This app can't run on your PC" | Tải sai phiên bản. Kiểm tra máy 32-bit hay 64-bit (Settings → System → About) |
| App không mở được | Thử gỡ cài đặt rồi cài lại |

---

## Yêu cầu hệ thống

| | Tối thiểu |
|--|-----------|
| **macOS** | macOS 10.15 (Catalina) trở lên |
| **Windows** | Windows 10 trở lên |
| **RAM** | 4 GB |
| **Dung lượng** | ~150 MB (bao gồm Java Runtime) |
| **Internet** | Cần khi Clone dữ liệu và xem ảnh sự kiện |
