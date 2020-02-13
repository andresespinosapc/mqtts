# MQTTS (MQTT Typescript)

MQTTS is a MQTT library. It currently supports _MQTT 3.1.1_ but will
add support for MQTT 5 in the future.

These are the key features:

-   Multiple Transports (**TLS**, **TCP**, more to come)
-   Focus On Extensibility (using easy to extend `classes`)
-   Written in Typescript
-   **RxJS** Observables and Subjects

# Example

```typescript
import { MqttClient, TcpTransport } from 'mqtts';
const client = new MqttClient({
    // connect to the hivemq testserver
    transport: new TcpTransport({ url: 'mqtt://broker.hivemq.com:1883' }),
});
// connect
await client.connect();
// subscribe and listen to the topic
client.listen({ topic: 'mqtts/test/publish', subscribe: true }).subscribe(message => {
    console.log(message);
});
// publish to the topic
await client.publish({ topic: 'mqtts/test/publish', payload: 'hi :)' });
```