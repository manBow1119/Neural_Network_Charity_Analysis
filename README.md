# Neural_Network_Charity_Analysis

### Project Overview
The purpose of this analysis was to use existing data about organizations that have been funded by Alphabet Soup. Specifically, the use of a sequential neural network was employed to determine how well the features of the data set could be used to create a binary success classifier for future applicants, predicting whether future investments would likely succeed or not.

### Approach and Results
* Data Pre-processing:
  * The target variable in this analysis was the column 'IS_SUCCESSFUL' which is the ultimate goal of the model to be able to predict.
  * The columns/variables that were eliminated are "EIN" and "NAME", as these columns are not likely to contribute to the model, and erroneous to its predictability. Other columns were considered to be dropped in the data exploration phase, but these did not appear to improve model performace. Ultimately, some columns were binned to help reduce noise. Binning "INCOME_AMT" as well as "APPLICATION" and "CLASSIFICATION" types improved the model's performance.
  * All remaining categorical columns were OneHotEncoded, and all data scaled. Once fit to the scaler, the data was split into training and testing groups before compilation.
* Compiling, Training, and Evaluating the Model:
  * After testing several models simultaneously, I manipulated certain parameters to determine the model with the best output. Attempts to add more hidden layers increased performance of all models (given no other changes). Three hidden layers performed better than two and four. 
  * Within these hidden layers, different activation functions were also tested. Because of its similarity to the output "sigmoid" I wanted to examine the hyperbolic tangent (tanh), which was balanced against the all-purpose "relu" function in various proportions as seen below. Comments reveal observed results after various adjustments:
   * Using all tanh activation for hidden layers  
   * ![All tanh hidden layers.](https://github.com/manBow1119/Neural_Network_Charity_Analysis/blob/main/NN_aa_tanh.png)
   * Using 2:1 tanh/relu for hidden layers
   * ![2 tanh, 1 relu hidden layers.](https://github.com/manBow1119/Neural_Network_Charity_Analysis/blob/main/NN_2tanh.png)
   * Using 1 tanh, others relu
   * ![1 tanh, 3 relu hidden layers.](https://github.com/manBow1119/Neural_Network_Charity_Analysis/blob/main/NN_1tanh.png)
   * Using all relu
   * ![All relu hidden layers.](https://github.com/manBow1119/Neural_Network_Charity_Analysis/blob/main/NN_all_relu.png)
   * Aside from the manipulation of activation functions, the number of nodes per layer was also changed to determine best fitness for the model. After lots of experimentation the ratio of 300:200:140 for the hidden layers proved the best outcomes (when compared to 30:20:14 or 600:400:280, for example)
   * While it did not meet the target threshhold, the best performing model had three hidden layers of which all their activation functions were "relu". These hidden layers had 300, 200, and 140 nodes in each successive sequential layer, before the final sigmoid output which provides the final classification prediction. Checkpoints for each model were saved, and the best for this model recorded .7483 accuracy, just shy of .7500 goal.

### Summary
While this final model did not meet the target goal, the exercise was of great benefit. Given more time, I would first like to do more data exploration, eliminating any more potential noise detected. Another (somewhat superficial) approach that was not tried was to examine the model's performance with different random seeds. Finally, after some further research I am interested in comparing the performance of an XGBoost classifier, which has been show to outperform neural networks on both classification and regression tasks- binary classification, in particular.

