---
id: doc_app_configuration
sidebar_label: App Configuration
sidebar_position: 1
---

# app_configuration

## Schema AppConfiguration

AppConfiguration is a developer-centric definition that describes how to run an Application.<br />This application model builds upon a decade of experience at AntGroup running super large scale internal developer platform, combined with best-of-breed ideas and practices from the community.

### Attributes

#### workload: [Service](workload/doc_job.md#schema-job) \| [Job](workload/doc_job.md#schema-job)
  `required`.
  Workload defines how to run your application code. Currently supported workload profile includes Service and Job.
<details><summary>Service</summary>

- **containers: [[Container](internal/container/doc_container.md#schema-container)]**
  `required`.
  Containers defines a list of containers belonging to the same workload.
  - **image: str**
    `required`.
    Image refers to the Docker image name to run for this container. More info: https://kubernetes.io/docs/concepts/containers/images
  - **command: [str]**
    `optional`.
    Entrypoint array. Not executed within a shell. Command will overwrite the ENTRYPOINT value set in the Dockfile, otherwise the Docker image's ENTRYPOINT is used if this is not provided.
  - **files: [[FileSpec](internal/container/doc_container.md#schema-filespec)]**
    `optional`.
    Entrypoint array. Not executed within a shell. Command will overwrite the ENTRYPOINT value set in the Dockfile, otherwise the Docker image's ENTRYPOINT is used if this is not provided.
    - **mode: str**
      `required`.
      Mode bits used to set permissions on this file, must be an octal value between 0000 and 0777 or a decimal value between 0 and 511
    - **content: str**
      `required`.
      File content in plain text.
    - **contentFrom: str**
      `required`.
      Source for the file content, reference to a secret of configmap value.	
  - **livenessProbe: [Probe](workload/doc_service.md#schema-probe)**
    `optional`.
    LivenessProbe indicates if a running process is healthy. Container will be restarted if the probe fails.
    - **probeHandler: [Exec](workload/doc_service.md#schema-Exec) | [Http](workload/doc_service.md#schema-http) | [Tcp](workload/doc_service.md#schema-tcp)**
      `required`.
      The action taken to determine the alive or health of a container
      <details><summary>Exec</summary>
      Exec describes a "run in container" action.
      <ul>
        <li><strong>command: [str]</strong></li>
        `required`.
        Command is the command line to execute inside the container.
      </ul>
      </details>
      <details><summary>Http</summary>
      Http describes an action based on HTTP Get requests.
      <ul>
        <li><strong>url: str</strong></li>
        `required`.
        The full qualified url to send HTTP requests.
        <li><strong>headers: &#123;str:str&#125;</strong></li>
        `optional`.
        Collection of custom headers to set in the request.
      </ul>
      </details>
      <details><summary>TCP</summary>
      Tcp describes an action based on opening a socket.
      <ul>
        <li><strong>url: [str]</strong></li>
        `required`.
        The full qualified url to open a socket.
      </ul>
      </details>
    - **initialDelaySeconds: int**
      `optional`.
      Number of seconds after the container has started before liveness probes are initiated.
    - **timeoutSeconds: int**
      `optional`.
      The number of seconds after which the probe times out. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
    - **periodSeconds: int**
      `optional`.
      How often (in seconds) to perform the probe.	
    - **successThreshold: int**
      `optional`.
      Minimum consecutive successes for the probe to be considered successful after having failed.
    - **failureThreshold: int**
      `optional`.
      Minimum consecutive failures for the probe to be considered failed after having succeeded.
  - **readinessProbe: [Probe](workload/doc_service.md#schema-probe)**
    `optional`.
    ReadinessProbe indicates whether an application is available to handle requests.
    - **probeHandler: [Exec](workload/doc_service.md#schema-Exec) | [Http](workload/doc_service.md#schema-http) | [Tcp](workload/doc_service.md#schema-tcp)**
      `required`.
      The action taken to determine the alive or health of a container
      <details><summary>Exec</summary>
      Exec describes a "run in container" action.
      <ul>
        <li><strong>command: [str]</strong></li>
        `required`.
        Command is the command line to execute inside the container.
      </ul>
      </details>
      <details><summary>Http</summary>
      Http describes an action based on HTTP Get requests.
      <ul>
        <li><strong>url: str</strong></li>
        `required`.
        The full qualified url to send HTTP requests.
        <li><strong>headers: &#123;str:str&#125;</strong></li>
        `optional`.
        Collection of custom headers to set in the request.
      </ul>
      </details>
      <details><summary>TCP</summary>
      Tcp describes an action based on opening a socket.
      <ul>
        <li><strong>url: [str]</strong></li>
        `required`.
        The full qualified url to open a socket.
      </ul>
      </details>
    - **initialDelaySeconds: int**
      `optional`.
      Number of seconds after the container has started before liveness probes are initiated.
    - **timeoutSeconds: int**
      `optional`.
      The number of seconds after which the probe times out. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
    - **periodSeconds: int**
      `optional`.
      How often (in seconds) to perform the probe.	
    - **successThreshold: int**
      `optional`.
      Minimum consecutive successes for the probe to be considered successful after having failed.
    - **failureThreshold: int**
      `optional`.
      Minimum consecutive failures for the probe to be considered failed after having succeeded.
  - **startupProbe: [Probe](workload/doc_service.md#schema-probe)**
    `optional`.
    StartupProbe indicates that the container has started for the first time.
    Container will be restarted if the probe fails.
    - **probeHandler: [Exec](workload/doc_service.md#schema-Exec) | [Http](workload/doc_service.md#schema-http) | [Tcp](workload/doc_service.md#schema-tcp)**
      `required`.
      The action taken to determine the alive or health of a container
      <details><summary>Exec</summary>
      Exec describes a "run in container" action.
      <ul>
        <li><strong>command: [str]</strong></li>
        `required`.
        Command is the command line to execute inside the container.
      </ul>
      </details>
      <details><summary>Http</summary>
      Http describes an action based on HTTP Get requests.
      <ul>
        <li><strong>url: str</strong></li>
        `required`.
        The full qualified url to send HTTP requests.
        <li><strong>headers: &#123;str:str&#125;</strong></li>
        `optional`.
        Collection of custom headers to set in the request.
      </ul>
      </details>
      <details><summary>TCP</summary>
      Tcp describes an action based on opening a socket.
      <ul>
        <li><strong>url: [str]</strong></li>
        `required`.
        The full qualified url to open a socket.
      </ul>
      </details>
    - **initialDelaySeconds: int**
      `optional`.
      Number of seconds after the container has started before liveness probes are initiated.
    - **timeoutSeconds: int**
      `optional`.
      The number of seconds after which the probe times out. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
    - **periodSeconds: int**
      `optional`.
      How often (in seconds) to perform the probe.	
    - **successThreshold: int**
      `optional`.
      Minimum consecutive successes for the probe to be considered successful after having failed.
    - **failureThreshold: int**
      `optional`.
      Minimum consecutive failures for the probe to be considered failed after having succeeded.
  - **lifecycle: [Lifecycle](workload/doc_service.md#schema-lifecycle)**
    `optional`.
    Lifecycle refers to actions that the management system should take in response to container lifecycle events.
    - **preStop: [Exec](workload/doc_service.md#schema-Exec) | [Http](workload/doc_service.md#schema-http)**
      `optional`.
      The action to be taken before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks
      <details><summary>Exec</summary>
      Exec describes a "run in container" action.
      <ul>
        <li><strong>command: [str]</strong></li>
        `required`.
        Command is the command line to execute inside the container.
      </ul>
      </details>
      <details><summary>Http</summary>
      Http describes an action based on HTTP Get requests.
      <ul>
        <li><strong>url: str</strong></li>
        `required`.
        The full qualified url to send HTTP requests.
        <li><strong>headers: &#123;str:str&#125;</strong></li>
        `optional`.
        Collection of custom headers to set in the request.
      </ul>
      </details>
    - **postStart: [Exec](workload/doc_service.md#schema-Exec) | [Http](workload/doc_service.md#schema-http)**
      `optional`.
      The action to be taken after a container is created. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks
      <details><summary>Exec</summary>
      Exec describes a "run in container" action.
      <ul>
        <li><strong>command: [str]</strong></li>
        `required`.
        Command is the command line to execute inside the container.
      </ul>
      </details>
      <details><summary>Http</summary>
      Http describes an action based on HTTP Get requests.
      <ul>
        <li><strong>url: str</strong></li>
        `required`.
        The full qualified url to send HTTP requests.
        <li><strong>headers: &#123;str:str&#125;</strong></li>
        `optional`.
        Collection of custom headers to set in the request.
      </ul>
      </details>
- **replicas: int = 2**
  `required`.
  Number of container replicas based on this configuration that should be ran.
- **ports: [Port](internal/network/doc_port.md#schema-port)**
  `optional`.
  Ports defines a list of ports that should be exposed on each container.
- **secrets: [Secret](internal/network/doc_port.md#schema-port)**
  `optional`.
- **labels: {str: str}**
  `optional`.
  Labels are key/value pairs that are attached to the workload.
- **annotations: {str: str}**
  `optional`.
  Annotations are key/value pairs that attach arbitrary non-identifying metadata to the workload.
- **type: "Deployment" | "CollaSet"**
  `optional`.
  Type represents the type of workload used by this Service. Currently, it supports several types, including Deployment and CollaSet.

</details>

<details><summary>Job</summary>todo job</details>

#### opsRule: [trait.OpsRule](trait/doc_opsrule.md#schema-opsrule)
optional.
OpsRule specifies collection of rules that will be checked for Day-2 operation.<details><summary>OpsRule</summary>todo opsrule</details>

#### database: [Database](trait/doc_opsrule.md#schema-opsrule) 
optional. 
<details><summary>Database</summary>todo</details>

#### labels: {str: str}
optional. 

#### annotations: {str: str}
optional. 

### Examples
```python
# Instantiate an App with a long-running service and its image is "nginx:v1"

import catalog.models.schema.v1 as ac
import catalog.models.schema.v1.workload as wl
import catalog.models.schema.v1.workload.container as c
import catalog.models.schema.v1.accessories.database as db
import catalog.models.schema.v1.accessories.monitoring as m
import catalog.models.schema.v1.accessories.trait as t

appConfiguration = ac.AppConfiguration {
    workload: wl.Service {
        containers: {
            "nginx": c.Container {
                image: "nginx:v1"
            }
        }
        type: "CollaSet"
    }
    opsRule: t.OpsRule {
        maxUnavailable: "30%"
    }
    database: db.Database {
        type: "aws"
        engine: "mysql"
        version: "5.7"
        instanceType: "db.t3.micro"
    }
    monitoring: m.Prometheus{
        interval:       "30s"
        timeout:        "15s"
        path:           "/metrics"
        port:           "web"
        scheme:         "http"
    }
}
```

<!-- Auto generated by kcl-doc tool, please do not edit. -->
