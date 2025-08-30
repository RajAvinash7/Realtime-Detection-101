
````markdown
# 📷 Camera Interaction App with SmolVLM + llama.cpp

This project is a simple **real-time camera interaction web app** that connects to a local [`llama.cpp`](https://github.com/ggerganov/llama.cpp) server running a **vision-language model** (SmolVLM 500M).  
It captures frames from your webcam, sends them to the model’s API along with an instruction, and displays the model’s response.

---

## ✨ Features
- Live webcam feed directly in the browser.
- Capture frames at configurable intervals (100ms, 250ms, 500ms, 1s, 2s).
- Send frames + text instruction to a local LLM server (`llama-server`).
- Display server response in real time.
- Simple start/stop button with camera permission handling.

---

## ⚡ Requirements

1. **Operating System**: Windows (64-bit), macOS, or Linux  
2. **llama.cpp binaries**: Download from [llama.cpp releases](https://github.com/ggerganov/llama.cpp/releases)  
   - **If you only want CPU support** → download: `llama-bxxxx-bin-win-cpu-x64.zip`  
   - **If you have NVIDIA GPU** → download: `llama-bxxxx-bin-win-cuda-12.4-x64.zip`  
   - **If you have AMD GPU** → download: `llama-bxxxx-bin-win-hip-radeon-x64.zip`  
   - Extract the zip file (contains `llama-server.exe`).

3. **Model**: SmolVLM (vision-language model)  
   It will be automatically pulled from Hugging Face when you run `llama-server`.

---

## 🚀 Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/camera-interaction-app.git
   cd camera-interaction-app
````

2. Start the **llama.cpp server**:
   Open a terminal where you extracted the binaries, then run:

   ```powershell
   .\llama-server.exe -hf ggml-org/SmolVLM-500M-Instruct-GGUF -ngl 99
   ```

   * `-hf` → automatically downloads the model from Hugging Face.
   * `-ngl 99` → enables GPU acceleration (optional, works if you have GPU).

   The server will start on:

   ```
   http://localhost:8080
   ```

3. Open the **web app**:
   Simply double-click `index.html` (or right-click → “Open with browser”).

---

## 🖥️ How to Use

1. On page load, grant **camera permission** when prompted.
2. Enter your **instruction** (default: *"What do you see?"*).
3. Adjust the **interval** (time between requests).
4. Click **Start**:

   * Webcam snapshots will be sent to the `llama.cpp` server.
   * The model’s response will appear in the **Response** text box.
5. Click **Stop** to pause requests.

---

## 📂 Project Structure

```
.
├── index.html    # Main web app (camera + API requests)
├── LICENSE       # License file
├── README.md     # You are here

```

---

## ⚠️ Troubleshooting

* **`llama-server` not recognized**
  → Make sure you downloaded the right binary, extracted it, and are running inside that folder.

* **CORS errors in browser**
  → Use the latest llama.cpp build (CORS is already enabled by default).

* **Camera not working**
  → Ensure you open the app from `localhost` or `file://`, and grant camera permission.

---



## 🙌 Credits

* [llama.cpp](https://github.com/ggerganov/llama.cpp) for model server backend.
* [SmolVLM](https://huggingface.co/ggml-org/SmolVLM-500M-Instruct-GGUF) for lightweight vision-language model.

---

```


