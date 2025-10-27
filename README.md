anything_data_Engineering_python_task 1
using logical functions to solve python challenge
Scenario:
You're building a monitoring system for a data pipeline in a data lakehouse architecture. Your job is to analyze the metadata logs from multiple data sources and determine the health status of each pipeline run. Each pipeline run is logged in a JSON-like format that will be provided below. You are given a list of such logs for different pipelines. Your task is to analyze each log and apply the following complex conditional rules to determine the pipeline health status:

Evaluation Rules:
Assign a health_status field with one of the following values:

"HEALTHY"

"WARNING"

"CRITICAL"

Based on the following logic:

HEALTHY if:

status_code is 200 AND errors is empty AND warnings is empty or only includes "late data arrival" AND duration_seconds is less than 600 AND max_latency_seconds is less than 10

WARNING if any of the following:
status_code is 200 AND duration_seconds is between 600 and 1200 OR max_latency_seconds is between 10 and 30 OR warnings contains non-late data warning messages OR there are fewer than 100 records ingested (record_count < 100) but no errors

CRITICAL if:
status_code is not 200 OR there are one or more errors OR duration_seconds > 1200 OR max_latency_seconds > 30 OR record_count == 0

Your Task:
Write a function evaluate_pipeline_health(log) that takes a single log dictionary and returns the same dictionary with a new key health_status assigned based on the above rules.

Write a function evaluate_all_pipelines(logs: List[Dict]) -> List[Dict] to apply this to a list of logs.

Print a summary:

Total pipelines evaluated

Count of each health status category

Tool used:
Colab
