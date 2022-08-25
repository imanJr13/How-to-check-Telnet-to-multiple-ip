# How-to-check-Telnet-to-multiple-ip
How to check Telnet to multiple ip

below script check multiple ip in powershell

```
$IPAddrs = '1.1.1.1','1.1.1.2',
           '1.1.1.1','1.1.1.2'     # or put it in a file
$Ports = 1111,1112,1113,1114       # this too - or in a CSV
Foreach ($IpAddr in $IPaddrs){
  Foreach ($Port in $Ports
    if (Test-NetConnection -Computername $IpAddr -Port $Port) {
      Write-Debug "*** IP [$IpAddr]    Port [$Port]   is OK" 
    } Else {
      Write Debug "*** IP [$IpAddr]    Port [$Port] UNREACHABLE"
      $Results += "IP [$IpAddr]    Port [$Port]   UNREACHABLE`n"
    }
  }  # End foreach ports
} # End foreach ipaddrs
If (! ($Results) {
   ...  send email $results -  left as an exercise for the OP
}
```
