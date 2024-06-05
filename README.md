# metaculus-bot-forecaster
This repository is used to use a Github actions to automate the periodic execution of a Google colab notebook that makes LLM-powered forecasts in Metaculus' [AI benchmarking competition](https://www.metaculus.com/project/ai-benchmarking-pilot/).

### :rotating_light: :rotating_light: :rotating_light: Warning :rotating_light: :rotating_light: :rotating_light:

**You are responsible for monitoring the costs of your implementation, especially if using the automated Github workflow. Cost estimates computed by this notebook are rough estimates only, make sure to check and monitor how much you are spending and the funds in your relevant accounts.**

## Getting Started

Note that I am a novice, so these instructions may contain mistakes or may not be the most efficient way to do it.

### Step One: Copy the Colab Notebook

First you need to have made a copy of the [Google colab notebook](https://colab.research.google.com/drive/1_P7_QNJiJyWBY2qCVu2-_8gVPD1X7mX3?usp=sharing) used to make forecasts.

*Note that currently only the linked notebook is setup properly to enable this automated process, so you should copy and modify that one. Metaculus has other Google colab templates that have not implemented the code necessary to be used with this Github action.*

### Step Two: Copy This Repository

Next you'll need to make a copy of this repository. If you don't already have one, make a Github account. Then, [follow these instructions to fork this repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo).

**Note:** You can do everything you need for this from the Github web UI, so you can ignore the sections in the above instructions titled [Cloning your forked repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) and [Configuring Git to sync your fork with the upstream repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo). If you'd like to try more advanced modifications and don't already have Git, [see these instructions to download and setup Git](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git).

### Step Three: Edit Your Repository

Once you have your own repository you can make the changes below (note these are described using the Github web UI, but you can do this locally with Git as well):

#### Step Three Part A: Add Your Colab Notebook

Replace `Ryan_LLM_Forecast_Bot.ipynb` with your own Colab notebook:
* Click on the notebook and in the top right of the page in the `. . .` menu you can click "Delete file". Click "Commit changes" to complete the deletion.
* Add your own notebook. I think the easiest way to do this is with Google Colab's Github integration.
    * In Colab go to `File > Save a copy in Github`. Follow the steps to link your Github account and select your repository, then add your notebook.
  
#### Step Three Part B: Edit the Workflow

Click on the `.github` folder, then click on the `schedule-BotPredict.yaml` file. In the top right corner click the pencil icon to edit it. Then make the following changes:

* Edit the name (line 1)
* (Optional) Edit the schedule (line 8)
    * You can use [this cron tool](https://crontab.guru/) to change the format. I have used every 6 hours, and I don't think it needs to be more frequent than that.
* Change the name of the notebook (line 32)
    * This line needs to be of the format `notebook: "your_notebook_name.ipynb"`

### Step Four: Set Your Secrets

All of the secrets described in the Colab notebook need to be set in your Github repo. Navigate to "Settings" at the top of your repo, then "Secrets and variables" under "Security" on the left.

Then, in the "Actions" section of secrets and variables click "New repository secret". Enter the name of each secret exactly as described in the Colab notebook, and the value of each secret in the box. When you're done it should look like this:

![Secrets](https://github.com/ryooan/metaculus-bot-forecaster/assets/45539871/03e2f4f1-fdee-4917-956f-efe47e4e7fe9)

### Step Five: Try it Out!

Before doing this you should first make sure that running the Colab notebook works successfully for you. If it doesn't, fix any issues with the Colab notebook before continuing.

Make sure the settings in your notebook reflect what you want for either testing or regular automation (for example, by changing whether it publishes the predictions or not, or whether it repredicts). Update your Colab notebook accordingly, and you can save a copy on Github to update the notebook in your repository.

Then go to "Actions" at the top of your repository and select `run [workflow name]` on the left side. The workflow has a manual trigger in it, so you can test it manually by clicking "Run workflow", leaving the dropdown as "Branch: main", and clicking run.

Cross your fingers and wait for it to complete! Hopefully it completed without errors, but if not you may have to do some troubleshooting. If you can't figure it out, feel free to ask me for help. If all worked well you should be able to see your Metaculus bot account making forecasts and comments in the project on the Metaculus platform (assuming you have set it to submit to Metaculus).

**Note:** To see the output of the notebook run (which can also add in troubleshooting), click on the run and then on the output artifact to download the artifact. That will download a zip file that contains the notebook and an html file, both of which will have the full output produced by the notebook.

![output artifact](https://github.com/ryooan/metaculus-bot-forecaster/assets/45539871/3311dc6c-19c3-4bb8-b7d2-9521ca02cf96)

## Monitor and Hone Your Bot!

You should hopefully be all set, so next you can just monitor your bot's forecasts and make tweaks to the file and its prompts as you see fit.
