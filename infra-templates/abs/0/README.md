## Rancher ABS

### Default Configuration

By default, when you using `rancher-abs` as volume driver, `rancher-abs` will help you to **create** a [20GB cloud_ssd](https://help.aliyun.com/document_detail/25513.html) disk. And after create successfully, `rancher-abs` will **format** the new disk by `mkfs.ext4`. 

**Notification!!!** Only when VPC is selected as the network type of the instance, you can use `rancher-abs` to manage Aliyun Block Storage.

```
version: '2'
services:
  foo:
    image: alpine
    stdin_open: true
    volumes:
    - bar:/data
volumes:
  bar:
    driver: rancher-abs
```

### Custom Configuration

If you are going to customize the block storage, you can pass some parameter pairs by `driver_opts`. Those supported pairs have already listed as below,  you can take more details from [here](https://help.aliyun.com/document_detail/25513.html).

```
version: '2'
services:
  foo:
    image: alpine
    stdin_open: true
    volumes:
    - bar:/data
volumes:
  bar:
    driver: rancher-abs
    driver_opts:
      diskName: <a name for disk>
      size: <20 default>
      diskCategory: <cloud_ssd default>
      snapshot_id: <disk snapshot id>
```
