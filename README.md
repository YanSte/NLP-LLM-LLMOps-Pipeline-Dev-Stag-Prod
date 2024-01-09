# | NLP | LLM | LLMOps | Pipeline Dev Stag Prod |

## Natural Language Processing (NLP) and Large Language Models (LLM) with LLMOps and make a Pipeline Dev Stag Prod.


![Learning](https://t3.ftcdn.net/jpg/06/14/01/52/360_F_614015247_EWZHvC6AAOsaIOepakhyJvMqUu5tpLfY.jpg)


# <b><span style='color:#78D118'>|</span> Overview</b>


In this example, we will walk through some key steps for taking an LLM-based pipeline to production.  Our pipeline will be: summarization of news articles using a pre-trained model from Hugging Face.  

But in this walkthrough, we will be more rigorous about LLMOps.

**Develop an LLM pipeline**

Our LLMOps goals during development are (a) to track what we do carefully for later auditing and reproducibility and (b) to package models or pipelines in a format which will make future deployment easier.  Step-by-step, we will:
* Load data.
* Build an LLM pipeline.
* Test applying the pipeline to data, and log queries and results to MLflow Tracking.
* Log the pipeline to the MLflow Tracking server as an MLflow Model.

**Test the LLM pipeline**

Our LLMOps goals during testing (in the staging or QA stage) are (a) to track the LLM's progress through testing and towards production and (b) to do so programmatically to demonstrate the APIs needed for future CI/CD automation.  Step-by-step, we will:
* Register the pipeline to the MLflow Model Registry.
* Test the pipeline on sample data.
* Promote the registered model (pipeline) to production.

**Create a production workflow for batch inference**

Our LLMOps goals during production are (a) to write scale-out code which can meet scaling demands in the future and (b) to simplify deployment by using MLflow to write model-agnostic deployment code.  Step-by-step, we will:
* Load the latest production LLM pipeline from the Model Registry.
* Apply the pipeline to an Apache Spark DataFrame.
* Append the results to a Delta Lake table.

### Notes about this workflow

**This notebook vs. modular scripts**: Since this demo is in a single notebook, we will divide the workflow from development to production via notebook sections.  In a more realistic LLM Ops setup, you would likely have the sections split into separate notebooks or scripts.

**Promoting models vs. code**: We track the path from development to production via the MLflow Model Registry.  That is, we are *promoting models* towards production, rather than promoting code.  For more discussion of these two paradigms, see ["The Big Book of MLOps"](https://www.databricks.com/resources/ebook/the-big-book-of-mlops).

### Learning Objectives
1. Walk through a simple but realistic workflow to take an LLM pipeline from development to production.
2. Make use of MLflow Tracking and the Model Registry to package and manage the pipeline.
3. Scale out batch inference using Apache Spark and Delta Lake.
