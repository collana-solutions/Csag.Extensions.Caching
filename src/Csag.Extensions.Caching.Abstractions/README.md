# Csag.Extensions.Caching.Abstractions

The interfaces and base classes of [Csag.Extensions.Caching](https://github.com/collana-solutions/Csag.Extensions.Caching): strongly typed caching with enum cache identifiers instead of magic strings.

Applications usually install one of the implementations, which bring this package along:

| Package | For |
| --- | --- |
| `Csag.Extensions.Caching.InMemory` | A single instance, on top of `Microsoft.Extensions.Caching.Memory` |
| `Csag.Extensions.Caching.Distributed` | Any registered `IDistributedCache` provider, with MessagePack serialization |
| `Csag.Extensions.Caching.RedisHybrid` | Several instances with Redis, a local cache in front of it and pub/sub to keep them in sync |

## Contents

- `IMemoryCache<TCacheId>` and `IDistributedCache<TCacheId>`: the cache operations, keyed by an enum value and an optional string key. `IDistributedCache<TCacheId>` adds async variants.
- `MemoryCache<TCacheId>` and `DistributedCache<TCacheId>`: base classes that build the cache keys, for your own implementations.
- `CacheEntryOptions`: absolute and sliding expiration of an entry.
- `[CacheKey("...")]`: a fixed key for an enum member, so renaming the member keeps the distributed cache entries.

The [repository README](https://github.com/collana-solutions/Csag.Extensions.Caching#readme) describes the setup and all options.
