# DEBIAN_PKG_PRACTICE   
Debian 패키징   

### DEBIAN/control

### abort 옵션   
- abort-upgrade: 이 옵션은 패키지 업그레이드 작업을 중단합니다. 패키지 업그레이드 중 문제가 발생하면 이 옵션을 사용하여 업그레이드 작업을 중지하고 이전 버전으로 되돌릴 수 있습니다.   
- abort-remove: 이 옵션은 패키지 삭제 작업을 중단합니다. 패키지 삭제 중 문제가 발생하면 이 옵션을 사용하여 삭제 작업을 중지하고 이전 상태로 되돌릴 수 있습니다.   
- abort-deconfigure: 이 옵션은 패키지 구성 작업을 중단합니다. 패키지 구성 중 문제가 발생하면 이 옵션을 사용하여 구성 작업을 중지하고 이전 상태로 되돌릴 수 있습니다.   
이러한 옵션은 패키지 관리 작업을 수행하는 도중 문제가 발생할 경우 사용할 수 있습니다. 이를 통해 문제를 해결하고 시스템을 안정적인 상태로 되돌릴 수 있습니다.   
- Ex)   
```
#!/bin/bash
############################################################
# postinst script
############################################################

set -e

case "$1" in
    configure)
                echo "configure in postinst"
        ;;
        abort-upgrade|abort-remove|abort-deconfigure)
                echo "Abort in postinst!"
                exit 1
                ;;
    *)
        echo "postinst called with unknown argument \`$1'" >&2
        exit 1
        ;;
esac

exit
```
