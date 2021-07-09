## Visual exploratory data analysis

## pandas line plots

```python
df.plot(x='column_name' , y='column_name or list of column_names')

plt.xlabel('Xaxis description')
plt.ylabel('Yaxis description')
plt.title('Title')

plt.show()
```
## pandas scatter plots

```python
df.plot(kind='scatter', x ='column_name', y ='column_name', s=size)
```
## pandas box plots
```python
cols = ['requiured','columns']
df[cols].plot(kind='box',subplots=True)
plt.show()
```

## pandas hist, pdf and cdf

```python
# This formats the plots such that they appear on separate rows
fig, axes = plt.subplots(nrows=2, ncols=1)

# Plot the PDF
df.fraction.plot(ax=axes[0], kind='hist', normed=True, bins=30, range=(0,.3))
plt.show()

# Plot the CDF
df.fraction.plot(ax=axes[1], kind='hist', normed=True, bins=30, cumulative=True, range=(0,.3))
plt.show()
```
## Statistical exploratory data analysis
### Describe
```python
df.describe()
```
>>Prints all the min max and quartiles of all the columns
 ### Min & Max
```python
df.min() or df.max()
```
>>Gives min or max of all the columns

### Count
```python
print(df.count())
```
>>prints the number of non missing values in all columns


### Quantiles
```python
print(df.quantile([0.05, 0.95]))
```
## Separating populations with Boolean indexing

```python
filtered_df=df.loc[df[column_name]='Value']
```
## Creating and using a DatetimeIndex
```python
# Prepare a format string: time_format
time_format = '%Y-%m-%d %H:%M'

# Convert date_list into a datetime object: my_datetimes
my_datetimes = pd.to_datetime(date_list, format=time_format)  

# Construct a pandas Series using temperature_list and my_datetimes: time_series
time_series = pd.Series(temperature_list, index=my_datetimes)

['20100101 00:00',
 '20100101 01:00',
 '20100101 02:00',
 '20100101 03:00',]
 
 2010-01-01 00:00:00    46.2
2010-01-01 01:00:00    44.6
2010-01-01 02:00:00    44.1
```
## Partial string indexing and slicing
```python
# Extract the hour from 9pm to 10pm on '2010-10-11': ts1
ts1 = ts0.loc['2010-10-11 21:00:00':'2010-10-11 22:00:00']

# Extract '2010-07-04' from ts0: ts2
ts2 = ts0.loc['2010-07-04']

# Extract data from '2010-12-15' to '2010-12-31': ts3
ts3 = ts0.loc['2010-12-15':'2010-12-31']
```
## Reindexing the Index
```python
ts4 = ts2.reindex(ts1.index, method='ffill')
```
## Resampling and frequency
```python
df1 = df['Temperature'].resample('6h').mean()

# Downsample to daily data and count the number of data points: df2
df2 = df['Temperature'].resample('D').count()
```

## Separating and resampling
```python
february = df['Temperature']['2010-Feb']

# Downsample to obtain the daily lowest temperatures in February: february_lows
february_lows = february.resample('D').min()
```
## Rolling mean and frequency
```python
# Extract data from 2010-Aug-01 to 2010-Aug-15: unsmoothed
unsmoothed = df['Temperature']['2010-Aug-01':'2010-Aug-15']

# Apply a rolling mean with a 24 hour window: smoothed
smoothed = unsmoothed.rolling(window=24).mean()

# Create a new DataFrame with columns smoothed and unsmoothed: august
august = pd.DataFrame({'smoothed':smoothed, 'unsmoothed':unsmoothed}
```
## Manipulating pandas time series
## Method chaining and filtering
```python
# Strip extra whitespace from the column names: df.columns
df.columns = df.columns.str.strip()

# Extract data for which the destination airport is Dallas: dallas
dallas = df['Destination Airport'].str.contains('DAL')

# Compute the total number of Dallas departures each day: daily_departures
daily_departures = dallas.resample('D').sum()

# Generate the summary statistics for daily Dallas departures: stats
stats = daily_departures.describe()
```
```python
ts2_interp = ts2.reindex(ts1.index).interpolate(how='linear')

# Compute the absolute difference of ts1 and ts2_interp: differences 
differences = np.abs(ts1 - ts2_interp)

# Generate and print summary statistics of the differences
print(differences.describe())
```

## Time zones and conversion

```python
mask = df['Destination Airport'] == 'LAX'

# Use the mask to subset the data: la
la = df[mask]

# Combine two columns of data to create a datetime series: times_tz_none 
times_tz_none = pd.to_datetime( la['Date (MM/DD/YYYY)'] + ' ' + la['Wheels-off Time'] )

# Localize the time to US/Central: times_tz_central
times_tz_central = times_tz_none.dt.tz_localize('US/Central')

# Convert the datetimes from US/Central to US/Pacific
times_tz_pacific = times_tz_central.dt.tz_convert('US/Pacific')
```

## Plotting time series, datetime indexing
```python
df.plot()
plt.show()

# Convert the 'Date' column into a collection of datetime objects: df.Date
df.Date = pd.to_datetime(df.Date)

# Set the index to be the converted 'Date' column
df.set_index('Date', inplace=True)

# Re-plot the DataFrame to see that the axis is now datetime aware!
df.plot()
plt.show()
```
