---
layout: default
title: Download s3
---


```python
def download(fh, **kwargs) -> bool:
    try:
        if kwargs.get('recursive', False) and fh.download(kwargs.get('source_file_path'),
                                                          kwargs.get('download_to_file_path')):
            logger.info(
                f'file: {kwargs.get("source_file_path")} downloaded to path: {kwargs.get("download_to_file_path")}')
        elif fh.download_folder(kwargs.get('source_file_path'), kwargs.get('download_to_file_path')):
            logger.info(
                f'folder: {kwargs.get("source_file_path")} downloaded to path: {kwargs.get("download_to_file_path")}')
        return True
    except S3FileDownloadError as e:
        logger.error(f'file download failed with an error: {str(e)}')
        raise e
```