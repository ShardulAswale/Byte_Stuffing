# Byte Stuffing over TCP

Java client/server exercise demonstrating message framing and escaping over a TCP connection.

## How it works

The client frames a message with `F`, escapes internal `F` and `E` characters and sends it using UTF data streams. The receiver prints the stuffed and reconstructed messages, acknowledges receipt and closes after the client sends `bye`.

## Usage

Requires a Java Development Kit. Compile from the repository root:

```sh
javac -d out src/bytestuffing/*.java
```

Start the receiver, then the client in a second terminal:

```sh
java -cp out bytestuffing.Byte_Stuffing
java -cp out bytestuffing.Byte_Stuffing_Client
```

Both programs use TCP port `45678` on the local machine.

## Notes

The current receiver reconstruction preserves only `D`, `F` and escaped `E` characters. Other message characters can be dropped, so general round-trip decoding needs correction.
