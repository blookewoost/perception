# Embedded Object Detection Project Notes

## 🎯 Goal
Deploy an object detection model (starting with people detection) on an edge device with a dedicated NPU, using a fully open Linux software stack where possible.

---

## 🧠 Object Detection

- **Model**: [YOLOv8](https://github.com/ultralytics/ultralytics)
  - State-of-the-art real-time object detection model
  - Excellent performance on people and vehicle detection
  - Built-in support for the COCO dataset (Common Objects in Context)
  - Highly configurable with Python API
  - ONNX export available for edge deployment

- **Training Pipeline**
  - Supports transfer learning and fine-tuning
  - Can extend dataset with custom classes or domain-specific footage
  - Potential future addition: Lidar-assisted perception fusion

---

## 🧰 Potential Hardware Platforms

### 🥇 **Radxa ROCK 5B** *(Preferred)*
- **SoC**: Rockchip RK3588
- **NPU**: 6 TOPS performance
- **RAM**: Options from 4 GB to 32 GB
- **Pros**:
  - Best-in-class performance at a reasonable price
  - Partial support for open-source Linux (Ubuntu/Debian)
  - Active community and decent documentation
- **Cons**:
  - VPU (video decoding chip) uses proprietary drivers (no open-source support for hardware-accelerated decoding)
- **Shopping Links**:
  - [8 GB Model](https://www.amazon.com/dp/B0D1TZHFQF?th=1)
  - [32 GB Model](https://www.amazon.com/Radxa-5B-Connector-Computer-32GB/dp/B0D1T9MK83?utm_source=chatgpt.com&th=1)

### ✅ Basic BOM (Bill of Materials)
- ✅ Radxa ROCK 5B (choose RAM size as needed)
- ✅ USB-C Power Supply (PD 5V/3A+ recommended)
- ✅ 64GB+ microSD Card (for OS and storage)
- ✅ Heatsink/Fan (RK3588 runs hot)
- ✅ USB to Ethernet Adapter *(if WiFi performance is poor)*

---

### 🧪 **NXP i.MX8M Plus**
- **SoC**: NXP i.MX8M Plus
- **NPU**: 2.3 TOPS
- **Pros**:
  - **Mainline Linux Kernel support**
  - **Open source VPU driver support**
- **Cons**:
  - Significantly lower performance than RK3588
  - Much harder to source and purchase
  - Targeted more at industrial clients

---

## 🎥 Peripherals

- **Camera Input**
  - Plan: Use an RTSP-compatible Ethernet IP camera
  - Familiarity with compressed video streams (e.g., H.264)
  - VPU acceleration would be helpful but isn’t mandatory

- **Lidar Integration** *(Future Consideration)*
  - No current experience — would require research into:
    - Common Lidar interfaces (USB, UART, Ethernet)
    - Data format compatibility (e.g. Point Cloud, ROS drivers)

---

## 📚 Topics to Research
- Interfacing with VPU (even if using proprietary APIs)
- OpenVINO / ONNX Runtime acceleration on RK3588
- RTSP video decoding without hardware acceleration
- Basic LiDAR sensor specs, ROS drivers, and visualization tools
