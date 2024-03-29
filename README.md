# Accumulated daily rainfall forecasting on the D day on observation ground stations

## A. Adressed problem 
We are adressingg a forecasting problem. We are attempting to predict the accumulated rainfall on a given day D by utilising a set of explanatory features from day D-1. Explanatory variables include dd (wind direction), ff (wind speed), hu (humidity), td (dew point temperature). 

## B. Methodology and implementation

### B.1. Methodology 
To adress this time series forecasting we are using a type of RNN (recurrent neural networks) as opposed to feed-forward networks. <br> 

<img src="images/rnn_arch.PNG"/> 

Regular feed-forward networks such as CNNs only consider the current input. Consequently, they do not have any memory about what happened in the past.  Therefore, they have trouble predicting what comes next in a sequence.  
RNNs differ in that they retain information about the input previously received.  They are networks with feedback loops that allow information to persist -- a trait that is analogous to short-term memory.  This sequential memory is preserved in the recurrent network’s hidden state vector and represents the context based on the prior inputs and outputs. LSTMs are explicitly designed to remember information for long periods of time.

### B.2. Implementation
A preprocessing phase mainly puts in a place a missing values management and normalisation to prepare the time series for LSTM. <br> 
<img src="images/lstm_data.PNG"/> 

After preprocessing we are implementing 3 architectures of LSTMs : vanilla, stacked and bidirectional. We then do and inter model comparison using the MAPE (mean absolute percentage error.) We attempt to optimise these models using techniques such as drop out and weight decay. 

## C. Results 
 The MAPE analysis over the same N epochs for all models indicates that the better model is the most simple model : vanilla model. 
 The more sophisticated models suffer from an overfitting very early in the training process. 
 
<img src="images/overfitting.PNG"/> 
