# metaculus-bot-forecaster
This repository is used to use a Github actions to automate the periodic execution of a Google colab notebook that makes LLM-powered forecasts in Metaculus' [AI benchmarking competition](https://www.metaculus.com/project/ai-benchmarking-pilot/).

## :rotating_light: :rotating_light: :rotating_light: Warning :rotating_light: :rotating_light: :rotating_light:

**You are responsible for monitoring the costs of your implementation, especially if using the automated Github workflow. Cost estimates computed by this notebook are rough estimates only, make sure to check and monitor how much you are spending and the funds in your relevant accounts.**

## Getting Started

### Step One

First you need to have made a copy of the [Google colab notebook](https://colab.research.google.com/drive/1_P7_QNJiJyWBY2qCVu2-_8gVPD1X7mX3?usp=sharing) used to make forecasts.

*Note that currently only the linked notebook is setup properly to enable this automated process, so you should copy and modify that one. Metaculus has other Google colab templates that have not implemented the code necessary to be used with this Github action.*