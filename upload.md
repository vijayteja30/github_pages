---
layout: default
title: Upload s3
---

```python
def upload(fh, **kwargs) -> str:
    try:
        if path := fh.upload(kwargs.get('source_file_path'), kwargs.get('upload_to_file_path')):
            logger.info(f'file upload successful. path: {path}')
            return path
    except S3FileUploadError as e:
        logger.error(f'file upload failed with an error: {str(e)}')
        raise e
    return ''
```