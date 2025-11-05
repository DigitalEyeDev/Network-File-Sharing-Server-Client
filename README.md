🛡️NETWORK FILE SHARING SYSTEM -LSP CAPSTONE PROJECT

𝗔𝘂𝘁𝗵𝗼𝗿: Subhrajit Nayak

𝗖𝗼𝘂𝗿𝘀𝗲: Linux System Programming (LSP)

𝗜𝗻𝘀𝘁𝗶𝘁𝘂𝘁𝗲: SOA - ITER

Project Summary📝
----------------------------------------------------------------------------------------------------------------------------------------
This project implements a secure Network File Sharing System using a client–server architecture built with Python sockets on a Linux environment (WSL2 / Ubuntu). The application supports listing, downloading, and uploading files between the client and server. Security features include user authentication and encrypted communication via SSL.

Goal📝
----------------------------------------------------------------------------------------------------------------------------------------
Design and implement a dependable and secure file transfer system that allows multiple clients to connect to a server and exchange files safely using TCP sockets and SSL encryption.

𝐃𝐞𝐯𝐞𝐥𝐨𝐩𝐦𝐞𝐧𝐭 𝐋𝐨𝐠 (𝐃𝐚𝐲-𝐛𝐲-𝐝𝐚𝐲)
----------------------------------------------------------------------------------------------------------------------------------------
Day 1️⃣ — Socket connection baseline

      •Set up a TCP server and client in Python.
      •Confirmed basic request/response messaging works end-to-end.

Day 2️⃣ — Directory listing & selection

      •Implemented server-side directory enumeration.
      •Client can request the file list and choose an item to download.

Day 3️⃣ — Download capability

      •Added download handling on the server and client.
      •Verified file integrity and correct saving to the client downloads/ folder.

Day 4️⃣ — Upload capability

      •Implemented client → server upload path.
      •Added server-side storage under received_uploads/ and success acknowledgements.

Day 5️⃣ — Authentication & encryption

      •Added simple username/password authentication handshake.
      •Wrapped sockets with TLS using OpenSSL-generated certificates to encrypt all traffic.

## ⚙️ Technologies Used

| Component | Technology |
| :--- | :--- |
| **Language** | Python 3 |
| **OS** | Ubuntu (WSL2 on Windows) |
| **Networking** | TCP Sockets |
| **Security** | SSL (OpenSSL Certificates) |
| **Tools** | nano, openssl, python3 |

