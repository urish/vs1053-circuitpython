# VS1053 Driver for CircuitPython

## Sample code (for nRF52840 Dongle)

```python
import vs1053
import board
import busio

spi = busio.SPI(board.P0_22, MISO=board.P0_20, MOSI=board.P1_00)
player = vs1053.Player(
    spi,
    xResetPin = board.P1_10,
    dReqPin = board.P1_13,
    xDCSPin = board.P1_15,
    xCSPin = board.P0_02,
    CSPin = board.P0_24
)

inputFile = open('test.mp3', mode='rb')
buf = inputFile.read(32)
while buf:
    player.writeData(buf)
    buf = inputFile.read(32)
```