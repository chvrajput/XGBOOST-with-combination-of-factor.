# XGBOOST-with-combination-of-factor.
XGBoost (eXtreme Gradient Boosting) is an advanced implementation of gradient boosting algorithm.Xgboost is short for eXtreme Gradient Boosting package.  The purpose of this Vignette is to show you how to use Xgboost to build a model and make predictions.  It is an efficient and scalable implementation of gradient boosting framework by J. Friedman et al. (2000) and J. H. Friedman (2001). Two solvers are included:  linear model ; tree learning algorithm. It supports various objective functions, including regression, classification and ranking. The package is made to be extendable, so that users are also allowed to define their own objective functions easily. 

#XGBoost Parameters
Before running XGboost, we must set three types of parameters: general parameters, booster parameters and task parameters.

General parameters relates to which booster we are using to do boosting, commonly tree or linear model
Booster parameters depends on which booster you have chosen
Learning Task parameters that decides on the learning scenario, for example, regression tasks may use different parameters with ranking tasks.
Command line parameters that relates to behavior of CLI version of xgboost.
Parameters in R Package
In R-package, you can use .(dot) to replace underscore in the parameters, for example, you can use max.depth as max_depth. The underscore parameters are also valid in R.

General Parameters
booster [default=gbtree]
which booster to use, can be gbtree, gblinear or dart. gbtree and dart use tree based model while gblinear uses linear function.
silent [default=0]
0 means printing running messages, 1 means silent mode.
nthread [default to maximum number of threads available if not set]
number of parallel threads used to run xgboost
num_pbuffer [set automatically by xgboost, no need to be set by user]
size of prediction buffer, normally set to number of training instances. The buffers are used to save the prediction results of last boosting step.
num_feature [set automatically by xgboost, no need to be set by user]
feature dimension used in boosting, set to maximum dimension of the feature
Parameters for Tree Booster
eta [default=0.3, alias: learning_rate]
step size shrinkage used in update to prevents overfitting. After each boosting step, we can directly get the weights of new features. and eta actually shrinks the feature weights to make the boosting process more conservative.
range: [0,1]
gamma [default=0, alias: min_split_loss]
minimum loss reduction required to make a further partition on a leaf node of the tree. The larger, the more conservative the algorithm will be.
range: [0,∞]
max_depth [default=6]
maximum depth of a tree, increase this value will make the model more complex / likely to be overfitting. 0 indicates no limit, limit is required for depth-wise grow policy.
range: [0,∞]
min_child_weight [default=1]
minimum sum of instance weight (hessian) needed in a child. If the tree partition step results in a leaf node with the sum of instance weight less than min_child_weight, then the building process will give up further partitioning. In linear regression mode, this simply corresponds to minimum number of instances needed to be in each node. The larger, the more conservative the algorithm will be.
range: [0,∞]
max_delta_step [default=0]
Maximum delta step we allow each tree's weight estimation to be. If the value is set to 0, it means there is no constraint. If it is set to a positive value, it can help making the update step more conservative. Usually this parameter is not needed, but it might help in logistic regression when class is extremely imbalanced. Set it to value of 1-10 might help control the update
range: [0,∞]
subsample [default=1]
subsample ratio of the training instance. Setting it to 0.5 means that XGBoost randomly collected half of the data instances to grow trees and this will prevent overfitting.
range: (0,1]
