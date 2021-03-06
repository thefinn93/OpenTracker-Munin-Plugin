# Munin Plugin for OpenTracker

Munin plugin for graphing information out of OpenTracker

OpenTracker: http://erdgeist.org/arts/software/opentracker/

Munin: http://munin-monitoring.org


## What does this plugin do?

This plugin graphs the stats information which come out of OpenTracker.


## Installation

*This was tested against Munin v1.4.x (Master / Client) but should be compatible with v1.2.x*

1) Install the dependencies:
 * `File::Basename`
 * `LWP::UserAgent`
2) Inform Munin of plugin dependencies, add necessary options. In `/etc/munin/plugin-conf.d/opentracker`, configure any options that may be needed. These are the default options:
```
[opentracker*]
env.host 127.0.0.1
env.port 6969
env.uri /stats
```
3) Let's see if munin can detect and use the plugin with its internal calls.
```
munin-node-configure --suggest | grep opentracker_
```
Should return this if everything checks out...
```
opentracker_ | no | yes (conn peer scrp syncs tcp4 torr udp4)
```
4) Let's see what munin thinks our symlinks should look like for plugin execution.
```
munin-node-configure --suggest --shell | grep opentracker_
```
Should return this if everything checks out...
```bash
ln -s '/usr/share/munin/plugins/opentracker_' '/etc/munin/plugins/opentracker_conn'
ln -s '/usr/share/munin/plugins/opentracker_' '/etc/munin/plugins/opentracker_peer'
ln -s '/usr/share/munin/plugins/opentracker_' '/etc/munin/plugins/opentracker_scrp'
ln -s '/usr/share/munin/plugins/opentracker_' '/etc/munin/plugins/opentracker_syncs'
ln -s '/usr/share/munin/plugins/opentracker_' '/etc/munin/plugins/opentracker_tcp4'
ln -s '/usr/share/munin/plugins/opentracker_' '/etc/munin/plugins/opentracker_torr'
ln -s '/usr/share/munin/plugins/opentracker_' '/etc/munin/plugins/opentracker_udp4'
```
5) Restart munin-node

# Information
If you'd like to learn further about the plugin, there is more documentation stored in the file as POD, you can view this info with perldoc.
* [Source Code](https://github.com/mhwest13/OpenTracker-Munin-Plugin)
* [Issues](https://github.com/mhwest13/OpenTracker-Munin-Plugin/issues)
* [Further Help](http://munin-monitoring.org/wiki/HowToGetHelp)
