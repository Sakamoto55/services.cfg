# services.cfg
#nagios services.cfg file

;Quicksearch index of machined
; BLADES
; WEB NODES
; DB MACHINES
; DEV/QA
; NGMS MACHINE
; MISC MACHINES
; OFFICE SERVERS
; WEBSITE
; VIPS
; DENVER
;
;------------------------- CORP -----------------------
#define host{
#        use                     generic-host
#        host_name               jira
#        alias                   jira
#        check_command           PING
#        check_interval          1
#        retry_interval          1
#        address                 10.100.4.51
#        max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        notification_interval   120 
#        notification_period     24x7
#        hostgroups              corp
#}
;------------------------- FILER -----------------------
define host{
        use                     generic-host
        host_name               netapp02
        alias                   netapp02
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.204
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   60
        notification_period     24x7
        hostgroups              dbmachines
}

define host{
        use                     generic-host
        host_name               netapp01
        alias                   netapp01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.205
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   60
        notification_period     24x7
        hostgroups              dbmachines
}

define host{
        use                     generic-host
        host_name               netapp03
        alias                   netapp03
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.211
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   60
        notification_period     24x7
        hostgroups              dbmachines
}

define host{
        use                     generic-host
        host_name               netapp04
        alias                   netapp04
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.212
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   60
        notification_period     24x7
        hostgroups              dbmachines
}

define host{
        use                     generic-host
        host_name               nagios
        alias                   nagios
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.30
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               ns1-prod
        alias                   ns1-prod
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.103.1
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               ns2-prod
        alias                   ns2-prod
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.103.5
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}

;------------------------- BLADES -----------------------
define host{
	use			generic-host
	host_name		web01
	alias			web01
	check_command		PING
	check_interval		1
        retry_interval          1
        address                 192.168.100.11
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              webnodes
}	
define host{
        use                     generic-host
        host_name               web02
        alias                   web02
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.12
        max_check_attempts      5
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              webnodes
}

define host{
        use                     generic-host
        host_name               web03
        alias                   web03
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.221
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              webnodes
}
define host{
        use                     generic-host
        host_name               pmta02
        alias                   pmta02
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.190
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              rmta
}
define host{
        use                     generic-host
        host_name               mp01
        alias                   mp01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.84
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
#define host{
#        use                     generic-host
#        host_name               blade03-09
#        alias                   blade03-09
#        check_command           PING
#        check_interval          1
#        retry_interval          1
#        address                 192.168.100.19
#        max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        notification_interval   90
#        notification_period     24x7
#        hostgroups              webnodes
#}
define host{
        use                     generic-host
        host_name               bounce01
        alias                   bounce01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.20
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              rmta
}
define host{
        use                     generic-host
        host_name               vm0311
        alias                   vm0311
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.21
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              rmta
}
define host{
        use                     generic-host
        host_name               vm0312
        alias                   vm0312
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.22
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              rmta
}
define host{
        use                     generic-host
        host_name               vm0313
        alias                   vm0313
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.23
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               cron01 
        alias                   cron01 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.212
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               mp03 
        alias                   mp03 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.61 
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               mcglynn 
        alias                   mcglynn 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.192 
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               cron02 
        alias                   cron02 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.27 
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               export01 
        alias                   export01 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.97 
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               earthworm2 
        alias                   earthworm2 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.59 
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               earthworm4
        alias                   earthworm4 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.80
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               earthworm1
        alias                   earthworm1
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.81
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}

define host{
        use                     generic-host
        host_name               blade04-01
        alias                   blade04-01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.25
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              webnodes
}
define host{
        use                     generic-host
        host_name               vm0405
        alias                   vm0405
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.29
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              webnodes
}
define host{
        use                     generic-host
        host_name               pmta01
        alias                   pmta01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.24
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              rmta
}
define host{
        use                     generic-host
        host_name               mp02
        alias                   mp02
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.85
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               blade04-08
        alias                   blade04-08
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.32
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   30
        notification_period     24x7
        hostgroups              webnodes
}
define host{
        use                     generic-host
        host_name               monitor2
        alias                   monitor2
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.33
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        #notification_interval   90
        notification_period     24x7
        hostgroups              webnodes
}
#define host{
#        use                     generic-host
#        host_name               console
#        alias                   console
#        check_command           PING
#        check_interval          1
###        retry_interval          1
#        address                 192.168.100.100
        #max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        #notification_interval   90
##        notification_period     24x7
#        hostgroups              webnodes
#}
define host{
        use                     generic-host
        host_name               bounce02 
        alias                   bounce02
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.34
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              rmta
}
define host{
        use                     generic-host
        host_name               vm0411
        alias                   vm0411
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.35
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               vm0412
        alias                   vm0412
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.36
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               vm0413
        alias                   vm0413
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.37
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               vm0414
        alias                   vm0414
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.38
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}

define host{
        use                     generic-host
        host_name               jenkins
        alias                   jenkins
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.98
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}

define host{
        use                     generic-host
        host_name               jenkins-b
        alias                   jenkins-b
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.86
        max_check_attempts      3
        check_period            24x7
        contact_groups          ops
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}

define host{
        use                     generic-host
        host_name               ngms01
        alias                   ngms01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.101
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}

define host{
        use                     generic-host
        host_name               ngms02
        alias                   ngms02
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.102
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}

define host{
        use                     generic-host
        host_name               ngms03
        alias                   ngms03
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.103
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}

define host{
        use                     generic-host
        host_name               ngms04
        alias                   ngms04
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.104
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms05
        alias                   ngms05
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.105
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms06
        alias                   ngms06
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.106
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms07
        alias                   ngms07
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.107
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms08
        alias                   ngms08
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.108
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}

define host{
        use                     generic-host
        host_name               vm0309 
        alias                   vm0309 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.67
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms09 
        alias                   ngms09 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.109
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms10 
        alias                   ngms10 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.110
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms11
        alias                   ngms11
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.111
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms12
        alias                   ngms12
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.112
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms13
        alias                   ngms13
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.113
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}
define host{
        use                     generic-host
        host_name               ngms14
        alias                   ngms14
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.114
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              enigma
}

define host{
        use                     generic-host
        host_name               blade01-01
        alias                   blade01-01(webslave01)
        check_command           PING
        check_interval          5
        retry_interval          3
        address                 192.168.100.39
        max_check_attempts      5
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               blade01-02
        alias                   blade01-02(backup)
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.40
        max_check_attempts      3
        check_period            24x7
        contact_groups          mikeh
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               blade01-04
        alias                   blade01-04 (NGMS carecards slave)
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.42
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
#define host{
#        use                     generic-host
#        host_name               blade01-05
#        alias                   blade01-05
#        check_command           PING
#        check_interval          1
#        retry_interval          1
#        address                 192.168.100.43
#        max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        notification_interval   90
#        notification_period     24x7
#        hostgroups              dbmachines
#}

define host{
        use                     generic-host
        host_name               redis1
        alias                   redis1
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.72
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               redis2
        alias                   redis2
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.74
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               redis3
        alias                   redis3
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.87
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               redis4
        alias                   redis4
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.88
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               redis5
        alias                   redis5
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.89
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               redis6
        alias                   redis6
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.90
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               blade01-12
        alias			blade01-12
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.50
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               blade01-13
        alias                   blade01-13(beslave01)
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.51
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               svpdb01
        alias                   svpdb01(master01)
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.52
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               blade02-01
        alias                   blade02-01(webslave03)
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.53
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               blade02-04
        alias                   blade02-04
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.56
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               blade02-10
        alias                   blade02-10
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.63 
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               webslave04
        alias                   webslave04
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.60 
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               utildb
        alias                   utildb
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.13
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               utildb2
        alias                   utildb2
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.49
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               blade02-12
        alias                   blade02-12
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.64
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               blade05-01
        alias                   blade05-01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.69
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               blade02-13
        alias                   blade02-13(beslave02)
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.65
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}

define host{
        use                     generic-host
        host_name               svpdb02
        alias                   svpdb02(master-standby)
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.66
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               puppet01
        alias                   puppet01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.75
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               crondb01
        alias                   crondb01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.119
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               crondb02
        alias                   crondb02
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.37
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               web04
        alias                   web04
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.222
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webnodes
}
define host{
        use                     generic-host
        host_name               ws-prod1
        alias                   ws-prod1
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.91
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod2
        alias                   ws-prod2
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.92
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod3
        alias                   ws-prod3
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.93
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod4
        alias                   ws-prod4
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.94
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod5
        alias                   ws-prod5
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.47
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod6
        alias                   ws-prod6
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.48
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod7
        alias                   ws-prod7
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.223
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod8
        alias                   ws-prod8
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.224
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod9
        alias                   ws-prod9
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.225
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               ws-prod10
        alias                   ws-prod10
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.226
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              webservices
}
define host{
        use                     generic-host
        host_name               archive03
        alias                   archive03
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.58
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               archive04
        alias                   archive04
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.54
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              dbmachines
}
define host{
        use                     generic-host
        host_name               ops1a
        alias                   ops1a
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 10.100.4.12
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               syslog
        alias                   syslog
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.103.7
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               syslog-old
        alias                   syslog-old
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.95
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               att
        alias                   att 
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 10.100.0.1
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               redis-backend-s1
        alias                   redis-backend-s1
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.73
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               redis-backend-s2
        alias                   redis-backend-s2
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.14
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               redis-backend-m1
        alias                   redis-backend-m1
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.100
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              misc
}

;----------------- WEBSITE --------------------
define host{
        use                     generic-host
        host_name               www.care2.com
        alias                   www.care2.com
        check_command           check_vhost!8.47.77.87!/!aw4y1n
        check_interval          1
        retry_interval          1
        address                 8.47.77.87
        max_check_attempts      5
        check_period            24x7
        contact_groups          downpage,eng1,eng2
        notification_interval   90
        notification_period     24x7
        hostgroups              websites
}
define host{
        use                     generic-host
        host_name               www.thepetitionsite.com
        alias                   www.thepetitionsite.com
        check_command           check_vhost!www.thepetitionsite.com!/!UA-41501525-1
        check_interval          1
        retry_interval          1
        address                 192.168.103.38
        max_check_attempts      5
        check_period            24x7
        contact_groups          downpage,eng1,eng2
        notification_interval   90
        notification_period     24x7
        hostgroups              websites
}

;---------------- VIPS -----------------------
define host{
        use                     generic-host
        host_name               vip-http-cdn
        alias                   VHTTP cdn.care2.com
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.52
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}

define host{
        use                     generic-host
        host_name               vip-http-care2
        alias                   VHTTP www.care2.com
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.200
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-http-thepetitionsite
        alias                   VHTTP www.thepetitionsite.com
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.201
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-http-webservices
        alias                   VHTTP Web Services
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.102
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-http-maint-page
        alias                   VHTTP Maintenance Page
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.51
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-backend-slave
        alias                   VMySQL Backend Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.4
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-ecards-slave
        alias                   VMySQL eCards Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.8
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-gallery-master
        alias                   VMySQL Gallery Master
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.32
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-gallery-slave
        alias                   VMySQL Gallery Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.33
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-mail-master
        alias                   VMySQL Mail Master
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.10
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-mail-slave
        alias                   VMySQL Mail Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.34
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-master-master
        alias                   VMySQL Master DB
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.2
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-ngms-slave
        alias                   VMySQL NGMS Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.14
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-pm-master
        alias                   VMySQL PM Master
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.11
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-pm-slave
        alias                   VMySQL PM Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.47
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-search-slave
        alias                   VMySQL Search Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.7
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-sessions-slave
        alias                   VMySQL Sessions Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.9
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
define host{
        use                     generic-host
        host_name               vip-mysql-web-slave
        alias                   VMySQL Web Slave
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.101.6
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   90
        notification_period     24x7
        hostgroups              vips
}
#define host{
#        use                     generic-host
#        host_name               unittest1
#        alias                   unittest1
#        check_command           PING
#        check_interval          1
#        retry_interval          1
#        address                 192.168.100.76
#        max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        notification_interval   0
#        notification_period     24x7
#        hostgroups              misc
#}
#define host{
#        use                     generic-host
#        host_name               unittest2
#        alias                   unittest2
#        check_command           PING
#        check_interval          1
#        retry_interval          1
#        address                 192.168.100.202
#        max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        notification_interval   0
#        notification_period     24x7
#        hostgroups              misc
#}
#define host{
#        use                     generic-host
#        host_name               unittest3
#        alias                   unittest3
#        check_command           PING
#        check_interval          1
#        retry_interval          1
#        address                 192.168.100.203
#        max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        notification_interval   0
#        notification_period     24x7
#        hostgroups              misc
#}
#define host{
#        use                     generic-host
#        host_name               edgecast01
 #       alias                   edgecast01
#        check_command           PING
#        check_interval          1
#        retry_interval          1
#        address                 192.168.100.210
#        max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        notification_interval   0
#        notification_period     24x7
#        hostgroups              misc
#}
#define host{
#        use                     generic-host
#        host_name               vlan-stack
#        alias                   vlan-stack
#        check_command           PING
#        check_interval          1
#        retry_interval          1
#        address                 172.40.255.254
#        max_check_attempts      3
#        check_period            24x7
#        contact_groups          downpage
#        notification_interval   0
#        notification_period     24x7
#        hostgroups              misc
#}
define host{
        use                     generic-host
        host_name               qa-esx02
        alias                   qa-esx02
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.102.190
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               qa-db01
        alias                   qa-db01
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.102.100
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               devdb-test
        alias                   devdb-test
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.102.141
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               vpn-rwc
        alias                   vpn-rwc
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 10.100.2.1
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}
define host{
        use                     generic-host
        host_name               vpn-cage
        alias                   vpn-cage
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.102.50
        max_check_attempts      3
        check_period            24x7
        contact_groups          downpage
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}

define host{
        use                     generic-host
        host_name               tableau-windows
        alias                   tableau-windows
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.117
        max_check_attempts      3
        check_period            24x7
        contact_groups          ops
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}

define host{
        use                     generic-host
        host_name               ops-windows
        alias                   ops-windows
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 192.168.100.194
        max_check_attempts      3
        check_period            24x7
        contact_groups          ops
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}

define host{
        use                     generic-host
        host_name               rwc-windows
        alias                   rwc-windows
        check_command           PING
        check_interval          1
        retry_interval          1
        address                 10.100.4.160
        max_check_attempts      3
        check_period            24x7
        contact_groups          ops
        notification_interval   0
        notification_period     24x7
        hostgroups              misc
}


[stevens@nagios care2-configs]$ sudo vi hosts.cfg
[stevens@nagios care2-configs]$ cat services.cfg
# Care2 services.cfg file

define service{
        name                    critical_service
        max_check_attempts      3
        check_interval          1
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        register                0
}
define service{
        name                    critical_service_24hr
        max_check_attempts      96
        check_interval          15
        retry_interval          15
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        register                0
}
 define service{
        name                    low_priority_service
        max_check_attempts      3
        check_interval          10
        retry_interval          1
        check_period            24x7
        notification_interval   0
        notification_period     24x7
        notification_options    n
        notifications_enabled   1
	register		0
}

define service{
        name                            netapp-device-class
        host_name                       netapp01,netapp02,netapp03,netapp04
        active_checks_enabled           1       ; Active service checks are enabled
        passive_checks_enabled          0       ; Passive service checks are enabled/disabled
        parallelize_check               1       ; Active service checks should be parallelized
                                                ; (disabling this can lead to major performance problems)
        obsess_over_service             1       ; We should obsess over this service (if necessary)
        check_freshness                 1       
        notifications_enabled           1       
        event_handler_enabled           1       
        flap_detection_enabled          0       
        process_perf_data               1       ; Process performance data
        retain_status_information       1       ; Retain status information across program restarts
        retain_nonstatus_information    1       ; Retain non-status information across program restarts
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              3
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  downpage
        notification_interval           240
        notification_period             24x7
        notification_options            u,c,r
        register                        0       ; DONT REGISTER THIS DEFINITION - ITS NOT A REAL SERVICE, JUST A TEMPLATE!
        }

define service {
	name graphed-service
	action_url /nagios/cgi-bin/show.cgi?host=$HOSTNAME$&service=$SERVICEDESC$' onMouseOver='showGraphPopup(this)' onMouseOut='hideGraphPopup()' rel='/nagios/cgi-bin/showgraph.cgi?host=$HOSTNAME$&service=$SERVICEDESC$&period=week&rrdopts=-w+450+-j
	register 0
}

#--------------- UNIVERSAL ALL -------------------
define service{
        host_name               archive04,blade01-01,blade01-02,blade01-04,blade01-12,blade01-13,svpdb01,blade02-01,blade02-10,webslave04,webslave04,archive04,blade02-04,utildb,utildb2,blade05-01,blade02-12,blade02-13,svpdb02,web01,web02,web03,web04,pmta02,blade04-01,mp01,pmta01,mp02,bounce01,bounce02,jenkins,cron01,cron02,mp03,mcglynn,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,,crondb01,crondb02
       service_description      ntp
       check_command            check_nrpe!check_ntp_time!192.168.100.1!30!60
       notes_url                http://earthworm.care2.com/wiki/index.php/check_ntp
       max_check_attempts       3
       check_interval           3
       retry_interval           1
       check_period             24x7
       notification_interval    120 
       notification_period      24x7
       notification_options     r,c
       notifications_enabled    0
       event_handler		ntp_update
       contact_groups           ops
}
define service{
        host_name               redis1,redis2,redis3,redis4,redis5,redis6,nagios,ns1-prod,ns2-prod,archive04,web01,web02,web03,mp01,bounce01,bounce02,jenkins,blade04-01,pmta01,mp02,blade01-01,blade01-02,blade01-04,blade01-12,blade01-13,svpdb01,blade02-01,blade02-10,webslave04,archive04,blade02-04,utildb,utildb2,blade05-01,blade02-12,blade02-13,cron01,cron02,mp03,mcglynn,earthworm1,earthworm2,earthworm4,svpdb02,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,syslog,web04,ws-prod1,ws-prod2,ws-prod3,ws-prod4,ws-prod5,ws-prod6,ws-prod7,ws-prod8,ws-prod9,ws-prod10,puppet01,redis-backend-s1,redis-backend-s2,redis-backend-m1,pmta02,crondb01,crondb02
        service_description     ssh
        check_command           check_ssh
	notes_url               http://earthworm.care2.com/wiki/index.php/check_ssh
        max_check_attempts      3
        check_interval          5
        retry_interval          1
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}

define service{
        host_name               archive04,pmta01,mp02,blade01-01,blade01-02,blade01-04,blade01-12,blade01-13,svpdb01,blade02-01,blade02-10,webslave04,archive04,blade02-04,blade04-01,utildb,utildb2,blade05-01,blade02-12,blade02-13,svpdb02,web01,web02,web03,pmta02,mp01,bounce01,bounce02,jenkins,cron01,cron02,mp03,mcglynn,earthworm1,earthworm4,earthworm2,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,syslog,web04,ws-prod1,ws-prod2,ws-prod3,ws-prod4,ws-prod5,ws-prod6,ws-prod7,ws-prod8,ws-prod9,ws-prod10,puppet01,redis-backend-s1,redis-backend-s2,redis-backend-m1,crondb01,crondb02
	use			low_priority_service
        service_description     nrpe
	notes_url               http://earthworm.care2.com/wiki/index.php/check_nrpe
        check_command           check_nrpe_status
        contact_groups          ops
}

define service{
        host_name               web01,web02,web03,blade05-01,blade02-12,utildb2,web04,blade01-04,blade02-10,svpdb01,crondb01,syslog,crondb02,ws-prod7,ws-prod8,ws-prod9,ws-prod10
        use                     low_priority_service
        service_description     syslog-ng
	notes_url               http://earthworm.care2.com/wiki/index.php/check_syslog
        check_command           check_nrpe!check_procs!syslog-ng!syslog-ng!1:1!2
        contact_groups          ops
}

define service{
        host_name               blade01-01,blade01-12,blade02-01,blade04-01,jenkins,ws-prod1,ws-prod2,ws-prod5,ws-prod6,mp01,mp02,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,utildb,cron01,cron02,mp03,bounce01,bounce02
        use                     low_priority_service
        service_description     syslog-ng Centos
	notes_url               http://earthworm.care2.com/wiki/index.php/check_syslog
        check_command           check_nrpe!check_procs!syslog-ng!syslog-ng!2:3!4
        contact_groups          ops
}
define service{
        host_name               blade01-02,blade01-13,archive04,blade02-04,blade02-13,svpdb02
        use                     low_priority_service
        service_description     syslog-ng Centos
	notes_url               http://earthworm.care2.com/wiki/index.php/check_syslog
        check_command           check_nrpe_1arg!check_syslog
        contact_groups          ops
}


define service{
        host_name               redis1,redis2,redis3,redis4,redis5,redis6,utildb,utildb2,blade01-04,blade02-04,web01,web02,web03,pmta02,blade04-01,mp01,pmta01,mp02,bounce01,bounce02,jenkins,cron01,cron02,mp03,mcglynn,earthworm1,earthworm4,earthworm2,syslog,web04,ws-prod1,ws-prod2,ws-prod3,ws-prod4,ws-prod5,ws-prod6,ws-prod7,ws-prod8,ws-prod9,ws-prod10,redis-backend-s1,redis-backend-s2,redis-backend-m1
        service_description     load
        check_command           check_remote_load!15,20,25!30,35,40
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    u,r,c
        notifications_enabled   1
        contact_groups          ops
}

define service{
        host_name               blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,blade02-10,webslave04,archive04,blade02-13,svpdb02,crondb01,crondb02
        service_description     load
        check_command           check_remote_load!30,25,20!40,35,30
        max_check_attempts      5
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    u,r,c
        notifications_enabled   1
        contact_groups          ops,pageops
}

define service{
        host_name               blade01-12
        service_description     load
        check_command           check_remote_load!20,18,16!30,25,20
        max_check_attempts      3
        check_interval          15
        retry_interval          15
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     load
        check_command           check_remote_load!12,12,12!15,15,15
        max_check_attempts      3
        check_interval          15
        retry_interval          15
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}

define service{
        host_name               netapp01,netapp02
       service_description      telnet
       check_command            check_tcp!23
       max_check_attempts       3
       check_interval           3
       retry_interval           1
       check_period             24x7
       notification_interval    0
       notification_period      24x7
       notification_options    w,u,r,c
       notifications_enabled   1
       contact_groups           ops
}

define service{
	use				netapp-device-class
	service_description		CPU LOAD 
	check_command			check_naCPU
	}

define service{
	use				netapp-device-class
	service_description		FAIL DISK
	check_command			check_naDISK
	}

define service{
	use				netapp-device-class
	service_description		FAN STATE
	check_command			check_naFAN
	}

define service{
	use				netapp-device-class
	service_description		DISK SPACE USAGE
	check_command			check_naSPACE
	}

define service{
	use				netapp-device-class
	service_description		UPTIME
	check_command			check_naUPTIME
	}

define service{
        use                             netapp-device-class
        service_description             PS
        check_command                   check_naPS
        }

define service{
	host_name		ns1-prod,ns2-prod
       service_description      ldap
       check_command            check_ldap!uid=nagios!dc=care2,dc=com!10!30
       max_check_attempts       3
       check_interval           3
       retry_interval           1
       check_period             24x7
       notification_interval    0
       notification_period      24x7
       notification_options    w,u,r,c
       notifications_enabled   1
       contact_groups           ops
}
#------------ WEB -------------
define service{
       host_name                www.care2.com,www.thepetitionsite.com,web01,web02,web03,blade04-01,vip-http-care2,vip-http-thepetitionsite,vip-http-cdn,web04,ws-prod1,ws-prod2,ws-prod3,ws-prod4,ws-prod5,ws-prod6,ws-prod7,ws-prod8,ws-prod9,ws-prod10
       service_description      http
       check_command            check_http
       max_check_attempts       3
       check_interval           3
       retry_interval           1
       check_period             24x7
       notification_interval    120 
       notification_period      24x7
       notification_options    w,u,r,c
       notifications_enabled   1
       contact_groups           ops,pageops
}
define service{
       host_name                vip-http-maint-page
       service_description      http maint
       check_command            check_http!-p 80 -e 503
       max_check_attempts       3
       check_interval           3
       retry_interval           1
       check_period             24x7
       notification_interval    0
       notification_period      24x7
       notification_options    w,u,r,c
       notifications_enabled   1
       contact_groups           ops
}

#define service{
#       host_name                ops
#       service_description      http maint
#       check_command            check_http!-p 8080 -e 503
#       max_check_attempts       3
#       check_interval           3
#       retry_interval           1
#       check_period             24x7
#       notification_interval    0
#       notification_period      24x7
#       notification_options    w,u,r,c
#       notifications_enabled   1
#       contact_groups           ops
#}

define service{
	name		care2-include-string
	service_description	care2 HTTP/Include String
	is_volatile		0
	check_period		24x7
	max_check_attempts	3
	normal_check_interval	3
	retry_check_interval	1
	contact_groups		pageops,ops,eng1,eng2
	notification_interval	1
	notification_period	24x7
	notification_options	w,u,c,r
	register		0
}
define service{
       use             care2-include-string
       host_name       www.care2.com
       check_command   check_vhost!www.care2.com!/!aw4y1n
       max_check_attempts       3
       check_interval           3
       retry_interval           1
       check_period             24x7
       notification_interval    1
       notification_period      24x7
       notification_options    w,u,r,c
       notifications_enabled   1
       contact_groups           ops,pageops
}
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String ecards
        host_name               www.care2.com
        check_command           check_vhost!www.care2.com!/ecards/!aw4y1n
}
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String HAGL
        host_name               www.care2.com
        check_command           check_vhost!www.care2.com!/greenliving/!aw4y1n
}
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String click-to-donate
        host_name               www.care2.com
        check_command           check_vhost!www.care2.com!/click-to-donate/!aw4y1n
}

define service{
	use		care2-include-string
	host_name	web01
	check_command	check_vhost!node1-www.care2.com!/!aw4y1n
}	
define service{
        use             	care2-include-string
	service_description	care2 HTTP/Include String ecards
        host_name      		web01
        check_command   	check_vhost!node1-www.care2.com!/ecards/!aw4y1n
}
define service{
        use             	care2-include-string
	service_description	care2 HTTP/Include String click-to-donate
        host_name       	web01
        check_command   	check_vhost!node1-www.care2.com!/click-to-donate/!aw4y1n
}
define service{
        use             care2-include-string
        host_name       web02
        check_command   check_vhost!node2-www.care2.com!/!aw4y1n
} 
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String ecards
        host_name               web02
        check_command           check_vhost!node2-www.care2.com!/ecards/!aw4y1n
}
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String click-to-donate
        host_name               web02
        check_command           check_vhost!node2-www.care2.com!/click-to-donate/!aw4y1n
}
define service{
        use             care2-include-string
        host_name       web03
        check_command   check_vhost!node3-www.care2.com!/!aw4y1n
}
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String ecards
        host_name               web03
        check_command           check_vhost!node3-www.care2.com!/ecards/!aw4y1n
}
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String click-to-donate
        host_name               web03
        check_command           check_vhost!node3-www.care2.com!/click-to-donate/!aw4y1n
} 
define service{
        use             care2-include-string
        host_name       web04
        check_command   check_vhost!node4-www.care2.com!/!aw4y1n
}
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String ecards
        host_name               web04
        check_command           check_vhost!node4-www.care2.com!/ecards/!aw4y1n
}
define service{
        use                     care2-include-string
        service_description     care2 HTTP/Include String click-to-donate
        host_name               web04
        check_command           check_vhost!node4-www.care2.com!/click-to-donate/!aw4y1n
} 
define service{
        name            petitionsite-include-string
        service_description     Petitionsite HTTP/Include String
        is_volatile             0
        check_period            24x7
        max_check_attempts      3
        normal_check_interval   3
        retry_check_interval    1
        contact_groups          pageops,ops,eng1,eng2
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,c,r
        register                0
	notifications_enabled	1
}
define service{
	use		petitionsite-include-string
	host_name	www.thepetitionsite.com
	service_description	CS Netscaler
	check_command	check_vhost!192.168.101.201!http://www.thepetitionsite.com/!UA-41501525-1
}
define service{
        use             petitionsite-include-string
        host_name       www.thepetitionsite.com
        service_description     CDN Netscaler
        check_command   check_vhost!192.168.101.52!http://www.thepetitionsite.com/!UA-41501525-1
}
define service{
        use             petitionsite-include-string
        host_name       www.thepetitionsite.com
        service_description     Ext IP .89
        check_command   check_vhost!8.47.77.89!http://www.thepetitionsite.com/!UA-41501525-1
}
define service{
        use             petitionsite-include-string-91
        host_name       www.thepetitionsite.com
        service_description     Ext IP .91
        check_command   check_vhost_ssl!8.47.77.91!https://www.thepetitionsite.com/!UA-41501525-1
}

define service{
        name                    petitionsite-include-string-91
        service_description     Petitionsite H/TTP/Include String nsite-include-string-91
        is_volatile             0
        check_period            24x7
        max_check_attempts      3
        normal_check_interval   3
        retry_check_interval    1
        contact_groups          ops
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,c,r
        register                0
        notifications_enabled   1
}

define service{
        name            earthworm homepage
        service_description     earthworm homepage
	host_name		utildb
	check_command		check_vhost!earthworm.care2.com!/!DAC960
        is_volatile             0
        check_period            24x7
        max_check_attempts      3
        normal_check_interval   3
        retry_check_interval    1
        contact_groups          pageops,ops
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,c,r
        register                1
        notifications_enabled   1
}
define service{
        name            earthworm4 Convio Page
        service_description     earthworm4 Convio Page
        host_name               earthworm4
        check_command           check_vhost!earthworm2.care2.com!/petitiontools!/convio_advocacy.php
        is_volatile             0
        check_period            24x7
        max_check_attempts      3
        normal_check_interval   3
        retry_check_interval    1
        contact_groups          pageops,ops
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,c,r
        register                1
        notifications_enabled   1
}
define service{
        name            earthworm1 Convio Page
        service_description     earthworm1 Convio Page
        host_name               earthworm1
        check_command           check_vhost!earthworm1.care2.com!/petitiontools!/convio_advocacy.php
        is_volatile             0
        check_period            24x7
        max_check_attempts      3
        normal_check_interval   3
        retry_check_interval    1
        contact_groups          pageops,ops
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,c,r
        register                1
        notifications_enabled   1
}


define service{
      host_name                 ns1-prod,ns2-prod
       service_description      dns  
       check_command            check_dns!www.care2.com!8.47.77.87!60
       max_check_attempts       3
       check_interval           3
       retry_interval           1
       check_period             24x7
       notification_interval    60
       notification_period      24x7
       notification_options    w,u,r,c
       notifications_enabled   1
       contact_groups           ops
}

define service{
	host_name		pmta02,pmta01,bounce01,bounce02
	service_description	smtp
	check_command		check_smtp
	max_check_attempts      3
        check_interval          5
        retry_interval          15
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}


define service{
        host_name               redis1,redis2,redis3,redis4,redis5,redis6,archive04,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,archive04,blade02-13,svpdb02,syslog,webslave04,crondb01
        service_description     disk /
        check_command           check_nrpe!check_disk!7%!4%!/
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               crondb02,blade02-10
        service_description     disk /
        check_command           check_nrpe!check_disk!2%!1%!/
        notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade01-04,blade02-04,utildb,utildb2,blade05-01,blade02-12,web01,web02,web03,pmta02,mp01,bounce01,bounce02,jenkins,blade04-01,mp02,web04,ws-prod1,ws-prod2,ws-prod3,ws-prod4,ws-prod5,ws-prod6,ws-prod7,ws-prod8,ws-prod9,ws-prod10
        service_description     disk /
        check_command		check_nrpe!check_disk!4%!3%!/
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               pmta01,pmta02
        service_description     disk /
        check_command		check_nrpe!check_disk!7%!5%!/
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,puppet01,redis-backend-s1,redis-backend-s2,redis-backend-m1
        service_description     disk /
        check_command           check_nrpe!check_disk!10%!5%!/
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade02-04,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,archive04,blade02-13
        service_description     disk /home
        check_command           check_nrpe!check_disk!8%!3%!/home
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade02-04,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,archive04,blade02-13
        service_description     disk /tmp
        check_command           check_nrpe!check_disk!10%!5%!/tmp
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
define service{
        host_name               blade02-04,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,archive04,blade02-13
        service_description     disk /usr
        check_command           check_nrpe!check_disk!10%!5%!/usr
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade02-04,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,archive04,blade02-13
        service_description     disk /usr/local
        check_command           check_nrpe!check_disk!10%!5%!/usr/local
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade02-04,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,archive04,blade02-13
        service_description     disk /var
        check_command           check_nrpe!check_disk!10%!5%!/var
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade02-04,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,archive04,blade02-13
        service_description     disk /var/log
        check_command           check_nrpe!check_disk!10%!5%!/var/log
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade02-04,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,archive04,blade02-13
        service_description     disk /var/spool
        check_command           check_nrpe!check_disk!10%!5%!/var/spool
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,blade02-10,archive04,utildb,utildb2,blade02-13,svpdb02
        service_description     disk /dev/shm
        check_command           check_nrpe!check_disk!6%!4%!/dev/shm
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade01-04,blade02-04,blade01-12,blade05-01,blade02-12,web01,web02,web03,blade04-01,mp01,bounce01,bounce02,mp02,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     disk /dev/shm
	check_command		check_nrpe!check_disk!6%!4%!/dev/shm
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               redis1,redis2,redis3,redis4,redis5,redis6,blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,blade02-13,svpdb02,web04,ws-prod1,ws-prod2,ws-prod3,ws-prod4,ws-prod5,ws-prod6,ws-prod7,ws-prod8,ws-prod9,ws-prod10
        service_description     swap
        check_command           check_nrpe!check_swap!95%!90%
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Swap
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    u,r,c
        notifications_enabled   1
        contact_groups          ops
}


define service{
        host_name               blade01-04,blade01-12,blade02-04,utildb,utildb2,blade05-01,blade02-12,web01,web02,web03,pmta02,mp01,blade04-01,pmta01,mp02,bounce01,bounce02,jenkins,nagios,ns1-prod,ns2-prod,archive04,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,syslog
        service_description     swap
        check_command           check_nrpe!check_swap!10%!5%
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Swap
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}

define service{
        host_name               nagios
        service_description     disk /mnt/netapp02/home
        check_command           check_nrpe!check_disk!3%!1%!/mnt/netapp02/home
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_NFS_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   0
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
define service{
        host_name               nagios
        service_description     disk /mnt/netapp02/WWW
        check_command           check_nrpe!check_disk!5%!3%!/mnt/netapp02/WWW
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_NFS_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
#define service{
#        host_name               nagios
#        service_description     disk /mnt/netapp02/logs
#        check_command           check_nrpe!check_disk!7%!5%!/mnt/netapp02/logs
#	notes_url               http://earthworm.care2.com/wiki/index.php/Check_NFS_Disk
#        max_check_attempts      10
#        check_interval          3
#        retry_interval          3
#        check_period            24x7
#        notification_interval   120
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          pageops,ops
#}
define service{
        host_name               nagios
        service_description     disk /
        check_command           check_nrpe!check_disk!7%!5%!/
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
define service{
        host_name               nagios
        service_description     disk /mnt/netapp02/care2
        check_command           check_nrpe!check_disk!4%!3%!/mnt/netapp02/care2
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_NFS_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
define service{
        host_name               nagios
        service_description     disk /mnt/netapp02/root
        check_command           check_nrpe!check_disk!7%!5%!/mnt/netapp02/root
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_NFS_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               nagios
        service_description     disk /mnt/netapp01/root
        check_command           check_nrpe!check_disk!7%!5%!/mnt/netapp01/root
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_NFS_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
define service{
        host_name               blade01-04,blade02-04,mp01,mp02
        service_description     disk /data
        check_command           check_nrpe!check_disk!5%!3%!/data
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   720
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}

define service{
        host_name               blade01-01,blade01-02,blade01-13,svpdb01,blade02-01,blade02-10,archive04,blade05-01,blade02-12,blade02-13,svpdb02,blade01-12,crondb01,crondb02
        service_description     disk /data
        check_command           check_nrpe!check_disk!2%!1%!/data
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   720
        notification_period     24x7
        notification_options    u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
define service{
        host_name               archive03
        service_description     disk /data2
        check_command           check_nrpe!check_disk!2%!1%!/data2
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   720
        notification_period     24x7
        notification_options    u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
define service{
        host_name               monitor2
        service_description     disk /var/log
        check_command           check_nrpe!check_disk!2%!1%!/var/log
        notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   720
        notification_period     24x7
        notification_options    u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops
}
#mount check only - only unknown notifications
define service{
        host_name               web01,web02,web03,web04,mp01,blade04-01,mp02
        service_description     disk /mnt/care2
        check_command           check_nrpe!check_disk!4%!3%!/mnt/care2
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_NFS_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    u
        notifications_enabled   1
        contact_groups          ops
}
#mount check only - only unknown notifications
define service{
        host_name               web01,web02,web03,web04,mp01,blade04-01,mp02,bounce01,bounce02,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     disk /var/c2/code/care2
        check_command           check_nrpe!check_disk!5%!3%!/var/c2/code/care2
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    u
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               web01,web02,web03,web04,mp01,mp02
        service_description     disk /var/c2/shared
        check_command           check_nrpe!check_disk!5%!3%!/var/c2/shared
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    u
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               bounce01,bounce02,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     disk /var/c2/shared-ngms
        check_command           check_nrpe!check_disk!5%!3%!/var/c2/shared-ngms
	notes_url               http://earthworm.care2.com/wiki/index.php/Check_Disk
        max_check_attempts      10
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    u
        notifications_enabled   1
        contact_groups          ops
}


define service{
        host_name               web01,web02,web03,web04,blade04-01
        service_description     httpd procs
	check_command		check_nrpe!check_procs!httpd!httpd!500!600
        max_check_attempts      3 
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   120
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,pageops
}

#define service{
#        host_name               jenkins-b
#        service_description     httpd procs
#        check_command           check_nrpe!check_procs!httpd!httpd!0!1
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   120
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          ops_only
#}

define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     Enigma svc ID 1
        check_command           check_nrpe!check_procs!php!service-id=1!1:1!2 
        max_check_attempts      3
        check_interval          3
        retry_interval          3
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     Enigma svc ID 2
        check_command           check_nrpe!check_procs!php!service-id=2!1:1!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     Enigma svc ID 3
        check_command           check_nrpe!check_procs!php!service-id=3!1:1!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     Enigma svc ID 4
        check_command           check_nrpe!check_procs!php!service-id=4!1:1!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     Enigma svc ID 5
        check_command           check_nrpe!check_procs!php!service-id=5!1:1!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     Enigma svc ID 6
        check_command           check_nrpe!check_procs!php!service-id=6!1:1!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     Enigma svc ID 7
        check_command           check_nrpe!check_procs!php!service-id=7!1:1!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     Enigma svc ID 8
        check_command           check_nrpe!check_procs!php!service-id=8!1:1!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     check memory
        check_command           check_nrpe_mem!check_mem
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    u,r,c
        notifications_enabled   1
        event_handler           clear_mem
        contact_groups          ops
}
define service{
        host_name               pmta02,pmta01
        service_description     PowerMTA   
        check_command           check_nrpe!check_procs_by_string!pmta!1:10!10   
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}

define service{
       host_name               mp01
       service_description     MQ Server Error 
       check_command           check_nrpe_minute!check_mq_error
       max_check_attempts      3
       check_interval          3
       retry_interval          1 
       check_period            24x7
       notification_interval   120
       notification_period     24x7
       notification_options    w,u,r,c
       notifications_enabled   1
       contact_groups          ops-alert,richard 
}

define service { 
	host_name		redis-backend-s1,redis-backend-s2,redis-backend-m1
	service_description 	Redis Stats 
	check_command 		check_redis!6379!"3,4"!blocked_clients,connected_clients!50,~!100,~ 
	max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
} 

define service { 
	host_name		redis1,redis2,redis3,redis4,redis5,redis6
	service_description 	Redis Response Times
	check_command 		check_redis_responsetimes!6379!100,200
	max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          mikeh
} 

define service { 
	host_name		redis1,redis2,redis3,redis4,redis5,redis6
	service_description 	Redis Memory
	check_command 		check_redis_memory!6379!78,90!42G
	max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          mikeh
} 

define service{
        host_name               bounce01,bounce02
        service_description     bounce error
        check_command           check_nrpe!check_bounce_error!unused
        max_check_attempts      3 
        check_interval          60
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,eng1,eng2
}
define service{
        host_name               blade02-04,blade01-04,web01,web02,web03,web04,mp01,mp02,bounce01,bounce02,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     postfix
        check_command           check_nrpe!check_procs!master!postfix!1:1!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14
        service_description     check_ngms_nodes
        check_command           check_nrpe_1arg!check_enigma_nodes
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        event_handler           ngms_kick 
        contact_groups          mikeh_email
}

define service{
        host_name               blade02-04,blade01-04,web01,web02,web03,web04,mp01,mp02
        service_description     mail queue
        check_command           check_nrpe!check_mailq!postfix!12500!25000!30
        max_check_attempts      10
        check_interval          5
        retry_interval          5
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               bounce01,bounce02
        service_description     mail queue
        check_command           check_nrpe!check_mailq!postfix!100000!200000!30
        max_check_attempts      12
        check_interval          5
        retry_interval          5
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,pageops
}

define service{
        host_name               syslog 
        service_description     signature count 
        check_command           check_nrpe_1arg!check_signature
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,slack-eugene
}

define service{
        host_name               att
        service_description     Care2 Office att Connection Slow
        check_command           check_ping!100.0,80%!200.0,100%
        max_check_attempts      3
        check_interval          5
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}

define service{
        host_name               archive04,blade01-01,blade01-02,blade01-04,blade01-12,blade01-13,svpdb01,blade02-01,blade02-10,webslave04,archive04,blade02-04,utildb,utildb2,blade05-01,blade02-12,blade02-13,svpdb02,web01,web02,web03,web04,mp01,pmta01,mp02,bounce01,bounce02,nagios,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,syslog,puppet01,crondb01,crondb02
        service_description     check inode
        check_command           check_nrpe_time!check_inode
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}

#define service{
#        host_name               archive03,archive04,blade01-01,blade01-02,blade01-04,blade01-12,blade01-13,blade02-01,blade02-04,blade02-10,blade02-12,blade02-13,blade04-01,blade04-08,blade05-01,bounce01,bounce02,cron01,cron02,export01,jenkins,jenkins-b,monitor2,mp01,mp02,mp03,nagios,netapp01,netapp02,netapp03,netapp04,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,ns1-prod,ns2-prod,pmta01,pmta02,puppet01,redis-backend-m1,redis-backend-s1,redis-backend-s2,redis1,redis2,redis3,redis4,redis5,redis6,syslog,syslog-old,vm0309,vm0311,vm0312,vm0313,vm0405,vm0411,vm0412,vm0413,vm0414,vpn-cage,vpn-rwc,web01,web02,web03,web04,webslave04,ws-prod1,ws-prod10,ws-prod2,ws-prod3,ws-prod4,ws-prod5,ws-prod6,ws-prod7,ws-prod8,ws-prod9
#        service_description     check_inodes_root_home
#        check_command           check_nrpe!check_inodes_root_home!
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   60
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          ops
#}


define service{
        host_name	        ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,jenkins,earthworm1
        service_description     check_inodes_root_home
        check_command           check_nrpe_remote!check_inodes_root_home
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}


define service{
        host_name               archive04,blade01-01,blade01-02,blade01-04,blade01-12,blade01-13,svpdb01,blade02-01,blade02-10,archive04,blade02-04,utildb,utildb2,blade05-01,blade02-12,blade02-13,svpdb02,pmta02,mp01,pmta01,mp02,bounce01,bounce02,jenkins,cron01,cron02,mp03,mcglynn,earthworm1,earthworm2,earthworm4,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,nagios,syslog,svpdb01,crondb01,crondb02
        service_description     check myswap 
        check_command           check_nrpe_time!check_myswap
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   720
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops_only
}
define service{
        host_name               web01,web02,web03,web04,blade04-01
        service_description     check myswap web
        check_command           check_nrpe_time!check_myswap
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   720
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
	event_handler		clear_swap_webservers
        contact_groups          pageops,ops 
}

define service{
        host_name               blade01-02,blade01-04,blade01-12,blade01-13,archive04,blade02-04,utildb,utildb2,blade05-01,blade02-12,blade02-13,web01,web02,web03,web04,pmta02,blade04-01,pmta01,bounce01,bounce02,jenkins,cron01,cron02,mp03,mcglynn,earthworm1,earthworm2,earthworm4,nagios,ngms01,ngms02,ngms03,ngms04,ngms09,ngms11,ngms12,ngms13,ngms14,syslog,svpdb01,puppet01
        service_description     check mydisk 
        check_command           check_nrpe_minute!check_mydisk
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   720 
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          pageops,ops 
}

#define service{
#        host_name               jenkins,earthworm1,earthworm2,earthworm4 
#        service_description     check myinode
#        check_command           check_nrpe_time!check_myinode
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   1440 
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          ops 
#}

define service{
        host_name               blade01-13,blade02-13,blade01-01,blade02-01,blade02-04,svpdb01,svpdb02,blade01-02,utildb,archive04,blade01-12
        service_description     check LUN
        check_command           check_nrpe_lun!check_lun
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   1440
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               syslog 
        service_description     check elastic search 
        check_command           check_nrpe_time!check_elastic
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,eugene,steven,slack-eugene
}

define service{
        host_name               syslog 
        service_description     check optin rejections 
        check_command           check_nrpe_time!check_optin_rejections
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          noc,slack-eugene
}
define service{
        host_name               syslog 
        service_description     check_served_optins_aa_requirements
        check_command           check_nrpe_time!check_served_optins_aa_requirements
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          steven,slack-eugene
}

define service{
        host_name               syslog 
        service_description     check unchecked optins 
        check_command           check_nrpe_time!check_unchecked_optins
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          slack-eugene
}

define service{
        host_name               syslog
        service_description     check enigma errors
        check_command           check_nrpe_time!check_enigma_errors
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          richard,ops-alert
}

define service{
        host_name               syslog
        service_description     check enigma injection queue
        check_command           check_nrpe_time!check_enigma_injection_queue
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          richard,ops-alert
}

define service{
        host_name               syslog
        service_description     check enigma newsletters
        check_command           check_nrpe_time!check_enigma_newsletters
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          richard,ops-alert
}

define service{
        host_name               syslog 
        service_description     check webservices errors
        check_command           check_nrpe_time!check_webservices_errors
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          slack-eugene,mikeh,eugene
}


define service{
        host_name               syslog 
        service_description     check unknown PHP errors 
        check_command           check_nrpe_time!check_unknown_php_errors
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          noc,slack-eugene
}

define service{
        host_name               syslog
        service_description     check unknown PHP warnings
        check_command           check_nrpe_time!check_unknown_php_warnings
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          noc,slack-eugene
}

define service{
        host_name               syslog
        service_description     check optin delivery failures and rejections
        check_command           check_nrpe_time!check_optin_delivery_failures_and_rejections
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,liudmila,slack-eugene
}

define service{
        host_name               syslog
        service_description     check optin delivery percentage
        check_command           check_nrpe_time!check_optin_delivery_percentage
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops-alert
}
define service{
        host_name               syslog
        service_description     check append errors
        check_command           check_nrpe_time!check_append_errors
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops-alert,steven,slack-eugene
}


define service{
        host_name               syslog 
        service_description     check care2 404 error 
        check_command           check_nrpe_time!check_care2_404s
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,slack-eugene
}
define service{
        host_name               syslog 
        service_description     check petitionsite 404 error 
        check_command           check_nrpe_time!check_petitionsite_404s
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,slack-eugene
}

define service{
        host_name               syslog 
        service_description     check care2 500 error 
        check_command           check_nrpe_time!check_care2_500s
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,slack-eugene
}
define service{
        host_name               syslog 
        service_description     check petitionsite 500 error 
        check_command           check_nrpe_time!check_petitionsite_500s
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,slack-eugene
}

define service{
        host_name               syslog 
        service_description     check ave care2 response time 
        check_command           check_nrpe_time!check_avg_response_time
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,ops-alert,slack-eugene
}

define service{
        host_name               syslog 
        service_description     check ave greenliving causes response time 
        check_command           check_nrpe_time!check_avg_response_time_causes
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,ops-alert,slack-eugene 
}

define service{
        host_name               syslog 
        service_description     check ave blog posts response time 
        check_command           check_nrpe_time!check_avg_response_blog
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,ops-alert,slack-eugene 
}

define service{
        host_name               syslog 
        service_description     check ave blog category pages response time 
        check_command           check_nrpe_time!check_avg_response_blog_cat
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,ops-alert,slack-eugene 
}

define service{
        host_name               syslog 
        service_description     check signature rejections 
        check_command           check_nrpe_time!check_signature_rejections
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,slack-eugene
}

define service{
        host_name               syslog 
        service_description     check signature count 
        check_command           check_nrpe_time!check_signature_count
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,slack-eugene
}

define service{
        host_name               syslog 
        service_description     check optin count 
        check_command           check_nrpe_time!check_optin_count
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,ops-alert,slack-eugene 
}
define service{
        host_name               syslog 
        service_description     check servlets response time
        check_command           check_nrpe_time!check_servlets_response_time
        max_check_attempts      3 
        check_interval          3 
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,ops-alert,slack-eugene
}
define service{
        host_name               syslog
        service_description     check bot requests
        check_command           check_nrpe_time!check_bot_requests
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,ops-alert,slack-eugene
}
define service{
        host_name               syslog
        service_description     check PHP error indexing
        check_command           check_nrpe_time!check_php_error_indexing
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          eugene,ops-alert,slack-eugene
}
define service{
        host_name               syslog 
        service_description     check Suhosin 
        check_command           check_nrpe_1arg!check_everything_errors
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   60
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}

define service{
        host_name               ws-prod1,ws-prod2,ws-prod3,ws-prod4,ws-prod5,ws-prod6,ws-prod7,ws-prod8,ws-prod9,ws-prod10
        service_description     check php FastCGI
        check_command           check_nrpe!check_procs!php-fpm!php-fpm!16:60!60
        max_check_attempts      3
        check_interval          5
        retry_interval          1
        check_period            24x7
        notification_interval   360
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               archive04,blade01-01,blade01-02,blade01-12,blade01-13,blade02-01,blade02-04,blade02-13,blade04-01,bounce01,bounce02,cron01,cron02,mp03,earthworm1,earthworm4,jenkins,mp01,mp02,ngms01,ngms02,ngms03,ngms04,ngms05,ngms06,ngms07,ngms08,ngms09,ngms10,ngms11,ngms12,ngms13,ngms14,ns2-prod,svpdb02,utildb,ws-prod1,ws-prod3,ws-prod4,ws-prod5,ws-prod6,redis-backend-s1,redis-backend-s2,redis-backend-m1
        service_description     Puppet
        check_command           check_nrpe!check_procs!puppetd!puppetd!1:2!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               ns1-prod
        service_description     Puppet Ubuntu
        check_command           check_nrpe!check_procs_by_string!puppetd!1:2!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
define service{
        host_name               web01,web02,web03,web04,blade02-12,blade05-01,blade01-04,blade02-10,svpdb01,export01,crondb01,syslog,crondb02,ws-prod7,ws-prod8,ws-prod9,ws-prod10
        service_description     Puppet
        check_command           check_nrpe!check_procs!puppet!puppet!1:2!2
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
#define service{
#        host_name               edgecast01
#        service_description     logstash on edgecast01 
#        check_command           check_nrpe!check_procs_by_string!logstash!1:1!1:1
#        notes_url               http://earthworm.care2.com/wiki/index.php/ELK_edgecast
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   30
#        notification_period     24x7
##        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          ops
#}
#define service{
#        host_name               edgecast01
#        service_description     kibana on edgecast01 
#        check_command           check_nrpe!check_procs_by_string!kibana!1:1!1:1
#        notes_url               http://earthworm.care2.com/wiki/index.php/ELK_edgecast
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   30
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          ops
#}
#define service{
#        host_name               edgecast01
#        service_description     elastic on edgecast01 
#        check_command           check_nrpe!check_procs_by_string!elasticsearch!1:1!1:1
#        notes_url               http://earthworm.care2.com/wiki/index.php/ELK_edgecast
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
##        notification_interval   30
#        notification_period     24x7
#        notification_options    w,u,r,c
##        notifications_enabled   1
#        contact_groups          ops
#}
#define service{
#        host_name               edgecast01
#        service_description     filebeat on edgecast01 
#        check_command           check_nrpe!check_procs_by_string!filebeat!1:5!1:5
#        notes_url               http://earthworm.care2.com/wiki/index.php/ELK_edgecast
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   30
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          ops
#}
#define service{
#        host_name               edgecast01
#        service_description     nginx on edgecast01 
#        check_command           check_nrpe!check_procs_by_string!nginx!1:10!1:10
#        notes_url               http://earthworm.care2.com/wiki/index.php/ELK_edgecast
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   30
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          ops
#}
define service{
        host_name               utildb2
        service_description     Email Signatures
        check_command           check_nrpe!check_procs!php!build_email_signatures!1:1!1:1
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,richard
}

define service {
  	host_name               jenkins 
  	service_description     Jenkins - publish_wp_missed_schedule_posts
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        check_command           check_jenkins_cron!publish_wp_missed_schedule_posts!jenkins.care2.com/job/cron-minutely!200!600
        contacts                mikeh,eugene
}
define service{
        host_name               nagios
        service_description     find empty images care2
        check_command           find_empty_images
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,pageops
}
define service{
        host_name               nagios
        service_description     check cache control dingo
        check_command           check_cache_control
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          mikeh
}
define service{
        host_name               nagios
        service_description     Check Tableau Petitions
        check_command           check_tab_pet
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,pageops
}
define service{
        host_name               nagios
        service_description     Check Msg Queue WsSignatures
        check_command           check_tab_sig
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,pageops,richard
}
define service{
        host_name               nagios
        service_description     Check Msg Queue WsOptins
        check_command           check_ws_optins_queue
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,pageops,richard
}
define service{
        host_name               nagios
        service_description     Check Jenkins Slaves
        check_command           check_jenkins_slaves!http://jenkins.care2.com!1
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,eugene,slack-eugene
}
define service{
        host_name               syslog
        service_description     Check Signature Languages
        check_command           check_nrpe_time!check_signature_languages
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops,eugene,slack-eugene
}
define service{
        host_name               nagios
        service_description     Email Activity Table Check
        check_command           email_activity_table_check
        max_check_attempts      3
        check_interval          3
        retry_interval          1
        check_period            24x7
        notification_interval   30
        notification_period     24x7
        notification_options    w,u,r,c
        notifications_enabled   1
        contact_groups          ops
}
#define service{
#        host_name               ops
#	use			generic-service,nagiosgraph
#        service_description     Check BB Queue
#        check_command           check_bb_queue
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   30
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          mikeh
#}
#define service{
#        host_name               ops
#	use			generic-service
#        service_description     Check woff cache
#        check_command           check_woff_font_cache
#        max_check_attempts      3
#        check_interval          3
#        retry_interval          1
#        check_period            24x7
#        notification_interval   30
#        notification_period     24x7
#        notification_options    w,u,r,c
#        notifications_enabled   1
#        contact_groups          mikeh
#}
