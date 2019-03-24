
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
  nmap -p- -oA [filename] [box_ip_address]
  ```

  # Gobuster (Directory scanning tool)
  
  Scan directories on port using list in file directory-list-2.3-medium.txt and output it to file gobuster.log
  
  ```bash
  gobuster -u http://[box_ip_address]:[port] -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster.log
  ```
  
  Scan multiple directories using a for loop
  ```bash
  for i in admin test dev backup loop; do
  gobuster -u http://[box_ip_address]:[port]/$i -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster-$i.log
  done
  ```

  # XXD (make a hexdump or do the reverse.)
  
  Reverse hex in a file
  
  ```bash
  cat [hexfile.txt] | xxd -r -p > [decodedfile.txt]
  ```
  
  # zip2john (Crack password protected zip files.)
  
  Get hash from zip file and send to an output file for cracking
  
  ```bash
  zip2john [zipfile.zip] > [outputfile.zip.hash]
  ```
  Crack zip file hash using wordlist rockyou.txt
  
  ```bash
  john --wordlist=[/usr/share/wordlists/rockyou.txt] [outputfile.zip.hash]
  ```
  
