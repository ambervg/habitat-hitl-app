# Habitat-HITL-App
Habitat application using Human-In-The-Loop and exporting visual+textual data from testing sequence.

## Installing and using Habitat-HITL apps
These steps describe how to get going with this application from the absolute beginning. You might have already performed some of these steps, in which case you can skip over them.
1. Prepare Conda environment.
    ```
    # We require python>=3.9 and cmake>=3.14
    $ conda create -n habitat python=3.9 cmake=3.14.0
    $ conda activate habitat
    ```
2. Install habitat-lab, habitat-sim, habitat-baselines (this is a subpackage that is not installed by default) and habitat-hitl. 
    ```
    $ pip install -e habitat-lab
    $ conda install habitat-sim withbullet -c conda-forge -c aihabitat-nightly
    $ pip install -e habitat-baselines
    $ pip install -e habitat-hitl
    ```
6. Download required assets for our example HITL applications:
    ```
    python -m habitat_sim.utils.datasets_download --uids hab3-episodes habitat_humanoids hab_spot_arm ycb hssd-hab --data-path data/
    ```

## Launch commands
To start the test app, you can use the following command:
```bash
# Activate virtual environment, if not activated yet
$ conda activate habitat

# Launch the test app
$ HABITAT_SIM_LOG=warning MAGNUM_LOG=warning \
python examples/hitl/my-thesis/test.py habitat_hitl.episodes_filter='0 2 4 10:15 1000:4000:500'
```

# Configuration
As an example, the app is configured to inspect the `pop_play` Habitat baseline on the Habitat-lab `hssd_spot_human` multi-agent benchmark. See [`config/basic_viewer.yaml`](./config/basic_viewer.yaml). See also [`habitat-baselines/README.md`](../../../habitat-baselines/README.md).
