# Graphics-and-Shaders-3D-Renderer


**A modern OpenGL rendering engine featuring real-time lighting, materials, post-processing effects, and interactive controls.**

---

## 🛠 Installation & Setup

###  Prerequisites
- **Visual Studio 2022+**
- **CMake 3.20+**
- **C++17** compatible compiler
- GPU supporting **OpenGL 4.3+**

###  Build & Run

"bash
"

1. Open "build/OpenGLRenderer.sln" in Visual Studio  
2. Set "graphics" as **Startup Project**  
3. Press **▶️ Local Windows Debugger** to run

---

## Controls

| **Movement**        | **Camera**             | **System**         |
|---------------------|------------------------|--------------------|
| "W" - Forward       | "Mouse" - Look         | "ESC" - Quit       |
| "S" - Backward      | "Space" - Free Camera  | "F1" - Toggle UI   |
| "A" - Left          | "L.Shift" - Lock Cam   | "F2" - Screenshot  |
| "D" - Right         |                        | "F11" - Fullscreen |
| "Q" - Down          |                        |                    |
| "E" - Up            |                        |                    |

---

## ⚡ Engine Features

### 🖼Core Rendering
- **Multi-camera** (Perspective / Orthographic)
- **PBR Materials** (Albedo / Normal / Metallic / Roughness)
- **Dynamic Lighting** (Point / Directional / Spot)
- **Advanced Shading** (Blinn-Phong, Gamma Correction)
- **Real-time Shadows**

###  Post-Processing

"mermaid
graph LR
A[Main Render] --> B[Framebuffer]
B --> C[Bloom Pass]
B --> D[Color Grading]
C --> E[AA Pass]
D --> E
E --> F[Final Output]
"

### 🧩 Tools & UI
- **Interactive scene controls** (ImGui)
- **Real-time parameter tuning**
- **Shader hot-reloading**
- **Debug visualization modes**

---

##  Project Structure

"
project-root/
├── assets/               # Resource files
│   ├── textures/         # PBR textures (HDR supported)
│   ├── models/           # 3D objects (glTF format)
│   └── scenes/           # Scene configurations
├── shaders/              # GLSL pipeline
│   ├── core/             # Main shaders
│   ├── postprocess/      # Screen effects
│   └── include/          # Shared code
├── src/                  # C++ source
│   ├── rendering/        # OpenGL abstractions
│   ├── core/             # Engine systems
│   ├── ui/               # ImGui interface
│   └── main.cpp          # Entry point
├── CMakeLists.txt        # Build configuration
└── README.md
"

---

## 🚀 Quick Start Guide

### 1. Basic Scene Setup

"cpp
// Create main camera
Camera camera(glm::vec3(0, 1, 5), 45.0f, 16.0f/9.0f);

// Load PBR shader
Shader pbrShader("shaders/core/pbr.vs", "shaders/core/pbr.fs");

// Create directional light
DirectionalLight sun;
sun.direction = glm::vec3(-0.5f, -1.0f, -0.3f);
sun.color = glm::vec3(1.0f, 0.95f, 0.9f);

// Load model
Model backpack("assets/models/backpack/backpack.gltf");
"

### 2. Adding Post-Processing

"cpp
// Create effect chain
PostProcessor pp;
pp.addEffect<BloomEffect>(0.5f);     // Glow effect
pp.addEffect<FXAAEffect>();          // Anti-aliasing
pp.addEffect<VignetteEffect>(0.3f);  // Darkened edges
"

### 3. UI Integration

"cpp
// ImGui control panel
ImGui::Begin("Scene Controls");
ImGui::SliderFloat3("Light Position", &lightPos.x, -10, 10);
ImGui::ColorEdit3("Light Color", &lightColor.r);
ImGui::Checkbox("Enable Bloom", &enableBloom);
ImGui::End();
"

---

## 📜 License

**Educational Use** — Free for personal/academic projects  
**Commercial Use** — Requires written permission  
**Attribution** — Required for derivative works

---
