<!SLIDE small>
# Task C: Packet-In Dumper #####################################################

## Handling Packet-In Messages


<!SLIDE small>
## Exercise: Displaying Packet-In Message Contents #############################

	$ trema run packetin-dumper.rb -c packetin-dumper.conf

* Start a Packet-In dumper controller process
* This also starts a virtual network (= one virtual switch + two virtual hosts host1, host2)


<!SLIDE center>
![overview](packetin_dumper1.png)


<!SLIDE small>
## Exercise: Displaying Packet-In Message Contents #############################

	$ trema send_packets --source host1 --dest host2

* Open another terminal, then send a test packet from host1 to host2
* This would cause the controller to dump the packet-in message


<!SLIDE center>
![overview](packetin_dumper2.png)


<!SLIDE>
## Q: How did you do that (sending test packets)? ##############################


<!SLIDE small>
# Virtual Host And Virtual Link ################################################

## Connect virtual hosts (host1, host2) to the virtual switch 0xabc

	@@@ ruby
	# Add one virtual switch
	vswitch { dpid "0xabc" }
	# Add two virtual hosts
	vhost "host1"
	vhost "host2"
	# Then connect them to the switch 0xabc
	link "0xabc", "host1"
	link "0xabc", "host2"

## Send test packets between virtual hosts as defined above

	$ trema send_packets --source host1 --dest host2


<!SLIDE small>
# Network Configuration File ###################################################

* Simple enough to configure a test environment
* Specify and construct any arbitrary network by just writing configuration statements in DSL
* And also send test packet by one simple command


<!SLIDE small>
# Example: A More Complicated Network ############################################

	@@@ ruby
	vswitch { dpid "0x1" }
	vswitch { dpid "0x2" }
	...
	vhost "host1"
	vhost "host2"
	vhost "host3"
	vhost "host4"
	  ...    
	link "0x1", "0x2
	  ...    
	link "0x1", "host1"
	link "0x1", "host2"
	link "0x2", "host3"
	link "0x2", "host4"
	  ...    


<!SLIDE>
# Handling Packet-In ###########################################################


<!SLIDE smaller>
# `PacketinDumper#packet_in` ###################################################

	@@@ ruby
	# packetin-dumper.rb    
	class PacketinDumper < Controller
	  def packet_in dpid, message
	    info "received a packet_in"
	    info "dpid: #{ datapath_id.to_hex }"
	    info "in_port: #{ message.in_port }"
	  end
	end

* `packet_in`: arguments are dpid and a Packet-In message object (`message`)
* `message.attribute` for inspecting the attributes of the Packet-In message


<!SLIDE smaller>
# Exercise: Inspecting Other Packet-In Attributes ##############################

	@@@ ruby
	# packetin-dumper.rb    
	class PacketinDumper < Controller
	  def packet_in dpid, message
	    info "received a packet_in"
	    info "dpid: #{ datapath_id.to_hex }"
	    info "in_port: #{ message.in_port }"
	    info "total_len: #{ message.total_len }"        
	      ...        
	  end
	end

* Display other Packet-In attributes (total_len, macsa, macda ...)
* Hint: Use `trema ruby` for the full API reference of PacketIn class
