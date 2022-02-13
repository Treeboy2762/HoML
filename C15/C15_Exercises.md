1. Can you think of few applications for a seq2seq RNN? seq2vec RNN? vec2seq RNN?

seq2seq: transfer style to a piece of music / translate sentences
seq2vec: take a time series data for confirmed cases (COVID) and predict the future
vec2seq: take a vocabulary and generate a full sentence with it. Will be great for zao ju homework (Chinese).

2. How many dimensions must the inputs of an RNN layer have? What does each dimension represent? What about its outputs?

There are three dimensions: [batch_size, time_stamps, dimension]. **Batch size** is the number of inputs in the data. **Time stamps** Refer to the number of unique time points in the data. Dimension is the number of variables on a given time stamp.

The output depends on the *return_sequences* parameter, which, set to True, will return a 2D array, a 3D array otherwise.

3. If you want to build a deep seq2seq RNN, which RNN layers should have *return_sequences=True*? What about a seq2vec RNN?

All RNN layers in seq2seq should have the return_sequences param set to True. However, the last RNN layer of seq2vec RNN need not specify the return_sequence param as such.

4. Suppose you have a daily univariate time series, and you want to forecast the next seven days. Which RNN architecture is suitable for this task?

Train a seq2seq RNN with a TimeDistributed(keras.layers.Dense(7)) layer at the end.

5. What are the main difficulties in training RNNs? What are the solutions?

Exploding gradients (or unstable gradients) is a big problem. Layer normalization can be implemented between layers to address the problem. To do so, a custom layer-normalized cell should be implemented and called in each layer.

Another problem is processing a long input. This is tackled by using LSTM / GRU cells, which stores additional memory cells to keep track of earlier context. For instance, forget gate is implemented (1=open, 0=close) to determine whether or not to drop the earlier context.

6. Can I sketch the LSTM cell's architecture?

I'll try

7. Why would you want to use 1D convolutional layers in an RNN?

Unlike CNN, RNN has 1D data

8. Which neural network architecture could you use to classify videos?

seq2vec with WaveNet
