# parse_RSRP_no_time

online tool => https://dustinchen26.github.io/parse_RSRP_no_time

## Example
```
【How to use】
    1. MobaXterm Session -> SSH -> Termnial settings -> Select "Log terminal output to": _DesktopDir_
	2. ssh into CPE. ex: 10.205.164.10
	3. use below command to read at+bnrinfo: read every 60 sec, until 3600 sec
	   start_time=$(date +%s); while [ $(( $(date +%s) - start_time )) -lt 3600 ]; do echo -ne "$(date) - "; echo -ne "at+bnrinfo\r\n" | microcom -t 1000 /dev/ttyUSB1 | grep -E "dBm|bnrinfo"; sleep 60; done
	4. paste the _DesktopDir_ output file content below to parse

【Example Input】	
root@AtopTechnologies:~# start_time=$(date +%s); while [ $(( $(date +%s) - start_time )) -lt 3600 ]; do echo -ne "$(date) - "; echo -ne "at+bnrinfo\r\n" | microcom -t 1000 /dev/ttyUSB1 | grep -E "dBm|bnrinfo"; sleep 1; done
Fri Mar 15 11:49:57 CST 2024 - at+bnrinfo
physical cell ID:1, averaged PUSCH TX power :19 dBm, averaged PUCCH TX power :-255 dBm, 
RSRQ -11 dB, RSRP -84 dBm,SINR 31 dB
RX0 power: -73 dBm,ecio: -10 dB, rsrp: -83 dBm, phase: 0 degree, sinr: 31 dB
RX1 power: -73 dBm,ecio: -10 dB, rsrp: -84 dBm, phase: 0 degree, sinr: 31 dB
RX2 power: -77 dBm,ecio: -10 dB, rsrp: -88 dBm, phase: 0 degree, sinr: 30 dB
RX3 power: -82 dBm,ecio: -10 dB, rsrp: -93 dBm,phase: 0 degree,sinr: 24 dB

【Output】
Time	PUSCH TX power	RSRP	SINR	RX0_rsrp	RX1_rsrp	RX2_rsrp	RX3_rsrp
Fri Mar 15 11:49:57 CST 2024	19 dBm	-84 dBm	31 dB	-83 dBm	-84 dBm	-88 dBm	-93 dBm

```
