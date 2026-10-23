# 🔥 Data Science Units 1--7 --- NUMERICALS ONLY

## One-go worked problems \| Easy steps \| Exam-ready

**How to use:** Read each worked example once, cover the solution, and
redo the calculation yourself. This file deliberately skips
theory/revision notes and focuses on calculations, worked tables,
algorithm traces, and numerical-style R outputs.

**Source boundary:** Units 2--7 include calculation-based examples
matching the topics found in the available unit slides and our revision
context. Unit 1 appears mainly conceptual in the available material; no
specific calculation-heavy Unit 1 numerical was identifiable, so the
small statistics examples below are practice support rather than a claim
that they appeared in its slides. For any exact method shown by your
faculty, follow that method.

------------------------------------------------------------------------

# UNIT 1 --- Basic numerical practice

The available Unit 1 material is primarily introductory/conceptual.
These are basic data-handling calculations that can support introductory
questions.

## 1.1 Calculate mean, median and mode

**Question:** Find mean, median and mode of `4, 6, 6, 8, 11`.

**Step 1 --- Mean**

\[ Mean=`\frac{\text{sum of values}}{\text{number of values}}`{=tex}
=`\frac{4+6+6+8+11}{5}`{=tex}=`\frac{35}{5}`{=tex}=`\boxed{7}`{=tex} \]

**Step 2 --- Median**

Data are already sorted: `4, 6, 6, 8, 11`. The middle value is
(`\boxed{6}`{=tex}).

**Step 3 --- Mode**

The most frequent value is (`\boxed{6}`{=tex}).

**Answer:** Mean = 7, Median = 6, Mode = 6.

## 1.2 Percentage calculation

**Question:** Out of 80 students, 60 passed. Find pass percentage.

\[ Pass%=`\frac{60}{80}`{=tex}`\times100`{=tex}=`\boxed{75\%}`{=tex} \]

------------------------------------------------------------------------

# UNIT 2 --- Data Preprocessing numericals

## 2.1 Missing values: mean, median and mode imputation

Dataset: `10, 12, 14, ?, 24`

### Mean imputation

Ignore the missing value while calculating:

\[
Mean=`\frac{10+12+14+24}{4}`{=tex}=`\frac{60}{4}`{=tex}=`\boxed{15}`{=tex}
\]

Replace `?` with **15**.

### Median imputation

Available sorted values: `10, 12, 14, 24`.

Even number of values, so take the mean of the two middle values:

\[ Median=`\frac{12+14}{2}`{=tex}=`\boxed{13}`{=tex} \]

Replace `?` with **13**.

### Mode imputation

Dataset: `2, 3, 3, 4, 5, ?`. The most frequent value is 3, so replace
`?` with **3**.

## 2.2 Min--max normalization (0 to 1)

**Formula**

\[ x'=`\frac{x-x_{\min}}{x_{\max}-x_{\min}}`{=tex} \]

**Question:** Normalize values `50, 75, 100`.

Here (x\_{`\min`{=tex}}=50), (x\_{`\max`{=tex}}=100).

-   For 50: ((50-50)/(100-50)=`\boxed{0}`{=tex})
-   For 75: ((75-50)/(100-50)=25/50=`\boxed{0.5}`{=tex})
-   For 100: ((100-50)/(100-50)=`\boxed{1}`{=tex})

**Answer:** `0, 0.5, 1`.

## 2.3 Standardization / Z-score

\[ z=`\frac{x-\mu}{\sigma}`{=tex} \]

**Question:** Mean = 60, standard deviation = 10, value = 80.

\[ z=`\frac{80-60}{10}`{=tex}=`\frac{20}{10}`{=tex}=`\boxed{2}`{=tex} \]

Interpretation: 80 is two standard deviations above the mean.

## 2.4 Train--test split

**Question:** Split 1,200 records into 80% training and 20% testing.

\[ Training=1200(0.80)=`\boxed{960}`{=tex} \]

\[ Testing=1200(0.20)=`\boxed{240}`{=tex} \]

Check: (960+240=1200).

## 2.5 Percentage of sampled data

**Question:** A sample has 500 rows from a dataset of 20,000 rows. Find
the sample percentage.

\[
Sample%=`\frac{500}{20000}`{=tex}`\times100`{=tex}=`\boxed{2.5\%}`{=tex}
\]

## 2.6 Feature reduction percentage

**Question:** Features reduce from 80 to 20. Find the reduction
percentage.

\[ Reduction%=`\frac{Old-New}{Old}`{=tex}`\times100`{=tex}
=`\frac{80-20}{80}`{=tex}`\times100`{=tex}
=`\frac{60}{80}`{=tex}`\times100`{=tex}=`\boxed{75\%}`{=tex} \]

## 2.7 Label encoding and one-hot encoding

Categories: `Blue, Green, Red`.

One possible label mapping:

  Colour     Label
  -------- -------
  Blue           0
  Green          1
  Red            2

For **Green**, one-hot vector in order `[Blue, Green, Red]` is:

\[ `\boxed{[0,1,0]}`{=tex} \]

Label values depend on the chosen factor/level order; use the order
stated in the question.

## 2.8 R output mini-question

``` r
x <- c(10, 20, 30)
mean(x)
median(x)
min(x)
max(x)
(x - min(x)) / (max(x) - min(x))
```

Output: - Mean = `20` - Median = `20` - Minimum = `10` - Maximum =
`30` - Normalized vector = `0, 0.5, 1`

------------------------------------------------------------------------

# UNIT 3 --- Concept Learning numerical-style traces

These are algorithm-tracing questions: the "answer" is the final
hypothesis/boundary rather than a numeric value.

## 3.1 Find-S --- complete worked trace

Training data:

  Example   Sky     Temp   Humidity   Wind     Play
  --------- ------- ------ ---------- -------- ------
  1         Sunny   Warm   Normal     Strong   Yes
  2         Sunny   Warm   High       Strong   Yes
  3         Rainy   Cold   High       Strong   No
  4         Sunny   Warm   High       Weak     Yes

Start with the most specific hypothesis:

\[
S_0=`\langle`{=tex}`\emptyset`{=tex},`\emptyset`{=tex},`\emptyset`{=tex},`\emptyset`{=tex}`\rangle`{=tex}
\]

-   Example 1 is positive:

\[ S_1=`\langle `{=tex}Sunny,Warm,Normal,Strong`\rangle`{=tex} \]

-   Example 2 is positive. Humidity changes from Normal to High, so
    generalize that attribute:

\[ S_2=`\langle `{=tex}Sunny,Warm,?,Strong`\rangle`{=tex} \]

-   Example 3 is negative. Find-S ignores negative examples, so no
    change:

\[ S_3=`\langle `{=tex}Sunny,Warm,?,Strong`\rangle`{=tex} \]

-   Example 4 is positive. Wind changes from Strong to Weak, so
    generalize Wind:

\[ S_4=`\boxed{\langle Sunny,Warm,?,?,\rangle}`{=tex} \]

**Final Find-S hypothesis:** `<Sunny, Warm, ?, ?>`.

## 3.2 Candidate Elimination --- boundary trace

Use the same four examples. Initial boundaries:

\[
S_0=`\langle`{=tex}`\emptyset`{=tex},`\emptyset`{=tex},`\emptyset`{=tex},`\emptyset`{=tex}`\rangle`{=tex}
\]

\[ G_0=`\langle `{=tex}?,?,?,?`\rangle`{=tex} \]

After Example 1: `Sunny Warm Normal Strong → Yes`

\[ S_1=`\langle `{=tex}Sunny,Warm,Normal,Strong`\rangle`{=tex} \]

\[ G_1={`\langle `{=tex}?,?,?,?`\rangle`{=tex}} \]

After Example 2: `Sunny Warm High Strong → Yes`

\[ S_2=`\langle `{=tex}Sunny,Warm,?,Strong`\rangle`{=tex} \]

After Example 3: `Rainy Cold High Strong → No`, specialize G minimally
so it excludes the negative example while remaining consistent with S.
The slide's candidate specializations include:

-   `<Sunny, ?, ?, ?>`
-   `<?, Warm, ?, ?>`
-   `<?, ?, Normal, ?>`

The candidate `< ?, ?, Normal, ?>` is inconsistent with the positive
example having Humidity = High, so remove it.

After Example 4: `Sunny Warm High Weak → Yes`

\[ S\_{final}=`\boxed{\langle Sunny,Warm,?,?\rangle}`{=tex} \]

The slide's final general boundary is:

\[
G\_{final}=`\boxed{\{\langle Sunny,?,?,?\rangle,\langle ?,Warm,?,?\rangle\}}`{=tex}
\]

**Exam note:** Candidate Elimination is sensitive to the exact
hypothesis representation and minimal-specialization rule taught in
class; use the stepwise convention shown in your PPT.

## 3.3 Version-space count

Suppose:

\[ H={h_1,h_2,h_3,h_4,h_5,h_6} \]

Training examples eliminate (h_2,h_4,h_6).

\[ VS=H-{h_2,h_4,h_6}=`\boxed{\{h_1,h_3,h_5\}}`{=tex} \]

Number of consistent hypotheses = (`\boxed{3}`{=tex}).

## 3.4 VC dimension

If a hypothesis class can shatter every labeling of 3 points, but cannot
shatter 4 points, then:

\[ `\boxed{VCdim(H)=3}`{=tex} \]

This is determined from shattering ability, not by counting the
hypotheses.

------------------------------------------------------------------------

# UNIT 4 --- Basics of R numerical questions

## 4.1 Vector operations

``` r
x <- c(10, 20, 30, 40)
sum(x)
mean(x)
median(x)
min(x)
max(x)
length(x)
```

Expected output:

  Expression      Output
  ------------- --------
  `sum(x)`           100
  `mean(x)`           25
  `median(x)`         25
  `min(x)`            10
  `max(x)`            40
  `length(x)`          4

## 4.2 R indexing and filtering

``` r
x <- c(12, 25, 8, 30, 17)
x[3]
x[x > 15]
```

-   `x[3]` → `8`
-   `x[x > 15]` → `25, 30, 17`

R indexing starts at **1**, not 0.

## 4.3 Data frame average and filtering

``` r
students <- data.frame(
  name = c("Aman", "Riya", "Raj"),
  marks = c(70, 80, 90)
)
mean(students$marks)
students[students$marks > 75, ]
```

-   Average marks = ((70+80+90)/3=`\boxed{80}`{=tex})
-   Filtered rows: Riya (80), Raj (90).

## 4.4 Scaling in R

``` r
x <- c(10, 20, 30)
(x - min(x)) / (max(x) - min(x))
```

Output: `0, 0.5, 1`.

``` r
x <- c(10, 20, 30)
as.numeric(scale(x))
```

Using sample standard deviation in R, output is approximately:

`-1, 0, 1`.

## 4.5 One-hot encoding in R

``` r
d <- data.frame(colour = factor(c("Blue", "Green", "Red")))
model.matrix(~ colour - 1, data = d)
```

Conceptual output (columns can follow factor-level order):

    colourBlue   colourGreen   colourRed
  ------------ ------------- -----------
             1             0           0
             0             1           0
             0             0           1

## 4.6 Data reduction

Old feature count = 1,000; new count = 100.

\[
Reduction%=`\frac{1000-100}{1000}`{=tex}`\times100`{=tex}=`\boxed{90\%}`{=tex}
\]

------------------------------------------------------------------------

# UNIT 5 --- Model Fitting in R numericals

## 5.1 Linear regression: use the equation

\[ `\hat{y}`{=tex}=b_0+b_1x \]

**Question:** (`\hat{y}`{=tex}=10+5x). Find prediction when (x=4).

\[ `\hat{y}`{=tex}=10+5(4)=10+20=`\boxed{30}`{=tex} \]

## 5.2 Calculate slope and intercept

Data points: ((1,2),(2,4),(3,6)).

\[ `\bar`{=tex}{x}=`\frac{1+2+3}{3}`{=tex}=2,`\qquad`{=tex}
`\bar`{=tex}{y}=`\frac{2+4+6}{3}`{=tex}=4 \]

Slope:

\[
b_1=`\frac{\sum(x_i-\bar{x})(y_i-\bar{y})}{\sum(x_i-\bar{x})^2}`{=tex}
\]

Numerator:

\[ (1-2)(2-4)+(2-2)(4-4)+(3-2)(6-4)=2+0+2=4 \]

Denominator:

\[ (1-2)^2+(2-2)^2+(3-2)\^2=1+0+1=2 \]

\[ b_1=4/2=`\boxed{2}`{=tex} \]

Intercept:

\[ b_0=`\bar`{=tex}{y}-b_1`\bar`{=tex}{x}=4-2(2)=`\boxed{0}`{=tex} \]

Regression line:

\[ `\boxed{\hat{y}=2x}`{=tex} \]

For (x=4), prediction = (`\boxed{8}`{=tex}).

## 5.3 Residual, SSE, MSE, RMSE

Actual: `3, 5, 7`\
Predicted: `2, 5, 8`

  ---------------------------------------------------------------------------
         Actual (y)          Predicted                Error     Squared error
                      (`\hat `{=tex}y)   (y-`\hat `{=tex}y) 
  ----------------- ------------------ -------------------- -----------------
                  3                  2                    1                 1

                  5                  5                    0                 0

                  7                  8                   -1                 1

          **Total**                                               **SSE = 2**
  ---------------------------------------------------------------------------

\[ SSE=1+0+1=`\boxed{2}`{=tex} \]

\[ MSE=`\frac{SSE}{n}`{=tex}=`\frac{2}{3}`{=tex}=`\boxed{0.6667}`{=tex}
\]

\[ RMSE=`\sqrt{0.6667}`{=tex}`\approx`{=tex}`\boxed{0.8165}`{=tex} \]

## 5.4 Logistic regression sigmoid

\[ p=`\frac{1}{1+e^{-z}}`{=tex} \]

**Case 1:** (z=0)

\[ p=`\frac{1}{1+e^0}`{=tex}=`\frac{1}{2}`{=tex}=`\boxed{0.5}`{=tex} \]

**Case 2:** (z=`\ln`{=tex}(3))

Since (e\^{-`\ln 3`{=tex}}=1/3):

\[ p=`\frac{1}{1+1/3}`{=tex}=`\frac{1}{4/3}`{=tex}=`\boxed{0.75}`{=tex}
\]

With threshold 0.5, 0.75 is classified as positive.

## 5.5 Decision tree: Gini impurity

\[ Gini=1-`\sum `{=tex}p_i\^2 \]

**Question:** 10 samples: 6 Yes and 4 No.

\[ p(Yes)=0.6,`\quad `{=tex}p(No)=0.4 \]

\[ Gini=1-(0.6^2+0.4^2)=1-(0.36+0.16)=`\boxed{0.48}`{=tex} \]

**Pure node:** 10 Yes, 0 No.

\[ Gini=1-(1^2+0^2)=`\boxed{0}`{=tex} \]

### Weighted Gini after a split

Parent has 10 records. Split gives: - Left: 4 records, Gini = 0.375 -
Right: 6 records, Gini = 0.4444

\[
Gini\_{split}=`\frac{4}{10}`{=tex}(0.375)+`\frac{6}{10}`{=tex}(0.4444)
\]

\[ =0.15+0.26664`\approx`{=tex}`\boxed{0.4167}`{=tex} \]

## 5.6 Entropy

\[ H(S)=-`\sum `{=tex}p_i`\log`{=tex}\_2p_i \]

For 6 Yes and 4 No:

\[ H(S)=-\[0.6`\log`{=tex}\_2(0.6)+0.4`\log`{=tex}\_2(0.4)\] \]

Using (`\log`{=tex}\_2(0.6)`\approx-0.737`{=tex}) and
(`\log`{=tex}\_2(0.4)`\approx-1.322`{=tex}):

\[ H(S)`\approx`{=tex}-\[0.6(-0.737)+0.4(-1.322)\] \]

\[ H(S)`\approx`{=tex}-\[-0.4422-0.5288\]=`\boxed{0.971\ bits}`{=tex} \]

Pure node entropy = (`\boxed{0}`{=tex}).

## 5.7 Information Gain

\[ IG=H(parent)-H(after split) \]

Parent entropy = 0.971. A split produces two equally sized children with
entropy 0 and 0.722.

\[ H(after)=0.5(0)+0.5(0.722)=0.361 \]

\[ IG=0.971-0.361=`\boxed{0.610}`{=tex} \]

## 5.8 Naïve Bayes / Bayes theorem

\[ P(C\|X)=`\frac{P(X|C)P(C)}{P(X)}`{=tex} \]

Suppose: - (P(Spam)=0.4) - (P(Offer\|Spam)=0.7) - (P(NotSpam)=0.6) -
(P(Offer\|NotSpam)=0.1)

Unnormalized class scores:

\[ Spam=0.7(0.4)=0.28 \]

\[ NotSpam=0.1(0.6)=0.06 \]

Normalize:

\[ P(Spam\|Offer)=`\frac{0.28}{0.28+0.06}`{=tex}
=`\frac{0.28}{0.34}`{=tex}`\approx`{=tex}`\boxed{0.8235}`{=tex} \]

Spam probability ≈ **82.35%** in this example.

## 5.9 Euclidean distance (K-Means)

For points (A=(1,2)) and (B=(4,6)):

\[ d=`\sqrt{(4-1)^2+(6-2)^2}`{=tex}
=`\sqrt{9+16}`{=tex}=`\sqrt{25}`{=tex}=`\boxed{5}`{=tex} \]

## 5.10 Find a centroid

Points: ((2,4),(4,6),(6,8)).

\[ `\bar`{=tex}{x}=`\frac{2+4+6}{3}`{=tex}=4 \]

\[ `\bar`{=tex}{y}=`\frac{4+6+8}{3}`{=tex}=6 \]

Centroid = (`\boxed{(4,6)}`{=tex}).

## 5.11 K-Means WCSS

Points: ((1,1),(2,2),(3,3)), centroid ((2,2)).

Squared distances: - ((1,1)): ((1-2)^2+(1-2)^2=2) - ((2,2)): (0) -
((3,3)): ((3-2)^2+(3-2)^2=2)

\[ WCSS=2+0+2=`\boxed{4}`{=tex} \]

## 5.12 Assign point to nearest centroid

Point (P=(3,2)); centroid A = (1,2), B = (5,2).

\[ d(P,A)=`\sqrt{(3-1)^2+(2-2)^2}`{=tex}=2 \]

\[ d(P,B)=`\sqrt{(3-5)^2+(2-2)^2}`{=tex}=2 \]

Both distances equal 2, so the point is tied between the centroids; a
specified tie rule/implementation decides assignment.

## 5.13 SVM decision boundary

Boundary: (x_1+x_2-5=0).

Calculate (f(x)=x_1+x_2-5): - Point (4,3): (4+3-5=`\boxed{2}`{=tex}) →
positive side. - Point (1,2): (1+2-5=`\boxed{-2}`{=tex}) → negative
side. - Point (2,3): (2+3-5=`\boxed{0}`{=tex}) → on the boundary.

The value indicates which side of the boundary the point lies on; it is
not a probability.

## 5.14 R code numerical outputs

``` r
df <- data.frame(x = c(1, 2, 3), y = c(2, 4, 6))
model <- lm(y ~ x, data = df)
predict(model, newdata = data.frame(x = 4))
```

Predicted value = `8`.

``` r
actual <- c(3, 5, 7)
predicted <- c(2, 5, 8)
mean((actual - predicted)^2)
sqrt(mean((actual - predicted)^2))
```

-   MSE ≈ `0.6667`
-   RMSE ≈ `0.8165`

------------------------------------------------------------------------

# UNIT 6 --- Visualization numericals

## 6.1 Box plot: quartiles, IQR and outlier fences

Dataset from the Unit 6 slide:

`10, 12, 15, 18, 20, 22, 25, 28, 100`

The slide's worked convention gives: - (Q_1=15) - Median = 20 - (Q_3=25)

IQR:

\[ IQR=Q_3-Q_1=25-15=`\boxed{10}`{=tex} \]

Lower fence:

\[ Q_1-1.5(IQR)=15-1.5(10)=15-15=`\boxed{0}`{=tex} \]

Upper fence:

\[ Q_3+1.5(IQR)=25+1.5(10)=25+15=`\boxed{40}`{=tex} \]

Since (100\>40), **100 is a potential outlier**.

**Follow the quartile convention shown in your PPT.** Different
software/textbooks can calculate quartiles differently.

## 6.2 Z-score outlier detection

Mean = 50, standard deviation = 10, value = 85.

\[
z=`\frac{x-\mu}{\sigma}`{=tex}=`\frac{85-50}{10}`{=tex}=`\boxed{3.5}`{=tex}
\]

Using the common (\|z\|\>3) rule, it is flagged as a potential outlier.

## 6.3 Histogram frequencies

Values: `12, 15, 18, 20, 22, 25, 30, 35`.

Using the unit example's listed frequencies:

  Bin           Frequency
  ----------- -----------
  10--20                3
  20--30                4
  30--40                1
  **Total**         **8**

\[ Total=3+4+1=`\boxed{8}`{=tex} \]

Boundary values such as 20 and 30 may be assigned differently depending
on whether bins include the left or right endpoint. In an exam, apply
the stated interval convention.

## 6.4 Correlation interpretation

Given a correlation matrix:

                 Age   Salary   Experience
  ------------ ----- -------- ------------
  Age            1.0      0.8          0.7
  Salary         0.8      1.0          0.9
  Experience     0.7      0.9          1.0

-   Age--Salary = **0.8** → strong positive linear association.
-   Salary--Experience = **0.9** → stronger positive association than
    Age--Salary in this table.
-   Diagonal values = **1** because each variable correlates perfectly
    with itself.

Correlation is between −1 and +1.

## 6.5 Data balancing and class ratio

Dataset: - Class Yes = 950 - Class No = 50 - Total = 1,000

\[ Yes%=`\frac{950}{1000}`{=tex}`\times100`{=tex}=`\boxed{95\%}`{=tex}
\]

\[ No%=`\frac{50}{1000}`{=tex}`\times100`{=tex}=`\boxed{5\%}`{=tex} \]

Ratio:

\[ 950:50=`\boxed{19:1}`{=tex} \]

If a classifier predicts Yes for every record: - Correct predictions =
950 - Incorrect predictions = 50 - Accuracy =
(950/1000`\times100`{=tex}=`\boxed{95\%}`{=tex}) - Recall for the No
class = (`\boxed{0\%}`{=tex}), because it never predicts No correctly.

This demonstrates why accuracy can be misleading on imbalanced data.

## 6.6 R output practice

``` r
x <- c(10, 12, 15, 18, 20, 22, 25, 28, 100)
IQR(x)
summary(x)
```

For a specific exam quartile answer, use the quartile convention given
in the slide/question; R's `IQR()` uses R's quantile convention, which
may differ from a hand-worked slide example.

``` r
study_hours <- c(2, 4, 6, 8)
marks <- c(40, 55, 70, 90)
cor(study_hours, marks)
```

The correlation is positive and close to +1, showing a strong positive
linear relationship.

------------------------------------------------------------------------

# UNIT 7 --- Performance Evaluation numericals

## 7.1 Error

Actual price = ₹50 lakh; predicted price = ₹45 lakh.

\[ Error=Actual-Predicted=50-45=`\boxed{5\text{ lakh}}`{=tex} \]

The model underpredicted by ₹5 lakh. Absolute error = ₹5 lakh.

## 7.2 MSE and RMSE

Actual: `50, 60, 70`\
Predicted: `48, 65, 68`

    Actual   Predicted   Error (Actual-Predicted)   Squared error
  -------- ----------- -------------------------- ---------------
        50          48                          2               4
        60          65                         -5              25
        70          68                          2               4
                                          **SSE**          **33**

\[ SSE=4+25+4=`\boxed{33}`{=tex} \]

\[ MSE=`\frac{33}{3}`{=tex}=`\boxed{11}`{=tex} \]

\[ RMSE=`\sqrt{11}`{=tex}`\approx`{=tex}`\boxed{3.317}`{=tex} \]

## 7.3 Confusion matrix --- identify TP, TN, FP, FN

  Actual / Predicted     Predicted Positive   Predicted Negative
  -------------------- -------------------- --------------------
  Actual Positive                   TP = 40              FN = 10
  Actual Negative                    FP = 5              TN = 45

Total:

\[ N=TP+TN+FP+FN=40+45+5+10=`\boxed{100}`{=tex} \]

## 7.4 Accuracy

\[ Accuracy=`\frac{TP+TN}{TP+TN+FP+FN}`{=tex} \]

\[
=`\frac{40+45}{100}`{=tex}=`\frac{85}{100}`{=tex}=`\boxed{85\%}`{=tex}
\]

## 7.5 Precision

\[ Precision=`\frac{TP}{TP+FP}`{=tex}
=`\frac{40}{40+5}`{=tex}=`\frac{40}{45}`{=tex} \]

\[ Precision`\approx0.8889`{=tex}=`\boxed{88.89\%}`{=tex} \]

## 7.6 Recall / Sensitivity

\[ Recall=`\frac{TP}{TP+FN}`{=tex}
=`\frac{40}{40+10}`{=tex}=`\frac{40}{50}`{=tex} =`\boxed{80\%}`{=tex} \]

Sensitivity = Recall = **80%**.

## 7.7 Specificity

\[ Specificity=`\frac{TN}{TN+FP}`{=tex}
=`\frac{45}{45+5}`{=tex}=`\frac{45}{50}`{=tex} =`\boxed{90\%}`{=tex} \]

## 7.8 F1-score

\[ F1=2`\frac{Precision\times Recall}{Precision+Recall}`{=tex} \]

Using exact values (Precision=40/45), (Recall=40/50):

\[ F1=2`\frac{(0.8889)(0.8)}{0.8889+0.8}`{=tex}
`\approx0.8421`{=tex}=`\boxed{84.21\%}`{=tex} \]

## 7.9 Second confusion-matrix example

Given TP = 30, TN = 50, FP = 10, FN = 10.

Total = (30+50+10+10=100).

-   Accuracy = ((30+50)/100=`\boxed{80\%}`{=tex})
-   Precision = (30/(30+10)=`\boxed{75\%}`{=tex})
-   Recall = (30/(30+10)=`\boxed{75\%}`{=tex})
-   Sensitivity = (`\boxed{75\%}`{=tex})
-   Specificity = (50/(50+10)=50/60=`\boxed{83.33\%}`{=tex})
-   F1 = (2(0.75)(0.75)/(0.75+0.75)=`\boxed{75\%}`{=tex})

## 7.10 R calculation --- metrics from counts

``` r
TP <- 40
TN <- 45
FP <- 5
FN <- 10

accuracy <- (TP + TN) / (TP + TN + FP + FN)
precision <- TP / (TP + FP)
recall <- TP / (TP + FN)
sensitivity <- recall
specificity <- TN / (TN + FP)
f1 <- 2 * precision * recall / (precision + recall)

accuracy     # 0.85
precision    # 0.8888889
recall       # 0.8
sensitivity  # 0.8
specificity  # 0.9
f1           # about 0.8421053
```

------------------------------------------------------------------------

# FINAL NUMERICAL FORMULA LIST

  --------------------------------------------------------------------------------------------------------------------------------
  Numerical type                      Formula
  ----------------------------------- --------------------------------------------------------------------------------------------
  Mean                                (`\sum `{=tex}x_i/n)

  Min--max normalization              ((x-x\_{min})/(x\_{max}-x\_{min}))

  Z-score                             ((x-`\mu`{=tex})/`\sigma`{=tex})

  Train count                         Total × training fraction

  Test count                          Total × testing fraction

  Percentage                          Part / Total × 100

  Feature reduction %                 ((Old-New)/Old × 100)

  Regression prediction               (`\hat `{=tex}y=b_0+b_1x)

  Regression slope                    (`\sum`{=tex}(x_i-`\bar `{=tex}x)(y_i-`\bar `{=tex}y)/`\sum`{=tex}(x_i-`\bar `{=tex}x)\^2)

  Intercept                           (`\bar `{=tex}y-b_1`\bar `{=tex}x)

  Residual                            Actual − Predicted

  SSE                                 (`\sum`{=tex}(Actual-Predicted)\^2)

  MSE                                 SSE / n

  RMSE                                (`\sqrt{MSE}`{=tex})

  Sigmoid                             (1/(1+e\^{-z}))

  Gini                                (1-`\sum `{=tex}p_i\^2)

  Entropy                             (-`\sum `{=tex}p_i`\log`{=tex}\_2(p_i))

  Information Gain                    Parent entropy − weighted child entropy

  Bayes                               (P(C

  Euclidean distance (2D)             (`\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}`{=tex})

  Centroid coordinate                 Mean of that coordinate

  IQR                                 (Q_3-Q_1)

  Lower outlier fence                 (Q_1-1.5(IQR))

  Upper outlier fence                 (Q_3+1.5(IQR))

  Accuracy                            ((TP+TN)/(TP+TN+FP+FN))

  Precision                           (TP/(TP+FP))

  Recall / Sensitivity                (TP/(TP+FN))

  Specificity                         (TN/(TN+FP))

  F1                                  (2(Precision×Recall)/(Precision+Recall))
  --------------------------------------------------------------------------------------------------------------------------------

**Exam method:** write the formula, substitute values, show arithmetic,
and box the final result. For algorithm traces, show each update
row-by-row.
