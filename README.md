# Home-Credit-Default-MSBA-Capstone

**Business Problem and Objective**

Home Credit is a multinational financial services provider offering a variety of loan products, they aim to make borrowing more accessible by offering loans to customers who are typically under served, the under or unbanked. A big challenge that arises from this is that some customers lack a traditional credit score, this makes it more difficult to determine credit worthiness and decide who to extend loans to.
The goal of this project is to build a predictive model on which customers will default or face repayment problems, and to maximize the accuracy by using the data available at the time of their application and supplementing, when possible, from a few additional available data sources.

**Group Approach**

This project was completed with three other individuals, and the general steps and approach were as follows. 
For each customer data was aggregated for use in modeling, this included the data provided at the time of the application, four additional data sources were evaluated as well that had more information for some customers. For these additional data sources summary data points were created as some customers had multiple items showing up while others had none. The data was all joined into one main data set and then cleaned to account for missing values while also keeping record of when data points were missing through additional feature creation. Prior to the data prep a process was established for modal and median values to impute for missing data, it was trained on a split of 80% of the initial training data which became the new training data source, with the other 20% being heldout for final model evaluation. 
After the data was ready different models were evaluated (regression, neural net, random forest, gradient boost and ensemble combining gradient boost and neural net) and the highest performing model was chosen. The first step for these models was to evaluate the best combination of hyper parameters using fivefold cross validation on the training data split. Once the parameters were determined a model was then trained on the full training data and tested on the holdout data. The test results on the holdout data were compared between the models to determine which had the best AUC-ROC. In this case the highest performing model was the gradient boosted model. 
Once a final and best model was trained the default probability scores were then tuned using Platt Scaling to ensure the predicted probabilities were accurate. Once we had precise default probabilities a hypothetical cost table was created that determined the value of extending loans to good customers, balanced against the opportunity cost of not extending to customers who wouldn’t default and expected loss from customers defaulting. This cost table was applied to the default probabilities, and an optimal approval cutoff was determined for which customers should be given a loan. It also determined what percentage of applicants in total would be approved for a loan. 

**Individual Contribution**

For this project I was responsible for creating the initial steps of loading in the data, creating the aggregated metrics for the additional data sets as well creating the pipeline for data cleaning. In addition, I trained the ensemble model that was evaluated but not ultimately used. 

**Business Value of Solution**

By training a highly accurate model that is good at distinguishing between which customers will and won’t default and calibrating it to have precise estimates of the probabilities of these events, Home Credit will be able to apply this to incoming loans and have a strong recommendation for approving a client or not for a loan. They can also use the approval probability threshold applied against the cost table so that they can maximize profit to their business. This model allows Home Credit to be confident in their lending decisions and be able to extend credit to worthy borrowers thus accomplishing their mission of making loans more accessible. 

**Difficulties Encountered**

The biggest difficulty encountered came around the size of the data in this project, this came from the number of observations present as well as a very high level of features, mainly from the additional data steps that were joined in and the cleaning pipeline that aimed to fix missing values while also retaining the signal that these values were missing. When attempting to find hyperparameters using cross validation we encountered massive delays and computer crashes due to the size of data and computational power required to train these complex models. Even with down sampling the data set was very large and required running models and coming back to them minutes or hours later, as well as saving models and loading them instead of trying to train from scratch each time. 
The other main difficulties were around version control; it was difficult to communicate changes or small fixes amongst the team to dependent code and processes. We did utilize GitHub but had issues with merge conflicts given we didn’t have robust commit rules and on a free plan encountered issues with multiple people all working simultaneously. 

**Individual Learning Takeaways**

In this project a major focus was to try and create one unified set of data that would work for everyone to then use individually when training their models. The recipe package was used which made it easy to do all the cleaning steps initially, and then these steps could be retained for the final data. This process proved to be invaluable about creating one cohesive plan at the start for data, so all members of the group were on the same page. 
Another major takeaway was around handling a large data set; in trying to optimize hyper parameters on the full training data set it was very limiting due to time constraints, so not that many combinations of parameters or diverse modeling approaches were ultimately attempted. In the future I would likely sacrifice the volume of data evaluated in cross validation and use a much smaller subject of observations so more tuning could take place, and then only once a set of parameters was chosen, then use the full training set to train a model.  

