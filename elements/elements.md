
!SLIDE

# Configuration Management is NOT: #

* Provisioning
* Scripting
** Especially not ssh-in-a-for-loop

# Elements of Configuration Management ARE: #

!SLIDE

# Abstraction #

## Not This ##

    @@@ bash
    apt-get install puppet
    rpm -Uvh puppet

## But This ##

    @@@ puppet
    package {'puppet': 
      ensure  => 'present',
    }

!SLIDE

# Declarative Language

    @@@ puppet
    class puppet::install {
      package{ 'puppet':
        ensure  => 'latest',
      }
      service{ 'puppet':
        ensure    => 'running',
        require   => Package['puppet']
        subscribe => File['/etc/puppet.conf']
      }
    }

!SLIDE

# Convergence #

Puppet _catalogs_ are _idempotent_: they can be run any number of times and
will always converge to the same state
