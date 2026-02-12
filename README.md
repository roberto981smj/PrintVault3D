# STLZ - 3D Printing Digital Asset Manager 🚀

![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white) ![.NET](https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white) ![WPF](https://img.shields.io/badge/WPF-Windows-0078D7?style=for-the-badge&logo=windows&logoColor=white) ![SQLite](https://img.shields.io/badge/SQLite-07405e?style=for-the-badge&logo=sqlite&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

**STLZ** is a high-performance, locally-hosted **Digital Asset Manager (DAM)** designed specifically for 3D printing enthusiasts. Built with **Modern WPF (.NET 8)**, it organizes STL, 3MF, and G-CODE files, provides automatic thumbnail generation, and performs advanced G-code analysis to calculate printing costs and time.

This project demonstrates the integration of modern desktop application patterns with system-level file operations and cross-language interoperability (C# + Python).

---

<div align="center">
  <a href="https://www.youtube.com/watch?v=yccCG2yYNDM">
    <img src="https://img.youtube.com/vi/yccCG2yYNDM/maxresdefault.jpg" alt="Watch the Demo" width="800" style="border-radius: 8px;">
  </a>
  <br>
  <em>▶️ Click above to watch the quick demo on YouTube</em>
</div>

---

## 📸 Gallery

<p align="center">
  <img src="Assets/home_page.png" alt="Main Dashboard" width="800" style="border-radius: 8px;">
  <br>
  <em>Organize thousands of STL/3MF files with ease.</em>
</p>

---

## 🛠️ Tech Stack & Architecture

### Core Technologies

- **Framework:** .NET 8 (C# 12)
- **UI Framework:** WPF (Windows Presentation Foundation)
- **Architecture:** MVVM (Model-View-ViewModel)
- **Database:** SQLite with Entity Framework Core 8
- **Scripting:** Python 3.10+ for 3D rendering and thumbnail generation

### Key Libraries & Patterns

- **Architecture:**
  - **MVVM (Model-View-ViewModel):** Clean separation of concerns using `CommunityToolkit.Mvvm`.
  - **Repository Pattern:** Abstracted data access layer for SQLite operations, ensuring testability and decoupling.
  - **Service-Oriented:** Business logic encapsulated in dedicated services (e.g., `FileWatcherService`, `PythonBridgeService`).
  - **Dependency Injection (DI):** Fully managed via `Microsoft.Extensions.DependencyInjection`.

- **Performance & Concurrency:**
  - **Asynchronous I/O:** Extensive use of `async/await` patterns to maintain a responsive UI during heavy file operations.
  - **Parallel Processing:** Multi-threaded thumbnail generation using `SemaphoreSlim` for resource throttling.
  - **UI Virtualization:** Optimized `ItemsControl` and `VirtualizingPanel` for rendering lists with thousands of items.

- **UI & Experience:**
  - **Advanced Data Binding:** Complex XAML bindings with custom Converters (`IValueConverter`).
  - **Custom Window Chrome:** Fully custom window styling with minimize-to-tray functionality.
  - **HelixToolkit.Wpf:** Integrated 3D viewport for real-time model interaction.

- **System Integration:**
  - **FileSystemWatcher:** Event-driven architecture for real-time library synchronization.
  - **Process Interop:** Robust `Process` management for communicating with the embedded Python environment via stdin/stdout.

---

## 🌟 Key Features

### 📂 Smart Library Management

- **Real-time Sync:** Utilizes `FileSystemWatcher` to verify library integrity and detect new files instantly.
- **Archive Support:** Reads and previews models directly inside `.zip` archives without extraction.
- **Auto-Tagging:** Intelligent categorization engine that tags models based on filename heuristics (e.g., "Benchy" -> "Calibration").
- **Duplicate Detection:** SHA-256 based file hashing to prevent duplicate imports.

### 🔍 Advanced G-CODE Analysis

- **Cost & Time Calculation:** Estimates print time and filament usage (grams/meters) by parsing G-code metadata.
- **Slicer Detection:** Automatically detects PrusaSlicer, Cura, OrcaSlicer, and more.
- **Print Tracking:** Track print status, actual print times, and rate your prints.

### 🎨 Modern UI/UX

- **Custom Styling:** Fully custom `ControlTemplates` for a cohesive Neon/Dark aesthetic.
- **Drag & Drop:** Drop files or ZIP archives directly into the app.
- **Collections:** Organize models into custom collections.
- **System Tray:** Minimize to system tray for background file watching.

### 🐍 Python Interop

- **Hybrid Architecture:** Leverages Python scripts for robust 3D rendering (using `numpy-stl` and `matplotlib`).
- **Batch Processing:** Efficient multi-threaded thumbnail generation for large libraries.

---

## 🚀 Installation

### Requirements

- Windows 10 or 11 (64-bit)
- .NET 8 Runtime (Included in release)
- **Python 3.10+** (Required for thumbnail generation & G-code analysis)
  - _Note: If Python is not installed, the app will work but thumbnails won't be generated._

### Running the App

1. Download the latest release from the **Releases** section.
2. Extract the ZIP file.
3. Run `STLZ.exe`.

### Python Dependencies (for thumbnail generation)

```bash
pip install numpy-stl matplotlib
```

---

## 👨‍💻 Build Instructions

To build this project from source:

1. **Clone the repository**

   ```bash
   git clone https://github.com/buraksamisirin/STLZ.git
   cd STLZ
   ```

2. **Restore Dependencies**

   ```bash
   dotnet restore
   ```

3. **Build & Run**

   ```bash
   dotnet build
   dotnet run
   ```

   Or open `STLİE.sln` in Visual Studio 2022.

---

## 📁 Project Structure

```
STLZ/
├── Assets/           # Application icons and images
├── Converters/          # WPF value converters
├── Data/           # Database context and keywords.json
├── Helpers/  # Helper classes (DragDrop, etc.)
├── Migrations/          # EF Core database migrations
├── Models/            # Data models (Model3D, Gcode, etc.)
├── PythonScripts/     # Python scripts for thumbnail generation
├── Repositories/        # Repository pattern implementation
├── Services/            # Business logic services
├── Themes/              # WPF styles and resources
├── ViewModels/   # MVVM ViewModels
└── Views/               # WPF Views (XAML)
```

---

## 🔒 Security Features

- **File Validation:** Comprehensive path traversal and file type validation
- **Input Sanitization:** All file paths and names are sanitized
- **No External Data:** All data stored locally in SQLite database
- **Log Sanitization:** Error messages are sanitized to prevent path disclosure

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

## 📝 License

Distributed under the MIT License. See `LICENSE` for more information.

---

## 👤 Author

**Burak Sami Sirin**

- GitHub: [@buraksamisirin](https://github.com/buraksamisirin)

---

_Developed with ❤️ for the 3D printing community - 2025_
