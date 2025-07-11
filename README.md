 # The Analysis

 ## 1. What are the most demanded skills for the  top 3 most popular data roles?
 
To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here:
[2_Skills_Count_ipynb](2_Skills_Count.ipynb)

## Visualize Data 

```python

fig,ax = plt.subplots(len(job_titles),1)

sns.set_theme(style='ticks')

for i,job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short']==job_title].head(5)
    #df_plot.plot(kind='barh', x='job_skills', y='skills_percent', ax=ax[i], title=job_title)
    sns.barplot(data=df_plot, x='skills_percent', y='job_skills', ax=ax[i], hue="skill_count", palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 78)

    for n, v in enumerate(df_plot['skills_percent']):
        ax[i].text(v + 1, n , f'{v:.0f}%', va= 'center')

    if i != len(job_titles) - 1:
        ax[i].set_xticks([])    

fig.suptitle('Likelihood of Skills Requested in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=0.5)
plt.show()
```

## Results

![Visualization of Top Skills for Data Nerds](images\skills_demand.png)


## Insights
- SQL is the most requested skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles. For Data Engineers, Python is the most sought-after skill, appearing in 68% of job postings.
- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).
- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).


