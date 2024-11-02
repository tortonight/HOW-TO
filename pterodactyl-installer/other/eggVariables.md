# Default Egg Variables

:::tip
These are the default variables that will always be available in the install script, startup, and parser.
:::

## Default Egg Variables

| Variable | Description | Example |
|----------|-------------|---------|
| TZ       | Time Zone set from panels `.env` |  `Etc/UTC` |
| STARTUP  | Startup command of the egg | `./Process` |
| SERVER_MEMORY | Memory available for the server in MB | `512` |
| SERVER_IP | Default ip of the server | `127.0.0.1` |
| SERVER_PORT | Primary Server Port | `27015` |
| P_SERVER_LOCATION | Location of the server | `Example Location` |
| P_SERVER_UUID | UUID of the server | `539fdca8-4a08-4551-a8d2-8ee5475b50d9` |
| P_SERVER_ALLOCATION_LIMIT | Limit of allocations allowed for the server | `0.000000` |
| USER | User that executes the startup command in the server | `container` |
| HOME | Home path of the container user | `/home/container` |

