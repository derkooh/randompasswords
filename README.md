# randompasswords
Bash commands for random passwords

## Easyiest
* `date | md5sum`
* `date +%s | sha256sum | base64 | head -c 32 ; echo`
* `openssl rand -base64 32`

## From Entropy Pool
* `< /dev/random tr -dc _A-Z-a-z-0-9 | head -c${1:-32};echo;`
* `tr -cd '[:alnum:]' < /dev/random | fold -w30 | head -n1`
* `strings /dev/random | grep -o '[[:alnum:]]' | head -n 30 | tr -d '\n'; echo`
* `< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c6`
* `dd if=/dev/urandom bs=1 count=32 2>/dev/null | base64 -w 0 | rev | cut -b 2- | rev`

## Left Handed
* `</dev/urandom tr -dc '12345!@#$%qwertQWERTasdfgASDFGzxcvbZXCVB' | head -c8; echo ""`

## Functions
### Single Passwords
* normpw(){ < /dev/random tr -dc _A-Z-a-z-0-9 | head -c${1:-16};echo;}
* strongpw(){dd if=/dev/random bs=1 count=32 2>/dev/null | base64 -w 0 | rev | cut -b 2- | rev}

### Create Entropy txt Files

mkentropy(){
for i in `seq 0 9`; do
  for j in `seq 0 9`; do
    for k in `seq 1 32`; do
      strongpw >> entropy0$i$j.txt
    done
  done
done}
