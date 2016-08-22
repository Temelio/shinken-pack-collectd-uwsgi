# shinken-pack-collectd-uwsgi

## Description

This Shinken monitoring pack is used to manage uwsgi services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-uwsgi: Manage all default thresholds and values for services

### Services

| Service name            | Description           | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|-------------------------|-----------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| UWSGI - $KEY$ processes | Check UWSGI processes | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _uwsgi_processes           |
| UWSGI - $KEY$           | Check listening ports | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _uwsgi_listen              |

## Default values

    _uwsgi_processes    uwsgi $(uwsgi)$$(1:)$$(1:)$
    _uwsgi_listen       app port $(3031)$$(1:1)$$(1:1)$
