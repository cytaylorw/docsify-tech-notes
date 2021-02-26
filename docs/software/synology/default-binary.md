# Get DSM Default Binary  {docsify-ignore-all}
I followed a guide to install composer and the steps altered the default php binary without backup. But the Package Center seems to rely on the default php binary so I can not install any packages afterward. Copying the same php version bunary from other directories did not solve the problem.

## Error from Pakcage Center

<kbd>![Operation failed](/../../_media/synology/package_center__operation_failed.png)</kbd>

## Steps to get the default PHP binary
1. Download a major version of the DSM
2. Unzip the *.pat DSM file
3. Find and unzip hda1.tgz
4. Find default PHP binary in /usr/bin/php
5. Copy the binary into your DSM

## Reference
The solution is provided Synology Support.