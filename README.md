# Steganography Studio

A modern, browser-based steganography tool for securely hiding messages and files inside images with AES encryption.

## Features

- **Hide Text Messages** — Embed secret text directly into carrier images
- **Hide Files** — Conceal any file type (documents, images, archives, etc.) within an image
- **AES Encryption** — All payloads are encrypted with a custom or auto-generated password
- **LSB Embedding** — Uses Least Significant Bit (LSB) steganography for imperceptible embedding
- **Password Protection** — Optional custom passwords or auto-generated secure keys
- **Zero Knowledge** — Everything runs client-side; nothing is uploaded to any server
- **Decode Hidden Data** — Extract and decrypt hidden messages and files from encoded images
- **Modern UI** — Dark theme with real-time feedback and progress indicators

## How It Works

### Encoding
1. Select a carrier image (the image that will contain the hidden data)
2. Choose what to hide: text message or a file
3. Optionally set a custom password (or let the app generate one)
4. Click "Encode" — the app embeds the encrypted data into the image using LSB steganography
5. Download the encoded image (visually indistinguishable from the original)

### Decoding
1. Upload an image that may contain hidden data
2. Click "Decode" to extract and decrypt the payload
3. View the hidden message or download the extracted file

## Technical Details

- **Encryption:** AES-256 via CryptoJS
- **Compression:** Optional gzip compression for file payloads
- **Embedding:** Least Significant Bit (LSB) steganography in PNG images
- **Packet Structure:** [Password Length][Password][Encrypted Data Length][Encrypted Data]
- **Browser Compatibility:** Modern browsers supporting Canvas, FileReader, and Crypto APIs

## Usage

Simply open `steganography_app-1.html` in your web browser. No installation or server required.

### Example Workflow

**Hiding a message:**
```
1. Drag or select a carrier image (e.g., vacation.png)
2. Enter your secret message in the text area
3. Optionally set a password
4. Click "Encode" → download encoded_[timestamp].png
5. Share the encoded image safely
```

**Recovering a message:**
```
1. Upload the encoded image
2. Click "Decode"
3. View the hidden message or download the extracted file
```

## Security Notes

- **Client-Side Only** — No data is sent to any server
- **AES Encryption** — Strong encryption ensures only password holders can decrypt
- **Password Strength** — Use strong, memorable passwords for custom protection
- **Image Quality** — Encoded images are lossless PNG; avoid re-encoding (JPEG compression will corrupt the hidden data)

## Browser Requirements

- Modern browser with support for:
  - Canvas API
  - FileReader API
  - WebCrypto or CryptoJS
  - Uint8Array manipulation

## Limitations

- Carrier image must be large enough to hold the payload (LSB embedding uses ~1 bit per pixel per channel)
- Payload size is limited by image dimensions (rough estimate: max ~[image width × height × 3 bits] bytes)
- Works best with PNG images; avoid lossy formats like JPEG

## Dependencies

External libraries loaded via CDN:
- [CryptoJS](https://cdnjs.cloudflare.com/ajax/libs/crypto-js/) — AES encryption
- [Pako](https://cdnjs.cloudflare.com/ajax/libs/pako/) — gzip compression
- [Google Fonts](https://fonts.googleapis.com/) — Space Mono and DM Sans typography

## License

MIT License — feel free to use, modify, and distribute.

## Disclaimer

This tool is for educational and lawful purposes. Users are responsible for complying with applicable laws regarding encryption and data hiding in their jurisdiction.

---

**Made with ❤️ for digital privacy.**
