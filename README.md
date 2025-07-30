# vmTest
Easy copy paste for my vm test?

# Fix sudo apt-get update
curl -fsSL https://archive.kali.org/archive-key.asc | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/kali-archive.gpg > /dev/null



# snort rule
alert tcp $HOME_NET 21 -> $EXTERNAL_NET any (
    msg:"FTP login failure";
    content:"530 ";
    nocase;
    flow:from_server,established;
    classtype:unsuccessful-user;
    sid:1000001;
    rev:1;
)


# snort conf

var HOME_NET any
var EXTERNAL_NET any
include /etc/snort/rules/local.rules

#launch snort

sudo snort -A console -q -c /etc/snort/snort.conf -i eth0


# new try

HOME_NET = 'any'
EXTERNAL_NET = 'any'
ips =
{
    rules =
    {
        include = 'local.rules'
    }
}

# new launch

snort -c /etc/snort/snort.lua -i eth0
