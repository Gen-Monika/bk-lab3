# L3 JOB Log Backup Console Development Log

Date: 2026-05-26

## Summary

Started the third BlueKing SaaS course project for JOB-based game host log backup. The provided JOB front-end and back-end packages are Git LFS pointer files, so the implementation is based on the working L2 Django project and adds a new `jobs` app.

## Changes

- Added the `jobs` Django app and made `/jobs/` the main application page.
- Added CMDB-backed business and host loading for selecting the target host scope.
- Added JOBV3 plan list, plan detail, plan execution, execution status, and execution log service wrappers.
- Added log search and backup APIs that execute selected JOB plans with host list, search path, suffix, and backup path variables.
- Added `JobExecutionRecord` to keep local execution history and status refresh data.
- Added a standalone JOB Log Backup Console UI.
- Avoided hard-coded course sample plan IDs by selecting JOB plans from the page.

## Verification

- `python manage.py check`: OK
- `BKPAAS_ENVIRONMENT=test python manage.py test jobs`: OK
