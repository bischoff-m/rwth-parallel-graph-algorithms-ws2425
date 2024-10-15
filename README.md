# RWTH Software Lab: Parallel Graph Algorithms WS24-25

## Links

[STCE Chair Software Lab
Description](https://www.stce.rwth-aachen.de/teaching/winter-2024-25/software-lab-parallel-graph-algorithms)

[Zotero Group](https://www.zotero.org/groups/5682542/parallel_graph_algorithms)

### Installing

You need to have CMake and OpenMPI installed. If you are using Ubuntu, you can
install them with the following command:

```shell
sudo apt-get install cmake openmpi-bin openmpi-common libopenmpi-dev
```

### Building

To build the project, run the following commands.

```shell
cmake -S . -B ./build
cmake --build ./build
```

### Running

Then use [OpenMPI](https://docs.open-mpi.org/en/v5.0.x/launching-apps/quickstart.html) to run the program.

```shell
mpirun -n 4 build/cologra
```

> [!NOTE]
> If you are using a Linux shell, you can use the scripts at `./cmd` as
> shortcuts. E.g. `source cmd/build.sh`

## Editor Setup

If you are using CLion, you can use [this
setup](https://www.jetbrains.com/help/clion/openmpi.html).

For VS Code you can install the [CMake Tools
extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)
and GDB.

```shell
sudo apt-get install gdb
```

`.vscode/tasks.json`

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "type": "shell",
      "label": "CMake build",
      "command": "sh",
      "args": ["cmd/build.sh"],
      "options": {
        "cwd": "${workspaceFolder}"
      },
      "problemMatcher": ["$gcc"],
      "group": {
        "kind": "build",
        "isDefault": true
      }
    }
  ]
}
```

`.vscode/launch.json`

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Build and Debug",
      "type": "cppdbg",
      "request": "launch",
      "program": "${workspaceFolder}/build/cologra",
      "cwd": "${workspaceFolder}",
      "externalConsole": false,
      "showDisplayString": true,
      "preLaunchTask": "CMake build",
      "stopAtEntry": false,
      "miDebuggerPath": "/usr/bin/gdb"
    }
  ]
}
```

## Notes

I wrote some notes using [Quarto](https://quarto.org/docs/get-started/). For
Ubuntu 18+/Debian 10+ install it using:

```shell
wget https://github.com/quarto-dev/quarto-cli/releases/download/v1.5.57/quarto-1.5.57-linux-amd64.deb
sudo dpkg -i quarto-1.5.57-linux-amd64.deb
quarto install tinytex
```

Then you can build or preview (with live reload) the notes using:

```shell
quarto render ./notes/index.qmd
```

```shell
quarto preview ./notes/index.qmd
```
