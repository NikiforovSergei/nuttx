Attempt to run sc-machine or sc-machine c-core with NuttX. Not yet successful because of problems with dependencies such as glib.

## Build

```sh
mkdir nuttxspace
cd nuttxspace
git clone -b sc_machine_connection_test https://github.com/NikiforovSergei/nuttx.git nuttx
git clone -b sc_machine_connection_test https://github.com/NikiforovSergei/nuttx-apps apps
cd apps
git git submodule update --init --recursive
cd ../nuttx
python3 -m venv ./venv
source ./venv/bin/activate
pip3 install -r requirements.txt
cd ..
cmake -B build  -DNUTTX_APPS_DIR=/home/gray/Work/Projects/nuttxspace/nuttx/ -DBOARD_CONFIG=sim:ns
cmake --build build
```

You should change config according to your needs: activate necessary app and possibly c++ support.  To change config:
```sh
cmake --build build -t menuconfig
```

To clean the build, you can do:
```sh
cmake --build build -t clean
```

## More information

You can get more information in README file of the [original NuttX repository](https://github.com/apache/nuttx/blob/master/README.md) and documentation on the [Documentation Page](https://nuttx.apache.org/docs/latest/).