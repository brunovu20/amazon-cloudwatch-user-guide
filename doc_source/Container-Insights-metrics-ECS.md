# Amazon ECS Container Insights Metrics<a name="Container-Insights-metrics-ECS"></a>

The following table lists the metrics and dimensions that Container Insights collects for Amazon ECS\. These metrics are in the `ECS/ContainerInsights` namespace\. For more information, see [Metrics](cloudwatch_concepts.md#Metric)\.

If you do not see any Container Insights metrics in your console, be sure that you have completed the setup of Container Insights\. Metrics do not appear before Container Insights has been set up completely\. For more information, see [Setting Up Container Insights](deploy-container-insights.md)\.

**Note**  
The network and disk metrics collected are cumulative per Amazon ECS task\. Because these cumulative metrics are aggregated in CloudWatch and then a `RATE` function is applied, it is expected to see spikes in those metrics\. For example, if one out of two Amazon ECS tasks in a cluster stops running, the `RATE` on the cumulative network metric will show a negative spike for that data point equal to the network metric data collected from the Amazon ECS task that has just stopped\. The CloudWatch team is aware of this behavior and is researching how best to collect, monitor, and alarm on cumulative metrics\.  
For more information about the `RATE` function, see [Metric Math Syntax and Functions](using-metric-math.md#metric-math-syntax)\.

The following metrics are available when you complete the steps in [Setting Up Container Insights on Amazon ECS for Cluster\- and Service\-Level Metrics](deploy-container-insights-ECS-cluster.md)


| Metric Name | Dimensions | Description | 
| --- | --- | --- | 
|  `ContainerInstanceCount` |  ClusterName  |  The number of EC2 instances running the Amazon ECS agent that are registered with a cluster\.  | 
|  `CpuUtilized` |  TaskDefinitionFamily, ClusterName ServiceName, ClusterName ClusterName  |  The CPU units used by tasks in the resource that is specified by the dimension set that you're using\. This metric is collected only for tasks that have a defined CPU reservation in their task definition\.   | 
|  `CpuReserved` |  TaskDefinitionFamily, ClusterName ServiceName, ClusterName ClusterName  |  The CPU units reserved by tasks in the resource that is specified by the dimension set that you're using\. This metric is collected only for tasks that have a defined CPU reservation in their task definition\.   | 
|  `DeploymentCount` |  ServiceName, ClusterName  |  The number of deployments in an Amazon ECS service\.  | 
|  `DesiredTaskCount` |  ServiceName, ClusterName  |  The desired number of tasks for an Amazon ECS service\.  | 
|  `MemoryUtilized` |  TaskDefinitionFamily, ClusterName ServiceName, ClusterName ClusterName  |  The memory being used by tasks in the resource that is specified by the dimension set that you're using\. This metric is collected only for tasks that have a defined memory reservation in their task definition\.   | 
|  `MemoryReserved` |  TaskDefinitionFamily, ClusterName ServiceName, ClusterName ClusterName  |  The memory that is reserved by tasks in the resource that is specified by the dimension set that you're using\. This metric is collected only for tasks that have a defined memory reservation in their task definition\.   | 
|  `NetworkRxBytes` |  TaskDefinitionFamily, ClusterName ServiceName, ClusterName ClusterName  |  The number of bytes received by the resource that is specified by the dimensions that you're using\. This metric is available only for containers in `bridge` network mode\. It is not available for containers in `awsvpc` network mode or `host` network mode\.  | 
|  `NetworkTxBytes` |  TaskDefinitionFamily, ClusterName ServiceName, ClusterName ClusterName  |  The number of bytes transmitted by the resource that is specified by the dimensions that you're using\. This metric is available only for containers in `bridge` network mode\. It is not available for containers in `awsvpc` network mode or `host` network mode\.  | 
|  `PendingTaskCount` |  ServiceName, ClusterName  |  The number of tasks currently in the `PENDING` state\.  | 
|  `RunningTaskCount` |  ServiceName, ClusterName  |  The number of tasks currently in the `RUNNING` state\.  | 
|  `ServiceCount` |  ServiceName  |  The number of services in the cluster\.  | 
|  `StorageReadBytes` |  TaskDefinitionFamily, ClusterName ServiceName, ClusterName ClusterName  |  The number of bytes read from storage in the resource that is specified by the dimensions that you're using\.  | 
|  `StorageWriteBytes` |  TaskDefinitionFamily, ClusterName ServiceName, ClusterName ClusterName  |  The number of bytes written to storage in the resource that is specified by the dimensions that you're using\.  | 
|  `TaskCount` |  ServiceName  |  The number of tasks running in the service\.  | 
|  `TaskSetCount` |  ServiceName, ClusterName  |  The number of task sets in the service\.  | 

The following metrics are available when you complete the steps in [Deploying the CloudWatch Agent to Collect EC2 Instance\-Level Metrics on Amazon ECS](deploy-container-insights-ECS-instancelevel.md)


| Metric Name | Dimensions | Description | 
| --- | --- | --- | 
|  `instance_cpu_limit` |  ClusterName  |  The maximum number of CPU units that can be assigned to a single EC2 Instance in the cluster\.  | 
|  `instance_cpu_reserved_capacity` |  ClusterName EC2InstanceId, ContainerInstanceId,ClusterName  |  The percentage of CPU currently being reserved on a single EC2 instance in the cluster\.  | 
|  `instance_cpu_usage_total` |  ClusterName  |  The number of CPU units being used on a Single EC2 instance in the cluster\.  | 
|  `instance_cpu_utilization` |  ClusterName EC2InstanceId, ContainerInstanceId,ClusterName  |  The total percentage of CPU units being used on a single EC2 instance in the cluster\.   | 
|  `instance_filesystem_utilization` |  ClusterName EC2InstanceId, ContainerInstanceId,ClusterName  |  The total percentage of file system capacity being used on a single EC2 instance in the cluster\.   | 
|  `instance_memory_limit` |  ClusterName  |  The maximum amount of memory, in bytes, that can be assigned to a single EC2 Instance in this cluster\.   | 
|  `instance_memory_reserved_capacity` |  ClusterName EC2InstanceId, ContainerInstanceId,ClusterName  |  The percentage of Memory currently being reserved on a single EC2 Instance in the cluster\.  | 
|  `instance_memory_utliization` |  ClusterName EC2InstanceId, ContainerInstanceId,ClusterName  |  The total percentage of memory being used on a single EC2 Instance in the cluster\.  | 
|  `instance_memory_working_set` |  ClusterName  |  The amount of memory, in bytes, being used on a single EC2 Instance in the cluster\.  | 
|  `instance_network_total_bytes` |  ClusterName  |  The total number of bytes per second transmitted and received over the network on a single EC2 Instance in the cluster\.  | 
|  `instance_number_of_running_tasks` |  ClusterName  |  The number of running tasks on a single EC2 Instance in the cluster\.  | 