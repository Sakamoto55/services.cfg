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
