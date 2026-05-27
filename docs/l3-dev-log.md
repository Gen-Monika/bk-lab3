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
- Migrated selectable visual backgrounds and the draggable desktop pet interaction from the earlier labs.

## Verification

- `python manage.py check`: OK
- `BKPAAS_ENVIRONMENT=test python manage.py test jobs`: OK

## Maintenance Update

- Expanded JOB execution status parsing so terminated, cancelled, stopping, string-based, and unmapped numeric statuses no longer render as `unknown` in Execution Records.
- Added regression coverage for refreshing a terminated JOB execution record.
- Added automatic refresh for active JOB records on page load, timer ticks, and tab visibility recovery.
- Added result backfill so successful JOB refreshes pull step logs into File Results and local record summaries.
- Added local archive controls for File Results and Execution Records; archived items are visually separated with a light amber background and can be restored.
- Added structured JOB script templates under `docs/job_scripts/`; scripts emit `BK_JOB_RESULT={...}` so SaaS can show file list, count, and total size instead of a plain completion summary.
- Added a unified structured JOB script that supports both search and backup by detecting whether `backup_path` is provided, which fits a single-script JOB plan.
- Removed the front-end three-item cap from File Results so all recent search and backup summaries returned by the records API remain visible after page refresh.
