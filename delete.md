---
layout: default
title: Delete s3
---


```python
def delete(fh, **kwargs) -> bool:
    try:
        if fh.delete(kwargs.get('source_file_path')):
            logger.info(f'file: {kwargs.get("source_file_path")} deleted successfully')
            return True
    except S3FileDeleteError as e:
        logger.error(f'file deletion failed with an error: {str(e)}')
        raise e
    return False
```