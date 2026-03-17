# 🛡️ DLL Injection Detection: Manual Memory Forensics with WinDbg

![Analysis Preview](your-image-or-gif.gif)

## 📖 Introduction
This repository contains the technical documentation and findings from our deep dive into **DLL Injection**. We bypass automated detection tools and focus on the manual identification of malicious artifacts within the Windows Memory using **WinDbg**.

## 🛠️ Injection Mechanism: `CreateRemoteThread`
The video demonstrates the classic injection flow:
* **Targeting:** Identifying the victim process.
* **Allocation:** Using `VirtualAllocEx` to carve out space.
* **Execution:** Triggering `LoadLibrary` via `CreateRemoteThread`.

## 🔍 Forensic Checklist (WinDbg Commands)
During the manual analysis, we utilize several WinDbg commands to hunt for the injected DLL:

1. **Identify the Process:** `!process 0 0 target_process.exe`
2. **Switch Context:** `.process /r /p [Process_Address]`
3. **Examine VAD Tree (Look for Execute/Read/Write):** `!vad [Address]`
4. **Inspect Loaded Modules (PEB):** `!peb`
5. **Analyze Thread Call Stacks:** `k` or `~*k`

## 🎥 Watch the Full Technical Breakdown
For the complete "Hands-on" experience and detailed explanation of the artifacts, watch the video on YouTube:

[![DLL Injection - WinDbg](https://img.shields.io/badge/YouTube-Watch%20Video-red?style=for-the-badge&logo=youtube)](https://youtu.be/N55MhbiybZk?si=mJiUMSoELqRijXC8)

---
**Developed by:** [0x0NullTrace](https://github.com/0x0NullTrace)  
**Community:** Join us at **NullTrace Hub** for more Windows Internals research.
