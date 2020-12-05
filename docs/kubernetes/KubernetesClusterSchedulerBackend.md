# KubernetesClusterSchedulerBackend

`KubernetesClusterSchedulerBackend` is a [CoarseGrainedSchedulerBackend](../scheduler/CoarseGrainedSchedulerBackend.md) for [Kubernetes](index.md).

## Creating Instance

`KubernetesClusterSchedulerBackend` takes the following to be created:

* <span id="scheduler"> [TaskSchedulerImpl](../scheduler/TaskSchedulerImpl.md)
* <span id="sc"> [SparkContext](../SparkContext.md)
* <span id="kubernetesClient"> `KubernetesClient`
* <span id="executorService"> Java's [ScheduledExecutorService]({{ java.api }}/java.base/java/util/concurrent/ScheduledExecutorService.html)
* <span id="snapshotsStore"> [ExecutorPodsSnapshotsStore](ExecutorPodsSnapshotsStore.md)
* <span id="podAllocator"> ExecutorPodsAllocator
* <span id="lifecycleEventHandler"> [ExecutorPodsLifecycleManager](ExecutorPodsLifecycleManager.md)
* <span id="watchEvents"> ExecutorPodsWatchSnapshotSource
* <span id="pollEvents"> ExecutorPodsPollingSnapshotSource

`KubernetesClusterSchedulerBackend` is created when:

* `KubernetesClusterManager` is requested for a [SchedulerBackend](KubernetesClusterManager.md#createSchedulerBackend)

## <span id="start"> Starting

```scala
start(): Unit
```

`start` is part of the [CoarseGrainedSchedulerBackend](../scheduler/CoarseGrainedSchedulerBackend.md#start) abstraction.

`start` [creates a delegation token manager](../scheduler/CoarseGrainedSchedulerBackend.md#start).

`start` requests the [ExecutorPodsAllocator](#podAllocator) to [setTotalExpectedExecutors](ExecutorPodsAllocator.md#setTotalExpectedExecutors) to [initialExecutors](#initialExecutors).

`start`...FIXME

## <span id="createDriverEndpoint"> Creating DriverEndpoint

```scala
createDriverEndpoint(): DriverEndpoint
```

`createDriverEndpoint` is part of the [CoarseGrainedSchedulerBackend](../scheduler/CoarseGrainedSchedulerBackend.md#createDriverEndpoint) abstraction.

`createDriverEndpoint` creates a [KubernetesDriverEndpoint](KubernetesDriverEndpoint.md).