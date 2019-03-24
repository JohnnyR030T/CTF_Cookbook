<h1># CTF_Cookbook</h1>
A collection of tool commands and scripts for capture the flag machines

  <h2>- Nmap</h2>
      
  Discover common ports and their versions. Output all formats to an nmap folder
      
  ```bash
  nmap -sC -sV -oA nmap/[filename] [box_ip_address]
  ```
  An aggressive detection scan 
      
  ```bash
  nmap -T4 -A -oA nmap/[filename] [box_ip_address]
  ```
