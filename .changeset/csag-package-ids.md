---
"@collana-solutions/csag-extensions-caching-abstractions": major
"@collana-solutions/csag-extensions-caching-distributed": major
"@collana-solutions/csag-extensions-caching-inmemory": major
"@collana-solutions/csag-extensions-caching-redishybrid": major
---

The packages move to new IDs and namespaces. The API and the behavior are the same as in 3.0.0.

**New package IDs:**

| Up to 3.0.0 | From 4.0.0 |
| --- | --- |
| `Neolution.Extensions.Caching.Abstractions` | `Csag.Extensions.Caching.Abstractions` |
| `Neolution.Extensions.Caching.Distributed` | `Csag.Extensions.Caching.Distributed` |
| `Neolution.Extensions.Caching.InMemory` | `Csag.Extensions.Caching.InMemory` |
| `Neolution.Extensions.Caching.RedisHybrid` | `Csag.Extensions.Caching.RedisHybrid` |

**To migrate:**

1. Replace each `Neolution.Extensions.Caching.*` package reference with the `Csag.Extensions.Caching.*` package of the same name, at 4.0.0 or later.
2. Change the namespaces: `using Neolution.Extensions.Caching.Abstractions;` becomes `using Csag.Extensions.Caching.Abstractions;`, and the same for `.Distributed`, `.InMemory` and `.RedisHybrid`. The registration methods (`AddInMemoryCache`, `AddSerializedDistributedCache`, `AddRedisHybridCache`) stay in the `Microsoft.Extensions.DependencyInjection` namespace.
3. Coming from 2.x: also follow `docs/MIGRATION_GUIDE_V3.md` for the breaking changes of 3.0.0.

Cache keys and the serialized format do not change, so entries written by 3.0.0 stay readable.

The `Neolution.Extensions.Caching.*` IDs get deprecated on nuget.org, with the `Csag.Extensions.Caching.*` packages as the alternates. Their existing versions stay available, but they get no new releases.
