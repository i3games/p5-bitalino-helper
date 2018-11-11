# P5 BITalino-helper

A helper class for using [Processing](https://processing.org) with [BITalino](http://bitalino.com/en/).

Supports Processing 3.4+ and BITalino (r)evolution (BITalino 2).

First connect your BITalino via Bluetooth / BLE.

To use the BITalino helper, start with one of the examples. Or open a new sketch in Processing and drag and drop `Bitalino.pde` from the `dist` folder on the sketch window. Then you can read data from the BITalino (r)evolution like this:

```
Bitalino2 bitalino;
final int PORT = 0; // the index of the BITalino port displayed in the console
int data[] = new int[6]; // data of the 6 acquisition channels

void setup() {
  bitalino = new Bitalino(this, PORT);
  bitalino.start(10); // data acquisition with 10 samples / second
}

void draw() {
  data = bitalino.receive(); // read a sample
  printArray(data); // print it to the console
}
```

Sometimes, you get an error message like this one: `Error opening serial port /dev/cu.BITalino-DevB: Port busy`. First wait a second and restart the sketch. If the message persists, double check the port and the Bluetooth connection to your BITalino.

See `VERSIONS.md` for more info about the roadmap and planned features.
