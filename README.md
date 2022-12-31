# Cron Gantt

This script generates a Gantt chart showing the schedules of multiple jobs. The input is a pandas DataFrame with columns 'job_name', 'schedule', 'category', and 'duration', where 'schedule' is in crontab format and 'duration' is a pandas Timedelta object representing the duration of each job. The script generates a Gantt chart showing all job schedules from now until a user-specified interval.

## Dependencies

This script requires the following packages:

- pandas
- plotly
- croniter

To install these dependencies, run the following command:
```
pip install pandas plotly croniter
```

## Usage

To use the script, you can follow these steps:

1. Clone the repository to your local machine:
```
git clone https://github.com/<your_username>/cron-gantt.git
```

2. Navigate to the cron-task-scheduler directory:
```
cd cron-gantt
```

3. To use the script, enter the following command:
```
python gantt_chart_generator.py
```

4. The script will prompt you for the interval for the Gantt chart (e.g. "days=7, weeks=2, months=1") and a list of tasks to include in the chart (separated by commas, or enter "all" to include all tasks). The Gantt chart will be generated and displayed using `plotly`.

## Example

Here is an example of how to use the script:

```python
import pandas as pd
from gantt_chart_generator import create_gantt_chart

# Create a sample DataFrame with job schedules
df = pd.DataFrame({'job_name': ['Job 1', 'Job 2', 'Job 3'], 'schedule': ['0 0 * * *', '0 0 * * 1', '0 0 * * 2'], 'category': ['category1', 'category1', 'category2'],'duration': [pd.Timedelta(minutes=60), pd.Timedelta(minutes=30), pd.Timedelta(minutes=45)]})

# Generate the Gantt chart
interval = {'days': 7}  # Show schedules for the next 7 days
tasks = ['Job 1', 'Job 3']  # Include only Job 1 and Job 3 in the chart
create_gantt_chart(df, interval, tasks)
```