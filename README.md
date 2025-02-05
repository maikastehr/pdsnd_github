>**Note**: Please **fork** the current Udacity repository so that you will have a **remote** repository in **your** Github account. Clone the remote repository to your local machine. Later, as a part of the project "Post your Work on Github", you will push your proposed changes to the remote repository in your Github account.

### Date created
1st June 2021

### Project Title
Bikeshare python project for Udacity Nanodegree Datascience Program

### Description
Bikeshare data from three different US contries (Chicago, Washington, New York City) has been automatically transformed and prepared for further calculations. It is an interactive project with User input to get more details on what the user would like to analyze within the given data. For example the User recieves details about most used bikesharing stations per city.
This project was there to get known to the python libraries numpry and pandas. As well as get more practice in working with Python and DataFrames. A readme file was created to give more information on what happens in my bikeshare.py file.

### Files used
chicago.csv, 
new_york_city.csv, 
washington.csv

### Credits
Repository forked from: https://github.com/udacity/pdsnd_github.git

### Used functions
Get user information and make sure one of the correct options was choosen. In this example for the city.

```
city = input("Which city (chicago, new york city, washington) would you like to analyze? ").lower()
    while city not in ("chicago", "new york city", "washington"):
       print("Please choose a city: chicago, new york city or washington")
       city = input("Which city (chicago, new york city, washington) would you like to analyze? ")
```

Get the necessary date-formatting using pandas library (date-formatting with function to_datetime: See also pandas documentation):
```
df['Start Time'] = pd.to_datetime(df["Start Time"])
df['month'] = df['Start Time'].dt.month
```

Get the filtered data with 'where' function from library. Filter the before given user input. Checkup data in pandas library.
```
if month != 'all':
    df = df.where(df['month'] == month_dict[month])
```

Get the most values with 'mode' function:
```
most_common_month = month_dict[int(df['month'].mode()[0])]
print("The most common month is: {}".format(most_common_month))
```

Get different statisticial data using 'sum', 'mean', 'value_counts', 'min', 'max' etc.
```
total_travel_time = pd.to_timedelta(df['Trip Duration'].sum(), unit = 's')
total_mean_time = pd.to_timedelta(df['Trip Duration'].mean(), unit = 's')
```

Get the first 5 rows of the data. Let the user interact if he wants to see 5 more rows:
```
start_loc = 0
while (view_data == 'yes'):
    print(df.iloc[start_loc : start_loc + 5])
    start_loc += 5
    view_data = input('Do you wish to continue? Enter yes or no. ').lower()
    if view_data == 'no':
        break
```