import pandas as pd
import matplotlib.pyplot as plt
from scipy.stats import linregress

def draw_plot():
    # Read data from file
    df = pd.read_csv('epa-sea-level.csv')

    # Create scatter plot
    df.plot.scatter(x='Year', y='CSIRO Adjusted Sea Level')
    # Create first line of best fit
    x = df['Year']
    extend = pd.Series([2050])
    x = x.append(extend)
    y=df['CSIRO Adjusted Sea Level']
    slope, intercept, r_value, p_value, std_err = linregress(x,y)
    plt.plot(x, intercept + slope*x, label = 'Fitted Line 1')
    plt.plot(df['Year'], df['CSIRO Adjusted Sea Level'], 'o')
    plt.legend()
    plt.show()

    # Create second line of best fit
    x = df.loc[df['Year']>=2000, 'Year']
    print(x)
    y=df['CSIRO Adjusted Sea Level']
    extend = pd.Series([2050])
    x = x.append(extend)

    # Add labels and title
    plt.title('Rise in Sea Level')
    plt.xlabel('Years')
    plt.ylabel('Sea Level (inches)')
    plt.plot(x, intercept + slope*x, label = 'Fitted Line 1')
    plt.plot(df['Year'], df['CSIRO Adjusted Sea Level'], 'o')
    plt.legend()
    plt.show()
    
    # Save plot and return data for testing (DO NOT MODIFY)
    plt.savefig('sea_level_plot.png')
    return plt.gca()
