# Csag.Extensions.Caching.InMemory

Strongly typed in-memory caching with enum cache identifiers instead of magic strings, on top of `Microsoft.Extensions.Caching.Memory`. For applications that run as a single instance.

## Installation

```bash
dotnet add package Csag.Extensions.Caching.InMemory
```

## Usage

```csharp
public enum MyCacheId
{
    UserProfile = 0,
}

services.AddInMemoryCache();
```

Then inject `IMemoryCache<MyCacheId>`:

```csharp
cache.Set(MyCacheId.UserProfile, userId.ToString(), profile);
var cached = cache.Get<UserProfile>(MyCacheId.UserProfile, userId.ToString());
```

The [repository README](https://github.com/collana-solutions/Csag.Extensions.Caching#readme) describes all options and compares the implementations.
