# HTTP Methods Enumerator

<p align="center">
  <pre>
██╗  ██╗████████╗████████╗██████╗      ███╗   ███╗███████╗████████╗██╗  ██╗
██║  ██║╚══██╔══╝╚══██╔══╝██╔══██╗     ████╗ ████║██╔════╝╚══██╔══╝██║  ██║
███████║   ██║      ██║   ██████╔╝     ██╔████╔██║█████╗     ██║   ███████║
██╔══██║   ██║      ██║   ██╔═══╝      ██║╚██╔╝██║██╔══╝     ██║   ██╔══██║
██║  ██║   ██║      ██║   ██║          ██║ ╚═╝ ██║███████╗   ██║   ██║  ██║
╚═╝  ╚═╝   ╚═╝      ╚═╝   ╚═╝          ╚═╝     ╚═╝╚══════╝   ╚═╝   ╚═╝  ╚═╝

         HTTP Method Enumeration & Verb Discovery
  </pre>
</p>

`http-methods` is a lightweight and fast Bash script designed to enumerate HTTP methods and hidden verbs on a specific URL using `curl`. It is a handy utility for security assessments, penetration testing, and bug bounty hunting.

---

## 🚀 Features

* **Comprehensive Testing:** Tests standard HTTP methods (GET, POST, etc.), WebDAV methods (PROPFIND, MKCOL, etc.), and custom/fictitious verbs (`HACKTHEPLANET`, `FOOBAR`) to check for misconfigurations or custom verb handling.
* **Redirect Detection:** Automatically detects if a URL redirects via the `Location` header and seamlessly updates the target.
* **Clean Output:** Displays results neatly in a structured table format with the method name and corresponding HTTP status code.
* **No Heavy Dependencies:** Requires only standard Unix tools like `bash` and `curl`.

---

## ⚙️ Prerequisites

Ensure that the following tools are installed on your system (they come pre-installed on most Linux and macOS distributions):
* `bash` (version 4+)
* `curl`
* `awk`, `tr`

---

## 📥 Installation

Clone the repository and make the script executable:

```bash
git clone https://github.com/4a6f62/http-methods.git
cd http-methods
chmod +x http-methods.sh

```
---

## 📖 Usage

Run the script using the `-u` flag followed by the target URL:

```bash
./http-methods.sh -u https://example.com

```

### Example Output

```text
██╗  ██╗████████╗████████╗██████╗      ███╗   ███╗███████╗████████╗██╗  ██╗
...

[+] Target : [https://example.com](https://example.com)
[+] Started: Tue Oct 20 12:00:00 CEST 

[+] Redirect detected
[+] Original : [https://example.com](https://example.com)
[+] New URL  : [https://www.example.com/](https://www.example.com/)


METHOD          STATUS    
------          ------    
GET             200       
POST            405       
PUT             403       
PATCH           405       
DELETE          405       
HEAD            200       
OPTIONS         200       
TRACE           405       
CONNECT         405       
PROPFIND        405       
PROPPATCH       405       
MKCOL           405       
COPY            405       
MOVE            405       
LOCK            405       
UNLOCK          405       
HACKTHEPLANET   501       
FOOBAR          501       
TESTMETHOD      501       

```

---

## 🛠️ Customizing Methods

Want to test additional HTTP methods? You can easily modify the `METHODS` array directly inside the script:

```bash
METHODS=(
    GET POST PUT PATCH DELETE HEAD OPTIONS TRACE CONNECT
    PROPFIND PROPPATCH MKCOL COPY MOVE LOCK UNLOCK
    HACKTHEPLANET FOOBAR TESTMETHOD YOUR_CUSTOM_METHOD
)

```

---

## ⚠️ Disclaimer

This tool is intended for educational purposes and authorized security assessments only. Make sure you have explicit permission before running pentesting scripts against any target. The author assumes no liability for misuse or damage caused by this tool.

---

## 📝 License

This project is licensed under the [MIT License](https://www.google.com/search?q=LICENSE).
