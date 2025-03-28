# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Jun 11, 2023, 5:24 AM_ (_daily_ updated).

This benchmark compares the performance of npm, pnpm, Yarn Classic, and Yarn PnP (check [Yarn's benchmarks](https://yarnpkg.com/benchmarks) for any other Yarn modes that are not included here).

Here's a quick explanation of how these tests could apply to the real world:

- `clean install`: How long it takes to run a totally fresh install: no lockfile present, no packages in the cache, no `node_modules` folder.
- `with cache`, `with lockfile`, `with node_modules`: After the first install is done, the install command is run again.
- `with cache`, `with lockfile`: When a repo is fetched by a developer and installation is first run.
- `with cache`: Same as the one above, but the package manager doesn't have a lockfile to work from.
- `with lockfile`: When an installation runs on a CI server.
- `with cache`, `with node_modules`: The lockfile is deleted and the install command is run again.
- `with node_modules`, `with lockfile`: The package cache is deleted and the install command is run again.
- `with node_modules`: The package cache and the lockfile is deleted and the install command is run again.
- `update`: Updating your dependencies by changing the version in the `package.json` and running the install command again.

## Lots of Files

The app's `package.json` [here](https://github.com/pnpm/pnpm.github.io/blob/main/benchmarks/fixtures/alotta-files/package.json)

| action  | cache | lockfile | node_modules| npm | pnpm | Yarn | Yarn PnP |
| ---     | ---   | ---      | ---         | --- | ---  | ---  | ---      |
| install |       |          |             | 36.7s | 17.7s | 22.1s | 20.2s |
| install | ✔     | ✔        | ✔           | 2s | 1.4s | 695ms | n/a |
| install | ✔     | ✔        |             | 9.1s | 4.7s | 8.8s | 668ms |
| install | ✔     |          |             | 13.8s | 8.3s | 22.8s | 15.2s |
| install |       | ✔        |             | 14.7s | 14.8s | 8.9s | 670ms |
| install | ✔     |          | ✔           | 2.4s | 4s | 16s | n/a |
| install |       | ✔        | ✔           | 2s | 1.5s | 681ms | n/a |
| install |       |          | ✔           | 2.4s | 14.3s | 16.6s | n/a |
| update  | n/a | n/a | n/a | 9.4s | 7.6s | 8.7s | 16.9s |

<img alt="Graph of the alotta-files results" src="/img/benchmarks/alotta-files.svg" />