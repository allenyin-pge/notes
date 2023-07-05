# TIMP-CE Roamdap

Overhauling the entire risk model process is unrealistic, disruptive, and prone to errors. We should insert changes in steps, in modular ways such that improvements to the process and risk models is __incremental__ and __measureable__.

The main stages of TIMP Risk Management we should focus on include:
- Data gathering
- Data integration
- Model run
- Validation
    - data validation (prior to integration)
    - results validation (model outputs)
- Result rollup/presentation

#TODO: Fill out more details about each stage.

## Toward measureable model improvements

Any improvements to a process need to be measureable -- therefore we need to devise a single metric, or a set of consistent metrics that can measure risk model performance, and which can be compared through time.

This set of model metrics need to be agnostic to the model implementation details, and capable of convincing SME of a model's quality.

### Timeline for model performance
1. Survey different techniques and collect suggestions
2. Settle on one approach
3. Implement and validate, with historical and last assessment data, ILI data, etc
4. SME approval/implement in process?

## Steps after model performance metric

A huge time sink is the data input validation stage. Several things we could do (#TODO: Fill out details from other notes):
1. Inherit previous year's validation dataset if no changes occur -- as time goes by, the model coverage improves rather than starting from 0.
2. When there are new cases (e.g. new code label, or segment with combination of characteristics), focus validation on these set. Essentially, replace random sampling during validation with targeted sampling to save iteration time and increase test case coverage.

## References

- TIMP Risk model [road map](https://pge-my.sharepoint.com/:b:/r/personal/ixh8_pge_com/Documents/Microsoft%20Teams%20Chat%20Files/RIsk%20model%20road%20map_final_June2021.pdf?csf=1&web=1&e=yePQc4)
- [Data sources presentation slides](https://pge-my.sharepoint.com/:p:/p/s3lg/Ec3AUFhrkw1Bke6Zf86sa44BGPXI5i9Y9MKDzVwEvkjapg?e=1dYRqR) describes the risk data collection and validation process.
