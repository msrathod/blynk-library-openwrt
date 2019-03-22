# Blynk OpenWRT package

Build from source:

```bash
echo "src-git blynkClient git://github.com/msrathod/blynk-library-openwrt.git" >> ./feeds.conf
./scripts/feeds update -a
./scripts/feeds install -p blynkClient -a
make menuconfig
```
### C++ client

Select in menuconfig: ```Network -> Blynk -> blynkClient```

**C++** example:
```cpp
#include <BlynkApiLinux.h>
static BlynkTransportSocket blynkTransport;
BlynkSocket Blynk(blynkTransport);

const char* AUTH = "YourAuthToken";

BLYNK_WRITE(V1) {
    printf("Got a value: %s\n", param[0].asStr());
}

int main(int argc, char* argv[]) {
    Blynk.begin(AUTH);

    while (true) {
        Blynk.run();
    }

    return 0;
}
```

## Build OpenWRT image:
```bash
make -j 8
```

## Build just Blynk:
```
make package/blynkClient/compile V=s
```

For a rebuild:
```
make package/blynkClient/{clean,compile,install} V=s
```
