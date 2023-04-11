# Picking cloud GPU provider for experiments

Looking for cheap one  for few hours

Google Cloud
https://cloud.google.com/compute/gpus-pricing

AWS 
https://instances.vantage.sh/?region=eu-west-1

Lambda labs
https://lambdalabs.com/service/gpu-cloud

For today prices per hour for 

## 1xNVIDIA A10 with 24GB VRAM 

Lambda Labs:
- 1x NVIDIA A10 	24 GB 	30 	200 GiB 	1.4 TiB 	$0.60 / hr

GCloud
- not in offer

AWS
- g5.2xlarge	32.0 GiB	8 vCPUs 	1 	NVIDIA A10G	24 GiB 	450 GB NVMe SSD 	Up to 10 Gigabit 	$1.3530 hourly




## 1xNVIDIA A100 with 40 GB VRAM

Lambda Labs:
- 1x NVIDIA A100	40 GB	30	200 GiB	512 GiB	$1.10 / hr

GCloud
- NVIDIA A100 40GB	1 GPU	40 GB HBM2	$2.934 per GPU

AWS
- p4d.24xlarge	1152.0 GiB	96 vCPUs 	8 	NVIDIA A100	320 GiB 	8000 GB (8 * 1000 GB NVMe SSD) 	4x 100 Gigabit 	$35.3965 hourly



I have to figure out how to use this instance only for necessary training time, and automate its shutdown to reduce costs:

Lambda Labs instaces does not support instance shutdown, only termination, so first the data must be stored to some block storage. 

https://docs.lambdalabs.com/cloud/terminate-instance-api/?_gl=1*1od6ru3*_ga*OTg5NjgxMzY1LjE2ODEyMzE0NDQ.*_ga_43EZT1FM6Q*MTY4MTIzMTQ0NC4xLjEuMTY4MTIzMjE0Ni40Mi4wLjA.

AWS, Gcloud supports proper instance shutdown

