# js-raspberrypi-rotary-encoder

## Reliable monitoring of rotary encoders from a raspberry pi

This module allows you to monitor the rotation and the switch state of a rotary encoder from a raspberry pi.
It's use shell to communicate with python awesome [gaugette](https://github.com/guyc/py-gaugette) library.

## Dependencies

You need python 2.7 and the following libraries installed on your raspberry pi:

Python dependencies:
```
    sudo apt-get install python-dev python-pip
```

[WiringPi](http://wiringpi.com/download-and-install/)
```
    sudo pip install wiringpi
```

[Gaugette](https://github.com/guyc/py-gaugette)
```
    cd
    git clone https://github.com/guyc/py-gaugette.git
    cd py-gaugette
    sudo python setup.py install
```

and

[Py-Spidev](https://github.com/doceme/py-spidev)
```
    cd
    git clone https://github.com/doceme/py-spidev.git
    cd py-spidev
    sudo python setup.py install
```

## Installation

Then install this module that way:
```
    npm install raspberrypi-rotary-encoder
```

## Usage

See more examples into the 'examples' folder

```
    const Rotary = require('raspberrypi-rotary-encoder');

    // WARNING ! This is WIRINGPI pin numerotation !! please see https://fr.pinout.xyz/pinout/wiringpi#*
    const pinClk = 0;
    const pinDt = 1;
    const pinSwitch = 2;  // Optional switch

    const rotary = new Rotary(pinClk, pinDt, pinSwitch);

    rotary.on("rotate", (delta) => {
      console.log("Rotation :"+delta);
    });
    rotary.on("pressed", () => {
      console.log("Rotary switch pressed");
    });
    rotary.on("released", () => {
      console.log("Rotary switch released");
    });
```

## API


  - constructor(pinClk, pinDt, [pinSwitch]).
    - The clock pin number [USING WIRINGPI NUMEROTATION !](https://fr.pinout.xyz/pinout/wiringpi#)
    - The data pin number [USING WIRINGPI NUMEROTATION !](https://fr.pinout.xyz/pinout/wiringpi#)
    - If your rotary encoder has a integrated switch you can specify it here, unless it will be ignored
  Tips: Revert the order of the two first parameters to inverse the rotary values (clock-wise/ anti clock-wise)

### Events

  - rotate. Fired when you rotate your rotary encoder.
    - delta : int. The number of steps your rotary has just rotate.
  - pressed. Fired when you press the switch of your rotary encoder.
  - released. Fired when you release the switch of your rotary encoder.

```
    const Rotary = require('raspberrypi-rotary-encoder');

    // WARNING ! This is WIRINGPI pin numerotation !! please see https://fr.pinout.xyz/pinout/wiringpi#*
    const pinClk = 0;
    const pinDt = 1;
    const pinSwitch = 2;  // Optional switch

    const rotary = new Rotary(pinClk, pinDt, pinSwitch);

    rotary.on("rotate", (delta) => {
      console.log("Rotation :"+delta);
    });
    rotary.on("pressed", () => {
      console.log("Rotary switch pressed");
    });
    rotary.on("released", () => {
      console.log("Rotary switch released");
    });
```

[Github sources](https://github.com/kevincastejon/js-raspberrypi-rotary-encoder)