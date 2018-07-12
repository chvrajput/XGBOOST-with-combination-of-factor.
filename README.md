Xgboost is short for eXtreme Gradient Boosting package.

The purpose of this Vignette is to show you how to use Xgboost to build a model and make predictions.

It is an efficient and scalable implementation of gradient boosting framework by J. Friedman et al. (2000) and J. H. Friedman (2001). Two solvers are included:

linear model ;
tree learning algorithm.
It supports various objective functions, including regression, classification and ranking. The package is made to be extendible, so that users are also allowed to define their own objective functions easily.

#XGBoost Parameters
Before running XGboost, we must set three types of parameters: general parameters, booster parameters and task parameters.

General parameters relates to which booster we are using to do boosting, commonly tree or linear model
Booster parameters depends on which booster you have chosen
Learning Task parameters that decides on the learning scenario, for example, regression tasks may use different parameters with ranking tasks.
Command line parameters that relates to behavior of CLI version of xgboost.
Parameters in R Package
In R-package, you can use .(dot) to replace underscore in the parameters, for example, you can use max.depth as max_depth. The underscore parameters are also valid in R.
