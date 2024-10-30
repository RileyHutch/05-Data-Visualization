# 05-Data-Visualization

A study on the effects various medications on tumor size of mice.

For this project I relied heavily upon the work files in section 5 as well as the learning assistant.

I added NumPy because the the array in this section looked different and learning assistant recomended it as a fix.
    duplicate_mice = study_df[study_df.duplicated(subset=['Mouse ID', 'Timepoint'])]
    duplicate_ids = duplicate_mice['Mouse ID'].unique()
    duplicate_ids_array = np.array(duplicate_ids)
    duplicate_ids_array


There was a pandas cheatsheet that had equations and explinations of values like == !=

Used intro to sum. statistics to get most of this BUT the standard error of means we covered was giving errors and would have to be created then
merged in. This was how the learning assistant helped me calculate it all at once.


# A more advanced method to generate a summary statistics table of mean, median, variance, standard deviation,
# and SEM of the tumor volume for each regimen (only one method is required in the solution)

# Using the aggregation method, produce the same summary statistics in a single line
summary_stats = clean_study_df.groupby('Drug Regimen')['Tumor Volume (mm3)'].agg(
    Mean='mean',
    Median='median',
    Variance='var',
    STD='std',
    SEM=lambda x: np.std(x, ddof=1) / np.sqrt(len(x))
).reset_index()

summary_stats.set_index('Drug Regimen', inplace=True)
summary_stats.columns = summary_stats.columns.str.replace('_', ' ')

# used assistant for this. couldn't find an example in class files.

summary_stats.columns = pd.MultiIndex.from_tuples([('Tumor Volume (mm3)', col) for col in summary_stats.columns])

summary_stats

when getting down to the graphs for box plots, scatter and line I had to trouble shoot like crazy on learning assistant because of needing to convert back to df, panda vs pyplot 
and my graphs kept acting funny without errors so I couldn't tell if I was/am missing anything or if I have to update a program or something.

The slack channel also provided some help with the bar graph about sorting it in decending order.