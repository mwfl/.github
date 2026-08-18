<p align="center">
  <a href="https://mwfl.github.io/">
    <img src="https://raw.githubusercontent.com/mwfl/mwfl/main/docs/images/mwfl-mark.svg" width="112" alt="MWFL logo">
  </a>
</p>

<h1 align="center">MWFL</h1>

<p align="center"><strong>Modern Windows Foundation Layer</strong></p>

<p align="center">
  Native Windows applications with modern C++20 ergonomics—without hiding Win32.
</p>

<p align="center">
  <a href="https://mwfl.github.io/"><img src="https://img.shields.io/badge/docs-mwfl.github.io-146c94" alt="Documentation"></a>
  <a href="https://github.com/mwfl/mwfl/releases/latest"><img src="https://img.shields.io/github/v/release/mwfl/mwfl?label=mwfl" alt="Latest MWFL release"></a>
  <a href="https://github.com/mwfl/mwfl/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-17a589" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/C%2B%2B-20-146c94" alt="C++20">
  <img src="https://img.shields.io/badge/platform-Windows%2010%2B-ff9f43" alt="Windows 10 or newer">
</p>

[MWFL](https://github.com/mwfl/mwfl) is a C++20 foundation for native Windows
desktop software. It keeps real HWND controls, Windows messages, styles,
handles, and return values available while removing repetitive Win32 ceremony
with typed events, RAII ownership, DPI-aware layout, checked operations, and
small independently linked components.

The project covers both the visible application layer and the foundations
behind it: native UI, Shell and document workflows, Process supervision,
local IPC, Windows Services, diagnostics, credentials and identity,
deployment primitives, and Task Scheduler integration. It does not introduce
a custom renderer, virtual DOM, code generator, reflection system, or hidden
background runtime.

<p align="center">
  <a href="https://mwfl.github.io/">
    <img width="100%" src="https://raw.githubusercontent.com/mwfl/mwfl/main/docs/images/showcase/mwfl-showcase-40s.gif" alt="MWFL applications running with populated native controls">
  </a>
</p>

## Lightweight Windows tools

These are small, local-first applications intended to be useful on their own.
They are also end-to-end proving grounds for MWFL: every real editor, reader,
browser, dialog, background task, package, and failure mode helps show whether
the library keeps application code compact without sacrificing native Windows
behavior.

All downloads below are Windows x64 Portable ZIPs. No installer is required:
download, verify the SHA-256 file on the Release page, and extract the archive.
Each application can check GitHub Releases for updates, defer a reminder, or
disable automatic update checks in Settings.

| Application | What it does | Release | Portable download |
|---|---|---:|---|
| [Folder Compare](https://github.com/mwfl/folder-compare) | Local-first file and folder comparison | [v0.1.0](https://github.com/mwfl/folder-compare/releases/tag/v0.1.0) | [Download ZIP](https://github.com/mwfl/folder-compare/releases/download/v0.1.0/folder-compare-v0.1.0-windows-x64-portable.zip) |
| [Folder Explorer](https://github.com/mwfl/folder-explorer) | Folder inventory and PE inspection workspace | [v0.1.1](https://github.com/mwfl/folder-explorer/releases/tag/v0.1.1) | [Download ZIP](https://github.com/mwfl/folder-explorer/releases/download/v0.1.1/folder-explorer-v0.1.1-windows-x64-portable.zip) |
| [Hex Editor](https://github.com/mwfl/hex-editor) | Safety-focused hex editing with read-only defaults and backed-up atomic saves | [v0.1.2](https://github.com/mwfl/hex-editor/releases/tag/v0.1.2) | [Download ZIP](https://github.com/mwfl/hex-editor/releases/download/v0.1.2/hex-editor-v0.1.2-windows-x64-portable.zip) |
| [Markdown Editor](https://github.com/mwfl/markdown-editor) | Local-first Markdown editing with Scintilla and offline preview | [v0.1.0](https://github.com/mwfl/markdown-editor/releases/tag/v0.1.0) | [Download ZIP](https://github.com/mwfl/markdown-editor/releases/download/v0.1.0/markdown-editor-v0.1.0-windows-x64-portable.zip) |
| [Notepad Colon](https://github.com/mwfl/notepad-colon) | Native text and code editor | [v0.1.0](https://github.com/mwfl/notepad-colon/releases/tag/v0.1.0) | [Download ZIP](https://github.com/mwfl/notepad-colon/releases/download/v0.1.0/notepad-colon-v0.1.0-windows-x64-portable.zip) |
| [PDF Reader](https://github.com/mwfl/pdf-reader) | Tabbed reader for local PDF documents | [v0.1.0](https://github.com/mwfl/pdf-reader/releases/tag/v0.1.0) | [Download ZIP](https://github.com/mwfl/pdf-reader/releases/download/v0.1.0/pdf-reader-v0.1.0-windows-x64-portable.zip) |
| [Rho PDF](https://github.com/mwfl/rhopdf) | Fast PDF reader and toolbox built with PDFium and qpdf | [v1.0.0](https://github.com/mwfl/rhopdf/releases/tag/v1.0.0) | [Download ZIP](https://github.com/mwfl/rhopdf/releases/download/v1.0.0/rhopdf-v1.0.0-windows-x64-portable.zip) |
| [SQLite Viewer](https://github.com/mwfl/sqlite-viewer) | Read-only SQLite browsing, bounded queries, and CSV export | [v0.1.0](https://github.com/mwfl/sqlite-viewer/releases/tag/v0.1.0) | [Download ZIP](https://github.com/mwfl/sqlite-viewer/releases/download/v0.1.0/sqlite-viewer-v0.1.0-windows-x64-portable.zip) |
| [Startup Manager](https://github.com/mwfl/startup-manager) | Safety-focused management of Windows startup entries | [v0.1.1](https://github.com/mwfl/startup-manager/releases/tag/v0.1.1) | [Download ZIP](https://github.com/mwfl/startup-manager/releases/download/v0.1.1/startup-manager-v0.1.1-windows-x64-portable.zip) |

## Build a native app

The smallest MWFL applications are ordinary C++ files using real Windows
controls. For standalone projects, CMake `FetchContent` is the quickest start:

```cmake
include(FetchContent)
FetchContent_Declare(mwfl
  GIT_REPOSITORY https://github.com/mwfl/mwfl.git
  GIT_TAG v0.2.0
  GIT_SHALLOW TRUE)
FetchContent_MakeAvailable(mwfl)

add_executable(my_app WIN32 main.cpp)
target_link_libraries(my_app PRIVATE mwfl::ui)
```

Start with the [MWFL repository](https://github.com/mwfl/mwfl), browse the
[component reference](https://mwfl.github.io/components/), or explore the
[62 compiled examples](https://github.com/mwfl/mwfl/tree/main/examples).

## Open and practical

MWFL and the applications above are developed in public under permissive
licenses. Issues, focused pull requests, usability reports, and small native
Windows tool ideas are welcome. If a tool is useful to you, download it and
tell us where the library still makes application development harder than it
should be—that feedback is part of how MWFL improves.
