# janus webrtc server Dockerfile

Default Work Volume : /opt/janus

## Usage


The following example equal `/opt/janus/bin/janus `.
```yml

docker run --name janus -v ~/janus:/opt/janus -d yousky/janus-webrtc-server:20190130-centos7.6.1810 /opt/janus/bin/janus --nat-1-1=192.168.0.16 --rtp-port-range=40000-40500

```


See also [janus docs](https://janus.conf.meetecho.com/docs/).

## License
Released under the [MIT license](http://opensource.org/licenses/MIT).
