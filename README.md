# whois-parser

## Installation
```
composer require DavidFricker/whois-parser
```

## Tests
Open in your browser
```
/vendor/DavidFricker/whois-parser/examples/simple-example.php
```

## Usage

```
require_once __DIR__ . '/../vendor/autoload.php';

use DavidFricker\DFWhois\DFWhois as DFWhois;

$domain_or_ip = 'sport24.lefogaro.fr'; // '212.95.72.8'

# Create Whois object
$DFWhois = new DFWhois($domain_or_ip);

$whois = [];

# Query whois database and return whois text as UTF-8
$whois['text'] = $DFWhois->get_whois_text();

$whois['is_ip'] = $DFWhois->is_ip();

# Is this tld available ?
$whois['is_available'] = $DFWhois->is_available();

# Extract whois informations
$whois['infos'] = $DFWhois->extract_infos();

# Extract all mails from whois
$whois['mails'] = $DFWhois->get_mails();
$whois['registrant_emails'] = $DFWhois->extract_whois_registrant_emails();
$whois['registrar_emails'] = $DFWhois->extract_whois_registrar_emails();

# Return whois as HTML (\n replaced by <br>)
//$whois['html'] = $DFWhois->whois_html();

# helper functions
$whois['registrable_domain'] = $DFWhois->get_registrable_domain();
$whois['domain'] = $DFWhois->get_domain();
$whois['hostname'] = $DFWhois->get_hostname();
$whois['full_host'] = $DFWhois->get_full_host();
$whois['tlds'] = $DFWhois->get_tld();
$whois['subdomain'] = $DFWhois->get_sub_domain();

# Print
echo $tld . ' : <br>';
echo '<pre>';print_r($whois);echo '</pre><br>';
```

### Whois servers list

Sources are:
```
[XML] The existing whois-server-list
[IANA] IANA
[PSL] Public Suffix List
[WHOIS_RB] Ruby Whois
[MD_WHOIS] Marco d'Itri's Whois list
[PHOIS] php-whois
[PHP_WHOIS] phpWhois
```

The latest list can be found at 

[whois-server-list.xml](http://whois-server-list.github.io/whois-server-list/2/whois-server-list.xml)
