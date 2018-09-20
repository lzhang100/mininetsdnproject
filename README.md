# mininetsdnproject

UCSC CMPE150 Introduction to Networking Final Project 
Goal: Getting a better understanding for software defined networks (SDNs). Mininet is a virtualization environment that allows programmers to create SDNs and interact with the network thorugh the CLI. As for every SDN, we need an application program in the application layer to set up the network topology that a programmer wants to deploy and this was given in the final_topo.py. Next the programmers needs a controller that will interface with the application layer. In this project, we used the Pox contoller and wrote rules on how the switches should forward or accept the frames in router4.py. In this case, there are two rules. The first rule are hosts that have the same address space should be able to ping each other. The second rule is that hosts that are on the same side of the switch are able to ping to each other. Finally, we used the Openflow protocol to interface with the data plane with the virtual switches does work in accepting or forwarding frames with the rules given by the controller.

To run the project:
1. Download the Mininet VM onto VirtualBox
2. Run the VM and log in with username: mininet password: mininet.
3. Open two Putty terminals and SSH both into the mininet VM. 
4. Use a File transfer program (WINSCP for windows) to add the final_topo.py files in the mininet@mininet-vm directory and router4.py in the mininet@mininet-vm/po/pox/forwarding directory
5. The first putty terminal should run the controller with the command with mininet@mininet-vm:~$ sudo ~/pox/pox.py forwarding.router4.py
6. The second putty terminal should run the network topology file. mininet@mininet-vm:~$ python final_topo.py
7. After running the network toplogy file, use the CLI to have all host ping 1 packet to every other host with pingall 1
8. You will see about 50 - 60% pings with success. This is because of the controllers rules of dropping packets if two host are not in the same address space.
