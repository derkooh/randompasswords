# randompasswords
Bash commands for random passwords


  date +%s | sha256sum | base64 | head -c 32 ; echo
  < /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c${1:-32};echo;
  openssl rand -base64 32
