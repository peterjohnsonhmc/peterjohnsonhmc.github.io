---
layout: post
title: Message and Location Display System
subtitle: Hardware and Software Codesign
cover-img: /assets/img/path.jpg
tags: [FPGA, SystemVerilog, IoT, RaspberryPi, C, apache]
---

My junior year, I took a Microprocessors course with a major lab component. The focus was embedded systems, with major components in C and SystemVerilog. One great aspect of the class was the focus on system design. Each of the labs and project were very open ended, requiring students to come up with their own system and implement it. For the final project my partner Teddy and I decided to build a system that we could use to notify our dorm friends where we were when they came to look for us in our rooms. The project needed to utilize a microprocessor and an FPGA in a significant way. 

We chose to develop a VGA driver for a display. This portion on the system would be done on the FPGA. The message that we would display would be delivered by an IOS application that Teddy a CS major would write. Basically, the app would receive a short message that you wanted to display and extract your location using apple's location service and then send an HTML request to an apache server running on a Raspberry Pi. The Pi would be running some C code to parse the HTML request, and format the message to be sent via SPI to the FPGA. Here you can see an overall block diagram of the system showing the flow of information.

![block_vga](/assets/img/blockdiagram_vga.png){: .center-block :}

Below is a detailed block diagram of the VGA driver I implemented on an FPGA with inputs and output signals as well as bus sizes labeled.

![block_fpga](/assets/img/blockdiagram_fpga.jpg){: .center-block :}

If you want to hear the details, you can read our final report and attached code [here](https://github.com/peterjohnsonhmc/E155/blob/master/E155Final_PJTD/Final%20Project%20Report.pdf).
You can look at the code as well as my other labs for the class (which are also very cool) [here](https://github.com/peterjohnsonhmc/E155).
One of the highlights is an [IoT light sensor](https://github.com/peterjohnsonhmc/E155/tree/master/lab6_PJ). 