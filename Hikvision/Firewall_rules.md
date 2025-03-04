### Ports used for incoming traffic (to manage camera) 

| state     | protocol | port number | description      |
|-----------|----------|-------------|------------------|
| mandatory | tcp      | 80          | http             |
| mandatory | tcp      | 443         | https            |
| mandatory | tcp+udp  | 554         | rtsp             |
| mandatory | tcp      | 7681        | websocket-video  |
| optional  | tcp      | 7070        | ?                |
| optional  | tcp      | 8554        | rtsp-alternative |

### Ports used for outgoing traffic (from camera to Hikconnect cloud)  

| state     | protocol | port number | description     |
|-----------|----------|-------------|-----------------|
| mandatory | tcp      | 80          | http            |
| mandatory | tcp+udp  | 443         | https           |
| mandatory | tcp+udp  | 53          | dns             |
| mandatory | tcp+udp  | 123         | ntp             |
| mandatory | tcp      | 8820        | ?               |
| mandatory | tcp+udp  | 8666        | cloud register  |
| mandatory | tcp+udp  | 6000-6020   | cloud           |
| mandatory | udp      | 6104-6108   | ?               |
| mandatory | udp      | 10150-10200 | camera stream   |
| mandatory | tcp      | 7000-7030   | cloud           |
| mandatory | udp      | 20000-20005 | send recordings |

### Ports used for outgoing traffic (from Hikconnect mobile app to cloud)  

| state     | protocol | port number | description        |
|-----------|----------|-------------|--------------------|
| mandatory | tcp      | 80          | http               |
| mandatory | tcp+udp  | 443         | https              |
| mandatory | tcp+udp  | 53          | dns                |
| mandatory | tcp+udp  | 554         | rtsp               |
| mandatory | tcp+udp  | 8554        | rtsp-alternative   |
| mandatory | tcp      | 7070        | ?                  |
| mandatory | tcp+udp  | 8666        | cloud register     |
| mandatory | tcp+udp  | 6000-6020   | cloud              |
| mandatory | tcp      | 6500        | ?                  |
| mandatory | tcp      | 8777        | ?                  |
| mandatory | tcp      | 8820        | ?                  |
| mandatory | udp      | 20000-20005 | receive recordings |
