# packArchiver
A custom file archiver and binary packer written from scratch in pure C, featuring custom header structures and manual memory management.

This project demonstrates low-level systems programming, custom binary header serialization, stream manipulation, and safe buffer-based file I/O without any external dependencies.

---

## 🚀 Features

* **Interactive CLI Shell:** Operates in an interactive loop with a custom prompt (`packArchiver> `) supporting continuous commands.
* **Custom Binary Format:** Packs multiple files sequentially into a single archive file, prepending a structured binary header (`Header`) containing file metadata (`fileName` and `fileSize`).
* **Chunk-Based I/O:** Uses buffered byte reading (`uint8_t buffer[512]`) to safely handle files of varying sizes with low memory overhead.
* **Zero External Dependencies:** Built solely using standard C libraries (`<stdio.h>`, `<stdint.h>`, `<string.h>`, `<stdbool.h>`, `<stdlib.h>`).

---

## 🛠️ Commands

Once you run the program, use the following commands inside the interactive shell:

| Command | Syntax | Description |
| :--- | :--- | :--- |
| **pack** | `pack <archive_name> <file1> <file2> ...` | Bundles multiple files into a single binary archive and removes the originals. |
| **unpack** | `unpack <archive_name>` | Extracts all bundled files back into the current directory and removes the archive. |
| **help** | `help` | Displays the list of available commands. |
| **exit** | `exit` | Exits the interactive shell session. |

---

## 📂 Binary Format Structure

The archive structure is stored sequentially on disk as a repeating pattern:
1. **Metadata Header (`Header` struct):**
   * `char fileName[100]` — The name of the original file.
   * `uint32_t fileSize` — The exact size of the file payload in bytes.
2. **File Payload:** Raw binary data bytes of the corresponding file size.

---

## ⚙️ Building and Running

### Prerequisites
* A C compiler (e.g., GCC, Clang, or MinGW-w64)

### Compilation
Compile the single-file source code using GCC:

```bash
gcc main.c -o packArchiver
