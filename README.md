
# CTF_Cookbook
A collection of tool commands and scripts for capture the flag machines

  # Nmap
      
  Discover common ports and their versions. Output all formats to an nmap folder
      
  ```bash
  nmap -sC -sV -oA nmap/[filename] [box_ip_address]
  ```
  An aggressive detection scan 
      
  ```bash
  nmap -T4 -A -oA nmap/[filename] [box_ip_address]
  ```

  # Gobuster
  
  Scan directories on port 9999 using list in file directory-list-2.3-medium.txt and output it to file gobuster.log
  
  ```bash
  gobuster -u http://10.10.10.111:9999 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster.log
  ```
