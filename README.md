# Datasheets

Index of reference documents for the ESP Drone hardware. Download each PDF and save it in this folder using the suggested filename. Links point to the manufacturer wherever possible; manufacturers sometimes move files, so if a link breaks, search the part number on their site.

## Downloads

| Component | Document | Save as | Link |
|-----------|----------|---------|------|
| Seeed XIAO ESP32S3 Sense | Schematic (PDF) and pinout sheet (XLSX) | `xiao-esp32s3-sense-schematic.pdf` | [Seeed wiki, "Resources" section](https://wiki.seeedstudio.com/xiao_esp32s3_getting_started/) |
| Seeed XIAO ESP32S3 Sense | Pin multiplexing guide | (read online) | [Seeed wiki](https://wiki.seeedstudio.com/xiao_esp32s3_pin_multiplexing/) |
| ESP32-S3 (SoC) | Datasheet | `esp32-s3-datasheet.pdf` | [Espressif](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf) |
| ESP32-S3 (SoC) | Technical Reference Manual | `esp32-s3-trm.pdf` | [Espressif](https://documentation.espressif.com/esp32-s3_technical_reference_manual_en.pdf) |
| BNO085 IMU | Datasheet | `bno085-datasheet.pdf` | [CEVA](https://www.ceva-ip.com/wp-content/uploads/BNO080_085-Datasheet.pdf) |
| BNO085 IMU | SH-2 Reference Manual (sensor reports and protocol) | `sh-2-reference-manual.pdf` | [CEVA](https://www.ceva-ip.com/wp-content/uploads/SH-2-Reference-Manual.pdf) |
| BNO085 IMU | Product brief | `bno085-product-brief.pdf` | [CEVA](https://www.ceva-ip.com/wp-content/uploads/BNO080_085-Product-Brief.pdf) |
| IRLML2502 MOSFET | Datasheet (Infineon) | `irlml2502-datasheet.pdf` | [Infineon PDF](https://www.infineon.com/dgdl/irlml2502pbf-1.pdf?fileId=5546d462533600a4015356680e672608) |
| IRLML2502 MOSFET | Product page (SPICE models, notices) | (read online) | [Infineon](https://www.infineon.com/part/IRLML2502) |
| 720 coreless motor | Seller spec listing (generic part; no formal datasheet) | `720-motor-listing.pdf` | [Example listing (Chaoli CL720)](https://racer.lt/item/chaoli-cl-720-7x20mm-coreless-motor-for-90mm-150mm-diy-micro-fpv-rc-quadcopter-frame-1951.html) |

## Not yet available

- **1S 400 mAh LiPo:** save the seller's listing (capacity, C-rating, connector type) once purchased.
- **1S charger:** save the listing or datasheet once chosen. The XIAO ESP32S3 has its own battery charging circuit, so check whether a separate charger is needed.
- **BNO085 breakout board:** if you are using a breakout (e.g. from Adafruit or SparkFun) rather than the bare chip, save that board's schematic and pinout too.

## Notes

- The 720 motor has no manufacturer datasheet because it is a generic part sold by many sellers. Treat the listing as a rough guide only and rely on your own measurements (`data/measurements/`).
- Record the source and download date of anything you add, so it is clear which revision you designed against.
