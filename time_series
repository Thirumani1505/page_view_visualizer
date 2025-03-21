import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

def draw_line_plot():
    # Load data
    df = pd.read_csv("fcc-forum-pageviews.csv", index_col='date', parse_dates=True)
    
    # Clean data
    df = df[(df['value'] >= df['value'].quantile(0.025)) &
            (df['value'] <= df['value'].quantile(0.975))]
    
    # Draw line plot
    fig, ax = plt.subplots(figsize=(12, 6))
    ax.plot(df.index, df['value'], color='red', linewidth=1)
    ax.set_title("Daily freeCodeCamp Forum Page Views 5/2016-12/2019")
    ax.set_xlabel("Date")
    ax.set_ylabel("Page Views")
    
    return fig

def draw_bar_plot():
    # Load data
    df = pd.read_csv("fcc-forum-pageviews.csv", index_col='date', parse_dates=True)
    
    # Clean data
    df = df[(df['value'] >= df['value'].quantile(0.025)) &
            (df['value'] <= df['value'].quantile(0.975))]
    
    # Prepare data for bar plot
    df['year'] = df.index.year
    df['month'] = df.index.month_name()
    df_bar = df.groupby(['year', 'month'])['value'].mean().unstack()
    
    # Draw bar plot
    fig = df_bar.plot(kind='bar', figsize=(12, 6)).figure
    plt.xlabel("Years")
    plt.ylabel("Average Page Views")
    plt.legend(title="Months")
    
    return fig

def draw_box_plot():
    # Load data
    df = pd.read_csv("fcc-forum-pageviews.csv", index_col='date', parse_dates=True)
    
    # Clean data
    df = df[(df['value'] >= df['value'].quantile(0.025)) &
            (df['value'] <= df['value'].quantile(0.975))]
    
    # Prepare data for box plots
    df['year'] = df.index.year
    df['month'] = df.index.strftime('%b')
    df['month_num'] = df.index.month
    df = df.sort_values('month_num')
    
    # Draw box plots
    fig, axes = plt.subplots(1, 2, figsize=(15, 6))
    sns.boxplot(x='year', y='value', data=df, ax=axes[0]).set(title='Year-wise Box Plot (Trend)')
    sns.boxplot(x='month', y='value', data=df, ax=axes[1]).set(title='Month-wise Box Plot (Seasonality)')
    
    return fig
