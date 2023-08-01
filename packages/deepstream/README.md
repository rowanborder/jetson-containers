# deepstream

<details open>
<summary><b>CONTAINERS</b></summary>
<br>

| **`deepstream`** | |
| :-- | :-- |
| &nbsp;&nbsp;&nbsp;Builds | [![`deepstream_jp46`](https://img.shields.io/github/actions/workflow/status/dusty-nv/jetson-containers/deepstream_jp46.yml?label=deepstream:jp46)](https://github.com/dusty-nv/jetson-containers/actions/workflows/deepstream_jp46.yml) [![`deepstream_jp51`](https://img.shields.io/github/actions/workflow/status/dusty-nv/jetson-containers/deepstream_jp51.yml?label=deepstream:jp51)](https://github.com/dusty-nv/jetson-containers/actions/workflows/deepstream_jp51.yml) |
| &nbsp;&nbsp;&nbsp;Requires | `L4T >=32.6` |
| &nbsp;&nbsp;&nbsp;Dependencies | [`build-essential`](/packages/build-essential) [`python`](/packages/python) [`cmake`](/packages/cmake/cmake_pip) [`numpy`](/packages/numpy) [`opencv`](/packages/opencv) [`gstreamer`](/packages/gstreamer) [`tritonserver`](/packages/tritonserver) |
| &nbsp;&nbsp;&nbsp;Dockerfile | [`Dockerfile`](Dockerfile) |
| &nbsp;&nbsp;&nbsp;Notes | https://docs.nvidia.com/metropolis/deepstream/dev-guide/text/DS_Quickstart.html |

</details>

<details open>
<summary><b>CONTAINER IMAGES</b></summary>
<br>

| Repository/Tag | Date | Arch | Size |
| :-- | :--: | :--: | :--: |
| &nbsp;&nbsp;[`dustynv/deepstream:r35.3.1`](https://hub.docker.com/r/dustynv/deepstream/tags) | `2023-07-29` | `arm64` | `6.8GB` |
| &nbsp;&nbsp;[`dustynv/deepstream:r32.7.1`](https://hub.docker.com/r/dustynv/deepstream/tags) | `2023-07-29` | `arm64` | `2.3GB` |

> <sub>Container images are compatible with other minor versions of JetPack/L4T:</sub><br>
> <sub>&nbsp;&nbsp;&nbsp;&nbsp;• L4T R32.7 containers can run on other versions of L4T R32.7 (JetPack 4.6+)</sub><br>
> <sub>&nbsp;&nbsp;&nbsp;&nbsp;• L4T R35.x containers can run on other versions of L4T R35.x (JetPack 5.1+)</sub><br>
</details>

<details open>
<summary><b>RUN CONTAINER</b></summary>
<br>

To start the container, you can use the [`run.sh`](/docs/run.md)/[`autotag`](/docs/run.md#autotag) helpers or manually put together a [`docker run`](https://docs.docker.com/engine/reference/commandline/run/) command:
```bash
# automatically pull or build a compatible container image
./run.sh $(./autotag deepstream)

# or explicitly specify one of the container images above
./run.sh dustynv/deepstream:r32.7.1

# or if using 'docker run' (specify image and mounts/ect)
sudo docker run --runtime nvidia -it --rm --network=host dustynv/deepstream:r32.7.1
```
> <sup>[`run.sh`](/docs/run.md) forwards arguments to [`docker run`](https://docs.docker.com/engine/reference/commandline/run/) with some defaults added (like `--runtime nvidia`, mounts a `/data` cache, and detects devices)</sup><br>
> <sup>[`autotag`](/docs/run.md#autotag) finds a container image that's compatible with your version of JetPack/L4T - either locally, pulled from a registry, or by building it.</sup>

To mount your own directories into the container, use the [`-v`](https://docs.docker.com/engine/reference/commandline/run/#volume) or [`--volume`](https://docs.docker.com/engine/reference/commandline/run/#volume) flags:
```bash
./run.sh -v /path/on/host:/path/in/container $(./autotag deepstream)
```
To launch the container running a command, as opposed to an interactive shell:
```bash
./run.sh $(./autotag deepstream) my_app --abc xyz
```
You can pass any options to [`run.sh`](/docs/run.md) that you would to [`docker run`](https://docs.docker.com/engine/reference/commandline/run/), and it'll print out the full command that it constructs before executing it.
</details>
<details open>
<summary><b>BUILD CONTAINER</b></summary>
<br>

If you use [`autotag`](/docs/run.md#autotag) as shown above, it'll ask to build the container for you if needed.  To manually build it, first do the [system setup](/docs/setup.md), then run:
```bash
./build.sh deepstream
```
The dependencies from above will be built into the container, and it'll be tested during.  See [`./build.sh --help`](/jetson_containers/build.py) for build options.
</details>