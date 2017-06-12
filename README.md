# NEventLite_Core
NEventLite fork targeting the .NET Standard framework. This is the source for the framework only. Storage providers have not been ported yet and you will need to implement your own (Very easily) by using the following interfaces. 

```csharp
public interface IEventStorageProvider
{
	Task<IEnumerable<IEvent>> GetEventsAsync(Type aggregateType, Guid aggregateId, int start, int count);
	Task<IEvent> GetLastEventAsync(Type aggregateType, Guid aggregateId);
	Task CommitChangesAsync(AggregateRoot aggregate);
}

public interface ISnapshotStorageProvider
{
    	int SnapshotFrequency { get; }
    	Task<Snapshot.Snapshot> GetSnapshotAsync(Type aggregateType, Guid aggregateId);
    	Task SaveSnapshotAsync(Type aggregateType, Snapshot.Snapshot snapshot);
}
 ```

# Full version targetting the .NET framework can be found at https://github.com/dasiths/NEventLite
NEventLite is a light weight .NET framework for Event Sourcing with support for custom Event and Snapshot Stores (EventStore, Redis, SQL Server or Custom) written in C#.
