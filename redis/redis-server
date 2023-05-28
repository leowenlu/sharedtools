#!/bin/sh
# redis - this script starts and stops the redis-server daemon
#
# chkconfig:   - 85 15 
# description:  Redis is a persistent key-value database
# processname: redis-server
# config:      /etc/redis/redis.conf
# pidfile:     /etc/redis/redis.pid

PIDFILE=/etc/redis/redis.pid

case "$1" in
start)
	/usr/local/bin/redis-server /etc/redis/redis.conf
;;
status)
        printf "%-50s" "Checking redis-server..."
        if [ -f $PIDFILE ]; then
            PID=`cat $PIDFILE`
            if [ -z "`ps axf | grep ${PID} | grep -v grep`" ]; then
                printf "%s\n" "Process dead but pidfile exists"
            else
                echo "Running"
            fi
        else
            printf "%s\n" "Service not running"
        fi
;;
stop)
        printf "%-50s" "Stopping redis-server"
            PID=`cat $PIDFILE`
        if [ -f $PIDFILE ]; then
            kill $PID
            printf "%s\n" "Ok"
        else
            printf "%s\n" "pidfile not found"
        fi
;;

restart)
  	$0 stop
  	$0 start
;;

*)
        echo "Usage: $0 {status|start|stop|restart}"
        exit 1
esac