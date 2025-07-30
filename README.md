# 📁 High-Performance Directory Tree Generator (PowerShell)

A blazing-fast PowerShell script that generates a comprehensive directory tree with optional streaming output, parallel processing, smart filtering, and multiple output formats.

> ⚙️ Designed for DevOps engineers, system administrators, PowerShell scripters, and technical contributors needing optimized and scalable file structure introspection.

---

## 🚀 Features

- ⚡ **Streaming Output** – Processes and writes huge directory trees incrementally.
- 🔀 **Parallel Processing** – Uses PowerShell 7+ for concurrent scanning of directories.
- 🧠 **Smart Caching** – Avoids redundant operations using intelligent in-memory caching.
- 🧵 **Memory-Efficient** – Uses StringBuilder and .NET I/O for minimal memory usage.
- 📦 **Customizable Output** – Markdown, PlainText, JSON, or XML formats.
- 🔍 **Filtered Listing** – Support for file extension and regex-based exclusions.
- 📈 **Statistics Reporting** – Optional size and count summary.
- 💾 **Large File Skipping** – Skip files above a certain size threshold.

---

## 🔧 Installation

```bash
git clone https://github.com/your-username/directory-tree-generator.git
cd directory-tree-generator
./index.ps1 -Path "C:\Path\To\Your\Project"
```

> Ensure you're running PowerShell 5.1 or PowerShell 7+ (`$PSVersionTable.PSVersion`).

---

## 📌 Usage

```powershell
.\index.ps1 [-Path] <String> [Other Options...]
```

By default, it scans the current directory and outputs a Markdown tree to `directory_tree.md`.

---

## 🛠️ Parameters

| Parameter             | Type      | Description                                                                 |
|-----------------------|-----------|-----------------------------------------------------------------------------|
| `-Path`               | `String`  | Root directory to scan. Defaults to current location.                       |
| `-MaxDepth`           | `Int`     | Recursion depth limit (1–50). Unlimited by default.                        |
| `-FileExtensionFilter`| `String`  | Only include files with this extension (e.g. `.ps1`).                      |
| `-OutputFile`         | `String`  | Path to the output file. Default: `directory_tree.md`.                     |
| `-ExcludePatterns`    | `String[]`| Regex patterns to exclude files or folders (e.g. `'^node_modules$'`).     |
| `-ShowProgress`       | `Switch`  | Displays a progress bar while scanning.                                    |
| `-IncludeStats`       | `Switch`  | Appends file and directory count + size stats.                             |
| `-UseParallel`        | `Switch`  | Enables multi-threaded directory traversal (requires PowerShell 7+).       |
| `-StreamOutput`       | `Switch`  | Outputs incrementally to disk (recommended for large trees).               |
| `-OutputFormat`       | `String`  | Format: `Markdown`, `PlainText`, `JSON`, `XML`. Default: `Markdown`.      |
| `-MaxFileSize`        | `Int`     | Skip files over this size (in MB). Default: `100`.                         |

---

## 📋 Examples

### Basic Markdown Tree
```powershell
.\index.ps1
```

### Limit Depth and Filter by Extension
```powershell
.\index.ps1 -Path C:\Repos -MaxDepth 3 -FileExtensionFilter ".ps1"
```

### Output in JSON Format
```powershell
.\index.ps1 -Path . -OutputFormat JSON -OutputFile tree.json
```

### Parallel Processing with Streaming and Stats
```powershell
.\index.ps1 -UseParallel -StreamOutput -IncludeStats -ShowProgress
```

---

## 🧠 Advanced Options

- **Regex Exclusion**  
  Use `-ExcludePatterns` to skip folders like `.git`, `node_modules`, `bin`, etc.

- **Streaming Output**  
  Useful for directories with **100,000+** files. Avoids memory bottlenecks.

- **Custom Output Formats**  
  JSON and XML output can be consumed by other tools, pipelines, or documentation generators.

- **File Size Control**  
  Skip large media, binaries, or log files using `-MaxFileSize`.

---

## 💻 Compatibility

| Feature             | PowerShell 5.1 | PowerShell 7+ |
|---------------------|----------------|----------------|
| Core functionality  | ✅             | ✅             |
| Parallel processing | ❌             | ✅             |
| Streaming output    | ✅             | ✅             |

> 📝 Recommend PowerShell 7+ for best performance and compatibility.

---

## ⚡ Performance Tips

- Use `-StreamOutput` for deep or large trees.
- Combine `-UseParallel` with `-MaxDepth` to avoid scanning unnecessary subtrees.
- Exclude directories like `node_modules`, `.git`, or `dist` for faster scans.
- On SSDs or fast NVMe drives, parallel mode can yield **3-5x** speedup.

---

## 🤝 Contributing

Pull requests are welcome! Please open an issue first for feature requests or bug reports.

To contribute:

1. Fork the repository
2. Create your branch: `git checkout -b feature/my-enhancement`
3. Commit your changes
4. Push to your branch
5. Open a pull request

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

> 📫 Questions or suggestions? Open an issue or email the maintainer.
