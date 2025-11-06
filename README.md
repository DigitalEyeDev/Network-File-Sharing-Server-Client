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
* Client can request the file list and choose an item to download.-

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
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## How to Run

Open two terminals (server and client) on your Ubuntu/WSL2 instance:

### Server terminal

```bash
cd network-file-sharing
python3 server.py
```

### Client terminal

```bash
cd network-file-sharing
python3 client.py
```

### When prompted on the client:
```bash
Enter username: admin
Enter password: password
```

### On success you should see:

```bash
Authentication successful
```

**Available client options:**

1️⃣List 2️⃣Download 3️⃣Upload 4️⃣Quit

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Example Terminal Sessions ###

**Client — downloading a file**

```vbnet
Connected to server using TLS.
Username: student
Password: ****
Authentication successful.
Menu: (1) LIST (2) DOWNLOAD (3) UPLOAD (4) QUIT
Choice: 2
Files available:
1. fileA.txt
Enter filename to DOWNLOAD: fileA.txt
Server: SIZE 15
Downloading... 15/15 bytes (100.0%)
Saved to downloads/fileA.txt (15 bytes)
Server: BYE
```
**Server — upload accepted**
```pgsql
[+] Incoming TLS connection from ('127.0.0.1', 52344)
Auth received: 'AUTH student password123\n'
[+] TLS session established with ('127.0.0.1', 52344)
Command: UPLOAD test_upload.txt
[+] Stored upload as received_uploads/test_upload.txt (24 bytes)
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Protocol Overview ###

The client and server exchange simple textual commands. The key commands are:
   * `AUTH <username> <password>` — initial authentication handshake.
   * `LIST` — server responds with `file1|file2|....`
   * `DOWNLOAD <filename>` — server replies `SIZE <N>` then sends N bytes.
   * `UPLOAD <filename>` — client sends `SIZE <N>` then N bytes.
   * `QUIT` — close connection.

Implementation accounts for TCP stream behavior (headers/data may arrive combined), so parsing handles merged messages and partial reads.

**Chunking**: File content is transferred in chunks (default `CHUNK_SIZE = 4096`) to support large files without loading whole files into memory.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Implementation Notes & Best Practices ###

* Always read the declared `SIZE` and loop until all bytes are received — never rely on a single recv() call.
* Use SSL context with `ssl.PROTOCOL_TLS_SERVER / ssl.PROTOCOL_TLS_CLIENT` and verify certificates as needed.
* Keep server private keys (e.g., `server_key.pem`) out of version control — add them to `.gitignore`.
* Store uploaded files in a dedicated directory (`received_uploads/`) and downloads in `downloads/`.
* Validate filenames to prevent path traversal (e.g., strip .. and absolute path characters).

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Testing Checklist (Before Submission) ###

Ensure each of the following passes:
* `server.py` starts and runs without throwing exceptions.
* `client.py` connects to the server and completes authentication.
* Download a server file; verify the file content in `downloads/`.
* Upload a local file; verify it appears correctly in `received_uploads/`.
* Confirm `server_key.pem` or any private keys are not in the repository.
