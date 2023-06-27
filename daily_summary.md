Sometimes summary, sometimes notes, anything I want to document and refer to later...hopefully more of my notes get digitized as well.

# 6/20/2023

## Meeting with Ian to establish expectations and understand goals

- Improve risk assessment model such that field engineers trust its results more.
- Provide evidence to SME that ML-models can be more reliable than the current model, while being interpretable.
  - Important to make the model outputs easy to understand (i.e. probability numbers are hard to interpret)
- Provide data quality assessment: give quantification and evidence to support additional data collection to improve models.

Expectations is I do anything to improve upon these axes.

__Other learnings__:
- Gordon Ye's data team understands how the data is collected and ingested into the current model -- important to work with them.
- Third-party damage (TPD) is the most prevalent type...but also the most difficult to model (many stochastic elements!)
- Record keeping is much better in 2011-2022. Prior to that not so much. Data not always in the same system, pipeline specs are in the same system though.
  - Ian to send excel sheet with location of the different data sources: [TIMP Dataset 2023](https://pge-my.sharepoint.com/:x:/p/tla3/EZaR-HD8-UlNmlSqlbrXdZoBeBC1ZeFU0tmqQsyM39KMpQ?e=gJipuR).
- Many documents on the Teams-Files page

## Palantir Foundry

- Ontology can be used to integrate all data sources in one place
  - Challenge: Setting up the workflow for everyone to use it, really need support from Gordon's team -- how to drive this?
    - Learn what they want to do, how can Foundry make this easier, at least more than their existing solutions?
- Code Workbook similar to Jupyter notebook + REPL, but has limited capability for using custom code.
  - Require Code Repository to use custom code.

#TODO: Check out Even's models inside Foundry..to understand how he cleans and integrate the data there.

## 4810S reading

Finished..see [doc_reading_notes](./doc_reading_notes.md).

## Next on TODOs:

1. Dev tooling setup:
   - Finish following the internal wiki on bitbucket/git code repos (necessary)?
   - Ask Even about his new workflow maybe
   - Prototype on laptop (Jupyter + Python + git) vs. Foundry Code Workbook/Repo?
2. Read attachment 3 on current risk model
   - How to find this year's results and replicate it?
3. Set up meeting with Even toward end of this week
   - ~~Read Even's machine learning notes on Teams~~
4. Set up meeting with Gordon/Steve Lu for next week?
   - Find and read Gordon's roadmap doc
5. Start a doc for my own roadmap, clean up stuff in [planning.txt](./planning.text).

# 6/21/2023

## Gas Data Management

Asset Knowledge Management team working on data quality work, using Foundry ontology layers and GIS layers..can be useful. Useful names:

- Gary Singh
- Kim Jackson
- Alec McCullick
- Susan Minarcin

#TODO: Figure out how they relate to Gordon's team (he's a customer?) and state of data ontology transformation..

[slides](https://pge.sharepoint.com/:p:/s/GasOperationsDataAssetManagement/ETvuD9ysKtVMvV5lGKulRlQBGQnzo5hX3r33Iw7X17hwxQ?e=LGaIg0&isSPOFile=1&clickparams=eyJBcHBOYW1lIjoiVGVhbXMtRGVza3RvcCIsIkFwcFZlcnNpb24iOiIyNy8yMzA1MTQwMTgyMyIsIkhhc0ZlZGVyYXRlZFVzZXIiOmZhbHNlfQ%3D%3D)


# 6/22/2023

- Reading the attachment3 model -- many layers of equations, temporal dependence encapsulated through mitigation factors depending on pipeline assessment events, OR-Gate models, etc.
- Overarching question is...why not a single or even multiple regression models fitted to data?

__Meeting with Brian Patrick__

- Discussed questions about the attachement 3 model, a lot of historical context:
  - Relative modeling previously resulted in the form of the current model equations. Relative modeling combines various "scores" to form "index" representing relative risks (e.g. pipeline1 has higher risk than pipeline2) that then gets converted into likelihood...the scale can be screwed up due to SME's faulty perception of log vs. linear scale.
  - Ajustment and improvement of the current model probably has reached its peak...
- Obstacles encountered toward data-driven approaches:
  - Model tuning driven by SME -- cultural resistance
  - Data cleaning/scrubbing, getting close now.
    - Need to get other groups to input data correctly, requires a lot of engineering time for the data to be usable.
    - Had to help a lot of groups to set up database and push things through.
- Missing historical data -- unclear for old pipes without previous inspection data when corrosion might've started... (leverage existing literature data? Run experiments?)
- __Strategy Advice__:
  - Cleaning data and automating the data ingestion process from the source groups can improve a lot, but can be a huge time sink.
  - Demonstrating improvements using data-driven approaches can help convince getting more buy-in and resources into the effort.
  - Makes sense to prioritize modeling over data cleaning, especially since TIMP has somewaht reliable dataset (Gordon Ye's team..)


#TODO:
- Make sure I understand attachement 3 model data-flow...make a flow chart and ask if I understand it correctly...
- Modeling questions:
  - Is causal dependence important for modeling? How much dependence? How important is using __Fault Tree__?
  - Can I throw everything into GAM? Hierarchical logistic regressions? Or just a single logistic regression FB style?
  - Ask about previous attempts at using Bayesian Networks (and Fault Tree?)...data issue?
  - How about Random Forest? 


- Good references:
  - Dynamic Bayesian Network (DBN) for pipeline corrosion risk modeling [here](https://oaktrust.library.tamu.edu/bitstream/handle/1969.1/174151/PALANIAPPAN-THESIS-2018.pdf?sequence=1&isAllowed=y)
  - Predicting pipeline failure using Gradient Boosted Trees (GBT) and weighted risk analysis [paper](https://www.nature.com/articles/s41545-022-00165-2) 


# 6/23/2023

## Trying to setup work flow

Foundry:
  - Get access through [MEA](https://sailpointui.utility.pge.com/identityiq/home.jsf), then log into [Palantir Foundry](https://damask.palantirfoundry.com/workspace/home/). Repos/projects requires access to be granted.

Bitbucket: Is deprecated. The wiki [here](https://wiki.comp.pge.com/display/DAF/Tool+Installation) lies.

Git:
  - Supposedly there are instructions on the wiki page [here](https://wiki.comp.pge.com/pages/viewpage.action?pageId=121635410), but I need to log-in, which I can't.
  - Can follow the screenshot below
  - Go to github and create an account with the pge email address. Note that using the `<fullname>@pge.com` doesn't work, I never got the confirmation code that way. So use `<lanID>@pge.com` instead for email, even though the screenshot recommended the first way.
  - Then request access through MEA to join the group `Apr-A2102-GithubEnterpriseCloudUsers ` and enter in the details something like "My group is TIMP, project is CE"...hopefully they approve access. WTF why is it so hard to access a git repo?!

  ![github-screenshot](./assets/github_pge.png)

  # 6/26/2023

  ## Accounts:

  All the github and wiki requests have been approved.

  ### Git:
  - Click on the email that invited to join `pgetech` github project.
  - Set up 2fac with Microsoft Authenticator app on the phone.
  - Follow steps on the wiki page [here](https://wiki.comp.pge.com/display/CCE/GitHub+-+Create+Personal+Access+Token) to generate personal authentication token and use for PGE SSO -- remember to rotate token every 90 days!!!
  - Join the `TIMP Risk ML-Team` on github: click on `pgetech` organization from profile (see screenshot), then `view organization` -> `Teams` -> `Search` for "TIMP" to join.
  ![github-screenshot2](./assets/github_teams1.png)
  - One of the team members will grant access.
  - Now we can see all the repositories belonging to the team [here](https://github.com/orgs/pgetech/teams/timp-risk-ml-team/repositories).

  ### Powershell and VSCode

  PGE has weird regulations for laptop, extra hacks have to get around these things...

  1. Install `git` and `vim` via `itstore` -- chose `github git` and `gvim` -- wait for all that to finish.
  2. Set Powershell alias:
      - First create the powershell profile: `new-item -type file -path $profile -force`
      - Set `vim` as default editor (could be notepad): `set-alias vim 'C:\Program Files (x86)\Vim\vim80\vim.exe'`
      - Do `vim $profile` and enter the following:
      ```
      set-alias vim 'C:\Program Files (x86)\Vim\vim80\vim.exe'
      set-alias l 'ls'
      set-alias c 'clear'

      function u { set-location .. }
      function src { . $profile }
      function rc { vim $profile }
      ```
  3. Do basic vim settings ...unfortunately I can't edit the `vimrc` settings in `$VIM` (in program files), and this makes me very frustrated.

# 6/27/2023

## More git stuff

- Setting up workflow -- decided to do most code and editting through VSCode.
- PGE restrictions are really annoying, couldn't use VSCode's github integration shown [here](https://code.visualstudio.com/docs/sourcecontrol/overview#_3way-merge-editor) because it required downloading VSCode updates!
- Go to all the steps outlined [here](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git), but do all of them in powershell using `git` instead of through `git-bash` application, they don't work otherwise.



  