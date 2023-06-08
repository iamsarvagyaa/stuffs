# IPTABLES

Random notes on iptables.

#### Basics
- `iptables -L` - list all rules
- `iptables -S` - list all rules in a format that we can later use to restore the rules
- `iptables -S INPUT` - list all rules for INPUT chain in a format that we can later use to restore the rules
- `iptables -n -L -v` - list all rules w/ verbose output
- `iptables -L INPUT -n -v` - list all rules for INPUT chain w/ verbose output
- `iptables -n -L -v --line-numbers` - list all rules w/ verbose output and line numbers
- `iptables -L INPUT -n -v --line-numbers` - list all rules for INPUT chain w/ verbose output and line numbers
... and so on, we can tweak many commands like this to list rules for specific chains.

#### Flushing & Deleting
- `iptables -F` - flush all rules
- `iptables -F INPUT` - flush all rules for INPUT chain
- `iptables -X` - delete all user-defined chains
- `iptables -X INPUT` - delete INPUT chain
- `iptables -t nat -F` - flush all rules for nat table
- `iptables -D INPUT 1` - delete rule number 1 from INPUT chain
- `iptables -D INPUT -m conntrack --ctstate INVALID -j DROP` - delete rule that matches the specified parameters

#### Firewalling Rules
- `iptables -P INPUT DROP` - set default policy for INPUT chain to DROP
- `iptables -P OUTPUT DROP` - set default policy for OUTPUT chain to DROP
- `iptables -P FORWARD DROP` - set default policy for FORWARD chain to DROP
- `iptables -A INPUT -i lo -j ACCEPT` - allow all traffic on loopback interface
- `iptables -A OUTPUT -o lo -j ACCEPT` - allow all traffic on loopback interface
- `iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT` - allow all established and related traffic
- `iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT` - allow all established and related traffic
- `iptables -A INPUT -p tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT` - allow incoming traffic on port 22 from anywhere
- `iptables -A OUTPUT -p tcp --sport 22 -m conntrack --ctstate ESTABLISHED -j ACCEPT` - allow outgoing traffic on port 22 from internal network
- `iptables -A INPUT -p tcp -s 1.1.1.1/32 --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT` - allow incoming traffic from specific IP on port 22
- `iptables -A OUTPUT -p tcp --sport 22 -m conntrack --ctstate ESTABLISHED -j ACCEPT` - allow outgoing traffic on port 22 from internal network
