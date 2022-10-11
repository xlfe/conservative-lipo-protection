# The Conservative LiPo Protection Circuit

### A small Over-discharge / over-charge LiPo protection circuit with sensible limits to prolong the life of your LiPo cells.

![Main](/images/front.jpg "FrontofBoard.jpg")

[View schematic](images/LiPo-Protection.pdf)

## What is it?

A small over-discharge / over-charge LiPo protection circuit with **sensible limits** to prolong the life of your LiPo cells.

* OverDischarge Detection Voltage `3.000V` 
* OverDischarge Release Voltage `3.300V`
* Overcharge Detection Voltage `4.280V` 
* Overcharge Release Voltage `4.080V` 
* Entire circuit - low power mode - measured current draw ~90uA 

### Why did I make it?

I was annoyed that I couldn't find a simple LiPo over-discharge / over-charge protection circuit that had sensible limits (e.g. 3v instead of 2.4v for over-discharge protection). 

I tried purchasing a FS312F-G (which claims to have a Over-discharge protection cut-off of 3.0v) and retrofitting it to a existing cheap protection circuit, but it turned out I'd purchased a fake FS312F-G, and it still cut off at 2.4v!

Frustrated at the time I'd spent already, I decided to build my own.

I've used the [AP9101C](specs/ap9101c.pdf) from Diodes Incorporated - specifically the BRTRG1 variant which has a over-discharge cut-off of 3.0v. I paired it with a [DS31770](specs/ds31770.pdf), also from Diodes Incorporated instead of using a FS8205.

### What makes it special?

It's very hard (if not impossible) to find LiPo over-discharge protection circuits that aren't based on the [DW01 chip](https://cdn.sparkfun.com/assets/learn_tutorials/2/5/1/DW01-P_DataSheet_V10.pdf), which has a over-discharge cutoff of 2.4v - but [many reccomendations](https://learn.adafruit.com/li-ion-and-lipoly-batteries/protection-circuitry) relating to discharging LiPo cells reccomend a over-discharge cutoff voltage of 3.0 volts!

IMHO, 2.4v is too low to discharge a LiPo cell if you want to maximise its life, and for most 3.3v based electronics is too low to be useful anyway.

What are some of your product features?

These boards are fully hand-assembled and reflowed but will require you to connect your circuit (probably soldering) as follows

* Battery negative connects to B- on the board
* Battery positive connects to B+ on the board
* Protected output positive connects to P+ on the board
* Protected output negative connects to P- on the board

Note: Once the over-discharge protection kicks in, the board enters power-down mode (to avoid discharging the battery even more). Once this happens, and once the battery voltage is above you need to briefly connect P- and B- to return the AP9101C to normal operating mode.

### Common uses

I've used this circuit to protect a LiPo battery that is powering a ePaper display with an ESP32, most of the time the circuit is in deep sleep, and once the battery is discharged (ie below 3v) I don't want it to keep discharging.

### Product dimensions

This is a pretty small board - 0.5cm by 2.7cm. You'll need a steady hand and perhaps a magnifying glass to work with it.

### Level of knowledge required

This product is for experienced hobbiests or professionals only as you will need to be comfortable with Low power electronics, soldering and working safely with LiPo batteries.
