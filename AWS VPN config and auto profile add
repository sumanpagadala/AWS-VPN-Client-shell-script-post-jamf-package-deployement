#!/bin/zsh

#Open the application
open /Applications/AWS\ VPN\ Client/AWS\ VPN\ Client.app

#Sleep for 10 sec to create default directories of VPN
sleep 10

#Close the application
osascript -e 'quit app "AWS VPN Client.app"'

#Sleep for 10 sec
sleep 10

#Set VPN Config File Name Here
vpnConfigFileName="$4"    

###### To update the profile the info between FOE needs to be updated ######

#Find the logged in user
loggedInUser=$(stat -f %Su /dev/console)

#Set the file path to the ConnectionProfiles file with the loggedIn user
vpnConfigFolder="/Users/$loggedInUser/.config/AWSVPNClient/OpenVpnConfigs/"


fullPathVpn="${vpnConfigFolder}${vpnConfigFileName}"
echo "$fullPathVpn"

#make the config file ready
cat << FOE > "$fullPathVpn"
PASTE VPN CONFIG FILE HERE
FOE

#Create VPN connection profiles
ConnectionProfilesPath="/Users/$loggedInUser/.config/AWSVPNClient/ConnectionProfiles"
cat << FOE > "$ConnectionProfilesPath"
PASTE CONNECTION PROFILE HERE IN JSON FORMAT
FOE

#make the owner of ConnectionProfiles file
chown "$loggedInUser" "$ConnectionProfilesPath"

#Open the application
open /Applications/AWS\ VPN\ Client/AWS\ VPN\ Client.app 
sleep 20
