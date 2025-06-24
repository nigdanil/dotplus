# 🧩 DotPlus — QR & Barcode Generator

**DotPlus** is a cross-platform tool for generating **QR codes** and **barcodes** (EAN-13, EAN-8, Code 39, Code 93, Codabar), optimized for A4 printing and compatible with label printers.

> **🇷🇺 Русская версия ниже**

---

## 🚀 Features

- ✅ **CLI and GUI** (Windows)
- 🖼️ Add logo overlays to QR codes
- 📄 Full layout customization (columns, rows, spacing, font size, label height)
- 📥 CSV input support
- 📦 Includes ready-to-use batch templates (`.bat`)
- 🔒 Works fully **offline**
- 🐧 Planned support for Linux and Docker

---

## 📦 Releases

| Platform | Status | Link |
|----------|--------|------|
| 🚀 Windows | ✅ Stable | [`release-win`](https://github.com/nigdanil/dotplus/tree/release-win) |
| 🐧 Linux   | 🚧 In progress | [`release-linux`](https://github.com/nigdanil/dotplus/tree/release-linux) |
| 🐳 Docker  | 🔜 Planned | [`release-docker`](https://github.com/nigdanil/dotplus/tree/release-docker) |

---

## 🧾 CSV Input Format

Example:

```csv
id,name,url
1,Product A,https://example.com/A
2,Product B,https://example.com/B
````

---

## ⚡ Quick Start (CLI)

### QR Mode:

```bash
dot-plus.exe ^
  --mode qr ^
  --csv "data.csv" ^
  --logo "logo.png" ^
  --output "output/" ^
  --cols 3 ^
  --rows 3 ^
  --qr-size 150 ^
  --font-size 24 ^
  --font-color "#000000"
```

### Barcode Mode:

```bash
dot-plus.exe ^
  --mode barcode ^
  --csv "barcodes.csv" ^
  --output "output/" ^
  --barcode-type EAN-13
```

---

## 📥 License

This software is **not open source**.  
Binaries are provided for **personal** and **evaluation** use only.  
Commercial usage requires written permission from the author.  

See [LICENSE.txt](./LICENSE.txt) for full terms.

---

## 🛠 Author

Created by [nigdanil](https://github.com/nigdanil)

---

## 🇷🇺 Описание на русском

**DotPlus** — генератор **QR-кодов** и **Штрихкодов**, поддерживает форматы EAN-13, EAN-8, Code 39, Code 93, Codabar.
Идеально подходит для печати на A4 и использования в логистике, торговле и документообороте.

### ⚙️ Возможности

* CLI и GUI (на Windows)
* Добавление логотипа в QR
* Настройка макета: количество строк и столбцов, отступы, размер шрифта, высота подписи
* Ввод из CSV
* Поддержка пакетной генерации
* Полная автономность — работает без интернета

### 📦 Релизы

См. [таблицу выше](#releases)

### 📄 Формат CSV

```csv
id,name,url
1,Товар A,https://example.com/A
2,Товар B,https://example.com/B
```
