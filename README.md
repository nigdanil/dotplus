# 🐧 DotPlus — Linux Release

## 🇷🇺 Русский (RU)

**dotplus** — кроссплатформенная CLI/GUI-утилита для генерации QR-кодов, штрихкодов и A4-совместимых PDF из CSV-файлов.  
Реализовано на Rust с использованием ImageMagick 6.9 для точного рендеринга. Поддерживается в Docker и через нативные сборки `.deb` и `.rpm`.

---

## 🖥️ Интерфейсы

| Интерфейс | Поддержка               |
|----------|--------------------------|
| ✅ CLI   | Да                       |
| ✅ GUI   | Да                       |

---

## ✅ Возможности

- Генерация **QR-кодов** и **штрихкодов** (EAN-13, Code128 и др.)
- Экспорт в PNG или PDF с размещением по **сетке на листе A4**
- Вставка логотипов, настройка шрифта, цвета, отступов
- Запуск через Docker или нативно

---

## 📥 Установка

Вы можете загрузить готовые сборки с [GitHub Releases](https://github.com/nigdanil/dotplus/releases) или использовать Docker.


📁 Файлы сборок находятся в папке [`./build/`](./build/):

- `dotplus_1.0.0_amd64.deb` — для x86_64
- `dotplus_1.0.0_arm64.deb` — для ARM64
- `dotplus_1.0.0_armhf.deb` — для ARMv7
- `dotplus-1.0.0-1.x86_64.rpm` — RPM-сборка

## 📂 Примеры использования (`./examples`)

В папке `examples/` находятся демонстрационные данные и шаблоны для запуска:

```
examples/
└── magnit/
    ├── data/        # CSV-файлы с кодами
    │   ├── barcode/ # Штрихкоды: EAN-13, Code-39 и др.
    │   └── qr/      # QR-коды: с логотипом и без
    ├── img/         # Сгенерированные изображения (PNG)
    │   ├── barcode/ # Штрихкоды в PNG
    │   └── qr/      # QR-коды в PNG и PDF
    └── logo/        # Логотипы для вставки в QR
```

### 📦 .deb / .rpm (Linux)

| Архитектура | DEB          | RPM         |
|-------------|--------------|-------------|
| `amd64`     | ✅ `x86_64`  | ✅ `x86_64` |
| `arm64`     | ✅ `aarch64` |             |
| `armhf`     | ✅ `armv7hf` |             |

> Необходимо наличие **ImageMagick версии 6.9** (например, `6.9.12-98`)

---

## 📦 Установка `.deb` (Debian/Ubuntu)

### 1. `dotplus_1.0.0_amd64.deb`

```bash
sudo dpkg -i dotplus_1.0.0_amd64.deb
sudo apt-get install -f
```

### 2. `dotplus_1.0.0_arm64.deb` (например, Raspberry Pi 4)

```bash
sudo dpkg -i dotplus_1.0.0_arm64.deb
sudo apt-get install -f
```

### 3. `dotplus_1.0.0_armhf.deb` (например, Raspberry Pi Zero)

```bash
sudo dpkg -i dotplus_1.0.0_armhf.deb
sudo apt-get install -f
```

---

## 📦 Установка `.rpm` (Fedora/RHEL/CentOS)

### 4. `dotplus-1.0.0-1.x86_64.rpm`

```bash
sudo rpm -i dotplus-1.0.0-1.x86_64.rpm
```

Или с авторазрешением зависимостей:

```bash
sudo dnf install ./dotplus-1.0.0-1.x86_64.rpm
# или
sudo yum install ./dotplus-1.0.0-1.x86_64.rpm
```

---

## 🔧 Зависимости

```bash
convert --version
```

Если ImageMagick не установлен:

```bash
# Debian/Ubuntu
sudo apt install imagemagick

# RHEL/Fedora
sudo dnf install ImageMagick
```

---

## ✅ Проверка установки

```bash
which dotplus
dotplus --help
```

---

## 📄 Примеры запуска

### 🔹 QR-коды

```bash
dotplus-cli \
  --mode qr \
  --csv ./examples/magnit/data/qr/magnit.csv \
  --logo ./examples/magnit/logo/v1.png \
  --output ./examples/magnit/img/qr \
  --cols 3 \
  --rows 3 \
  --qr-size 150 \
  --font-size 24 \
  --font-color "#000000"
```

### 🔹 Штрихкоды (EAN-13)

```bash
dotplus-cli \
  --mode barcode \
  --csv ./examples/magnit/data/barcode/magnit-barcodes-EAN-13.csv \
  --output ./examples/magnit/img/barcode \
  --barcode-type EAN-13 \
  --cols 3 \
  --rows 4 \
  --width 300 \
  --height 100 \
  --font-size 22 \
  --label-height 40 \
  --offset-y 10 \
  --spacing-x 20 \
  --spacing-y 20
```

---

## ⚙️ Архитектуры сборки

| Тип    | Target                          | Архитектура |
| ------ | ------------------------------- | ----------- |
| Debian | `x86_64-unknown-linux-gnu`      | `amd64`     |
| Debian | `aarch64-unknown-linux-gnu`     | `arm64`     |
| Debian | `armv7-unknown-linux-gnueabihf` | `armhf`     |
| RPM    | `x86_64`                        | `x86_64`    |

> Сборка через `cross`, `docker buildx`, `cargo-deb`, `cargo-generate-rpm`.

---

## 📦 Распаковка артефактов

```bash
which dotplus
dotplus --help
```

---

## 🇬🇧 English (EN)

**dotplus** is a cross-platform CLI/GUI tool for generating QR codes, barcodes, and A4-ready PDFs from CSV files.
Built in Rust with ImageMagick 6.9. Supports both Docker and native `.deb` / `.rpm` Linux packages.

---

## 🖥️ Interfaces

| Interface | Supported                  |
| --------- | -------------------------- |
| ✅ CLI    | Yes                        |
| ✅ GUI    | Yes                        |

---

## ✅ Features

* Generate **QR codes** and **barcodes** (EAN-13, Code128, etc.)
* Output to **PNG** or **PDF** with grid layout for A4 paper
* Logo embedding, custom font, color, padding
* Runs via Docker or native binary

---

## 📥 Installation

You can download prebuilt binaries from [GitHub Releases](https://github.com/nigdanil/dotplus/releases) or use Docker.


📁 Build files are located in the [`./build/`](./build/) directory:

- `dotplus_1.0.0_amd64.deb` — for x86_64
- `dotplus_1.0.0_arm64.deb` — for ARM64
- `dotplus_1.0.0_armhf.deb` — for ARMv7
- `dotplus-1.0.0-1.x86_64.rpm` — RPM package for x86_64

In the `examples/` folder, you'll find demonstration data and templates for quick usage:

```
examples/
└── magnit/
    ├── data/        # CSV files with codes
    │   ├── barcode/ # Barcodes: EAN-13, Code-39, etc.
    │   └── qr/      # QR codes: with and without logos
    ├── img/         # Generated images (PNG)
    │   ├── barcode/ # Barcodes in PNG format
    │   └── qr/      # QR codes in PNG and PDF formats
    └── logo/        # Logos for embedding into QR codes
```


### 📦 .deb / .rpm (Linux)

| Architecture | DEB         | RPM        |
| ------------ | ----------- | ---------- |
| `amd64`      | ✅ `x86_64`  | ✅ `x86_64` |
| `arm64`      | ✅ `aarch64` |            |
| `armhf`      | ✅ `armv7hf` |            |

> Requires **ImageMagick 6.9** (e.g. `6.9.12-98`) to be installed.

---

## 📦 Install `.deb` (Debian/Ubuntu)

### 1. `dotplus_1.0.0_amd64.deb`

```bash
sudo dpkg -i dotplus_1.0.0_amd64.deb
sudo apt-get install -f
```

### 2. `dotplus_1.0.0_arm64.deb` (Raspberry Pi 4, etc.)

```bash
sudo dpkg -i dotplus_1.0.0_arm64.deb
sudo apt-get install -f
```

### 3. `dotplus_1.0.0_armhf.deb` (Raspberry Pi Zero/3)

```bash
sudo dpkg -i dotplus_1.0.0_armhf.deb
sudo apt-get install -f
```

---

## 📦 Install `.rpm` (Fedora/RHEL/CentOS)

### 4. `dotplus-1.0.0-1.x86_64.rpm`

```bash
sudo rpm -i dotplus-1.0.0-1.x86_64.rpm
```

With automatic dependency resolution:

```bash
sudo dnf install ./dotplus-1.0.0-1.x86_64.rpm
# or
sudo yum install ./dotplus-1.0.0-1.x86_64.rpm
```

---

## 🔧 Dependencies

```bash
convert --version
```

If ImageMagick is missing:

```bash
# Debian/Ubuntu
sudo apt install imagemagick

# RHEL/Fedora
sudo dnf install ImageMagick
```

---

## ✅ Verify Installation

```bash
which dotplus
dotplus --help
```

---

## 📄 Usage Examples

### 🔹 QR Codes

```bash
dotplus-cli \
  --mode qr \
  --csv ./examples/magnit/data/qr/magnit.csv \
  --logo ./examples/magnit/logo/v1.png \
  --output ./examples/magnit/img/qr \
  --cols 3 \
  --rows 3 \
  --qr-size 150 \
  --font-size 24 \
  --font-color "#000000"
```

### 🔹 Barcodes (EAN-13)

```bash
dotplus-cli \
  --mode barcode \
  --csv ./examples/magnit/data/barcode/magnit-barcodes-EAN-13.csv \
  --output ./examples/magnit/img/barcode \
  --barcode-type EAN-13 \
  --cols 3 \
  --rows 4 \
  --width 300 \
  --height 100 \
  --font-size 22 \
  --label-height 40 \
  --offset-y 10 \
  --spacing-x 20 \
  --spacing-y 20
```

---

## ⚙️ Build Targets

| Type   | Target                          | Arch     |
| ------ | ------------------------------- | -------- |
| Debian | `x86_64-unknown-linux-gnu`      | `amd64`  |
| Debian | `aarch64-unknown-linux-gnu`     | `arm64`  |
| Debian | `armv7-unknown-linux-gnueabihf` | `armhf`  |
| RPM    | `x86_64`                        | `x86_64` |

> Built using `cross`, `docker buildx`, `cargo-deb`, `cargo-generate-rpm`.

---

## 📦 Binary Verification

```bash
which dotplus
dotplus --help
```
