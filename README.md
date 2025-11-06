**🛡️𝗡𝗘𝗧𝗪𝗢𝗥𝗞 𝗙𝗜𝗟𝗘 𝗦𝗛𝗔𝗥𝗜𝗡𝗚 𝗦𝗬𝗦𝗧𝗘𝗠 -𝗟𝗦𝗣 𝗖𝗔𝗣𝗦𝗧𝗢𝗡𝗘 𝗣𝗥𝗢𝗝𝗘𝗖𝗧**

𝗔𝘂𝘁𝗵𝗼𝗿: Subhrajit Nayak

𝗖𝗼𝘂𝗿𝘀𝗲: Linux System Programming (LSP)

𝗜𝗻𝘀𝘁𝗶𝘁𝘂𝘁𝗲: SOA - ITER

Project Summary📝
----------------------------------------------------------------------------------------------------------------------------------------
This project implements a secure Network File Sharing System using a client–server architecture built with Python sockets on a Linux environment (WSL2 / Ubuntu). The application supports listing, downloading, and uploading files between the client and server. Security features include user authentication and encrypted communication via SSL.

Goal📝
----------------------------------------------------------------------------------------------------------------------------------------
Design and implement a dependable and secure file transfer system that allows multiple clients to connect to a server and exchange files safely using TCP sockets and SSL encryption.

## 𝐃𝐞𝐯𝐞𝐥𝐨𝐩𝐦𝐞𝐧𝐭 𝐋𝐨𝐠 (𝐃𝐚𝐲-𝐛𝐲-𝐝𝐚𝐲)

**🔌Day 1 — Socket connection baseline**
* Set up a TCP server and client in Python.
* Confirmed basic request/response messaging works end-to-end.

**📒Day 2 — Directory listing & selection**
* Implemented server-side directory enumeration.
* Client can request the file list and choose an item to download.

**📤Day 3 — Download capability**
* Added download handling on the server and client.
* Verified file integrity and correct saving to the client `downloads/` folder.

**📥Day 4 — Upload capability**
* Implemented client → server upload path.
* Added server-side storage under `received_uploads/` and success acknowledgements.

**🔐Day 5 — Authentication & encryption**
* Added simple username/password authentication handshake.
* Wrapped sockets with TLS using OpenSSL-generated certificates to encrypt all traffic.

## ⚙️ Technologies & Tools

| Component | Technology |
| :--- | :--- |
| **Language** | Python 3 |
| **Platform** | Ubuntu (WSL2 on Windows) |
| **Networking** | TCP Sockets |
| **Security** | SSL/TLS via OpenSSL certificates (ssl module) |
| **Utilities** | nano, openssl, python3 |


**How to Run**

Open two terminals (server and client) on your Ubuntu/WSL2 instance:

**Server terminal**
    cd network-file-sharing
    python3 server.py

