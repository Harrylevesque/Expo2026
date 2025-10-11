# Expo2026

current code is at :
# https://github.com/Harrylevesque/SuperSL2


## welcome to my science fair project diarey

* please note that the readme will be updated evrey few days as i make major advances in the code.
* also note that not the entire document will be filled out automagically and will advace over the course of the science fair project

sept 1 2025

this year, after a great sucess for my first year at a science fair, i will be making sonething very interesting
i am planning to make a log in systemment for security and ease of use
the concept is that there is no passwords

sept 2 2025
i have a list of things i want to put in my project, and listed all of my major steps, i will enter the tasks to be done under it with the date

sept 3 2025
i found my guide teacher for the science fair, she is also doing a local science fair with her classes of sec 1, i will tag along for the science fair when we go to lapoc in the end of febuary. 
I remember last year how i needed to scramble through all the websites i used for wrighting my report. I DONT want that to happen again

sept 7 2025
started making my flow charts and completed the first : the regeneration flow. 

sept 10 2025
today i tried to change the way that K *(key to use to encrypt D with a pq algo)* and D*(the device bound key wich will be used to encrypt the actuall important stuff and sign chalenger)* are generated. i tried multiple pq algos like "Dilithium" and "Kyber" wich was not ideal for the attempt to use web assembly. 

I have made the executive desision that i will use a wrapper for the mobile app, i will make the bare minimum swift and koltyn and it will just launch one of my gomobile binaries wich will start a web server with my interface in html css and will have its own go server to do the local processing and send back to the backends server

also i will be condensing the 40+files of my entire project into only a few:



<pre>
slqrpdf/
├── cmd/
│   └── server/
│       └── main.go              # Entry point, starts backend server
│
├── internal/
│   ├── api.go                   # HTTP/gRPC handlers, QR endpoints
│   ├── crypto.go                # PQC wrappers (Kyber, Dilithium, etc.)
│   ├── core.go                  # protocol flow, session mgmt
│   ├── storage.go               # JSON/.json.enc storage
│   ├── config.go                # load/save encrypted configs
│   └── utils.go                 # logging, hashing, misc helpers
│
├── internal/mobile/             # all gomobile-related code
│   ├── export.go                # gomobile exported functions
│   ├── parse.go                 # parsing data from the scaned qr codes
│   ├── read.go                  # reading qr codes shown
│   ├── static.go                # the aforementioned web setver / main app gui
│   └── terminal.go              # interaction with device terminal/console
│
├── storage/
│   ├── users/                   # per-user encrypted JSON files
│   │   └── <user-id>.json.enc
│   ├── images/                  # uploaded/scanned images
│   └── └── <hash>.jpg
│
│
├── go.mod
└── go.sum
</pre>

the code repo will update within a few days

sept 11
restructured the code base and created over 250 tasks for the entire project code. this exclude actuall science fair prep like reports, keyosks and paperwork.
also created multiple different binarys for the users, the 3rd pary services that will use SLQRPDF. 

sept 12
today i tried to calculate the time for the project just for fun and i was worried by my calcs...
coding, testing and debugging : ~300h
wrighting report, paperwork, keyosk and all of that : 20h

great. 

sept 13
today i added all routes but did not create the functions it calles, also did not add the appropreate request types. 
* so excited for the project to pop off *
i know it is soon so i should really get going

sept 14
today i started making the account creation final's version, using real post quantum algos and device bound secrets

sept 15
got stuck on a dumb bug connecting my js to my golang user backend, it does not seem to actually send over the info needed and just stops working

sept 16
continued on sept 14th work:
<pre>

  sept 14
  today i started making the account creation final's version, using real post quantum algos and device bound secrets
  
</pre>

sept 18
continued yesterday's work

sept 19
struggled with evcrypting local secret with a PQC safe algorithm 

sept 20
continued trying to get circl/kyber1024 to work.
as i am writing this, i just got an idea. the problem is that for security reasons i keep thr public key on all devices that can use that account and the private secret is different for all devices. so if i just make the server side generate a key pair and ditch the provate key and each device creates a pair and ditches the public key then we have a kay pair. will attempt tomorrow. 

sept 21
continuing on yesterday's idea. it seems that this idea might work

sept 22
continue on yesterday's stuff

sept 23
attempted to clean up code and dealed with spontaneous failing

sept 27
today i decided to switch to python. i was overwhelmed by the golang version and it could make for a great year 2 version, anyway, i think that it feels better to use python because it actually makes sense and i need to look at docs a lot less. the repo is at

https://github.com/Harrylevesque/SuperSL2

sept 28
worked on the usercreation and recovery bu using a passphrase / list of words and a checksum

sept 29
today i worked on service creation and linking a user to a service
i am finding this a lot better, i feel more in controll of what i am doing and less at the mercy of my reaserch
i also realises that the repo i listed 2 days ago was private, it is now public, please look at it and give your feedback

sept 30
today i applied for a mentorship

oct 1
continued on sept 29's work

oct2
crested a account with oracle cloud and trued to setup a vps for this project. i am basicly waiting for. spot to open with 4ocpus and 24 gb ram

oct 3
attempted to  continue user and service creation

oct 4
continued to setup server hosting. sucseeded at getting a vps but installed an image for a x86 computer instead of aarch64

oct 5 - 6
planned flow for main elements

oct 7
worked on creating endpoints for the flow crested yesterday. 

oct 8
did research on best practices for security and user storage

oct 10
continued linking service into user
----------------------------
### the plan
create a system for loging in using a simple qr code scan
i will need to: 
* create a secure envierment on my vps
* create a dynamic session storer ( not a db storing cookies)
* create a generation software for making the wr codes the end user will use to log in
* find a way to keep it rotating all of the time with different data
* create a mobile inteeface for scanning the special qr code
* make the phone do some authing and cracking based on info about the device and what it scanned on the qr code
* create a heartbeat system for enshuring no device swapping man in the middle ect
* create the responce mechsnism
* find a way to stay logged in and continussly ensure no changes in the device, none of the stuff could be live session hacked
a bunch more things





# Todo list 
*(please enter date then in a tabbed form enter tasks for each feature)*

## Features of the Secure QR + Passkey System
## Security & Identity
* Biometric authentication via device-native passkeys (Face ID, Touch ID, Android Biometrics).
* Each QR code tied to a unique identity record.
* Optional integration with certificates or encrypted creator signatures.
* On-device secure enclave usage for keys (no raw passwords).

## Mobile App

* Scan special QR codes (optimized for 64×64 / high-density encoding).
* Validate authenticity of scanned codes against backend.
* Secure login via passkeys (no password entry).
* Offline-first mode: store scans until connectivity is available.
* Simple UI: “Scan”, “History”, “Profile”.

## Backend System
* API server for verifying QR codes and user authentication.
* Written in Python (FastAPI/Django) or Go (Gin/Fiber).
* Stores user accounts, event logs, and code validity in a secure database.
* Uses JWT or session tokens for app <-> server communication.
* Built-in rate limiting and API key protection.
* Logging & audit trail of all access attempts.

## Database & Storage
* User identity database (UUIDs, biometrics linked via device, not stored directly).
* QR code metadata (who issued it, when, validity).
* Encrypted at rest (AES-256) and in transit (TLS).
* Optional certificate/authority layer for trusted code issuance.

## QR Code Layer
* Compact 64×64 encoding for efficient scanning.
* Encodes database ID + page ID + creator certificate ID.
* Error correction for real-world scanning (smudges, partial scans).
* Can optionally embed timestamps or expiration logic.

## Security Features
* Zero password model: relies only on passkeys + secure device biometrics.
* Codes signed digitally to prevent forgery.
* Tamper-proof data storage (chip-level secure enclave on device).
* Audit trail for every scanned or generated QR code.

## Infrastructure & Deployment
* Lightweight VPS deployment (2 cores, 2 GB RAM, 80 GB storage).
* Dockerized backend for reproducibility.
* Reverse proxy (NGINX/Caddy) with HTTPS (Let’s Encrypt).
* Scalable later to Kubernetes / cloud if needed.

## Science Fair Demonstration
* Prototype backend (Python or Go) running live on VPS.
* Mobile demo app that scans special QR codes.
* Simulation of identity checks (no real face data needed).
* Visual dashboard: show QR validity checks, logs, and passkey login flow.
* Optional “attack mode” demo (fake QR code gets rejected).


### idea parapgraph 
*(please enter date and idea)*


### completed feature list


### upcoming feature list


### sources 
*(please enter url page name and date of visiting)*


### code explication 
*(please enter file and explication and important sectors)*


### file structure


### ideas for presentation


### how to use


### system setup / backend "how to use"


### ideas for science fair report

