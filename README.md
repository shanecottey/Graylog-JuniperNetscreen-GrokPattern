# Graylog-JuniperNetscreen-GrokPattern
A grok extractor for traffic logs from Juniper Netscreen devices


## Example Juniper Netscreen traffic logs
isg1000-A2: NetScreen device_id=0000011001000011 [Root]system-notification-00257(traffic): start_time="2015-11-11 10:02:10" duration=0 policy_id=244 service=https proto=6 src zone=Untrust dst zone=Trust action=Permit sent=0 rcvd=0 src=74.168.138.252 dst=72.72.72.72 src_port=1732 dst_port=443 src-xlated ip=1.255.20.1 port=22041 dst-xlated ip=1.244.136.50 port=443 session_id=488451 reason=Creation


## Grok extractor
start_time=%{DATA:start_time} duration=%{INT:duration} policy_id=%{INT:policy_id} service=%{DATA:service} proto=%{INT:proto} src zone=%{WORD:src_zone} dst zone=%{WORD:dst_zone} action=%{WORD:action} sent=%{INT:sent} rcvd=%{INT:rcvd} src=%{IP:src_ip} dst=%{IP:dst_ip} src_port=%{INT:src_port} dst_port=%{INT:dst_port} src-xlated ip=%{IP:scr-xlated_ip} port=%{INT:src-xlated_port} dst-xlated ip=%{IP:dst-xlated_ip} port=%{INT:dst-xlated_port} session_id=%{INT:session_id} reason=%{GREEDYDATA:reason}




I did not worry about the device_id field because the very first word of the log is the device hostname, which is automatically converted into 'source' field in Graylog.
