# MLOps-Use-Cases
Machine Learning Use cases
Car Price Prediction - ML Report
1. Objective
The goal of this project is to predict used car prices using regression models and analyze feature
importance.
2. Data Preprocessing
Performed feature engineering, handled categorical variables using one-hot encoding, treated
outliers, and scaled numerical features.
The dataset underwent extensive preprocessing to ensure high-quality inputs for model
training. Initially, categorical variables such as fuel type, body type, and transmission
were transformed using one-hot encoding. Complex multi-value columns like
Comfort_Convenience, Entertainment_Media, Extras, and Safety_Security were
engineered into numerical features by counting the number of features present (e.g.,
num_comfort, num_media).
New features such as km_per_year and power_per_cc were created to capture more
meaningful relationships. Highly correlated and redundant features (e.g.,
Displacement_cc, power_per_cc, and total_features) were removed based on VIF
analysis to reduce multicollinearity.
Outliers were identified using statistical methods and treated appropriately to prevent
distortion in model learning. The target variable (price) was log-transformed to reduce
skewness and improve normality, as seen in the distribution plot. Finally, numerical
features were scaled using MinMaxScaler after train-test splitting to avoid data leakage.
3. Models Used
Three models were implemented: Linear Regression, Ridge Regression, and Lasso Regression.
PRICE AFTER LOG TRANSFORMATION
NORMALITY IN RESIDUAL DISTRIBUTION
4. Hyperparameter Tuning
Ridge best alpha: 2. Lasso best alpha: 0.0002.
Hyperparameter tuning was performed to identify the optimal regularization strength for
Ridge and Lasso regression models. Initially, a coarse grid of alpha values was tested to
identify the approximate optimal range. This was followed by fine-tuning within a
narrower range around the best-performing values.
For Ridge regression, the optimal alpha value was found to be 2, indicating that
moderate regularization helped stabilize coefficients without significantly reducing
model performance. For Lasso regression, the optimal alpha was 0.0002, suggesting that
only minimal regularization was required and most features were already relevant.
Cross-validation using negative mean absolute error (neg MAE) was used as the scoring
metric to ensure robust model selection. The tuning process confirmed that excessive
regularization leads to underfitting, while very small alpha values maintain performance
similar to linear regression.
FINE TUNED RIDGE
LASSO FINE TUNED
5. Model Performance
All three models—Linear Regression, Ridge, and Lasso—achieved very similar
predictive performance, with R² values close to 0.90, indicating that each model was
able to explain a high proportion of variance in car prices. This suggests that the
underlying relationships between features and the target variable are largely linear and
well captured even by the baseline model. Ridge regression demonstrated slightly better
stability by shrinking coefficients and reducing the impact of multicollinearity, which
led to more consistent and reliable predictions across different data splits. On the other
hand, Lasso regression, with a very small optimal alpha value, performed minimal
feature selection and retained most of the predictors, indicating that the majority of
features were relevant and contributed meaningfully to the model. Overall, the similarity
in performance highlights that the dataset was well-preprocessed, and no model had a
significant advantage in terms of predictive accuracy.
6. Key Insights and features
Price tends to increase with higher engine power, greater comfort features, and larger
vehicle weight, as these characteristics are often associated with premium or higher-end
vehicles. Cars with more powerful engines typically deliver better performance and
driving experience, which justifies a higher market price. Similarly, an increased number
of comfort features—such as climate control, advanced infotainment systems, and driver
assistance technologies—enhances the overall user experience and perceived value of
the vehicle. Heavier vehicles often belong to larger segments like SUVs or luxury
sedans, which naturally command higher prices due to their build quality, space, and
additional features.
On the other hand, price decreases with higher usage and age. Vehicles that have been
driven more frequently (higher kilometers per year) experience greater wear and tear,
reducing their resale value. Likewise, older cars depreciate over time due to factors such
as outdated technology, reduced efficiency, and increased maintenance requirements,
leading to lower market prices.
Feature importance analysis revealed that variables such as engine power (hp_kW),
usage (km_per_year), comfort features (num_comfort), and vehicle weight (Weight_kg)
had the strongest influence on price prediction.
Lasso regression was used for feature selection by shrinking less important feature
coefficients to zero. However, due to the small optimal alpha value, only a few features
were eliminated, indicating that most features were informative and contributed to the
model.
Additionally, multicollinearity analysis using VIF led to the removal of redundant
features such as Displacement_cc and total_features, improving model stability. Ridge
regression further helped by shrinking correlated feature coefficients, ensuring more
reliable and interpretable results.
.
7. Conclusion
The linear regression model was found to be sufficient for this problem, as it already achieved
strong performance with an R² score of around 0.90, indicating that it explained a large portion of
the variance in car prices. Regularisation techniques such as Ridge and Lasso did not lead to
significant improvements in performance because the dataset was already well-preprocessed,
with proper feature engineering, scaling, and handling of multicollinearity. Overfitting was not
observed, as the train and test R² scores were very close, showing that the model generalized
well to unseen data. Evaluation metrics such as Mean Squared Error (MSE), Root Mean
Squared Error (RMSE), Mean Absolute Error (MAE), and R² were used to assess performance,
and all three models produced similar results across these metrics. The optimal alpha values
were relatively small (Ridge ≈ 2, Lasso ≈ 0.0002), indicating that only mild regularisation was
needed. This further confirms that the base linear model was already stable and effective, and
additional regularisation provided only marginal benefits.
