<h1># CTF_Cookbook</h1>
A collection of tool commands and scripts for capture the flag machines

  <h2>- Nmap</h2>
  
    <h4>Discover common ports and their versions. Output all formats to an nmap folder</h4>
      
      <code>nmap -sC -sV -oA nmap/[boxname] [box_ip_address]</code>
