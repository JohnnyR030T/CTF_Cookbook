
# CTF_Cookbook
A collection of tool commands and scripts for capture the flag machines

  # Nmap
      
  Discover common ports and their versions. Output all formats to an nmap folder
      
  ```nmap
  nmap -sC -sV -oA nmap/[filename] [box_ip_address]
  ```
  An aggressive detection scan 
      
  ```nmap
  nmap -T4 -A -oA nmap/[filename] [box_ip_address]
  ```

  # Gobuster
  
  Scan directories on port 9999 using list in file directory-list-2.3-medium.txt and output it to file gobuster.log
  
  ```gobuster
  gobuster -u http://10.10.10.111:9999 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster.log
  ```
  
  scan multiple directories using a for loop
  ```bash
  for i in admin test dev backup loop; do
  gobuster -u http://10.10.10.111:9999/$i -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster-$i.log
  done
  ```
