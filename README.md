# Overview:

This project implements a timer-triggered ADC acquisition system on an STM32 Black Pill (STM32F4 series) microcontroller using bare-metal CMSIS programming.

A 100 Hz hardware timer triggers the ADC conversion. The ADC result is transferred to memory using DMA, and once the DMA transfer completes, the ADC value is transmitted via UART to a serial monitor.

This project was developed as part of an assignment from Unmanned Dynamics (via Internshala).



# Features:

100 Hz timer-based ADC triggering

External trigger–based ADC conversion

DMA-based ADC data transfer

UART transmission of ADC values

Fully bare-metal CMSIS implementation

Debugged using live expressions and register inspection

No HAL abstraction layers used


# Hardware Used:

STM32 Black Pill (STM32F4 series)

ST-Link V2 (clone) for flashing and debugging

Arduino Uno used as a USB-to-TTL UART converter

Jumper wires 




# Software Tools:

STM32CubeIDE

CMSIS (no HAL)

STM32F4 Reference Manual


# ADC Configuration:
Single-channel ADC mode

12-bit resolution

External trigger from timer

Right-aligned data

ADC data register connected to DMA

# Timer Configuration:

Timer configured to generate an update event at 100 Hz

Prescaler (PSC) and Auto-Reload Register (ARR) calculated from system clock

Timer update event configured as TRGO to trigger ADC


# DMA Configuration:

Peripheral-to-memory mode

ADC data register as peripheral source

Memory buffer as destination

DMA transfer complete interrupt enabled


# UART Configuration:

UART used to transmit ADC values

Output displayed in STM32CubeIDE console and PuTTY

Arduino Uno used as USB-to-Serial bridge due to unavailability of USB-to-TTL converter


# Debugging Strategy:

Used Live Expressions in STM32CubeIDE to monitor ADC values,Timer counters

Verified DMA buffer updates in real time

Inspected Special Function Registers (SFRs) by pausing execution to confirm correct register configuration

UART debugging added after hardware workaround


# Results:

ADC values update continuously at 100 Hz

ADC readings:

    4095 when connected to 3.3 V
    otherwise 600-1000
    0 when connected to GND
    
Smooth variation for intermediate voltages

Successful DMA transfer and UART output verified
