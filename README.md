# HTTPTunnel-revshell
Script to easily setup an (upgradable) reverse shell over HTTPTunnel

## How it works
1. First we create an HTTPTunnel like so (where `Attacker` is our machine and `Target` is the machine we're trying to get access to)
```
Attacker:4444 <--> Attacker:4445 <--HTTPTunnel--> Target:4444
```
2. Then we start a listening netcat on `Attacker:4444`
3. Finally, we send a reverse shell from the target machine

## Usage
0. Configure the variables on `generate.sh` to your desired ports and attacker IP address
1. Generate `attacker.sh` and `target.sh`:
```bash
./generate.sh
```
2. Run `attacker.sh`
```bash
./attacker.sh
```
3. Transfer `target.sh` to the target/victim machine
4. Run `target.sh` on the target/victim machine
```bash
./target.sh
```

5. (Optional) [Upgrade your shell to an interactive shell](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/).

## Common Issues
- `nc: invalid option -- 'e'`: The netcat installed on the target probably doesn't have the `-e` functionality, try changing the `nc` line to [some other alternative](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#netcat-traditional) or [using `ncat` instead](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#ncat)
