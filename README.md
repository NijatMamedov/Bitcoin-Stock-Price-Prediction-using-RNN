# Bitcoin-Stock-Price-Prediction-using-RNN

1. 📚 First, I imported all the necessary libraries:
I brought in optuna for hyperparameter tuning, numpy, pandas for data handling, matplotlib.pyplot for plotting, and various components from keras and tensorflow to build my RNN model. I also used MinMaxScaler to normalize data.
---------------------------------------------------
2. 📂 I read the Bitcoin dataset:
I loaded the data from 'bitcoin.csv' using pandas and printed it out to get an initial look.
---------------------------------------------------
3. ✂️ I split the data into training and test sets:
I converted the 'Date' column into datetime format.

Then I created the training set with rows before 2021 and the test set with rows from 2021.
---------------------------------------------------
4. 🧹 I performed preprocessing on the train and test sets:
I chose the 24h Open (USD) column for the time series analysis since it's relevant for price prediction.

Then I applied MinMaxScaler to scale the values between 0 and 1.

After that, I created a data structure using 31 timesteps, meaning each input sequence contains 31 previous values.

Finally, I reshaped the data to fit the expected input shape for RNN models.
----------------------------------------------------
5. 🧪 I optimized hyperparameters with Optuna:
I let it choose RNN type (LSTM/GRU), number of layers, units, dropout, optimizer, and learning rate.

I used early stopping during training.

The model was evaluated on training loss.

Ran 10 trials to find the best configuration.

--------------------------------------------------------
6. 🏗️ I built the final model using the best parameters:
I took the best hyperparameters found by Optuna.

Then I created a new model using those settings:

Used the chosen RNN type (LSTM or GRU)

Set the exact number of layers, units, and dropout rates

Applied the selected optimizer and learning rate

I compiled the model with mean_squared_error as the loss.

Finally, I trained this model on the full training data for 10 epochs with the best batch size.
---------------------------------------------------------
7. 🔮 I made predictions on the test set:
I used the final trained model to predict values on the test data.

I inverse-transformed both predictions and actual values to the original price scale.
---------------------------------------------------------
8. 📈 I visualized the results:
I plotted the real vs. predicted Bitcoin prices to see how well the model performed.
----------------------------------------------------------

9. 🔮 Predicting future bitcoin prices for next 30 days after test set
I used the last 31 days of scaled data as input to predict the next 30 days with my trained model.

I iteratively predicted each next day and updated the input sequence.

Then I inverse-transformed the predictions to original prices and created a DataFrame with future dates and predicted prices.
------------------------------------------------------------
10. Used 4 variables ('24h Open (USD)', '24h High (USD)', '24h Low (USD)', 'Closing Price (USD)') to predict Bitcoin Open Prices 🔮
