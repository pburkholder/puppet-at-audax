
!SLIDE title

# Puppet #

## Third Generation Configuration Management

.notes To better illustrate what Puppet is and is not, a quick look at the
evoluion of C.M.



!SLIDE incremental 

# CM Generations #

1. DIY, Provisioning, RDist, SSH-in-a-For-Loop
1. Enterprise SiaFL: OpsWare, Bladelogic, Tivoli
1. Infrastructure-as-Code

.notes I've heard Puppet described as 3rd-gen, but w/o any clear delineation
of what the first 2 were. Instead of informing myself, I'm making up my own
taxonomy here.





!SLIDE incremental

# Infrastructure As Code #

* Resource Abstraction
* Declarative Language
* Convergence/Idempotency

.notes Marc Burgess, Oslo.  CfEngine 2 had a lot of the features of a 3rd gen
system but lacked a language rich enough to express all of the relationships
in a system.  E.g., at NIH we used a Perl templating system to write the
manifests that were the used by CfEngine 2 -- a CM system for our CM system.




!SLIDE

# Resource Abstraction #
## Not This ##

    @@@ sh
    apt-get install apache2
    rpm -Uvh httpd

## But This ##

    @@@ 
    package { $apache_package
      ensure  => 'present',
    }
    # (Same for Window(TM) too)



!SLIDE incremental

# Declarative Language #

* The apache2 package should be installed
* The apache.conf file should contain...
* The apache service should be running

.notes This is _not_ apt-get install, scp apache.conf, service apache start,
all of which would be 'imperative'. 

!SLIDE transition=fade

# Declarative Language

    @@@
    package{ 'apache':
      ensure  => 'latest',
    }
    service{ 'apache':
      ensure    => 'running',
      require   => Package['apache']
      subscribe => File['/etc/apache.conf']
    }

.notes The use of 'require' and 'subscribe' is part of what leads us to the
next point:

!SLIDE incremental

# Idempotency #
## Same result on every run ##
# Convergence #
## Structure resource dependencies so one run _converges_ to correct state ##

.note Puppet _catalogs_ are _idempotent_: they can be run any number of times and
will always converge to the same state.  And they will take no action if the
system is in the desired state

!SLIDE incremental

# Core Puppet Features #

## Written in Ruby ##
## External DSL ##
## Client/Server Model (master/agent) ##
## Convergence via Acyclic Dependency Graph ##
## Facts ##

.notes The characteristics of Resource Abstraction, Declarative Language and
Idempotency are common to CfEngine 3, Chef, Puppet and other 3rd Gen systems.
Puppet's feature include:...  Also, Puppet works great in standalone mode.
That said, let's hold off further discussion and see Puppet in action

