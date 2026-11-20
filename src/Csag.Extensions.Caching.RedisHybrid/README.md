# Csag.Extensions.Caching.RedisHybrid

Strongly typed caching with enum cache identifiers instead of magic strings, for applications that run as several instances with Redis. Each instance keeps a local in-memory cache in front of Redis, and Redis pub/sub keeps the local caches in sync ([Foundatio.Redis](https://github.com/FoundatioFx/Foundatio.Redis)). Values are serialized with MessagePack.

## Installation

```bash
dotnet add package Csag.Extensions.Caching.RedisHybrid
```

## Usage

```csharp
public enum MyCacheId
{
    UserProfile = 0,
}

services.AddRedisHybridCache("localhost:6379");
```

An overload takes an existing `IConnectionMultiplexer`, so the cache can share the connection with other Redis services. Then inject `IDistributedCache<MyCacheId>`:

```csharp
await cache.SetAsync(MyCacheId.UserProfile, userId.ToString(), profile);
var cached = await cache.GetAsync<UserProfile>(MyCacheId.UserProfile, userId.ToString());
```

The [repository README](https://github.com/collana-solutions/Csag.Extensions.Caching#readme) describes all options, such as `SchemaVersion`, `EnvironmentPrefix` and the `[CacheKey]` attribute.
