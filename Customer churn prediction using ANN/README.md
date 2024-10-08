Dataset = Telecom customer churn dataset from kaggle

Exploratory data analysis

Shape of dataset = (7043, 21)
Number of features (20) + Target feature (1) 
Data type of the features: object, int64, float64
Features with numeric data type:
> SeniorCitizen
> tenure
> MonthlyCharge

There were presence of null string in TotalCharges column. This must be addressed.
But Pandas will recognise a value as null if it is a np.nan object, which will print as NaN in the DataFrame.
Your missing values are probably empty strings, which Pandas doesn't recognise as null.
To fix this, you can convert the empty stings (or whatever is in your empty cells) to np.nan objects
using replace(), and then call dropna()on your DataFrame to delete rows with null values.

Eg: customer_data['TotalCharges'].replace(' ', np.nan, inplace=True)

Now that the null strings were addressed, the existing data type of the
column which is object type can be converted to the numeric type using:

pd.to_numeric(column name)

The columns like Partners, PhoneService, OnlineBackup etc have (Yes and No) as the value.
Replacing Yes and No with 1 and 0 respectively.

PaymentMethod: ['Electronic check' 'Mailed check' 'Bank transfer (automatic)'
 'Credit card (automatic)']

Here the each values are converted into the column names.

After converting for all the columns with similar value types, the number of 
column increased from 21 to 27.

Since, each feature values are of type numeric, stadardizing the columns like tenure to
have value in between 0 and 1 using min max scaler.

Architecture of neural network

input layer -> no of neurons = 26 (input shape)
1st hidden layer -> no of neurons = 22, activation fucntion =  relu
2nd hidden layer -> no of neurons = 26, activation function = relu
output layer -> no of neurons = 1, activation function = sigmoid

Optimizer used = adam
