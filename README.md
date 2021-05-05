## MICRO SERVICE WITH MOLECULER

# > moicroservice-moleculer > npm init
    
    package name: (microservice-molecular)
    version: (1.0.0)
    description: microservice-molecular
    entry point: (index.js) math.service.js
    test command:
    git repository:
    keywords:
    author:
    license: (ISC)

# > moicroservice-moleculer > npm i moleculer@0.14.12

# https://moleculer.services/docs/0.14/usage.html
# Crie uma pasta chamada math 
# Dentro dela o arquivo do serviço: math.service.js

    const { ServiceBroker } = require("moleculer");

    // Create a ServiceBroker
    const broker = new ServiceBroker();

    // Define a service
    broker.createService({
        name: "math",
        actions: {
            add(ctx) {
                return Number(ctx.params.a) + Number(ctx.params.b);
            }
        }
    });

    // Start the broker
    broker.start()
        // Call the service
        .then(() => broker.call("math.add", { a: 5, b: 3 }))
        // Print the response
        .then(res => console.log("5 + 3 =", res))
        .catch(err => console.error(`Error occured! ${err.message}`));

# microservice-molecular\math > node math.service.js

[2021-03-16T22:36:24.953Z] INFO  tsp3427324-25060/BROKER: Moleculer v0.14.12 is starting...
[2021-03-16T22:36:24.956Z] INFO  tsp3427324-25060/BROKER: Namespace: <not defined>
[2021-03-16T22:36:24.956Z] INFO  tsp3427324-25060/BROKER: Node ID: tsp3427324-25060
[2021-03-16T22:36:24.958Z] INFO  tsp3427324-25060/REGISTRY: Strategy: RoundRobinStrategy
[2021-03-16T22:36:24.959Z] INFO  tsp3427324-25060/REGISTRY: Discoverer: LocalDiscoverer
[2021-03-16T22:36:24.970Z] INFO  tsp3427324-25060/BROKER: Serializer: JSONSerializer
[2021-03-16T22:36:25.042Z] INFO  tsp3427324-25060/BROKER: Validator: FastestValidator
[2021-03-16T22:36:25.053Z] INFO  tsp3427324-25060/BROKER: Registered 13 internal middleware(s).
[2021-03-16T22:36:25.094Z] INFO  tsp3427324-25060/REGISTRY: '$node' service is registered.
[2021-03-16T22:36:25.112Z] INFO  tsp3427324-25060/REGISTRY: 'math' service is registered.
[2021-03-16T22:36:25.122Z] INFO  tsp3427324-25060/$NODE: Service '$node' started.
[2021-03-16T22:36:25.135Z] INFO  tsp3427324-25060/MATH: Service 'math' started.
[2021-03-16T22:36:25.144Z] INFO  tsp3427324-25060/BROKER: ✔ ServiceBroker with 2 service(s) is started successfully in 62ms.
5 + 3 = 8
[2021-03-16T22:36:25.196Z] INFO  tsp3427324-25060/$NODE: Service '$node' stopped.
[2021-03-16T22:36:25.206Z] INFO  tsp3427324-25060/MATH: Service 'math' stopped.
[2021-03-16T22:36:25.225Z] INFO  tsp3427324-25060/BROKER: ServiceBroker is stopped. Good bye.

