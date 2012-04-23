!SLIDE title

# Puppet #

## In Action ##

!SLIDE transition=fade

# Bootstrapping: Tags #

## RightScale Tags to Puppet Facts ##

![RightScale Tags](rs_tags.png)

![etc_facts_d](etc_facts_d.png)

.notes Usually a RightScale instance ends with a run of puppet agent to
complete configuring the host, but in this case we will watch it run.

!SLIDE bullets incremental transition=fade

# Bootstrapping: Agent Run #

## puppet agent --test ##

### Exchange Certs with Puppet Master
### Send facts to server
### Receive 'catalog' from server
### Execute the catalog...
### ...Install users, monitoring, MOTD




!SLIDE bullets incremental transition=fade

# CV Deployments: initial run #

## Look at ![site.pp](cvrecommend_site.png)
## Add 'role:cvcarerecommend' to /etc/facts.c/metadata.txt
## Run 'puppet agent --test'
## Watch the ScreenCast:

http://screencast.com/t/iq17poCZ9



!SLIDE bullets incremental transition=fade

# CV Deployments: new release #

## Bump the version number
## Run puppet
## Verify



