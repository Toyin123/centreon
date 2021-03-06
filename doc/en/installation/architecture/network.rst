.. networktab:

======================
Table of network flows
======================

**************************************************************
Tables of network flows to integrate monitoring platform to IT
**************************************************************

+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| From           | To             | Protocol   | Port               | Application                                                                          |
+================+================+============+====================+======================================================================================+
| Central server | NTP server     | NTP        | UDP 123            | Synchronization of the system clock                                                  |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Central server | DNS server     | DNS        | UDP 53             | Domain name resolution                                                               |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Central server | SMTP server    | SMTP       | TCP 25             | Notification via email                                                               |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Central server | LDAP(s) server | LDAP(s)    | TCP 389 (636)      | Authentication to access the Centreon web interface                                  |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Central server | DBMS server    | MySQL      | TCP 3306           | Access to Centreon databases                                                         |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Central server | HTTP Proxy     | HTTP(s)    | TCP 80, 8080 (443) | If your platform needs to connect to a web proxy to access the Centreon IMP solution |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Central server | Repository     | HTTP (FTP) | TCP 80 (FTP 20)    | Repository for system and application packages                                       |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+

+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| From           | To             | Protocol   | Port               | Application                                                                          |
+================+================+============+====================+======================================================================================+
| Poller         | NTP server     | NTP        | UDP 123            | Synchronization of the system clock                                                  |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Poller         | DNS server     | DNS        | UDP 53             | Domain name resolution                                                               |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Poller         | SMTP server    | SMTP       | TCP 25             | Notification via email                                                               |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+
| Poller         | Repository     | HTTP (FTP) | TCP 80 (FTP 20)    | Repository for system and application packages                                       |
+----------------+----------------+------------+--------------------+--------------------------------------------------------------------------------------+

.. note::
    Other flows can be necessary for Centreon web authentication (RADIUS, etc.)
    or notification system defined.

**************************
Tables of monitoring flows
**************************

+-------------------+----------------------------------+------------+-----------+----------------------------------+
| From              | To                               | Protocol   | Port      | Application                      |
+===================+==================================+============+===========+==================================+
| Central server    | Poller                           | SSH        | TCP 22    | Export of Centreon configuration |
+-------------------+----------------------------------+------------+-----------+----------------------------------+
| Poller            | Central server                   | BBDO       | TCP 5669  | Transfer of collected data       |
+-------------------+----------------------------------+------------+-----------+----------------------------------+
| Poller            | Network equipment, servers, etc. | SNMP       | UDP 161   | Monitoring                       |
+-------------------+----------------------------------+------------+-----------+----------------------------------+
| Network equipment | Poller                           | Trap SNMP  | UDP 162   | Monitoring                       |
+-------------------+----------------------------------+------------+-----------+----------------------------------+
| Poller            | Servers                          | NRPE       | TCP 5666  | Monitoring                       |
+-------------------+----------------------------------+------------+-----------+----------------------------------+
| Poller            | Servers                          | NSClient++ | TCP 12489 | Monitoring                       |
+-------------------+----------------------------------+------------+-----------+----------------------------------+

.. note::
    If the Centreon server is a poller too, do not forget to open monitoring flows.

.. note::
    Other flows can be necessary to monitor databases, access to API, or
    applicative ports.
