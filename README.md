# CNN Hardware Acceleration Platform & Application (Vitis / HLS)

This repository contains the complete end-to-end hardware acceleration workspace for running a CNN model on AMD/Xilinx FPGAs using **Vitis HLS** and the **Vitis Unified Software Platform**.

---

## 📁 Repository Zip Components

```text
Vitis/
├── Readme.md
├── cnn_hls.zip       # Vitis HLS source code & kernel definition
├── cnn_platform.zip  # Hardware Platform Archive (.xsa & BSP definition)
└── cnn_app.zip       # Embedded C/C++ Host Application & Drivers
```

---

## ⚙️ How to Recreate and Run the Project

### Step 1: Recreate Hardware IP (Vitis HLS)
1. Extract `cnn_hls.zip`.
2. Open **Vitis HLS**.
3. Select **File** $\rightarrow$ **Open Project** and point to the extracted HLS project directory.
4. Run **C Synthesis** and **Export RTL** (generates the hardware IP core used in the platform).

### Step 2: Import Hardware Platform & Application into Vitis
1. Open **Vitis Unified Software Platform** (or Vitis Classic).
2. Select **File** $\rightarrow$ **Import...**
3. Choose **Existing Projects into Workspace** (or **Vitis Workspace Archive**).
4. Import **`cnn_platform.zip`** first to register the target hardware system.
5. Import **`cnn_app.zip`** to load the host application code.
6. Right-click the **`cnn_app`** project and select **Build Project**.

---

## 🖥️ Running Inference & Output Monitoring

1. Connect your target FPGA evaluation board to your host PC via USB-JTAG/UART.
2. Open a serial terminal (e.g., Tera Term, PuTTY, or Vitis Terminal) with:
   * **Baud Rate:** `115200`
   * **Data Bits:** `8`
   * **Stop Bits:** `1`
   * **Parity:** `None`
3. In Vitis, right-click `cnn_app` and select **Run As** $\rightarrow$ **1 Launch Hardware (Single Application Debug)**.
4. The application will program the FPGA bitstream, initialize memory, pass input tensors to the CNN acceleration kernel, and print output predictions over UART.

---

## ⚙️ Requirements

* **Software:** AMD/Xilinx Vitis Unified Software Platform & Vitis HLS
* **Target Hardware:** Supported FPGA board with UART serial interface configured
* **Drivers:** FTDI / USB-to-UART bridge drivers installed on the host machine
