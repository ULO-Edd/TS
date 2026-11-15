# ProjetoTS – Secure Client/Server Chat

Client/server application developed for the **TS (Tópicos de Segurança)** course, 1st year / 2nd semester of the TeSP in Programação de Sistemas de Informação (IPL).

A Windows Forms client connects to a console server over TCP using the `ProtocolSI` library. Users can exchange messages with a server-side chatbot and send/receive files, with cryptography applied to messages and files.

## Authors

- Eduardo Amado (2202420)
- João Fernandes (2201158)
- Tiago Tavares (2202418)

## Features

- **Authentication** – user login and registration
- **Chat** – messages sent to the server, which answers through a simple chatbot (greetings, current time, etc.)
- **File transfer** – send and receive files
- **Cryptography**
  - RSA key pair for asymmetric encryption
  - AES for symmetric encryption of messages and files
  - Key derivation with `Rfc2898DeriveBytes` (PBKDF2)
- **Multi-client server** – each client is handled on its own thread

## Solution structure

```
ProjetoTS/
├── ProjetoTS.sln
├── Cliente/      # Windows Forms client (login, main menu, chat, files, crypto forms)
├── Servidor/     # Console server (Listening, ClientHandler, ChatBot, ReceiveFile)
└── ProtocolSI/   # ProtocolSI.dll communication library + help file (.chm)
```

## Tech stack

- C#, .NET Framework 4.6.1
- Windows Forms (client) and Console app (server)
- `System.Net.Sockets` (TCP) + `ProtocolSI`
- `System.Security.Cryptography` (RSA, AES, PBKDF2)

## Running

1. Open `ProjetoTS.sln` in Visual Studio and build the solution.
2. Start the **Servidor** project first. It listens on **port 10000** on all interfaces.
3. Start the **Cliente** project. It connects to `127.0.0.1:10000`.

To run both at once, right-click the solution → **Configure Startup Projects…** → **Multiple startup projects**, and set *Servidor* and then *Cliente* to **Start**.
