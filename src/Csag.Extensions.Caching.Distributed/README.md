# Csag.Extensions.Caching.Distributed

Strongly typed distributed caching with enum cache identifiers instead of magic strings. It wraps any registered `IDistributedCache` provider, such as Redis, SQL Server or the distributed memory cache, and serializes the values with MessagePack (LZ4 compression on by default).

## Installation

```bash
dotnet add package Csag.Extensions.Caching.Distributed
```

## Usage

Register an `IDistributedCache` provider first, then the wrapper:

```csharp
public enum MyCacheId
{
    UserProfile = 0,
}

services.AddStackExchangeRedisCache(options => options.Configuration = "localhost:6379");
services.AddSerializedDistributedCache();
```

Then inject `IDistributedCache<MyCacheId>`:

```csharp
await cache.SetAsync(MyCacheId.UserProfile, userId.ToString(), profile);
var cached = await cache.GetAsync<UserProfile>(MyCacheId.UserProfile, userId.ToString());
```

The [repository README](https://github.com/collana-solutions/Csag.Extensions.Caching#readme) describes all options, such as `SchemaVersion`, `EnvironmentPrefix` and the `[CacheKey]` attribute.
