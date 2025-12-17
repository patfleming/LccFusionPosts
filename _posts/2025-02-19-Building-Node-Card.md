---
layout: posts
classes: wide 
toc: false
date: 2025-11-20
author_profile: true

title: "Building The LCC Fusion Node Card"
excerpt: "A detailed walkthrough for assembling the LCC Fusion Node Card, from ordering the PCB to verifying the final build."
categories: [LCC Fusion Project, Tutorial]
tags: [lcc, node card, pcb, diy, esp32, assembly]

gallery:
  - url: /assets/images/Building_First_Node_Card.png
    image_path: /assets/images/Building_First_Node_Card_100.png
    alt: "Building The LCC Node"
    title: "Building The LCC Node"

  - url: /assets/images/Applying_paste.png
    image_path: /assets/images/Applying_paste_100.png
    alt: "Applying Paste"
    title: "Apply Paste"
---

{% include gallery layout="third" caption="Building the LCC Fusion Node Card" %}

For those interested in **model railroad automation**, the **LCC Fusion Node Card** provides device control, **power distribution,** and **network communications** with other LCC-enabled devices. The Node Card's MCU (ESP32) provides the firmware to interoperate with other LCC-compatible systems and interacts with various LCC Fusion Project devices., the **LCC Fusion Node Card** provides device control, **power distribution,** and **network communications** with other LCC enabled devices. The Node Card's MCU (ESP32) provides the firmware to interoperate with other LCC compatible and interacts with the many LCC Fusion Project devices. This guide walks through the **entire assembly process**, following the official **project documentation** step-by-step. Documentation can be found here; https://patfleming.github.io/LccFusionProject/node-card-assembly-guide/

## **Ordering the PCB and Choosing a Configuration**

The first step in building the Node Card is to **order the PCB** using the provided **Gerber files (link found in the Components section)**. These files ensure a **high-quality fabrication** from your preferred PCB manufacturer. Once the board is ordered, the next step is to decide on the **hardware configuration**.

For this build, the **CAT-Wired CAN BUS Option** was selected, allowing for easy communications and power **connections with other NMRA compatible LCC Nodes** via standard network cables. This option enables **easy daisy-chaining** and expands the flexibility of the system.

### **Printing Assembly Guides for Reference**

To simplify the build process:

- **Print the PCB image and component list** using the printer icon in the documentation.
- **Print the color-coded assembly diagram** to match components with their correct placements.
- Print the tables for component orientation 
- Having a **printed reference on hand** significantly reduces assembly time and minimizes errors.

------

## **Sourcing Components: What You’ll Need**

Before starting assembly, it’s helpful to review the **Components** section in the project documentation. This provides a complete **bill of materials**, along with links to details about all LCC Fusion components with **pricing details and ordering links** under **Builder's Resources & Tips**. This is especially important for ordering the correct 'package' size and ratings.

### **Essential Components**

- **Microcontroller:** ESP32 DevKitC
- **Voltage Regulators:** LM2596-5V, LM1117-3V3 (or equivalent)
- **Protection Components:** TVS diode, Schottky diodes, resettable fuse
- **Power Inputs:** USB-C, ATX 5557 connector, DC barrel jack (depending on configuration)
- **Networking & I/O:** RJ45 sockets for CAN and Node Bus, additional I2C and SPI headers
- **LED Indicators & Buttons:** Power status LEDs, alert LED, CDI reset button

Use the Assembly-Configuration Options table to verify that you have all of the necessary components on hand before proceeding with assembly. Double-check that all components are correctly labeled and match the specified values to avoid errors during assembly. 

------

## **Preparing the Workspace and Assembling the Board**

With all components ready, setting up a **clean workspace** helps ensure a smooth assembly process:

### **1. Cleaning and Preparing the PCB**

- **Wipe the PCB with isopropyl alcohol** to remove any manufacturing residue.
- **Verify alignment marks** to ensure proper orientation.

### **2. Applying Solder Paste and Stenciling**

- **Ordering a stencil with the PCB** is required for this board, as it allows for **quick and accurate paste application** across the many **SMD components**.
- If using a solder paste stencil:
  - **Align the stencil** using the **two small tooling holes**.
  - **Apply a thin, even layer** of solder paste using a squeegee.
  - **Remove excess paste** before carefully lifting the stencil.

### **3. Placing Components**

- Start with **small surface-mount components** such as resistors and capacitors.
- Place **ICs and voltage regulators** next, ensuring correct orientation.
- Through-hole components like **connectors, headers, and large capacitors** are added last.
- **Use the provided tables** in the assembly documentation to correctly orient all components.
- Note that additional optional components and parts can be added later using a soldering gun and/or heat blower. Because of possible damage to components and parts, it is not recommended to perform a 2nd reflow after PTH components have been added.

### **4. Reflow Soldering or Hand Soldering**

- If using **reflow soldering**, preheat your oven and follow **recommended temperature profiles**.
- For **hand soldering**, use a fine-tip soldering iron at **350–375°C** with **flux** for clean joints.

### **5. Inspecting Solder Joints**

- Use a **magnifying glass or microscope** to check for **cold joints, bridges, or missing connections**.
- Reflow any problematic areas with a **heat gun or soldering iron**.

------

## **Configuration and Testing**

### **1. Verifying Electrical Continuity**

Before applying power:

- Use a **multimeter in continuity mode** to check for shorts between **VCC and GND**.
- Verify that **critical power paths are intact**.

### **2. Powering Up the Board**

- If using a **bench power supply**, start with **current limiting enabled** to prevent damage.
- If using a **12V or 5V adapter**, confirm correct polarity before connecting.

### **3. Checking Node Bus and CAN Communications**

To verify **CAN and I2C communication**:

- Connect the **Node Card to another LCC device** using an **RJ45 cable**.
- Open a **serial monitor** on your computer and check for **successful CAN bus initialization**.
- Run an **I2C scan** to detect connected I/O devices.

### **4. Flashing the ESP32 Firmware**

Once power and communication are verified:

- Use the **provided firmware flashing tool** to install the Node Card firmware.
- Open a **serial monitor** (e.g., YAT or Arduino Serial Monitor) to check **startup messages**.
- If necessary, use the **CDI reset button** to restore factory settings.

## Parts List

To assist you in sourcing the necessary components for building the node card, we've compiled a comprehensive parts list from [AliExpress.com](). This table details each component, the supplier, pricing, and quantities required, providing a clear overview to streamline your assembly process.

| **Product Name**                                             | **Seller**                                  | **Price (USD)** | **Quantity** |
| ------------------------------------------------------------ | ------------------------------------------- | --------------- | ------------ |
| ESP32-DevKitC core board ESP32 development board ESP32-WROOM-32D ESP32-WROOM-32U | WCMCU Store                                 | $3.13           | 1            |
| 10pcs Black RJ45 8P8C Computer Internet Network PCB Jack Socket | C&S Store                                   | $1.71           | 1            |
| 100pcs 1206 SMD Chip Multilayer Ceramic Capacitor 0.5pF - 100uF | DSSRQI Official Store                       | $1.41           | 1            |
| 10pcs/lot PESD1CAN TAN SOT-23 CAN bus ESD protection diode   | Shenzhen IC Global Pass Co LI's Store       | $1.20           | 1            |
| 1808 125V 0451 SMD Fast Blow Fuse 0.5A - 15A                 | HKW Store                                   | $2.85           | 1            |
| 10pcs/lot AMS1117-3.3V Voltage Regulator                     | LuLuMi Phone Store                          | $0.94           | 1            |
| 10pcs LM2596S Voltage Regulator Modules                      | Jin Tank Store                              | $1.84           | 1            |
| 5/10/20pcs LM7805 L7805 7805 L7812CV Voltage Regulator ICs   | Moviitroni Electronic Group Store           | $1.48           | 1            |
| 50pcs LM393 LM393DR LM393D SOP-8 Comparators                 | Supplier of Electronic Components           | $1.41           | 1            |
| 10pcs SN65HVD Series CAN Transceivers                        | Jin Tank Store                              | $3.62           | 1            |
| 100Pcs SMD 1206 Resistors 0ohm - 10M Ohm 1%                  | CHANZON Official Store                      | $1.91           | 1            |
| 10PCS DIP Power Inductor 8x10mm Various Values               | TLZWLA Official Store                       | $1.00           | 1            |
| 100PCS 1206 BLM31PG121SN1L 120 OHM SMD Chip EMI Ferrite Bead | C&G Semiconductor                           | $2.73           | 1            |
| Resettable Fuse 30V PTC Polymer PPTC DIP JK30 0.5A - 10A     | DQLZV Official Store                        | $1.89           | 1            |
| 100pcs SOD-123 1206 SMD Zener Diode 2V - 47V                 | JINLU Store                                 | $1.28           | 1            |
| 100PCS TVS Diode SMBJ Series 16A - 33A SMD                   | Good Good Cheap Electronics Wholesale Store | $4.76           | 1            |
| 10pcs SMD Polymer Solid Capacitor 6.3V - 1000uF              | Auwah Store                                 | $1.94           | 1            |
| 10pcs DIP Solid Electrolytic Capacitor Super Low ESR 6.3V - 1000uF | HKW Store                                   | $2.97           | 1            |
| 10PCS A B C D Case Tantalum Capacitor 6V - 50V 0.1uF - 330uF | FXI Electronics Co., Ltd.                   | $1.32           | 1            |

------

## **Final Thoughts**

The **LCC Fusion Node Card** is a versatile addition to any **model railroad automation project, providing interoperability with other LCC Nodes in your network and communicating with LCC Fusion cards for automation. By following the documented process, assembling the board becomes an **accessible and repeatable** task.

### **Key Takeaways:**

✅ **Ordering a stencil** with the PCB ensures **quick and accurate paste application**.
 ✅ **Printing the color-coded assembly diagram** simplifies component placement.
 ✅ **Using the provided tables** ensures **correct component orientation**.
 ✅ **Verifying continuity before power-up** helps prevent damage.
 ✅ **Testing CAN/I2C communication** ensures seamless integration with other LCC nodes.

For those planning their own build, the **documentation provides everything needed** to get started. 
