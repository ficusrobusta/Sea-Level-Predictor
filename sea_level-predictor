import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
from pandas.plotting import register_matplotlib_converters
register_matplotlib_converters()

# Import data (Make sure to parse dates. Consider setting index column to 'date'.)
df = pd.read_csv('fcc-forum-pageviews.csv', index_col=0, parse_dates=True, header=0)

# Clean data
df_clean = df[(df['value']>df['value'].quantile(0.025))&(df['value']<df['value'].quantile(0.975))]
       


def draw_line_plot():
    # Draw line plot
    fig = plt.figure(figsize=(12, 6))
    plt.plot(df_clean, color='red')
    plt.title("Daily freeCodeCamp Forum Page Views 5/2016-12/2019")
    plt.xlabel("Date")
    plt.ylabel('Page Views')




    # Save image and return fig (don't change this part)
    fig.savefig('line_plot.png')
    return fig

def draw_bar_plot():
    # Copy and modify data for monthly bar plot
    df_bar["month"] = df_clean.index.month
    df_bar["year"]  = df_clean.index.year
    df_bar = df_clean.groupby(["year","month"])["value"].mean().unstack()

    # Draw bar plot





    # Save image and return fig (don't change this part)
    fig.savefig('bar_plot.png')
    return fig

def draw_box_plot():
    # Prepare data for box plots (this part is done!)
    df_box = df.copy()
    df_box.reset_index(inplace=True)
    df_box['year'] = [d.year for d in df_box.date]
    df_box['month'] = [d.strftime('%b') for d in df_box.date]

    # Draw box plots (using Seaborn)

    ax = sns.boxplot(x=df_box['year'], y= df_box['value']).set_title('Year-wise Box Plot (Trend)')
    plt.xlabel('Year')
    plt.ylabel('Page Views')
    plt.ylim(2000,180000)

    ax = sns.boxplot(x=df_box['month'], y=df_box['value'], order=["Jan","Feb", "Mar", "Apr", "May","Jun","Jul","Aug", "Sep","Oct","Nov","Dec"]).set_title('Month-wise Box Plot (Seasonality)')
    plt.xlabel('Year')
    plt.ylabel('Page Views')
    plt.ylim(2000, 180000)


    # Save image and return fig (don't change this part)
    fig.savefig('box_plot.png')
    return fig

