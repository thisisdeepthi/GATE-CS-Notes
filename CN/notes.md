# CN notes

## MAC AND IP Address

[![image.png](https://i.postimg.cc/8CTZ4LBY/image.png)](https://postimg.cc/K1s7vkW7)

## IPv6 header

[![image.png](https://i.postimg.cc/zfX2Fnqf/image.png)](https://postimg.cc/21MxzLbp)

- Next header => points to the extension header if present
- Extension header => to rectify the limitations of ipv4

### Limitaions of ipv4 overcome by ipv6

[![image.png](https://i.postimg.cc/0j2N8Xvs/image.png)](https://postimg.cc/mzJ4jwhX)

## Congestion

- the msg traffic is so heavy which slows down the network response time

## TCP congestion control

- by reducing the sender window size which depends on receiver window and congestion window size
- three phases

  - Slow start
  - Congestion avoidance
  - Congestion Detection

1. Slow start

- sets CWS = 1(Max segment size)
- on receiving each ack, inc cws by 1 MSS
- cws inc exponentially
- CWS doubles on each round trip time and inc by 1 MSS on each ack

```
CWS = CWS + MSS
```

2. Congestion Avoidance

- CWS inc to avoid congestion
- on each ack, inc CWS by 1

```
CWS = CWS + 1
```

3. Congestion Detection

- case 1: Detection on time out
- case 2: Detection on 3 duplicate ack

## Wrap around time in tcp

- unique number ti each data byte for identification is called sequence number
- seq num is 32 bit field
- Max number of possbile seq num is 2^32
- But this doesn't imply that only 2^32 bytes of data can be sent using tcp
- After all the seq num are used and more data is to be sent, then the deq num can be wrapped arounf and used again from the start. this is called wrap around time
- it depends on the bandwidth

```
Wrap around time = 2^32/bandwidth
```
