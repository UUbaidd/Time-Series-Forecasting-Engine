
1. The Problem (The Why): Stock data is difficult due to non-stationary patterns and noise. This project implements a stacked LSTM (Long Short-Term Memory) network to capture long-term dependencies in temporal data, moving beyond simple moving averages.

2. Engineering Trade-offs

Data Scaling: I utilized MinMaxScaler to squash values between 0 and 1 before feeding them into the LSTM.

Reasoning: LSTMs are sensitive to the scale of input data; without this, the gradients could vanish or explode during backpropagation.

Windowing Strategy: I implemented a sliding window approach (e.g., using the past 60 days to predict the next 1). This transforms a sequence into a supervised learning problem.

3. Performance Verification

Inverse Transformation: As seen in my implementation, I perform an inverse_transform on the predictions.

This ensures that the error metrics (like RMSE) are calculated in the original domain units (e.g., Dollars) rather than the scaled 0-1 range, making the results interpretable for business stakeholders.

Visual Convergence: The graphs show the model successfully capturing the general trend and volatility of the test set, proving the architecture is effectively learning the underlying distribution.
