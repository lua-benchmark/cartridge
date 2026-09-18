# cartridge - Lua SAST benchmark snapshot

Frozen snapshot of an upstream project, republished for Lua static-analysis benchmarking.
**This is not a fork for contribution.** File issues and pull requests upstream.

## Provenance

| | |
|---|---|
| Upstream | <https://github.com/tarantool/cartridge> |
| Branch | `master` |
| Commit | `8ae92501a52f07daea4d34e81bfe674badc61bd8` |
| Snapshot taken | 2026-09-18 |
| Upstream stars at snapshot | 100 |
| Deliberately vulnerable (GOAT) | No |

The tree is byte-identical to upstream at that commit, with two exceptions: the `.git` directory
was removed and replaced by a single `initial version` commit, and this `BENCHMARK.md` was added.
No upstream file was modified, so every line number still matches upstream.

## Corpus metadata

**Project type:** Cluster management framework + admin web UI (GraphQL/HTTP API, config upload)

**Lua version:** 5.1 / LuaJIT 2.1 (Tarantool 1.10-2.11)

**Frameworks and libraries:** Tarantool (box, net.box, fiber, fio, socket), tarantool/http server, graphql-lua, frontend-core, vshard, ddl, membership, errors, checks

**Size class:** Medium (~46107 LOC)

## Taint sources of interest

Tarantool HTTP request (req:param, req:read_cached, req:read, req.headers), HTTP request body (GraphQL JSON body json.decode; multipart config upload via utils.http_read_body), HTTP headers and cookies (req.headers['authorization'], auth cookie), Command-line arguments and environment variables (arg[i], os.environ TARANTOOL_*), Local file read (fio + YAML clusterwide config), Database read (box.space)
