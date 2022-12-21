# ElasticFlow Traces

This repository contains job traces of the 1st party deep learning training workloads in Microsoft's internal ITP clusters.
The traces are used in "ElasticFlow: An Elastic Serverless Training Platform for Distributed Deep Learning" in ASPLOS '23.

## Overview

### Characteristics

* Duration: 2 months from 2021-03-04 to 2021-05-03
* Total number of clusters: 10
* Total number of jobs: 69,351
* Total GPU horus: 1,632,719.7

### Schema for raw-traces

`data/raw-traces.tar.gz` contains raw trace data collected from ITP clusters.
There are 10 csv files, each file represents one cluster.
Detailed descriptions for each column are as follows:

|            Column | Description                                                                        |
|------------------:|:-----------------------------------------------------------------------------------|
|          `job_id` | Job unique id, the UUID is re-generated after trace is collected.                  |
| `submission_time` | Job submission time, relative time in seconds to the beginning of collection time. |
|        `duration` | Job duration in seconds.                                                           |
|         `num_gpu` | Number of GPUs requested/used by the job.                                          |

Here's an example for each csv:
```
job_id,submission_time,duration,num_gpu
6b2d9ccc-6279-403c-e1a2-cfe7810d5c57,16566,3890,4
```

### Schema for elasticflow-traces

`data/elasticflow-traces.tar.gz` contains extra randomly generated data based on raw trace data.
The traces are actually used in ElasticFlow experiments, 10 csv files are used for simulation and 195job csv is used to run in real testbed.
Detailed descriptions for each column are as follows:

|            Column | Description                                                                        |
|------------------:|:-----------------------------------------------------------------------------------|
|          `job_id` | Job unique id, the UUID is re-generated after trace is collected.                  |
| `submission_time` | Job submission time, relative time in seconds to the beginning of collection time. |
|   `num_iteration` | Randomly generated itertion number for the job's training.                         |
|      `model_name` | Randomly generated model name for the job.                                         |
|        `deadline` | Generated deadline based on specific rules.                                        |
|      `batch_size` | Generated batch size for the job's training.                                       |
|         `num_gpu` | Number of GPUs requested/used by the job.                                          |
|        `duration` | Job duration in seconds.                                                           |

Here's an example for each csv:
```
job_id,submission_time,num_iteration,model_name,deadline,batch_size,num_gpu,duration
6b2d9ccc-6279-403c-e1a2-cfe7810d5c57,16566,40285,bert,21347,64,4,3890
```

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
