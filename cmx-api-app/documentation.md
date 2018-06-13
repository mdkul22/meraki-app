# MERAKI-CMX-CUSTOM-app

### EXPLANATION
this code has been modified from the https://github.com/meraki/cmx-api-app
repository. The major code has been done on ruby and javascript. Most of the modifications
are based on the classes and objects provided by the example itself.

This app allows us to  view BLE clients on the google API and also the associated Clients

UDP ports need to be opened for meraki firstly, please contact the necessary people to open
the required ports on the required IP addresses. Also assign static addresses to the meraki
routers.

Once opened access points show green i.e. fully setup. All of the APs act as APs and not as repeaters.
Will experiment with the meraki APIs.

### Location Scanning API

This API provides all the location based details to the application servers
You could make your own application server by following the protocol followed
by the link https://documentation.meraki.com/MR/Monitoring_and_Reporting/Scanning_API

But meraki provides their own example (link above). This basically provides a built in
database and server which you NEED to put in the AWS server as you need a publicly accessible
domain which the meraki can communicate with.
Create an EC2 Ubuntu 16.04 instance in your AWS server and create it. Along with this, you need to
modify the security details for this instance to allow REST server communication. Go in security
groups in EC2 dashboard and create your own custom group.

## Security Table
Type               Protocol    Port Range    Source
HTTP                 TCP           80        0.0.0.0/0
HTTP                 TCP           80          ::/0
SSH                  TCP           22        0.0.0.0/0
SSH                  TCP           22          ::/0
Custom TCP Rule      TCP        8000-9000    0.0.0.0/0
Custom TCP Rule      TCP        8000-9000      ::/0
Assign the security group to the instance and begin installing ruby

### IMPORTANT: follow these steps to get a properly working server
1.	Get aws ec2 instance with Ubuntu 16.04
2.	$sudo apt-get update
3.  $sudo apt-get install build-essentials
4.	$sudo apt-get install ruby-full
5.	$git clone https://github.com/meraki/cmx-api-app
6.	$cd cm*
7.	$sudo gem install sinatra
8.  $sudo gem install data_mapper
9.  $sudo apt-get install sqlite3 libsqlite3-dev
10. $sudo gem install sqlite3-ruby
11. $sudo gem install dm-sqlite-adapter  
12. Follow README thereafter.

### Result

The code puts the BLE client data and the associated wifi clients in a single data base and
displays the position on the google map API.
