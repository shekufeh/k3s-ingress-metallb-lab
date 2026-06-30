```mermaid
%%{init: {'theme': 'neutral', 'flowchart': {'curve': 'linear'}}}%%
graph TD
%% Define main components as simple rectangular boxes
Client[Client <br> browser / curl]
MetalLB[MetalLB <br> LoadBalancer IP <br> 192.168.1.40]
Ingress[NGINX Ingress <br> Controller]

app1[app1 <br> nginx]
app2[app2 <br> httpbin]
app3[app3 <br> nginx]

%% Main traffic flow with straight lines
Client -->|HTTPS| MetalLB
MetalLB --> Ingress

%% Fan-out routing from Ingress to backend services
Ingress --> app1
Ingress --> app2
Ingress --> app3

%% Invisible link to force Routing Rules block below main diagram
app2 ~~~ RoutingRules

%% Routing rules section placed at the bottom
subgraph RoutingRules [Routing Rules]
direction TB
subgraph AppLab [app.lab.local]
direction TB
rule1[ /foo ➔ app1 ]
rule2[ /api ➔ app2 ]
end
subgraph AdminLab [admin.lab.local]
direction TB
rule3[ /value ➔ app3 ]
end
end

%% Simple black and white styling
style Client fill:#fff,stroke:#333,stroke-width:1.5px
style MetalLB fill:#fff,stroke:#333,stroke-width:1.5px
style Ingress fill:#fff,stroke:#333,stroke-width:1.5px
style app1 fill:#fff,stroke:#333,stroke-width:1.5px
style app2 fill:#fff,stroke:#333,stroke-width:1.5px
style app3 fill:#fff,stroke:#333,stroke-width:1.5px
style RoutingRules fill:#fff,stroke:#ccc,stroke-dasharray: 5 5
style AppLab fill:#fff,stroke:#fff
style AdminLab fill:#fff,stroke:#fff
