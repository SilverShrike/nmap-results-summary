Here is the code to read-in nmap scan results and then parse for only hostname, ports and protocols:

#!/bin/bash

# Check if a file path is provided
if [ -z "$1" ]; then
    echo "Usage: $0 <nmap_output_file>"
    exit 1
fi

nmap_output="$1"

# Extract hostnames, active ports, and services using awk
awk '/Nmap scan report/{print "\nHostname:", $5} /open/{print "Port:", $1, "Service:", $3}' "$nmap_output"
