
## Content

- [About](#about)
- [Examples](#example)
- [Paramaters](#paramaters)

## About
Lean RedHat NTP client module, with the most common settings.

## Examples

# Use all the default settings.
```puppet
   include '::ntp'
```

# **Set prefered servers.
```puppet
  class { '::ntp':
    servers => ['0.pool.ntp.org', '1.pool.ntp.org'],
  }
```

3. **Set prefred servers with the iburst option.**
```puppet
  class { '::ntp':
    servers => ['0.pool.ntp.org iburst', '1.pool.ntp.org iburst'],
  }
```

4. **Use a custom template for ntp.conf with the specified servers and the iburst option.**
```puppet
  class { '::ntp':
    servers => ['0.pool.ntp.org iburst', '1.pool.ntp.org iburst'],
    conffile => "${module_name}/ntp.conf-${::operatingsystemmajrelease}.erb", 
  }
```

5. **Use a static file for ntp.conf**
```puppet
  class { '::ntp':
    conffile => ["puppet:///modules/${module_name}/ntp.conf-${::operatingsystemmajrelease}"], 
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
- *type:* array
- *default:* ['/etc/ntp/crypto/pw']

`keys`
- *type:* string
- *default:* '/etc/ntp/keys'
- *description:*  

`disable`
- *type:* array
- *default:* ['monitor']

`conffile`
- *type:* string|array
- *default:* "${module_name}/ntp.conf.erb"

`ensure`
- *type:* string
- *values:* 'enabled'|'disabled'
- *default:* 'enabled'

`onboot`
- *type:* string
- *values:* 'running'|'stopped'
- *default:* 'running'

