# JOB Log Backup Console

BlueKing Django SaaS course project for JOB-based game host log search and backup.

## Features

- Business and host loading through BlueKing CMDB.
- JOBV3 plan list and plan detail API integration.
- Search selected hosts for log files by directory and suffix.
- Trigger backup plans for selected hosts and record execution history.
- Refresh JOB instance status and link back to BlueKing JOB.
- Clear API error reporting without fabricated execution results.

## Routes

- `/jobs/`: log backup console
- `/jobs/api/businesses/`: CMDB business list
- `/jobs/api/hosts/?bk_biz_id=2`: CMDB host list
- `/jobs/api/plans/?bk_biz_id=2`: JOB plan list
- `/jobs/api/plans/<job_plan_id>/?bk_biz_id=2`: JOB plan detail
- `/jobs/api/search-files/`: execute search plan
- `/jobs/api/backup-files/`: execute backup plan
- `/jobs/api/records/`: execution records
- `/jobs/api/records/<record_id>/refresh/`: refresh execution status

## Local Development

Use the shared Python environment and set BlueKing environment variables as in the first two labs.

```powershell
$env:BKPAAS_ENVIRONMENT = "test"
$env:BKPAAS_APP_ID = "bk-lab3"
python manage.py migrate
python manage.py runserver 127.0.0.1:8004
```

The page reads live data from BlueKing CMDB and JOB. If the platform returns an error, the UI reports the API message directly.

Recommended checks:

```powershell
python manage.py check
$env:BKPAAS_ENVIRONMENT = "test"
python manage.py test jobs
```

## Course Material Note

The provided `JOB - front-end code package.zip` and `JOB - back-end code package.zip` are Git LFS pointer files rather than complete zip archives. This project implements the required workflow with Django templates and the BlueKing component SDK.

The JOB plan IDs are selected in the UI instead of being hard-coded in source code, which avoids leaving course sample IDs in business logic.

