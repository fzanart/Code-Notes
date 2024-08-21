# Managing Spaces with GitHub Actions

You can keep your app in sync with your GitHub repository using GitHub Actions. For files larger than 10MB, Spaces requires Git-LFS. If you prefer not to use Git-LFS, review your files and history, and use [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/) to remove large files from history.

## Initial Setup

1. **Add Spaces App as Remote**

   Add your Spaces app as an additional remote to your existing Git repository:
   ```bash
   git remote add space https://huggingface.co/spaces/HF_USERNAME/SPACE_NAME
   ```

2. **Force Push to Sync**

   Force push to sync everything for the first time:
   ```bash
   git push --force space main
   ```

3. **Set up a GitHub Action to push your main branch to Spaces**  

   In your repository, go to **Settings > Actions**. Ensure that actions are enabled and configure permissions for workflows, then add the following files into `.github/workflows`.

   Action to push your main branch to Spaces. In the example below:

   - Replace HF_USERNAME with your username and SPACE_NAME with your Space name.
   - Create a Github secret with your HF_TOKEN. You can find your Hugging Face API token under API Tokens on your Hugging Face profile.  


    ```yaml
    on:
      push:
        branches: [main]
    
      # to run this workflow manually from the Actions tab
      workflow_dispatch:
    
    jobs:
      sync-to-hub:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v3
            with:
              fetch-depth: 0
              lfs: true
          - name: Push to hub
            env:
              HF_TOKEN: ${{ secrets.HF_TOKEN }}
            run: git push https://HF_USERNAME:$HF_TOKEN@huggingface.co/spaces/HF_USERNAME/SPACE_NAME main
    ```


    Action that automatically checks the file size of any new pull request:




    ```yaml
    name: Check file size
    on:               # or directly `on: [push]` to run the action on every push on any branch
      pull_request:
        branches: [main]
    
      # to run this workflow manually from the Actions tab
      workflow_dispatch:
    
    jobs:
      sync-to-hub:
        runs-on: ubuntu-latest
        steps:
          - name: Check large files
            uses: ActionsDesk/lfs-warning@v2.0
            with:
              filesizelimit: 10485760 # this is 10MB so we can sync to HF Spaces
    ```

## Branch Renaming
   
   Rename Branches Locally:
   
   ```bash
   git branch -m main newfeaturebranch
   git branch -m feature1 main
   ```
   
   Push Changes to Remote:
   
   ```bash
   git push -uf origin main
   git push -u origin newfeaturebranch
   ```  
   
   If necessary, adjust tracking branches:
   
   ```bash
   git branch -u origin/main main
   git branch -u origin/newfeaturebranch newfeaturebranch
   ```
