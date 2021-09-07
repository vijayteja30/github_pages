---
layout: default
title: List Files s3
---

```python
def list_files(fh, **kwargs) -> list:
    try:
        if res := fh.list_files(kwargs.get("prefix")):
            res = [obj.key for obj in res]
            logger.info(f'list of keys matching given prefix: {res}')
            return res
    except S3ListFilesError as e:
        logger.error(f'error occurred while getting the file list: {str(e)}')
```