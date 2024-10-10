# Task 1: Manual Calculation Using Bayes' Theorem

## 1. Leave-One-Out Cross-Validation:
We use the first 13 rows as the training set and the last row as the test set.

**Test Row:**  
Outlook = rainy, Temperature = mild, Humidity = high, Windy = TRUE

---

## 2. Calculate Prior Probabilities:
The prior probabilities \(P(\text{Play} = \text{yes})\) and \(P(\text{Play} = \text{no})\) are calculated based on the training set.

From the training set (first 13 rows):
- Total number of instances: 13
- Instances where Play = yes: 8
- Instances where Play = no: 5

\[
P(\text{Play} = \text{yes}) = \frac{8}{13} \approx 0.615
\]
\[
P(\text{Play} = \text{no}) = \frac{5}{13} \approx 0.385
\]

---

## 3. Calculate Likelihoods:
Now, we calculate the likelihood of each feature given the class labels (Play = yes and Play = no).

### For Play = yes:
- **Outlook = rainy:**
  - Count of Outlook = rainy when Play = yes: 3
  - Total Play = yes instances: 8
  - \(P(\text{Outlook = rainy} \mid \text{Play} = \text{yes}) = \frac{3}{8} = 0.375\)

- **Temperature = mild:**
  - Count of Temperature = mild when Play = yes: 2
  - \(P(\text{Temperature = mild} \mid \text{Play} = \text{yes}) = \frac{2}{8} = 0.25\)

- **Humidity = high:**
  - Count of Humidity = high when Play = yes: 3
  - \(P(\text{Humidity = high} \mid \text{Play} = \text{yes}) = \frac{3}{8} = 0.375\)

- **Windy = TRUE:**
  - Count of Windy = TRUE when Play = yes: 2
  - \(P(\text{Windy = TRUE} \mid \text{Play} = \text{yes}) = \frac{2}{8} = 0.25\)

### For Play = no:
- **Outlook = rainy:**
  - Count of Outlook = rainy when Play = no: 1
  - Total Play = no instances: 5
  - \(P(\text{Outlook = rainy} \mid \text{Play} = \text{no}) = \frac{1}{5} = 0.2\)

- **Temperature = mild:**
  - Count of Temperature = mild when Play = no: 2
  - \(P(\text{Temperature = mild} \mid \text{Play} = \text{no}) = \frac{2}{5} = 0.4\)

- **Humidity = high:**
  - Count of Humidity = high when Play = no: 4
  - \(P(\text{Humidity = high} \mid \text{Play} = \text{no}) = \frac{4}{5} = 0.8\)

- **Windy = TRUE:**
  - Count of Windy = TRUE when Play = no: 2
  - \(P(\text{Windy = TRUE} \mid \text{Play} = \text{no}) = \frac{2}{5} = 0.4\)

---

## 4. Apply Bayes' Theorem:
We now calculate the posterior probabilities for both Play = yes and Play = no using Bayes' Theorem. Since \(P(X)\) (the total probability) is constant, we only calculate the numerator for both classes:

\[
\text{Posterior for Play = yes} \propto P(\text{Play = yes}) \times P(\text{Outlook = rainy} \mid \text{Play = yes}) \times P(\text{Temperature = mild} \mid \text{Play = yes}) \times P(\text{Humidity = high} \mid \text{Play} = \text{yes}) \times P(\text{Windy = TRUE} \mid \text{Play = yes})
\]

Substitute the values:

\[
\text{Posterior for Play = yes} \propto 0.615 \times 0.375 \times 0.25 \times 0.375 \times 0.25 = 0.00864
\]

Similarly:

\[
\text{Posterior for Play = no} \propto P(\text{Play = no}) \times P(\text{Outlook = rainy} \mid \text{Play = no}) \times P(\text{Temperature = mild} \mid \text{Play = no}) \times P(\text{Humidity = high} \mid \text{Play = no}) \times P(\text{Windy = TRUE} \mid \text{Play = no})
\]

Substitute the values:

\[
\text{Posterior for Play = no} \propto 0.385 \times 0.2 \times 0.4 \times 0.8 \times 0.4 = 0.009856
\]

---

## 5. Final Prediction:
Comparing the posterior probabilities:

- Posterior for Play = yes: \(0.00864\)
- Posterior for Play = no: \(0.009856\)

Since \(P(\text{Play = no}) > P(\text{Play = yes})\), the prediction for the test row is **Play = no**.

---

### Final Prediction: **No**
