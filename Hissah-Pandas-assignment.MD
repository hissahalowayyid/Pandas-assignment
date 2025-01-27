Week 2, Assignment C1:

Exploring some Crowdfunding Data with Pandas

Hissah Alowayyid

# Objective 1.
#Use this cell to import your packages
import pandas as pd

# Objective 2.
# Complete the following cell using pandas.read_csv() 
# and the file included in this assignment.
# Tip: set index_col to 'created_at' and parse_dates=True
#df = pd.read_csv('kickstarter_sample.csv',index_col='created_at',parse_dates=True)

df = pd.read_csv('kickstarter_sample.csv',index_col='created_at',parse_dates=True)

#assert len(df)>0
# if you get an error, try again

# Objective 3.
# Use this cell to examine the data you've loaded, specifically note the headers and index
df

# Objective 4.
# Create a slice from the years 2018 to 2021

df = df.loc['2018':'2021']
df

# Objective 5.
# slice into the following collumns
# 'backers_count','blurb','country','usd_pledged','state'

df = df[['backers_count','blurb','country','usd_pledged','state']]
df

# Objective 6.
# Use integer-location based indexing to exclude the last 3 row of data

df = df.iloc[:-3]
df

# Objective 7.
# Inside of your slice, count the total number of backers

total_backers = df['backers_count'].sum()
total_backers

# Objective 8.
# Use a mask to split the DataFrame into two parts and assign each to a variable.
# Here we will use state.
# Examine the state variable above.
# and create one variable for on-going vs concluded projects.

ongoing_df = df[df.state=='live'] 
    
concluded_df = df[df.state=='successful']

# Objective 9.
# Examine on-going projects
ongoing_df

# Objective 10.
# Examine concluded projects
concluded_df

# Objective 11.
# Use the above DataFrames to answer the following

# On-going average funding
ongoing_avg_funding = ongoing_df['usd_pledged'].mean()

# Concluded average funding
concluded_avg_funding = concluded_df['usd_pledged'].mean()

# On-going total backers
ongoing_total_backers = ongoing_df['usd_pledged'].sum()

# Concluded total backers
concluded_total_backers = concluded_df['usd_pledged'].sum()

# Objective 12.
print(f"The average funding for live projects: {ongoing_avg_funding}")
print(f"The average funding for successful projects: {concluded_avg_funding}")

print(f"The total number of backers for live projects: {ongoing_total_backers}")
print(f"The total number of backers for successful projects: {concluded_total_backers}")

# Objective 13.
# Using pandas helper methods, plot historgrams for each country.
# Do not change the order of these
import pylab as pl
pl.title('Country histogram')
concluded_df['country'].hist(grid=False, xlabelsize=9)
ongoing_df['country'].hist(grid=False)

Congratulations! You've completed this assignment 🎉
