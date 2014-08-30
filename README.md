## Examples

### Use all the default settings.
```puppet
   include '::ntp'
```

### Set prefered servers.
```puppet
  class { '::ntp':
    servers => ['0.pool.ntp.org', '1.pool.ntp.org'],
  }
```

### Set prefred servers with the iburst option.
```puppet
  class { '::ntp':
    servers => ['0.pool.ntp.org iburst', '1.pool.ntp.org iburst'],
  }
```

### Use a custom template with prefered servers and the iburst option.
```puppet
  class { '::ntp':
    servers => ['0.pool.ntp.org iburst', '1.pool.ntp.org iburst'],
    conffile => template("${module_name}/ntp.conf-${::operatingsystemmajrelease}.erb"), 
  }
```


## Paramaters

`server`
- *type:* array 
- *default:* ['0.rhel.pool.ntp.org', '1.rhel.pool.ntp.org', '2.rhel.pool.ntp.org']

`driftfile`
- *type:* string
- *default:* '/var/lib/ntp/drift'

`restrict`
- *type:* array
- *default:* ['default nomodify notrap nopeer noquery', '127.0.0.1', '::1']

`includefile`
- *type:* string
- *default:* '/etc/ntp/crypto/pw'

`keys`
- *type:* string
- *default:* '/etc/ntp/keys'
- *description:*  

`disable`
- *type:* array
- *default:* ['monitor']

