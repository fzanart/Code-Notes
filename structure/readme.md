The inside of a ML project folder should look like:

> Approaching (Almost) Any Machine Learning Problem
>
> -- <cite> Abhishek Thakur </cite>

```
project
|-- input
|     |-- tran.csv   
|     |-- test.csv
|-- src
|     |-- create_folds.py 
|     |-- train.py
|     |-- inference.py
|     |-- models.py
|     |-- config.py
|     |-- model_dispacher.py
|-- models
|     |-- model_rf.bin
|     |-- model_et.bin
|-- notebooks
|     |-- exploration.ipynb
|     |-- check_data.ipynb
|-- README.md
|-- LICENSE

```


### Adding existing source code to GitHub:
1. Execute:
   
  ```
  git init -b main
  ```

2. Add the files in your new local repository. This stages them for the first commit.

  ```
  $ git add .
  ```

3. Commit the files that you've staged in your local repository.

  ```
  git commit -m "First commit"
  ```


### Adding a local repository to GitHub using Git:

1. Create a new repository on GitHub, copy the remote repository url e.g.: REMOTE-URL: https://github.com/fzanart/new-project.git

  ```
  git remote add origin REMOTE-URL
  ```

2. Verify that you set the remote URL correctly, run the following command.

  ```
  git remote -v
  ```

3. Push the changes in your local repository to GitHub

  ```
  git push -u origin main
  ```

### Merge local and remote git repositories containing different files:

1. Execute:  


   ```
   git pull
   ```
   
2. Resolve any conflicts during merge locally, then `push` your local branch to GitHub
