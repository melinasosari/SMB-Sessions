# Windows Firewall Rule - Allow File and Printer Sharing only to one windows machine
This Project creates a custom windows firewall rule that allows *outgoing file and printer sharing (smb connections)* only to one machine(e.g. DC) from a source windows machine(e.g. win11) . All other systems are blocked from receiving SMB Connections from this machine.


Steps to Create this Rule:                                                
1.Open Windows Firewall: in run menu type *wf.msc*        
2.Create a New Outbound Rule:  

      i.Select *Outbound Rule* then click *New Rule*   
      
      ii.Choose *Custom* then click next       

      
      iii.Choose *All Programs* then click next            
      iv.for *Protocol Type* choose *TCP* and for *Remote Port* select *Specific Ports* then type *445*   
      
      v.under *remote ip address* select *these ip adress*: -add the ip adress of the destination machine (e.g. DC)    
      
      vi.Choose *Allow the Connections*           
      
      vii.type a name for example *Allow SMB Sessions to DC*
      
      viii.Finish the rule                  


Result: in my example --> The Windows 11 Machine "can successfully access shared folders and printers hosted on the dc" and it "cannot access file or print shares on any other machine" on the network
  
*Note*: Make sure your windows firewall is set to block outbound connections by default(in windows defender firewall properties). otherwise this rule may not restrict access as expected
